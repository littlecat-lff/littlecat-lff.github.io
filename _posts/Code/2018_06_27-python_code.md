---
layout: post
title: Blog&#58 python 代码问题
categories: [python]
tags: python
---

### 删除字符串中不可见字符

``` python
for i in range(0,32):
	 query = query.replace(chr(i),'')
```