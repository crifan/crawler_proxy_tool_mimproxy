# `-s`时无法指定python版本

此处

```bash
mitmdump -s xxx.py
```

中，无法指定加载`xxx.py`脚本时，所用的`Python的版本`

-> 会导致，导入一些python库时，即使你Python环境已安装了该库（比如`pyyaml`），仍会报错

-> 因为其只用调用（mitmdump所）内置的Python的版本，无法换成当前（Mac）系统中的某个版本的Pyton

* 细节详见
  * 【无法解决】Mac中mitmdump通过-s加载python脚本时指定Python版本
  * 【已解决】mac中Python2和Python3都已安装了yaml但mitmdump -s加载python脚本中导入yaml还是报错
  * 【已解决】Mac中让mitmdump解析python脚本不用自己内置Python而是用系统Python
  * 【已解决】Mac中运行mitmdump再次报错：Failed to import yaml
  * 【已解决】Mac中mitmdump运行命令报错：in script py No module named yaml
