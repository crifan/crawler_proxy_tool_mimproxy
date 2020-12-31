# Mac

Mac中也可以直接用`brew`去安装：

```bash
brew install mitmproxy
```

也可以用Python中的pip去（给Python环境中）安装：

```bash
pip install mitmproxy
```

注：如果后续`mitmdump`用到`-s`去加载的`.py`的python脚本中，用到了`pyaml`的话，则记得要先用`pip`安装`pyyaml`：

```bash
pip instal pyyaml
```
