# 打包exe

`windows`中用`PyInstaller`打包`python`脚本为exe文件

其中python脚本调用到`mitmdump`

可以理解为：打包mitmdump的Python为exe

核心命令：

```bash
pyinstaller pymitmdump\mitmdumpStartApi.py --distpath pymitmdumpstartdist --add-data "pymitmdump\mitmdump_executable;mitmdump_executable" --add-data "pymitmdump\mitmdumpUrlSaver.py;."

pyinstaller pymitmdump\mitmdumpOtherApi.py --distpath pymitmdumpotherdist
```

可以生成2个exe文件。

* 细节详见：【已解决】windows中用PyInstaller打包mitmdump的Python脚本为exe

