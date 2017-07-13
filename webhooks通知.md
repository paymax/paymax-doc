##webhooks通知


###什么是webhooks通知？
通过配置 webhooks，商户可订阅需要的事件，当这些事件发生时，Paymax会将对应的事件消息推送到商户指定的地址。Paymax现支持如下webhooks：</br>

* 支付结果通知
* 退款结果通知


###如何订阅
1. 从应用列表里点击某应用

![应用中心](image/app_center.png) 

2. 点击左侧导航中webhooks

![](image/app_preview_webhooks.png)

3. 点击右上角添加按钮，开始添加webhooks

![](image/add_webhooks.png)


###可靠通知规则
由于网络等原因，商户可能未接收或未正常处理webhooks通知，Paymax会通过一定重发机制来保证通知的可靠性。

Paymax是否重发，取决于商户收到通知后response的结果是否为success字符串。若不是，才会按照一定机制重发，直到收到success为止。

当然，Paymax重发的时间间隔也会随着重发次数逐步变长。

对后台通知交互时，如果Paymax收到商户的应答不是成功或超时（正常的response是：http code 200 && content 为 success），Paymax认为通知失败，在36小时之内，一共发送17次，第一次发送失败之后，之后每次发送的间隔为：2s,4s,8s,16s,32s,64s,128s,256s,512s,1024s,2048s,4096s,8192s,16384s,32768s,65536s


###通知格式

**支付示例**

```

 {
    "data":{
        "amount":7,
        "amount_refunded":0,
        "amount_settle":0,
        "body":"测试商品",
        "client_ip":"120.197.202.48",
        "credential":{
            "wechat_wap":{
                "jsApiParams":"{"appId":"wxbtest9e022e2d07","timeStamp":"1478361807","signType":"MD5","package":"prepay_id=test211060003265e6f4f86970458446dd081","nonceStr":"06ZSHzTTeswakmu4","paySign":"BB4706E3F97174AAC1341F25dssw88DA16"}"
            }
        },
        "currency":"CNY",
        "description":"测试商品描述信息",
        "extra":{
            "terminal_id":"9223131",
            "open_id":"oOOL0jdyiLwslASo7UmSwrtOCW4k",
            "merchant_id":"8221023420011716"
        },
        "id":"ch_5d0eca3b8f707ed425122e56",
        "livemode":false,
        "metadata":{
            "callbackUrl":"http://www.demo.com"
        },
        "order_no":"ch_828d6ef97f3c45a3acd41a59",
        "refunds":[

        ],
        "status":"SUCCEED",
        "subject":"测试商品标题",
        "time_created":1478361807000,
        "time_expire":1478362046272,
        "time_paid":1478361806000,
        "transaction_no":"4004512001201611068876533536"
    },
    "notifyNo":"evt_7fb2378f457ewerwa9afe17a942ae389e",
    "timeCreated":1478361840304,
    "type":"CHARGE"
}
```
**退款示例**

```

 {
    "data":{
        "amount":0.01,
        "charge":"ch_6abba29e41edddd8b062dab",
        "description":"协商一致退款",
        "extra":{
            "refundUrl":"http://www.demo.com/gateway.do?sign=251af6477bxxxxxxx"
        },
        "id":"re_06cfeewewe4dc14de10fe",
        "metadata":{
            "use_id":"12345678"
        },
        "order_no":"06cf59c008b004dc14de10fe",
        "status":"SUCCEED",
        "time_created":1478518692000,
        "time_succeed":1478518705000,
        "transaction_no":"2016110721001004480236849549"
    },
    "notifyNo":"evt_eff98bb453f0429b9b8fd5adfasdfc7c9",
    "timeCreated":1478518708532,
    "type":"REFUND"
}
```
**参数说明**

| 参数          | 类型                 | 描述                                       |
| ----------- | ------------------ | ---------------------------------------- |
| data        | Charge对象或者Refund对象 | 详情见 [API文档](API文档.md#支付) 中对Charge对象、Refund对象的说明 |
| notifyNo    | String             | 通知事件唯一标识                                 |
| timeCreated | Long               | 时间戳，自1970年以后的毫秒数                         |
| type        | String             | 通知类型，共以下几种:<br/> CHARGE : 支付 <br/> REFUND : 退款 |



###如何验签

每一次事件通知，Paymax都会对request body整体做签名，并将签名后的结果放request header中，header名称sign。

签名算法为SHA1WithRSA，签名时会使用Paymax官方私钥做签名，所以商户验签时需要用Paymax官方公钥来做验签。

Paymax官方公钥可通过商户后台“开发信息”中获取。





