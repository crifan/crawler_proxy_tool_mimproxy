# Mac

接着介绍，如何在`Mac`中使用`mitmdump`

举例：

`Mac`中终端去运行：

```bash
mitmdump -k -p 8081 -s middleware/Save1.py
```

启动mitmdump的代理

然后给手机端加上此处Mac的mitmdump的代理

即可实现：脚本`Save1.py`把手机端发出的所有的`url`=`请求`=`链接地址`（还可以根据自己需要做一定过滤处理后再）保存起来（比如保存到一个文件中），供后续使用。

## 说明

### 此处的Save1.py是个python脚本

具体内容：

```python
# _*_ coding: utf-8 _*_

import json
import re
import os
import sys
# print("sys.executable=%s" % sys.executable)

try:
    import yaml
except Exception as err:
    print("Failed to import yaml: %s" % err)

class Saver:
    
    def __init__(self):
        self.Allurls = set()
        self.DataFilePath = self.get_DataFilePath()
        self.REMOVED = self.get_NeedSkip()
    
    def get_DataFilePath(self):
        # SavePath = "./middleware/Save.json"
        SavePath = os.path.join("middleware", "Save.json")
        with open(SavePath,"r",encoding="utf-8") as f:
            text = f.read()
            data = json.loads(text)
            return data["1"]
        
    def get_NeedSkip(self):
        # filepath = "./middleware/config.yml"
        filepath = os.path.join("middleware", "config.yml")
        try:
            with open(filepath, "r", encoding="utf-8") as f:
                text = f.read()
        except Exception:
            with open(filepath, "r") as f:
                text = f.read()
        config = yaml.load(text)
        REMOVED = [item.replace('.','\.') for item in config["skip"]]
        return "|".join(REMOVED)
    
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
        if not url in self.Allurls and not re.search(self.REMOVED, url):
            self.Allurls.add(url)
            print(url)
            with open(self.DataFilePath, "a", encoding="utf-8") as f:
                f.write(url + "|" + ContentType)
                f.write('\n')

addons = [Saver()]
```

### 若想要后台运行，则后面加`&`

```bash
mitmdump -k -p 8081 -s middleware/Save1.py &
```
