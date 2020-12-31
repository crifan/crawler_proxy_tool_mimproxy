# mitmproxy概述

* `mitmproxy`
  * 名词解析
    * `mitmproxy`=`mitm`的`proxy`
      * `mitm`=`MITM`=`Man-In-The-Middle`
        * 直译：`人在中间`
            * 在中间 ->
              * 首先要确保原先网络请求能继续
                * 所以就是代理的功能：**正常转发**原有网络请求
              * 但也可以干很多事情
                * 比如
                  * **记录**、**保存**网络请求
                  * **拦截**（符合特定规则的）网络请求
                  * （甚至）**篡改**、**伪造**成新的合法的或不合法的网络请求
        * 相关：往往也被叫做
          * `Man-In-The-Middle attack`=`中间人攻击`
  * `mitmproxy`是一套工具的总称，包含
    * `mitmproxy`：交互式命令行工具
      * 是什么=一句话概述
        * 英文
          * mitmproxy is an interactive, SSL/TLS-capable intercepting proxy with a console interface for HTTP/1, HTTP/2, and WebSockets
        * 中文
          * mitmproxy是一个代理工具
            * 功能和特点
              * 交互式的
              * 支持https拦截
              * 支持协议：`HTTP/1`、`HTTP/2`、`WebSockets`
                * 产品形态：控制台console中显示交互界面
      * 长什么样=截图
        * ![mitmproxy_screenshot_demo](../assets/img/mitmproxy_screenshot_demo.jpg)
    * `mitmweb`：基于命令行的带UI界面
      * 可以理解为：**网页版的mitmproxy**
      * 是什么=一句话描述
        * mitmweb is a web-based interface for mitmproxy
      * 长什么样=截图
        * ![mitmproxy_mitmweb](../assets/img/mitmproxy_mitmweb.png)
    * `mitmdump`：命令行版本
      * 是什么=一句话描述
        * mitmdump is the command-line version of mitmproxy. Think tcpdump for HTTP
      * 类比
        * `mitmdump`之于`mitmproxy`
          * 就像
            * `tcpdump`之于`HTTP`
      * 可以理解为
        * 命令行版本的`Charles`/`Fiddler`
* 主要用途：实现对网页、app的抓包
* 网址
  * 官网文档
    * Introduction
      * https://docs.mitmproxy.org/stable/
  * GitHub
    * mitmproxy/mitmproxy: An interactive TLS-capable intercepting HTTP proxy for penetration testers and software developers
      * https://github.com/mitmproxy/mitmproxy
