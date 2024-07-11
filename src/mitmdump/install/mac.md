# Mac

## 通过brew安装mitmproxy

Mac中也可以直接用`brew`去安装：

```bash
brew install mitmproxy
```

安装mitmproxy后，就自带了命令行版本的`mitmdump`

### 用pip安装Python版本

如果后续需要用到`mitmdump`的`-s`去加载的`.py`的python脚本，那么此处就应该先要通过安装Python中的pip去（给Python环境中）安装mitmproxy

```bash
pip install mitmproxy
```

### 安装其他依赖的Python库

举例：

如果后续`mitmdump`用到`-s`去加载的`.py`的python脚本中，用到了`pyaml`的话，则记得要先用`pip`安装`pyyaml`：

```bash
pip instal pyyaml
```
