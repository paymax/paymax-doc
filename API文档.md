## 签名和验签

1. https传输协议
2. 数据使用RSA签名和验签

签名生成方法： 
我们采用的签名方式是对HTTP请求的请求体签名，并将签名值放入Header中，key为sign。

假如请求体为：

```javascript
{
	"order_no":"paymax-11110002",
	"amount":2.01,
	"subject":"test",
	"body":"test",
	"channel":"alipay_app",
	"app":"app_kdjksldf93oksd923oks",
	"client_ip":"127.0.0.1"
}
```

需要将请求体以UTF-8编码转换成字节数组，然后使用商户私钥对其签名，签名算法为SHA1WithRSA。并将签名结果和Secret Key分别放入HTTP请求的Header中，例如：

```http
POST /v1/charges HTTP/1.1
Host: https://www.paymax.cc/merchant-api
ContentType: application/json
Authorization: {填入Secret Key}
sign: {填入签名结果}
```


## 支付

支付订单相关的要素通过Charge对象来承载。


**Charge对象结构：**

| 参数              | 类型      | 描述                                       |
| :-------------- | ------- | ---------------------------------------- |
| id              | String  | 支付订单id，系统内唯一，以“ch_”开头，后跟24位随机数           |
| order_no        | String  | 商户订单号，在商户系统内唯一，8-20位数字或字母，不允许特殊字符        |
| amount          | Decimal | 订单总金额，大于0的数字，单位是该币种的货币单位                 |
| subject         | String  | 购买商品的标题，最长32位                            |
| body            | String  | 购买商品的描述信息，最长128个字符                       |
| channel         | String  | 支付渠道编码，唯一标识一个支付渠道，参考[支付渠道编码](#支付渠道编码)    |
| client_ip       | String  | 发起支付的客户端IP                               |
| description     | String  | 订单备注，限制300个字符内                           |
| extra           | Map     | 特定渠道需要的的额外附加参数，参考[支付渠道附加参数](#支付渠道附加参数)   |
| transaction_no  | String  | 支付渠道订单号                                  |
| metadata        | Map     | 用户自定义元数据                                 |
| app             | String  | 应用的appKey                                |
| amount_settle   | Decimal | 已结算金额                                    |
| amount_refunded | Decimal | 已退款金额                                    |
| currency        | String  | 三位ISO货币代码，只支持人民币cny，默认cny                |
| refunded        | Boolean | 是否已经开始退款                                 |
| refunds         | List    | 退款记录                                     |
| time_created    | Long    | 订单创建时间，13位Unix时间戳                        |
| time_paid       | Long    | 订单支付完成时间，13位Unix时间戳                      |
| time_expire     | Long    | 订单失效时间，13位Unix时间戳                        |
| time_settle     | Long    | 订单结算时间，13位Unix时间戳                        |
| credential      | String  | 支付凭据，用于调起支付APP或者跳转支付网关                   |
| livemode        | Boolean | 是否是生产模式                                  |
| status          | String  | 订单状态，只有三种（PROCESSING-处理中，SUCCEED-成功，FAILED-失败） |
| failure_code    | String  | 订单的错误码，详见ERROR说明                         |
| failure_msg     | String  | 订单的错误消息的描述                               |



### 发起支付

使用HTTP协议调用支付接口发起请求：


```http
POST /v1/charges HTTP/1.1
Host: https://www.paymax.cc/merchant-api
ContentType: application/json
Authorization: {SECRET_KEY}
sign: {sign}
```

请求参数：

| 参数          | 类型      | 必须    | 描述                                       |
| :---------- | ------- | ----- | ---------------------------------------- |
| order_no    | String  | true  | 商户订单号，在商户系统内唯一，8-20位数字或字母，不允许特殊字符        |
| amount      | Decimal | true  | 订单总金额，大于0的数字，单位是该币种的货币单位                 |
| subject     | String  | true  | 购买商品的标题，最长32位                            |
| body        | String  | true  | 购买商品的描述信息，最长128个字符                       |
| channel     | String  | true  | 支付渠道编码，唯一标识一个支付渠道，参考[支付渠道编码](#支付渠道编码)    |
| app         | String  | true  | 应用的appKey                                |
| client_ip   | String  | true  | 发起支付的客户端IP                               |
| description | String  | false | 订单备注，限制300个字符内                           |
| time_expire | Long    | false | 订单失效时间，13位Unix时间戳，默认1小时，微信公众号支付对其的限制为3分钟 |
| currency    | String  | false | 三位ISO货币代码，只支持人民币cny，默认cny                |
| extra       | Map     | false | 特定渠道需要的的额外附加参数，参考[支付渠道附加参数](#支付渠道附加参数)   |
| metadata    | Map     | false | 用户自定义元数据                                 |



返回：

Charge对象


### 查询支付

```http
GET /v1/charges/{CHARGE_ID} HTTP/1.1
Host: https://www.paymax.cc/merchant-api
ContentType: application/json
Authorization: {SECRET_KEY}
sign: {sign}
```

返回：

Charge对象


## 退款

退款订单相关的要素通过Refund对象来承载。各个渠道对于退款的处理有一定的差异，具体请参考[关于退款的说明](#关于退款的说明)。

**Refund对象结构：**

| 参数             | 类型      | 描述                                       |
| :------------- | ------- | ---------------------------------------- |
| id             | String  | 退款订单id，系统内唯一，以“re_”开头，后跟24位随机数           |
| order_no       | String  | 商户订单号，在商户系统内唯一，8-20位数字或字母，不允许特殊字符        |
| charge         | String  | 退款订单对应的支付订单id                            |
| amount         | Decimal | 退款订单总金额，大于0的数字，单位是该币种的货币单位               |
| description    | String  | 退款备注，限制300个字符内                           |
| extra          | Map     | 特定渠道需要的的额外附加参数以及特定渠道的额外返回值，具体请参考[支付渠道附加参数](#支付渠道附加参数)和参考[关于退款的说明](#关于退款的说明) |
| transaction_no | String  | 支付渠道退款订单号                                |
| metadata       | Map     | 用户自定义元数据                                 |
| time_created   | Long    | 订单创建时间，13位Unix时间戳                        |
| time_succeed   | Long    | 订单退款完成时间，13位Unix时间戳                      |
| status         | String  | 订单状态，只有三种（PROCESSING-处理中，SUCCEED-成功，FAILED-失败） |
| failure_code   | String  | 订单的错误码，详见ERROR说明                         |
| failure_msg    | String  | 订单的错误消息的描述                               |


### 发起退款

使用HTTP协议调用退款接口发起请求：

```http
POST /v1/charges/{CHARGE_ID}/refunds HTTP/1.1
Host: https://www.paymax.cc/merchant-api
ContentType: application/json
Authorization: {SECRET_KEY}
sign: {sign}
```

请求参数：

| 参数          | 类型      | 必须    | 描述           |
| :---------- | ------- | ----- | ------------ |
| amount      | Decimal | false | 退款金额，默认为全额退款 |
| metadata    | Map     | false | 用户自定义元数据     |
| description | String  | true  | 退款原因和描述      |

返回：

Refund对象

### 查询退款

```http
GET /v1/charges/{CHARGE_ID}/refunds/{REFUND_ID} HTTP/1.1
Host: https://www.paymax.cc/merchant-api
ContentType: application/json
Authorization: {SECRET_KEY}
sign: {sign}
```

返回：

Refund对象



## 支付渠道编码

| 渠道         | 编码            |
| :--------- | :------------ |
| 支付宝移动支付    | alipay_app    |
| 微信移动支付     | wechat_app    |
| Apple Pay  | apple_pay_app |
| 微信公众号      | wechat_wap    |
| 支付宝即时到账    | alipay_web    |
| 拉卡拉PC端支付   | lakala_web    |
| 拉卡拉移动SDK支付 | lakala_app    |



## 支付渠道附加参数

| 渠道         | 附加参数                                     | 示例                                       |
| :--------- | :--------------------------------------- | :--------------------------------------- |
| 支付宝移动支付    | 无                                        |                                          |
| 微信移动支付     | 无                                        |                                          |
| Apple Pay  | 无                                        |                                          |
| 微信公众号      | 无                                        |                                          |
| 支付宝即时到账    | 无                                        |                                          |
| 拉卡拉PC端支付   | user_id: 必填，用户在商户系统中的唯一标识；               | {"user_id":"aaa111"}                     |
| 拉卡拉移动SDK支付 | user_id: 必填，用户在商户系统中的唯一标识；<br>return_url: 必填，支付完成后的回调地址； | {"user_id":"aaa111","return_url":"http://www.abc.cn/"} |



## 关于退款的说明

各个渠道对于退款的处理有一定的差异，主要包括两种形式：

1. 需要商户手动确认的退款

   支付宝：商户发起支付宝退款申请后，如果申请提交成功，Paymax会返回一个status为PROCESSING的refund对象，会在extra参数中有一个refundUrl参数，值为需要用户手动确认的退款URL地址。

2. 不需要商户手动确认的退款

   除了支付宝之外，其他的渠道进行退款都不需要用户手动确认，Paymax会在退款状态发生改变时发送Webhooks通知。