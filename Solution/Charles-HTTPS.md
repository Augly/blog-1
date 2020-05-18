# Charles HTTPS 抓包

> [Charles官网](https://www.charlesproxy.com/)

iPhone抓包 和 Mac端抓包 设置步骤都很简单，推荐阅读[Charles 4.2.1 HTTPS抓包](https://juejin.im/post/5a30a52a6fb9a0451d4175ed)。

下面重点说说Android上的抓包（以我的红米K20 Pro为例）：
1. 尽量用第三方浏览器下载（如微软的Edge）pem证书文件。
2. 安装证书：
    1. 设置——WiFi——高级设置——安装证书
    2. 设置——更多设置——系统安全——加密与凭据——从存储设备安装证书

这时，你可以在：设置——系统安全——加密与凭据——用户凭据 里查看已安装的证书。当然，不想用了我们可以点击清除凭据，一键完成！
 
但是发现Charles上https还是显示unknown，直接告诉你：设置步骤没问题，是因为Android 7以后开始系统默认不再杏仁用户证书，即使你安装了，证书对APP也是无效的。 

安卓版本7+，并且微信版本7+，使用Charles也不能抓包，是微信调整了如下安全证书策略：

| 策略 | 安卓版本 | 微信版本 | 是否可以代理 |
|----|------|------|--------|
| A  | 7-   | 任意版本 | 是      |
| B  | 7+   | 7-   | 是      |
| C  | 7+   | 7+   | 否      |

苹果手机不受任何影响。

**那怎么解决呢？**

* 方案一：将证书安装到系统证书中（需要root）。（过程比较复杂，跳过）
* 方案二：一般情况下Android App内部使用的okhttp，如果让okhttp信用用户证书，应该也比较麻烦。所以建议更改APP的策略，参考[官方推荐配置](https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/)

> As of Android N, you need to add configuration to your app in order to have it trust the SSL certificates generated by Charles SSL Proxying. This means that you can only use SSL Proxying with apps that you control.

> In order to configure your app to trust Charles, you need to add a Network Security Configuration File to your app. This file can override the system default, enabling your app to trust user installed CA certificates (e.g. the Charles Root Certificate). You can specify that this only applies in debug builds of your application, so that production builds use the default trust profile.

Add a file res/xml/network_security_config.xml to your app:
```
<network-security-config> 
  <debug-overrides> 
    <trust-anchors> 
      <!-- Trust user added CAs while debuggable only -->
      <certificates src="user" /> 
    </trust-anchors> 
  </debug-overrides> 
</network-security-config>
```
Then add a reference to this file in your app's manifest, as follows:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config" ... >
        ...
    </application>
</manifest>
```
意思就是让APP信任用户证书，然后就能实现抓包了。

-------

参考链接：
* [Charles 4.2.1 HTTPS抓包](https://juejin.im/post/5a30a52a6fb9a0451d4175ed)
* [Charles官方推荐配置](https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/)
* [小米手机安装 charles 证书，提示“没有可安装的证书”](https://cloud.tencent.com/developer/article/1527037)