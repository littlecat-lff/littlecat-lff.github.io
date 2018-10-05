
---
layout: post
title: Blog&#58 shell相关代码
categories: [python]
tags: python
---




## awk 相关代码

### awk清除首尾空格

``` shell
awk -F\, '{gsub(/^[ \t]+/, "", $2); gsub(/[ \t]+$/, "", $2); print $2 ":"}'
```


