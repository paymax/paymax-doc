## 目录

* [Paymax开发者指南](README.md#paymax%E5%BC%80%E5%8F%91%E8%80%85%E6%8C%87%E5%8D%97)
  * [关于Paymax](README.md#%E5%85%B3%E4%BA%8Epaymax)
  * [我们能做什么](README.md#%E6%88%91%E4%BB%AC%E8%83%BD%E5%81%9A%E4%BB%80%E4%B9%88)
  * [需要您做什么](README.md#%E9%9C%80%E8%A6%81%E6%82%A8%E5%81%9A%E4%BB%80%E4%B9%88)

* [快速开始](quick_start.md#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B)
  * [1\. 下载SDK](quick_start.md#1-%E4%B8%8B%E8%BD%BDsdk)
  * [2\. 集成开发](quick_start.md#2-%E9%9B%86%E6%88%90%E5%BC%80%E5%8F%91)
    * [服务器端集成](quick_start.md#%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E9%9B%86%E6%88%90)
    * [客户端集成](quick_start.md#%E5%AE%A2%E6%88%B7%E7%AB%AF%E9%9B%86%E6%88%90)

* [API文档](API文档.md#%E7%9B%AE%E5%BD%95)
  * [签名和验签](API文档.md#%E7%AD%BE%E5%90%8D%E5%92%8C%E9%AA%8C%E7%AD%BE)
      * [请求数据签名：](API文档.md#%E8%AF%B7%E6%B1%82%E6%95%B0%E6%8D%AE%E7%AD%BE%E5%90%8D)
      * [响应数据验签](API文档.md#%E5%93%8D%E5%BA%94%E6%95%B0%E6%8D%AE%E9%AA%8C%E7%AD%BE)
      * [注意事项](API文档.md#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
  * [支付](API文档.md#%E6%94%AF%E4%BB%98)
    * [发起支付（下单）](API文档.md#%E5%8F%91%E8%B5%B7%E6%94%AF%E4%BB%98%E4%B8%8B%E5%8D%95)
    * [查询支付](API文档.md#%E6%9F%A5%E8%AF%A2%E6%94%AF%E4%BB%98)
  * [退款](API文档.md#%E9%80%80%E6%AC%BE)
    * [发起退款](API文档.md#%E5%8F%91%E8%B5%B7%E9%80%80%E6%AC%BE)
    * [查询退款](API文档.md#%E6%9F%A5%E8%AF%A2%E9%80%80%E6%AC%BE)
    * [下载对账单](API文档.md#%E4%B8%8B%E8%BD%BD%E5%AF%B9%E8%B4%A6%E5%8D%95)
	* [发起下载](API文档.md#%E5%8F%91%E8%B5%B7%E4%B8%8B%E8%BD%BD)
	* [返回结果](API文档.md#%E8%BF%94%E5%9B%9E%E7%BB%93%E6%9E%9C)
  * [支付渠道编码](API文档.md#%E6%94%AF%E4%BB%98%E6%B8%A0%E9%81%93%E7%BC%96%E7%A0%81)
  * [支付渠道附加参数](API文档.md#%E6%94%AF%E4%BB%98%E6%B8%A0%E9%81%93%E9%99%84%E5%8A%A0%E5%8F%82%E6%95%B0)
      * [支付宝移动支付](API文档.md#%E6%94%AF%E4%BB%98%E5%AE%9D%E7%A7%BB%E5%8A%A8%E6%94%AF%E4%BB%98)
      * [微信移动支付](API文档.md#%E5%BE%AE%E4%BF%A1%E7%A7%BB%E5%8A%A8%E6%94%AF%E4%BB%98)
      * [Apple Pay](API文档.md#apple-pay)
      * [微信公众号](API文档.md#%E5%BE%AE%E4%BF%A1%E5%85%AC%E4%BC%97%E5%8F%B7)
      * [支付宝即时到账](API文档.md#%E6%94%AF%E4%BB%98%E5%AE%9D%E5%8D%B3%E6%97%B6%E5%88%B0%E8%B4%A6)
      * [拉卡拉 PC 网关支付](API文档.md#%E6%8B%89%E5%8D%A1%E6%8B%89-pc-%E7%BD%91%E5%85%B3%E6%94%AF%E4%BB%98)
      * [拉卡拉 PC 快捷支付](API文档.md#%E6%8B%89%E5%8D%A1%E6%8B%89-pc-%E5%BF%AB%E6%8D%B7%E6%94%AF%E4%BB%98)
      * [拉卡拉移动SDK支付](API文档.md#%E6%8B%89%E5%8D%A1%E6%8B%89%E7%A7%BB%E5%8A%A8sdk%E6%94%AF%E4%BB%98)
      * [拉卡拉 H5 支付](API文档.md#%E6%8B%89%E5%8D%A1%E6%8B%89-h5-%E6%94%AF%E4%BB%98)
  * [关于下载对账单的说明](API文档.md#%E5%85%B3%E4%BA%8E%E4%B8%8B%E8%BD%BD%E5%AF%B9%E8%B4%A6%E5%8D%95%E7%9A%84%E8%AF%B4%E6%98%8E)
  * [关于退款的说明](API文档.md#%E5%85%B3%E4%BA%8E%E9%80%80%E6%AC%BE%E7%9A%84%E8%AF%B4%E6%98%8E)
  * [响应错误码](API文档.md#%E5%93%8D%E5%BA%94%E9%94%99%E8%AF%AF%E7%A0%81)

* [人脸识别接口文档](人脸识别.md#%E4%BA%BA%E8%84%B8%E8%AF%86%E5%88%AB%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3)
  * [查询用户识别信息](人脸识别.md#%E6%9F%A5%E8%AF%A2%E7%94%A8%E6%88%B7%E8%AF%86%E5%88%AB%E4%BF%A1%E6%81%AF)
  * [响应错误码](人脸识别.md#%E5%93%8D%E5%BA%94%E9%94%99%E8%AF%AF%E7%A0%81)

* 交易流程和接入流程
  * [交易流程](流程.md)
    * [支付流程](流程.md#%E6%94%AF%E4%BB%98%E6%B5%81%E7%A8%8B)
    * [退款流程](流程.md#%E9%80%80%E6%AC%BE%E6%B5%81%E7%A8%8B)
  * [扫码支付流程（C扫B）](扫码支付流程（C扫B）.md#%E6%89%AB%E7%A0%81%E6%94%AF%E4%BB%98%E6%B5%81%E7%A8%8Bc%E6%89%ABb)
  * [移动APP支付流程](移动APP支付流程.md#%E7%A7%BB%E5%8A%A8app%E6%94%AF%E4%BB%98%E6%B5%81%E7%A8%8B)
  * [PC网页、移动网页支付流程](PC网页、移动网页支付流程.md#pc%E7%BD%91%E9%A1%B5%E7%A7%BB%E5%8A%A8%E7%BD%91%E9%A1%B5%E6%94%AF%E4%BB%98%E6%B5%81%E7%A8%8B)
  * [微信公众号支付对接流程](微信公众号支付对接流程.md#%E5%BE%AE%E4%BF%A1%E5%85%AC%E4%BC%97%E5%8F%B7%E6%94%AF%E4%BB%98%E5%AF%B9%E6%8E%A5%E6%B5%81%E7%A8%8B)
    * [第一步、获取用户openid](微信公众号支付对接流程.md#%E7%AC%AC%E4%B8%80%E6%AD%A5%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7openid)
      * [前提条件：OAuth2\.0网页授权](微信公众号支付对接流程.md#%E5%89%8D%E6%8F%90%E6%9D%A1%E4%BB%B6oauth20%E7%BD%91%E9%A1%B5%E6%8E%88%E6%9D%83)
      * [获取openid方法](微信公众号支付对接流程.md#%E8%8E%B7%E5%8F%96openid%E6%96%B9%E6%B3%95)
    * [第二步、下单](微信公众号支付对接流程.md#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E4%B8%8B%E5%8D%95)
    * [第三步、调出支付控件](微信公众号支付对接流程.md#%E7%AC%AC%E4%B8%89%E6%AD%A5%E8%B0%83%E5%87%BA%E6%94%AF%E4%BB%98%E6%8E%A7%E4%BB%B6)
      * [前提条件：公众号支付授权目录设置成功](微信公众号支付对接流程.md#%E5%89%8D%E6%8F%90%E6%9D%A1%E4%BB%B6%E5%85%AC%E4%BC%97%E5%8F%B7%E6%94%AF%E4%BB%98%E6%8E%88%E6%9D%83%E7%9B%AE%E5%BD%95%E8%AE%BE%E7%BD%AE%E6%88%90%E5%8A%9F)
      * [调用支付控件方法](微信公众号支付对接流程.md#%E8%B0%83%E7%94%A8%E6%94%AF%E4%BB%98%E6%8E%A7%E4%BB%B6%E6%96%B9%E6%B3%95)
    * [第四步、处理支付结果](微信公众号支付对接流程.md#%E7%AC%AC%E5%9B%9B%E6%AD%A5%E5%A4%84%E7%90%86%E6%94%AF%E4%BB%98%E7%BB%93%E6%9E%9C)

* [webhooks通知](webhooks通知.md#webhooks%E9%80%9A%E7%9F%A5)
  * [什么是webhooks通知？](webhooks通知.md#%E4%BB%80%E4%B9%88%E6%98%AFwebhooks%E9%80%9A%E7%9F%A5)
  * [如何订阅](webhooks通知.md#%E5%A6%82%E4%BD%95%E8%AE%A2%E9%98%85)
  * [可靠通知规则](webhooks通知.md#%E5%8F%AF%E9%9D%A0%E9%80%9A%E7%9F%A5%E8%A7%84%E5%88%99)
  * [通知格式](webhooks通知.md#%E9%80%9A%E7%9F%A5%E6%A0%BC%E5%BC%8F)
  * [如何验签](webhooks通知.md#%E5%A6%82%E4%BD%95%E9%AA%8C%E7%AD%BE)

* SDK接入指南
  * [iOS SDK 接入指南](iOS SDK.md#ios-sdk-%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97)
    * [安装](iOS SDK.md#%E5%AE%89%E8%A3%85)
        * [手动导入](iOS SDK.md#%E6%89%8B%E5%8A%A8%E5%AF%BC%E5%85%A5)
    * [调用支付](iOS SDK.md#%E8%B0%83%E7%94%A8%E6%94%AF%E4%BB%98)
    * [接收并处理交易结果](iOS SDK.md#%E6%8E%A5%E6%94%B6%E5%B9%B6%E5%A4%84%E7%90%86%E4%BA%A4%E6%98%93%E7%BB%93%E6%9E%9C)
    * [注意事项](iOS SDK.md#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
  * [Paymax Android SDK 使用文档](Android SDK.md#paymax-android-sdk-%E4%BD%BF%E7%94%A8%E6%96%87%E6%A1%A3)
    * [一、下载](Android SDK.md#%E4%B8%80%E4%B8%8B%E8%BD%BD)
    * [二、快速体验](Android SDK.md#%E4%BA%8C%E5%BF%AB%E9%80%9F%E4%BD%93%E9%AA%8C)
    * [三、快速集成](Android SDK.md#%E4%B8%89%E5%BF%AB%E9%80%9F%E9%9B%86%E6%88%90)
      * [导入 Paymax SDK](Android SDK.md#%E5%AF%BC%E5%85%A5-paymax-sdk)
        * [Android Studio](Android SDK.md#android-studio)
        * [权限声明](Android SDK.md#%E6%9D%83%E9%99%90%E5%A3%B0%E6%98%8E)
        * [注册 activity](Android SDK.md#%E6%B3%A8%E5%86%8C-activity)
    * [四、获得 Charge](Android SDK.md#%E5%9B%9B%E8%8E%B7%E5%BE%97-charge)
    * [五、发起支付](Android SDK.md#%E4%BA%94%E5%8F%91%E8%B5%B7%E6%94%AF%E4%BB%98)
      * [六、获取支付状态](Android SDK.md#%E5%85%AD%E8%8E%B7%E5%8F%96%E6%94%AF%E4%BB%98%E7%8A%B6%E6%80%81)
    * [注意事项](Android SDK.md#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
    * [混淆设置](Android SDK.md#%E6%B7%B7%E6%B7%86%E8%AE%BE%E7%BD%AE)
    * [日志开关](Android SDK.md#%E6%97%A5%E5%BF%97%E5%BC%80%E5%85%B3)
* 工具
  * [生成RSA公私钥](rsa_generate.md#%E7%94%9F%E6%88%90rsa%E5%85%AC%E7%A7%81%E9%92%A5)
    * [Linux用户(以Mac为例)](rsa_generate.md#linux%E7%94%A8%E6%88%B7%E4%BB%A5mac%E4%B8%BA%E4%BE%8B)
    * [Windows用户](rsa_generate.md#windows%E7%94%A8%E6%88%B7)
    * [RSA样例](rsa_generate.md#rsa%E6%A0%B7%E4%BE%8B)


## Paymax开发者指南

### 关于Paymax
Paymax为您提供一站式集成化支付接入解决方案，通过Paymax的SDK，您可轻松连接任意Paymax支持的支付渠道，并通过交易管理平台监控、管理已开通渠道的所有交易。


### 我们能做什么

**Paymax能够帮您：**
​	
* 便捷的接入各主流支付渠道
* 在后台统一管理所有支付渠道交易信息
* 可视化的统计分析功能

**我们支持的支付渠道：**

* Apple Pay
* 微信移动支付
* 微信公众号支付
* 支付宝移动支付
* 支付宝即时到账
* 拉卡拉移动 SDK 支付
* 拉卡拉 PC 网关支付
* 拉卡拉 PC 快捷支付

**我们支持的开发语言：**
​	
服务器端接口方面，我们提供了基于HTTP协议的Web接口，因此理论上来说，任何语言都可以接入Paymax服务。同时我们提供Server SDK，方便您的服务器端集成Paymax服务；下载地址：
​	
* [下载Server SDK Java版](https://github.com/paymax/paymax-server-sdk-java/archive/master.zip)
* [下载Server SDK PHP版](https://github.com/paymax/paymax-server-sdk-php/archive/master.zip)
* [下载Server SDK C#版](https://github.com/paymax/paymax-server-sdk-csharp/archive/master.zip)
* [下载Server SDK NodeJS版](https://github.com/paymax/paymax-server-sdk-nodejs/archive/master.zip)
* [下载Server SDK Python版](https://github.com/paymax/paymax-server-sdk-python/archive/master.zip)
* Ruby 开发中
* Go 开发中

同时我们提供了Client SDK，方便您在自己的APP中集成Paymax支付服务；Client SDK现在有iOS和Android版本，请根据您的APP平台选择相应的开发包。
​	
* [下载Android SDK](https://github.com/paymax/paymax-demo-android/archive/master.zip)
* [下载iOS SDK](https://github.com/paymax/paymax-demo-ios/archive/master.zip)


### 需要您做什么

如果您已经通过Paymax成功代申请了支付渠道或者自行申请过我们支持的支付渠道，您只需要通过一些简单的技术接入，即可实现相应的支付能力。

接入之前，您可以先简单了解一下我们的业务流程：[交易流程](流程.md)

接下来可以参考我们的“[快速接入指南](quick_start.md)”，使用我们的SDK快速完成对Paymax的集成。

如果您的服务器语言暂时不在我们的支持列表，您可以参考“[API文档](API文档.md)”自行完成对Paymax的接入。
