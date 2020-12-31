# if you can see this, traffic is not passing through mitmproxy

* **现象**

手机中浏览器打开 http://mitm.it 后，看到页面提示：

`if you can see this, traffic is not passing through mitmproxy`

* **原因**

需要你手机中WiFi加上PC端的mitmproxy（mitmdump）的代理后，打开 http://mitm.it 后才能正常显示页面

* **解决办法**
  * PC端（Mac）中启动mitmproxy的代理
    * 举例
      * `mitmdump -k -p 8081 -s middleware/Save1.py`
  * 然后再给手机端的当前WiFi中加上对应的mitmdump的代理

细节详见：

【已解决】红米Note8Pro中去下载mitmproxy证书提示：if you can see this, traffic is not passing through mitmproxy
