# Mac

接着介绍，如何在`Mac`中使用`mitmdump`

举例：

`Mac`中终端去运行：

```bash
mitmdump -k -p 8081 -s saveUrl.py
```

启动mitmdump的代理

然后给手机端加上此处Mac的mitmdump的代理

即可实现：脚本`saveUrl.py`把手机端发出的所有的`url`=`请求`=`链接地址`（还可以根据自己需要做一定过滤处理后再）保存起来（比如保存到一个文件中），供后续使用。

## 说明

先要手动创建一个：`output`文件夹，其中新建一个空文件`SavedUrl.txt`，供后续保存url到其中。

### 此处的saveUrl.py是个python脚本

具体内容：

```python
# Function: using mitmproxy to save url
# Author: Crifan Li
# Date: 20240711

import re
import os

class Saver:
    def __init__(self):
      self.Allurls = set()
      self.DataFilePath = self.initOutputFile()

    def initOutputFile(self):
      saveFile = os.path.join("output", "SavedUrl.txt")
      return saveFile

    def get_ContentType(self, headers):
      ContentType = "None"
      patten = "b'Accept', b'(.*?)'"
      result = re.search(patten, headers)
      if result:
        ContentType = result.group(1)
        ContentType = ContentType.split(",")[0]
      return ContentType if not "*" in ContentType else "None"

    def request(self, flow):
      url = flow.request.url
      ContentType = self.get_ContentType(str(flow.request.headers))
      if not url in self.Allurls:
        self.Allurls.add(url)
        print(url)
        with open(self.DataFilePath, "a", encoding="utf-8") as f:
          f.write(url + "|" + ContentType)
          f.write('\n')

addons = [Saver()]
```

### 若想要后台运行，则后面加`&`

```bash
mitmdump -k -p 8081 -s saveUrl.py &
```
