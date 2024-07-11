# 移动端安装mitmproxy根证书

## 通用逻辑

即给移动端手机中安装`mitmproxy`的

`SSL代理证书`=`ssl证书`=`根证书`=`root CA`

核心逻辑：

* 手机中浏览器中打开 http://mitm.it
* 然后根据提示去下载（`.pem`/`.crt`/`.cer`等）证书（文件）
* 点击安装证书文件
