# No module named yaml

* **现象**

Mac中用brew安装了mitmproxy，然后去运行：

```bash
mitmdump -p 8081 -s middleware/Save1.py
```

但是报错：

```bash
No module named yaml
```

* **原因**

Mac中通过brew安装的mitmproxy，会调用自己内部安装的python（此处是3.7.5）

而不是Mac中自己Python（2.7或3.8），mac中的python中都安装过yaml了

而mitmproxy中python，没有安装过yaml，所以上述脚本会报错。

* **解决办法**

不要用brew安装，而是用系统中的python的pip去安装mitmproxy

```bash
pip install mitmproxy
```

注：系统中的python是,此处是用的3.8，用pyenv设置全局为3.8

另外此处2.7的python中，pip安装mitmproxy会失败。

之后即可正常调用

```bash
mitmdump -p 8081 -s middleware/Save1.py
```

其中python解析器用的是此处系统的python了，因此可以正常找到（系统中python中已安装的）yaml，而不会报错了。

具体细节详见：

* 【基本解决】Mac中mitmdump运行命令报错：in script py No module named yaml
