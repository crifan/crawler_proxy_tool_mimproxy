# 抓包代理利器：mitmproxy

* 最新版本：`v1.9.2`
* 更新时间：`20240714`

## 简介

介绍主要用于抓包领域的代理工具mitmproxy，尤其是常用的命令行版的mitmdump。先对mitmproxy概述，再介绍mitmdump的下载和安装。包括Mac和Win中如何安装和常见问题。接下来介绍如何使用mitmdump，包括核心的通用逻辑，即先电脑端启动mitmdump代理，再去移动端初始化安装mitmproxy的根证书ssl代理证书文件，其中总结了各种iOS和安卓手机在安装根证书时候的各种坑和问题及解决办法。再去介绍如何给移动端中WiFi去设置代理。总结了常见的问题，比如No module named yaml、if you can see this, traffic is not passing through mitmproxy、Cannot validate certificate hostname without SNI、ssl3_read_bytes sslv3 alert certificate unknown、-s时无法指定python版本、检测到代理显示异常、mitmdump偶尔突然无效、ssl3_get_record wrong version number、SysCallError 10054 WSAECONNRESET等等。还有其他方面，比如用代码控制mitmdump的运行、win中如何给mitmdump的python打包成exe。最后附上mitmdump、mitmproxy和mitmweb的help语法供需要时查阅。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/crawler_proxy_tool_mimproxy: 抓包代理利器：mitmproxy](https://github.com/crifan/crawler_proxy_tool_mimproxy)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [抓包代理利器：mitmproxy book.crifan.org](https://book.crifan.org/books/crawler_proxy_tool_mimproxy/website/)
* [抓包代理利器：mitmproxy crifan.github.io](https://crifan.github.io/crawler_proxy_tool_mimproxy/website/)

### 离线下载阅读

* [抓包代理利器：mitmproxy PDF](https://book.crifan.org/books/crawler_proxy_tool_mimproxy/pdf/crawler_proxy_tool_mimproxy.pdf)
* [抓包代理利器：mitmproxy ePub](https://book.crifan.org/books/crawler_proxy_tool_mimproxy/epub/crawler_proxy_tool_mimproxy.epub)
* [抓包代理利器：mitmproxy Mobi](https://book.crifan.org/books/crawler_proxy_tool_mimproxy/mobi/crawler_proxy_tool_mimproxy.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 其他

### 作者的其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)

### 关于作者

关于作者更多介绍，详见：

[关于CrifanLi李茂 – 在路上](https://www.crifan.org/about/)
