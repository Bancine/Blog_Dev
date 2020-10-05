---
title: 数组树形结构转json
date: 2020-08-18 12:11:03
tags: python
---

```python
import json

# 定义json样式结构树
d = {
    "name": "根",
    "children": []
}
# 打印结构样子
print(json.dumps(d, indent=4, ensure_ascii=False))

# 定义数据[(当前节点编号, 父亲节点编号)...]
data = [
    ("1", "根"),
    ("2", "1"),
    ("3", "1"),
    ("4", "2"),
    ("5", "2"),
    ("6", "3"),
]

# 打印数据
print(data)

# 查找父亲节点的函数
def findFatherNode(fatherName, data):
    if data['name'] == fatherName:
        return data
    for i in data["children"]:
        node = findFatherNode(fatherName, i)
        if node is not None:
            return node
    return None

# 遍历数据，并将数据添加到json结构树中
for i in data:
    node = findFatherNode(i[1], d)
    if node is not None:
        node["children"].append({
            "name": i[0],
            "children": []
        })

# 打印结果
print(json.dumps(d, indent=4, ensure_ascii=False))
```

