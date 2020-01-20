---
layout: post
title: Blog&#58 python 代码问题
categories: [python]
tags: python
---



[TOC]



``` python
if __name__ == '__main__':
```





## 基本操作

### 三目运算

```python
h = "变量1" if a>b else "变量2"
```





## random相关



### random常见用法

```python
import random

random.random()                          # 产生 0 到 1 之间的随机浮点数
random.randint(start,stop)               # 产生 1 到 10 的一个整数型随机数
random.randrange(start,stop,step)        # 生成从1到100的间隔为2的随机整数
random.uniform(a, b)                     # 产生1.1 到5.4之间的随机浮点数，区间可以不是整数
random.shuffle(seq,random=None):         # 对传入的集合进行乱序操作。只能针对可变序列，如字符串、列表
random.sample(list,k)                    # 从list序列中，随机获取k个元素，生成一个新序列。sample不改变原来序列
```







## 数组list相关



### range倒序列遍历

```python
1: 正序
    range(6):
	0,1,2,3,4,5

2: 倒序:
    range(5, -1, -1):
    5,4,3,2,1,0
  
3.用切片逆序：
    range(6)[::-1]
    5,4,3,2,1,0
   
4.reversed():
	reversed(range(6))
	5,4,3,2,1,0
```



### set 运算: 交集, 并集, 差集

```
a = t | s          # t 和 s的并集
 
b = t & s          # t 和 s的交集
 
c = t – s          # 求差集（项在t中，但不在s中）
 
d = t ^ s          # 对称差集（项在t或s中，但不会同时出现在二者中）
```



### set 增加

```
>>> s=set('one')
>>> s
{'e', 'o', 'n'}
>>> s.add('two')
>>> s
{'e', 'two', 'o', 'n'}
```







### Slice操作

Python中符合序列的有序序列都支持切片（slice），例如列表，字符串，元组。

```
格式：【start:end:step】
start:起始索引，从0开始，-1表示结束
end：  结束索引
step： 步长，end-start，步长为正时，从左向右取值。步长为负时，反向取值. 
注意切片的结果不包含结束索引，即不包含最后的一位，-1代表列表的最后一个位置索引

b1=a[:] #省略全部，代表截取全部内容，可以用来将一个列表拷给另一个列表
c1=a[:3] #省略起始位置及步长, 默认起始位置从头开始，默认步长为1，结束位置索引为3
```





### 合并两个数组

**zip()** 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。

如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 * 号操作符，可以将元组解压为列表。



```python
>>>a = [1,2,3]
>>> b = [4,5,6]
>>> c = [4,5,6,7,8]

>>> zipped = zip(a,b)     # 打包为元组的列表
[(1, 4), (2, 5), (3, 6)]

>>> zip(a,c)              # 元素个数与最短的列表一致
[(1, 4), (2, 5), (3, 6)]

>>> zip(*zipped)          # 与 zip 相反，*zipped 可理解为解压，返回二维矩阵式
[(1, 2, 3), (4, 5, 6)]

## 直接讲两个list进行合并或者将dict的key和value对换
reversed_dictionary = dict(zip(dictionary.values(), dictionary.keys()))

```



### 遍历数组并获取索引: enumerate

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

```python
enumerate(sequence, [start=0])
sequence -- 一个序列、迭代器或其他支持迭代对象。
start -- 下标起始位置。

普通的 for 循环
>>>i = 0
>>> seq = ['one', 'two', 'three']
>>> for element in seq:
...     print i, seq[i]
...     i +=1

>>> for i, element in enumerate(seq):
...     print i, element
... 
0 one
1 two
2 three
```





## dict相关

### 两个dict合并

```python
self.pinlei_cate = dict( self.pinlei_cate1.items() + self.pinlei_cate2.items() )
```



### dict 排序

```python
keys = adict.keys() 
keys.sort() 
return [dict[key] for key in keys] 
```





## 数学相关

### 十进制转二进制字符串

bin(7) —> '0b111' 



##字符串相关

### 字符串反转

```python

result = s[::-1]  # 使用字符串切片

# 使用列表的reverse
l = list(s)
l.reverse()
result = "".join(l)
```



### 字符串数字转二进制bitmap

```python
bit_match_info = format( int(match_info), 'b' )   # 7 输出 '111'
```



###常见标点

```python
self.biaodian = [
    u"。", u"！", u"!", u"？", u"/?", u"！", u"!", u""
    , u"[", u"]", u"。", u"，", u",", u"！", u"…", u"…", u"!", u"《", u"》"
    , u"<", u">", u"/", u"\"", u"'", u":", u"：", u"？", u"/", u"?", u"、"
    , u"/", u"|", u"“", u"”", u"‘", u"’", u"；", u"]", u"{", u"}", u"（", u"）", u"{", u"}", u"【", u"】", u"(", u")", u"｛", u"｝", u"（"
    , u"）", u"：", u"？", u"！", u"。", u"，", u";", u"、", u"~", u"—", u"—", u"+", u"％", u"%", u"`", u":", u"“", u"”", u"\＂", u"'"
    , u"\n"
]

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



### 字符串按照多个字符分割

```python
import re
records = re.split('[:\t]', line)
```



### 字符串包含

```python
if str1 in str2:  包含的话，True
if str1.find(str2)>=0: 包含的话，返回第一次出现的位置，没有的话为负数
```



### 剔除Non-breaking space

```python
Non-breaking space的东西，用于阻止在此处自动换行和阻止多个空格被压缩成一个。
至于解决方法，先用subplace("\xc2\xa0", " ")把这个特殊的空格替换一下就行了。
```





## 文件处理相关

### 生成文件路径

python里面如果不指定生成文件的绝对路径, 会在脚本执行的目录生成文件.

```
[jianhui.jjh@rs1c16389.et2sqa /home/jianhui.jjh/tensorflow/odps_tensorflow/word2vec_example/evaluate]
$python ~/test.py

会在当前目录生成文件
```



### python写入中文乱码

``` python
outFile.write(json.dumps(dict_question, indent=4, ensure_ascii=False))
```

### 读写文件并进行处理
with: 不用处理close
``` python
with open('test1.txt', 'r') as f1:
    for line in f1:
        line = line.rstrip('\n')
        process(line)
```



### 获取临时文件路径: gettempdir

```python
tempfile. gettempdir()
    返回临时文件所使用目录的目录名。它定义了dir参数在该模块中所有函数内的默认值。
    Python检索一个标准目录列表取找出一个调用者可在其中更顺利创建文件的目录。

该列表为：
    1.由环境变量TMPDIR命名的目录；
    2.由环境变量TEMP命名的目录；
    3.由换将变量TMP命名的目录；
    4.一个平台指定的位置：
    在Windows中，目录为C:\TEMP、C:\TMP、\TEMP和\TMP。
    在其它所有平台上，目录为/tmp、/var/tmp和/usr/tmp。

import os
import sys
from tempfile import gettempdir
local_filename = os.path.join(gettempdir(), filename)  # 获取一个存放文件的临时路径
```



### 遍历文件夹下的文件

```python
rootdir = './temp'
list = os.listdir(rootdir) #列出文件夹下所有的目录与文件
for i in range(0,len(list)):
    path = os.path.join(rootdir,list[i])
    if os.path.isfile(path):
```







## json相关

###json中文loads乱码
```python
import sys
reload(sys)
sys.setdefaultencoding('utf8')
```

###读入json文件

``` python
import json
reload(sys)
sys.setdefaultencoding('utf8')

f = open("./manual_faq_jieba_seg_processed_for_mrc.json", 'r')

ln = 0
for line in  f.readlines():
    line = line.rstrip('\n')
    ln = ln + 1
    jscontent = json.loads(line)
    print "%s\t%s"%(jscontent["question_id"],jscontent["question"]),
```

### json Format

* vim 使用: %!python ~/conf/tool.py进行格式化.  命令行使用 cat *.json | python ~/conf/too.py

    * 注意. tool.py是从python库里面cp出来, 将json.dumps函数加上ensure_ascii=False, 防止对非ascii码进行unicode转换
    * 同时, 需要设置utf-8编码. 

    ```python
    import sys
    import json
    import re
    reload(sys)
    sys.setdefaultencoding('utf8')
    
    def main():
        if len(sys.argv) == 1:
            infile = sys.stdin
            outfile = sys.stdout
        elif len(sys.argv) == 2:
            infile = open(sys.argv[1], 'rb')
            outfile = sys.stdout
        elif len(sys.argv) == 3:
            infile = open(sys.argv[1], 'rb')
            outfile = open(sys.argv[2], 'wb')
        else:
            raise SystemExit(sys.argv[0] + " [infile [outfile]]")
        with infile:
            try:
                obj = json.load(infile)
            except ValueError, e:
                raise SystemExit(e)
        with outfile:
            output = json.dumps(obj, indent=4, ensure_ascii=False)
            outfile.write(output)
            outfile.write('\n')
    
    if __name__ == '__main__':
        main()
    ```






## 打印日志相关

```python
	# this is the full
    log_path = ""
    logger = logging.getLogger("tfmodel")
    logger.setLevel(logging.INFO)
    formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')

    console_handler = logging.StreamHandler()
    console_handler.setLevel(logging.INFO)
    console_handler.setFormatter(formatter)
    logger.addHandler(console_handler)

    self.logger.info("getting vocab size:[{}]".format(len(self.word_count)))

    # this is the simple
	logging.basicConfig(format='%(asctime)s - %(name)s - %(levelname)s - %(message)s', level=logging.DEBUG)
```

##示例程序

### 获取命令行参数

```python
如果想对python脚本传参数，python中对应的argc, argv(c语言的命令行参数)是什么呢？
import sys
参数个数：len(sys.argv)
脚本名：    sys.argv[0]
参数1：     sys.argv[1]
参数2：     sys.argv[2]
```





###cosine计算

```python
import math
import sys 
import numpy as np
class jq_cosine(object):

    def evaluate(self, str1, str2, insep):
        if not str1 or not str2:
            return 0

        vec_1 = np.array(str1.split(insep), dtype = float)
        vec_2 = np.array(str2.split(insep), dtype = float)

        norm_score = np.linalg.norm(vec_1) * np.linalg.norm(vec_2)

        if np.fabs(norm_score) < 0.000000006:
            return 0

        return  ( np.inner(vec_1, vec_2) /  norm_score ).item()
```



### 使用python自带的counter计数

Counter类的目的是用来跟踪值出现的次数。它是一个无序的容器类型，以字典的键值对形式存储，其中元素作为key，其计数作为value。

```python
>>> c = Counter()  # 创建一个空的Counter类
>>> c = Counter('gallahad' or list or dict )  # 从一个可iterable对象（list、tuple、dict、字符串等）创建
>>> c = Counter({'a': 4, 'b': 2})  # 从一个字典对象创建
>>> c = Counter(a=4, b=2)  # 从一组键值对创建

当所访问的键不存在时，返回0，而不是KeyError；否则返回它的计数。


most_common([n])
返回一个TopN list。如果n没有被指定，则返回所有元素。 按照元素个数进行排序, 当多个元素计数值相同时，排列是无确定顺序的. 

>>> c = Counter('abracadabra')
>>> c.most_common(3)
[('a', 5), ('r', 2), ('b', 2)]


# 常见操作
sum(c.values())  # 所有计数的总数
c.clear()  # 重置Counter对象，注意不是删除
list(c)  # 将c中的键转为列表
set(c)  # 将c中的键转为set
dict(c)  # 将c中的键值对转为字典
c.items()  # 转为(elem, cnt)格式的列表
Counter(dict(list_of_pairs))  # 从(elem, cnt)格式的列表转换为Counter类对象
c.most_common()[:-n:-1]  # 取出计数最少的n-1个元素
```







### 计算不同阈值下正负样本的准确率

```python
#coding: utf-8
list_scores = "0.5,0.6,0.61,0.62,0.63,0.65,0.7,0.8,0.85,0.9".split(",")
f = open("./aa", 'r')

all_pair = 0
query_set = set()
l_th = {}
l_th_q = {}  # 计算query维度的准确率

for line in  f.readlines():
    cur_list = line.rstrip('\n').split('\t')
    score = float(cur_list[3])
    label = cur_list[4]
    all_pair = all_pair + 1
    query_set.add(cur_list[0])

    for th in list_scores:
        if score <= float(th):
            continue
        if th not in l_th:
            l_th[th] = {}

        l_th[th]["all"] = l_th[th]["all"] + 1 if "all" in l_th[th] else 1
        l_th[th][label] = l_th[th][label] + 1 if label in l_th[th] else 1

        if th not in l_th_q:
            l_th_q[th] = {}
            l_th_q[th]["all"] = set()
        if label not in l_th_q[th]:
            l_th_q[th][label] = set()
        l_th_q[th][label].add(cur_list[0])
        l_th_q[th]["all"].add(cur_list[0])

print "all query pair:[%d] unique query number:[%d]\n"%(all_pair, len(query_set))
for f_th in sorted( [ float(score) for score in l_th.keys() ] ):
    th = str(f_th)
    all_recall = l_th[th]["all"]
    for label in l_th[th]:
        if label == "all":
            continue
        if all_recall > 0:
            #print "threshold:[%s] all_number:[%d] label:[%s] number:[%d] ratio:[%.2f]"%(th, all_recall, label, l_th[th][label], l_th[th][label]*1.0/all_recall)
            #print ""
            print "%s %d %s %d %.2f"%(th, all_recall, label, l_th[th][label], l_th[th][label]*1.0/all_recall)
        else:
            print "threshold:[%s] all_recall:[%d]"%(th, all_recall)

print "unique query维度"
for f_th in sorted( [ float(score) for score in l_th.keys() ] ):
    th = str(f_th)
    all_q = len(query_set)

    all_recall = len(l_th_q[th]["all"])
    bad_q = len(l_th_q[th]["0"])
    good_q = all_recall - bad_q  # query labelshould all be 1

    #print "threshold:[%s] all_number:[%d] label:[0] number:[%d] ratio:[%.2f]"%(th, all_recall, bad_q, bad_q*1.0/all_recall)
    #print "threshold:[%s] all_number:[%d] label:[1] number:[%d] ratio:[%.2f]"%(th, all_recall, good_q, good_q*1.0/all_recall)
    #print ""
    print "%s %d 0 %d %.2f"%(th, all_recall, bad_q, bad_q*1.0/all_recall)
    print "%s %d 1 %d %.2f"%(th, all_recall, good_q, good_q*1.0/all_recall)

f.close()
```

