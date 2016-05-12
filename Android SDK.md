## PayRight Android SDK 使用文档

### 一、下载

Android SDK下载地址：https://github.com/swwx-payright/payright-doc/tree/master/sdk

下载Android SDK，下载列表如下包含：

![下载列表](https://raw.githubusercontent.com/coderbook/MarkDownRes/master/PayRightPic/payright_sdk_android_dir.png)



### 二、快速体验

PayRight SDK 为开发者提供了demo 程序，可以快速体验 PayRight 接入流程。下载 PayRight SDK 之后将整个目录导入到您的 Android Studio 中。

使用 Android Studio 时，请选择 `File` → `Open...`→ `PayRightDemo` 

<div align="center">
<img src="https://raw.githubusercontent.com/coderbook/MarkDownRes/master/PayRightPic/payright_sdk_android_files.png" width = "400" height = "400" alt="图片名称" align=center />
</div>



### 三、快速集成

#### 导入 PayRight SDK

##### Android Studio

1. 在你的项目里创建 `libs` 目录:将项目切换到project模式，定位到你的module，右击 `New` → `Directory`→ 输入 `libs`→ `OK` 
2. 将下载的  `payRightSDK.jar` 复制、粘贴到 `libs` 目录
3. 同时将下载的微信 `libammsdk.jar` 、支付宝 `alipaySdk-20160223` 官方jar文件复制、粘贴到 `libs` 目录
4. 找到module的 `build.gradle` → `dependencies` 填写
  
   
         compile fileTree(dir: 'libs', include: ['*.jar'])  




##### 权限声明


    <!--微信和支付宝公共权限-->
    <uses-permission android:name="android.permission.INTERNET" />
    <!--微信所需权限-->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <!--支付宝所需权限-->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />




##### 注册 activity



     <!-- 注册微信 -->
       <activity
            android:name="com.swwx.payright.PaymentActivity"
            android:launchMode="singleTop"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" />

       <activity-alias
            android:name=".wxapi.WXPayEntryActivity"
            android:exported="true"
            android:targetActivity="com.suwx.payright.PaymentActivity" />

     <!-- 注册支付宝 -->
        <activity
            android:name="com.alipay.sdk.app.H5PayActivity"
            android:configChanges="orientation|keyboardHidden|navigation|screenSize"
            android:exported="false"
            android:screenOrientation="behind"
            android:windowSoftInputMode="adjustResize|stateHidden" >
        </activity>



### 四、获得 Charge
Charge 对象是一个包含支付信息的 JSON 对象，是 `PayRight SDK` 发起支付的必要参数。该参数需要请求用户服务器获得，服务端生成 charge 的方式参考 [PayRight 官方文档]。SDK 中的 demo 里面提供了如何获取 charge 的实例方法，供用户参考。

### 五、发起支付
 

    /**
     * 发起支付
     * @param activity
     * @param charge   与服务器交互后的充值要素
     * @param callback  充值结果回调接口
     */

    PayRightSDK.pay(Activity activity, String charge, PayRightCallback callback);

    
#### 六、获取支付状态
从 `PayRightCallback` 的 `onPayFinished()` 方法中获得支付结果。支付成功后，用户服务器也会收到PayRight 服务器发送的异步通知。 最终支付成功请根据服务端异步通知为准。



    @Override
     public void onPayFinished(PayResult result) {
        String msg = "Unknow";
        switch (result.getCode()) {
            case PayRight.CODE_SUCCESS:
                //支付成功
                msg = "Complete, Success!";
                break;

            case PayRight.CODE_ERROR_CHARGE_JSON:
                //非空格式
                msg = "charge string isn't a json string error.";
                break;

            case PayRight.CODE_FAIL_CANCEL:
                //用户取消
                msg = "cancel pay.";
                break;

            case PayRight.CODE_ERROR_CHARGE_PARAMETER:
                //字段不全
                msg = "some charge paramters error.";
                break;

            case PayRight.CODE_ERROR_WX_NOT_INSTALL:
                //微信未安装
                msg = "wx not install.";
                break;

            case PayRight.CODE_ERROR_WX_NOT_SUPPORT_PAY:
                //微信版本不支持
                msg = "ex not support pay.";
                break;

            case PayRight.CODE_ERROR_WX_UNKNOW:
                //微信未知错误
                msg = "wechat failed.";
                break;

            case PayRight.CODE_ERROR_ALI_DEAL:
                //支付宝正在处理中
                msg = "alipay dealing.";
                break;

            case PayRight.CODE_ERROR_CONNECT:
                //支付宝网络连接错误
                msg = "alipay network connection failed.";
                break;

        }
        


### 注意事项
Android 不允许在 UI 线程中进行网络请求，所以请求 charge 对象的时候请使用 thread+handler 或者使用 AsyncTask 。example 里面的示例程序使用的就是 AsyncTask 方式请求 charge 对象。
    
    
### 混淆设置
用户进行 apk 混淆打包的时候，为了不影响 PayRight SDK 以及渠道 SDK 的使用，请在 proguard-rules 中添加一下混淆规则。



    -dontwarn com.alipay.**
    -keep class com.alipay.** {*;}

    -dontwarn  com.tencent.**
    -keep class com.tencent.** {*;}

    -dontwarn com.swwx.payright.**
    -keep class com.swwx.payright.** {*;}



### 日志开关

SDK 提供了日志功能，默认日志为关闭状态。
开发者可以通过下面设置打开日志开关。通过 `PayRight` 来对日志进行筛选。

    PayLog.DEBUG = true;

