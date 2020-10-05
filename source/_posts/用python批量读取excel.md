---
title: 用python批量读取excel
date: 2020-08-18 12:30:57
tags: python
---

```python
import pandas as pd
import numpy as np
import glob,os
import matplotlib.pyplot as plt
path=r'C:\Users\Bancine\Desktop\a.xlsx'        #批量表格所在文件路径
file=glob.glob(os.path.join(path, "*.csv"))      #每一个表格相同名称部分
print(file)
dl= []
for f in file:
    dl.append(pd.read_csv(f,index_col=None,encoding='gbk'))     #读取每个表格
    ac_df=pd.concat(dl)
```

