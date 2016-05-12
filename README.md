## Paymax开发者指南

### 关于Paymax
Paymax为您提供一站式集成化支付接入解决方案，通过Paymax的SDK，您可轻松连接任意Paymax支持的支付渠道，并通过交易管理平台监控、管理已开通渠道的所有交易。


### 我们能做什么

**Paymax能够帮您：**
	
* 便捷的接入各主流支付渠道
* 在后台统一管理所有支付渠道交易信息
* 可视化的统计分析功能

**我们支持的支付渠道：**

* Apple Pay
* 微信移动支付
* 微信公众号支付
* 支付宝移动支付
* 支付宝即时到账

**我们支持的开发语言：**
	
服务器端接口方面，我们提供了基于HTTP协议的Web接口，因此理论上来说，任何语言都可以接入Paymax服务。同时我们提供Server SDK，方便您的服务器端集成Paymax服务；现在只提供Java语言版的Server SDK，其他语言的版本正在开发中。
	
[下载Server SDK Java版](https://github.com/paymax/paymax-server-sdk-java/archive/master.zip)
	
同时我们提供了Client SDK，方便您在自己的APP中集成Paymax支付服务；Client SDK现在有iOS和Android版本，请根据您的APP平台选择相应的开发包。
	
[下载Android SDK](https://github.com/paymax/paymax-demo-android/archive/master.zip)
[下载iOS SDK](https://github.com/paymax/paymax-demo-ios/archive/master.zip)
	

### 需要您做什么

如果您已经通过Paymax成功代申请了支付渠道或者自行申请过我们支持的支付渠道，您只需要通过一些简单的技术接入，即可实现相应的支付能力。

接入之前，您可以先简单了解一下我们的业务流程：[交易流程](流程.md)

接下来可以参考我们的“[快速接入指南](quick_start.md)”，使用我们的SDK快速完成对Paymax的集成。

如果您的服务器语言暂时不在我们的支持列表，您可以参考“[API文档](API文档.md)”自行完成对Paymax的接入。
