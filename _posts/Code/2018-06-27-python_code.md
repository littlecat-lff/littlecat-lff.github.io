---
layout: post
title: Blog&#58 python 代码问题
categories: [python]
tags: python
---

```python
#coding: utf-8
```

``` python
if __name__ == '__main__':
```

### 删除字符串中不可见字符

``` python
for i in range(0,32):
	 query = query.replace(chr(i),'')
```

### 判断字符串是否是纯数字
``` python
str_a = "1243"
str_a.isdigit() --> return True
```

### 两个list的element直接进行相加:

``` python
embedding = [x + y for x, y in zip(first, cur_embedding)]
```

## 文件处理相关
### python写入中文乱码
``` python
outFile.write(json.dumps(dict_question, indent=4, ensure_ascii=False))
```

### 读取文件并进行处理
with: 不用处理close
``` python
with open('test1.txt', 'r') as f1:
    for line in f1:
        process(line)
```

## json相关
### 读入json文件

``` python
import json
reload(sys)
sys.setdefaultencoding('utf8')

f = open("./manual_faq_jieba_seg_processed_for_mrc.json", 'r')

ln = 0
for line in  f.readlines():
    ln = ln + 1
    jscontent = json.loads(line)
    print "%s\t%s"%(jscontent["question_id"],jscontent["question"]),
```


## 打印日志相关
```python
    log_path = ""
    logger = logging.getLogger("tfmodel")
    logger.setLevel(logging.INFO)
    formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')

    console_handler = logging.StreamHandler()
    console_handler.setLevel(logging.INFO)
    console_handler.setFormatter(formatter)
    logger.addHandler(console_handler)

    self.logger.info("getting vocab size:[{}]".format(len(self.word_count)))
```



