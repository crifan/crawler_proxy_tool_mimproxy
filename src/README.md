# 抓包代理利器：mitmproxy

* 最新版本：`v0.8`
* 更新时间：`20201231`

## 简介

介绍主要用于抓包领域的代理工具mitmproxy，尤其是常用的命令行版的mitmdump。先对mitmproxy概述，再介绍mitmdump的下载和安装。包括Mac和Win中如何安装和常见问题。接下来介绍如何使用mitmdump，包括核心的通用逻辑，即先电脑端启动mitmdump代理，再去移动端初始阿虎安装mitmproxy的根证书ssl代理证书文件，其中总结了各种iOS和安卓手机在安装根证书时候的坑和问题及解决办法。再去介绍如何给移动端中WiFi去设置代理。总结了常见的问题，比如No module named yaml、traffic is not passing through mitmproxy等等。还有其他方面，比如代码中调用控制mitmdump的运行、win中如何给mitmdump的python打包成exe。最后附上help语法供需要时查阅。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### Gitbook源码

* [crifan/crawler_proxy_tool_mimproxy: 抓包代理利器：mitmproxy](https://github.com/crifan/crawler_proxy_tool_mimproxy)

#### 如何使用此Gitbook源码去生成发布为电子书

详见：[crifan/gitbook_template: demo how to use crifan gitbook template and demo](https://github.com/crifan/gitbook_template)

### 在线浏览

* [抓包代理利器：mitmproxy book.crifan.com](http://book.crifan.com/books/crawler_proxy_tool_mimproxy/website)
* [抓包代理利器：mitmproxy crifan.github.io](https://crifan.github.io/crawler_proxy_tool_mimproxy/website)

### 离线下载阅读

* [抓包代理利器：mitmproxy PDF](http://book.crifan.com/books/crawler_proxy_tool_mimproxy/pdf/crawler_proxy_tool_mimproxy.pdf)
* [抓包代理利器：mitmproxy ePub](http://book.crifan.com/books/crawler_proxy_tool_mimproxy/epub/crawler_proxy_tool_mimproxy.epub)
* [抓包代理利器：mitmproxy Mobi](http://book.crifan.com/books/crawler_proxy_tool_mimproxy/mobi/crawler_proxy_tool_mimproxy.mobi)

## 版权说明

此电子书教程的全部内容，如无特别说明，均为本人原创和整理。其中部分内容参考自网络，均已备注了出处。如有发现侵犯您版权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 更多其他电子书

本人`crifan`还写了其他`100+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)
