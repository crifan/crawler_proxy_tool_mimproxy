# Android

此处整理安卓手机中，安装mitmproxy的根证书，对于不同手机的详细情况：

* Android
  * 华为
    * 荣耀
      * 【记录】给安卓手机中安装mitmproxy代理的SSL证书
      * 【记录】给自动抓包工具的安卓手机设置mitmproxy代理用于能抓包到链接地址
  * 小米
    * 小米9
      * 相关
        * 【已解决】安卓手机小米9中安装mitmproxy的SSL代理证书
          * 【无需解决】小米9中WLAN或WAPI证书中找不到mitmproxy的SSL的pem证书文件
          * 【无法解决】小米9中用ES文件管理器安装pem证书
    * 红米Note8Pro
      * 问题
        * 用微信或小米浏览器无法下载pem证书文件
      * 解决办法：
        * 换QQ浏览器就可以正常下载pem证书文件 mitmproxy-ca-cert.pem
          * 细节
            * 不能用：
              * 微信
                * 点击Android无反应
              * 小米浏览器
                * 点击Android，弹框下载：perm.crt
                  * 而不是希望的：mitmproxy-ca-cert.pem
                  * 关键是：始终无法下载成功
            * 只能用：QQ浏览器
              * 点击Android，可以弹框下载：mitmproxy-ca-cert.pem
                * 是我们希望的pem证书
                * 也可以正常（瞬间）下载完毕
      * 详见
        * 【无法解决】红米Note8Pro中用微信或小米浏览器下载mitmproxy的SSL代理证书
        * 【已解决】红米Note8Pro中用QQ浏览器下载mitmproxy的Android的SSL代理证书
      * 相关
        * 【已解决】红米Note8Pro中安装mitmproxy的SSL代理证书
    * 红米10X
      * 问题：下载证书失败
        * 自带小米浏览器
          * 可弹框下载pem.crt，但下载失败
        * QQ浏览器
          * 可弹框下载mitmproxy-ca-cert.pem，但下载失败
          * 偶然甚至会提示：
            * if you can see this, traffic is not passing through mitmproxy
        * UC浏览器
          * 可弹框下载mitmproxy-ca-cert.pem，但下载失败
          * 偶然甚至会提示：
            * if you can see this, traffic is not passing through mitmproxy
      * 解决办法：
        * 试了多次，最后终于：
          * UC浏览器
            * 可弹框并成功下载mitmproxy-ca-cert.pem
      * 详见：
        * 【已解决】红米10X安卓手机中无法下载mitmproxy的证书文件
  * Vivo
    * iQOO U1x
      * 用QQ浏览器无法下载pem文件，提示下载失败
        * 解决办法：换Vivo的内置浏览器，即可下载 mitmproxy-ca-cert.pem
      * 直接点击pem证书文件，无法安装：未找到证书文件
        * 问题现象
          * QQ浏览器下载到mitmproxy-ca-cert.pem，直接点击提示：找不到对应程序打开该文件
          * 更多安全设置-》从手机存储和SD卡安装，点击提示：未找到证书文件
          * 从文件管理中点击已下载的mitmproxy-ca-cert.pem，选 证书安装程序，也提示：未找到证书文件
        * 原因：Vivo不支持pem证书文件，只支持crt证书文件
        * 解决办法：把文件pem后缀改为crt
          * 点击即可正常安装
      * 详见：
        * 【已解决】给安卓手机ViVo的iQOO U1x下载和安装mitmproxy的SSL代理证书
        * 【已解决】安卓手机Vivo的iQOO U1x中手动安装mitmproxy-ca-cert.pem证书文件
        * 【已解决】安卓手机Vivo的iQOO U1x中点击安装mitmproxy的pem证书报错：未找到证书文件
        * 【未解决】给安卓手机Vivo的iQOO U1x初始化mitmdump的代理环境
