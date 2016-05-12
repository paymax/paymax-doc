# iOS SDK 接入指南

## 安装
#### 手动导入
1.下载iOS SDK开发包，将lib目录下的文件添加到你的项目
	iOS SDK下载地址：https://github.com/paymax/paymax-doc/tree/master/sdk

2.依赖 Frameworks：
>必需：

>CFNetwork.framework

>SystemConfiguration.framework

>Security.framework

>libc++.dylib

>libz.dylib

>libsqlite3.0.dylib

3.添加 URL Schemes：在 Xcode 中，选择你的工程设置项，选中 TARGETS 一栏，在 Info 标签栏的 URL Types 添加 URL Schemes，如果使用微信，填入微信平台上注册的应用程序 id（为 wx 开头的字符串），如果不使用微信，则自定义，建议起名稍复杂一些，尽量避免与其他程序冲突。允许英文字母和数字，首字母必须是英文字母，不允许特殊字符。
![](https://pay.weixin.qq.com/wiki/doc/api/img/chapter8_5_1.png)

## 调用支付
###### 客户端从服务器端拿到支付要素后，调用下面的方法
```/**
 *  支付接口
 *
 *  @param charge           支付要素
 *  @param schemeStr        调用支付的app注册在info.plist中的scheme
 *  @param complethionBlock 支付结果回调Block
 */
[PayRightSDK pay:responseObject
       appScheme:kappScheme
      completion:^(PayRightBack *payRightBack) {

      switch (payRightBack.explain) {
                              case PayRight_CODE_SUCCESS:
                                  NSLog(@"成功");
                                  break;
                              case PayRight_CODE_FAIL_CANCEL:
                                  NSLog(@"用户取消支付");
                                  break;
                              case PayRight_CODE_ERROR_DEAL:
                                  NSLog(@"处理中");
                                  break;
                              case PayRight_CODE_Failure:
                                  NSLog(@"支付失败");
                                  break;
                              case PayRight_CODE_ERROR_CONNECT:
                                  NSLog(@"网络错误");
                                  break;
                              case PayRight_CODE_ChannelWrong:
                                  NSLog(@"渠道信息错误");
                                  break;
                              case PayRight_CODE_ERROR_CHARGE_PARAMETER:
                                  NSLog(@"参数信息错误");
                                  break;
                              case PayRight_CODE_ERROR_WX_NOT_INSTALL:
                                  NSLog(@"未安装微信");
                                  break;
                              case PayRight_CODE_ERROR_WX_NOT_SUPPORT_PAY:
                                  NSLog(@"微信不支持");
                                  break;
                              case PayRight_CODE_ERROR_WX_UNKNOW:
                                  NSLog(@"微信未知错误");
                                  break;
                          }
NSLog(@"payRightBack.channelBackCode=%@\npayRightBack.channel=%@\npayRightBack.backDescription=%@\npayRightBack.prCode=%ld",payRightBack.channelBackCode,payRightBack.channel,payRightBack.backDescription,(long)payRightBack.prCode);
}];                
                

         
```
## 接收并处理交易结果
###### 渠道为微信、支付宝且安装了支付宝钱包，请在AppDelegate.m里实现下面的方法

```
// iOS 8 及以下请用这个
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
    
    return [PayRightSDK handleOpenURL:url withCompletion:^(PayRightBack *payRightBack) {
        NSLog(@"AppDelegate----------payRightBack.channelBackCode=%@\npayRightBack.channel=%@\npayRightBack.backDescription=%@\npayRightBack.prCode=%ld",payRightBack.channelBackCode,payRightBack.channel,payRightBack.backDescription,(long)payRightBack.prCode);
    }];

}

// iOS 9 以上请用这个
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary *)options {
    
    return [PayRightSDK handleOpenURL:url withCompletion:^(PayRightBack *payRightBack) {
        NSLog(@"AppDelegate-----------payRightBack.channelBackCode=%@\npayRightBack.channel=%@\npayRightBack.backDescription=%@\npayRightBack.prCode=%ld",payRightBack.channelBackCode,payRightBack.channel,payRightBack.backDescription,(long)payRightBack.prCode);
        
    }];
}
```
###### 错误返回
```
    PayRight_CODE_SUCCESS,                  /**< 成功*/
    PayRight_CODE_FAIL_CANCEL,              /**< 用户取消支付*/
    PayRight_CODE_ERROR_DEAL,               /**< 处理中*/
    PayRight_CODE_Failure,                  /**< 失败*/
    PayRight_CODE_ERROR_CONNECT,            /**< 网络错误*/
    PayRight_CODE_ChannelWrong,             /**< 渠道信息错误*/
    PayRight_CODE_ERROR_CHARGE_PARAMETER,   /**< 参数信息错误*/
    PayRight_CODE_ERROR_WX_NOT_INSTALL,     /**< 未安装微信*/
    PayRight_CODE_ERROR_WX_NOT_SUPPORT_PAY  /**< 微信不支持*/
    PayRight_CODE_ERROR_WX_UNKNOW           /**< 微信未知错误*/
```




## 注意事项

1.

针对使用 Xcode 7 编译失败，遇到错误信息为：
XXXXXXX does not contain bitcode. You must rebuild it with bitcode enabled (Xcode setting ENABLE_BITCODE), obtain an updated library from the vendor, or disable bitcode for this target.

请到 Xcode 项目的 Build Settings 标签页搜索 bitcode，将 Enable Bitcode 设置为 NO 即可。


2.

针对 iOS 9 限制 http 协议的访问，如果 App 需要访问 http://， 则需要在 Info.plist 添加如下代码：

```
在Info.plist中添加NSAppTransportSecurity类型Dictionary。
在NSAppTransportSecurity下添加NSAllowsArbitraryLoads类型Boolean,值设为YES
```
3.
如果微信支付完成后无法跳回到自己的APP可能是获取到的APPID与URL Types里添加 的URL Schemes不同

4.
在plist里添加微信的白名单
LSApplicationQueriesSchemes NSArray
