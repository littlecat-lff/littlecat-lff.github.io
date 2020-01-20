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





































洪波老师: 

我对我升6之后这两年的实际工作做了个总结: 

1:业务指标&技术&影响力: 
17年全程参与了迪拜塔项目, 在改写这块拿到了大盘2个点的提升; 并把改写覆盖率从81%提高到了90%. 同时在技术深度上尝试了skip-thought, doc2vec等在改写方面的应用并拿到了实际的业务效果; 最后和肖荣一起完成了一篇基于改写和相关性的论文, 发表在了wsdm2018上.   

在技术和影响力方面, 入职近5年来, 一直在负责query处理的基础算法相关. 包括: 拼写纠错, 丢词, 同义词改写, 基础改写和相似query改写, 目前支持了淘宝搜索和部分天猫搜索(拼写纠错&丢词等query算法)
同时针对外部的一些query需求, 打包开放了query处理相关的算法. 主搜的改写&纠错已经有外部业务方在使用( 包括: opensearch, 猫客, 闲鱼, 天猫海外, 阿里妈妈广告联盟等). 

2: 在创新业务方面:
2017年S2和墨青一起做了内容搜， 搭建了整个内容搜的流程并在2017年双十二全量, 之后整个内容搜交接给了孝恭他们. 17年底开始做QA这个创新业务. 产品上配合PD一起对QA的业务进行了不同尝试; 技术上和idst一起合作通过MRC，summarization等技术构建question对应的answer，并基于gbdt优化了线上bts的实际ctr效果. 最终推动从0到1构建了整个产品链路; 同时也指导实习生完成了一篇相关领域的论文, 目前在投.   

































我对我升6之后这两年的实际工作做了个总结: 

1:业务指标&技术&影响力: 
17年全程参与了迪拜塔项目, 在改写这块拿到了大盘2个点的提升; 并把改写覆盖率从81%提高到了90%. 同时在技术深度上尝试了skip-thought, doc2vec等在改写方面的应用并拿到了实际的业务效果; 最后和肖荣一起完成了一篇基于改写和相关性的论文, 发表在了wsdm2018上.   

在技术和影响力方面, 入职近5年来, 一直在负责query处理的基础算法相关. 包括: 拼写纠错, 丢词, 同义词改写, 基础改写和相似query改写, 目前支持了淘宝搜索和部分天猫搜索(拼写纠错&丢词等query算法)
同时针对外部的一些query需求, 打包开放了query处理相关的算法. 主搜的改写&纠错已经有外部业务方在使用( 包括: opensearch, 猫客, 闲鱼, 天猫海外, 阿里妈妈广告联盟等). 

2: 在创新业务方面:
2017年S2和墨青一起做了内容搜， 搭建了整个内容搜的流程并在2017年双十二全量, 之后整个内容搜交接给了孝恭他们. 17年底开始做QA这个创新业务. 产品上配合PD一起对QA的业务进行了不同尝试; 技术上和idst一起合作通过MRC，summarization等技术构建question对应的answer，并基于gbdt优化了线上bts的实际ctr效果. 最终推动从0到1构建了整个产品链路; 同时也指导实习生完成了一篇相关领域的论文, 目前在投.   





老婆想稳定, 生娃

* plan A : 继续待一年
    * 优点: 
        * 有可能拿到好的结果和绩效
        * 肖老板很挺, 峰哥有承诺
    * 缺点: 
        * 不一定能拿到太好的效果
        * 面子问题
* plan B : pdd
    * 优点: 钱多
    * 缺点:
        * 没有职级, 大家不知道你的真实水平label
        * 不一定那么缺人, 杂事多
* plan C: 转岗
    * 优点: 新的事情, 新的机会
    * 缺点: 从头再来

* plan D: wx 牧宇师兄
    * 优点: 靠谱的人, 很相信
    * 



plan A: 继续待一年

(1) 这个hb说如果改写拿到1个点, 纠错优化好. 会给很好的绩效.  

(2) 如果改写比较难没拿到1个点, 纠错优化好, 35+

(3) 实习生可以挑一个

 

plan B: pdd

* 







* 富含维生素B12的食物
    * 肉、鱼、奶制品中
* 富含维生素C的食物
    * 可多吃些桔子、浆果、土豆、西红柿和菠菜，可提高精子数, 有些时候甚至能在数月内让精子数翻倍

* 坚果
    * 饮食中多加入杏仁、核桃、榛子让受试者的精子数在14周内平均提高了16%
* 锻炼
    * 建议行走20分钟、做些俯卧撑或其他运动
    * 但注意不要过于激烈，尤其是长时间骑自行车、爬山、跑步，反而可能使精液质量下降







  jq: 最近也在考虑明年的情况, 担心现在做的和前面比较重复. 或者考虑下拿到效果之后, 后面或者下半年做一些新的? 

xlb: 其实做两三件事情就可以, 到时候再换新的方向, 也不一定能拿到很好的效果. 改写这块可以考虑先粗暴做下, 你懂的.



  jq: 那你感觉明年的 ppt里面会不会太单薄啊

xlb: 除了事情, 评委重要的是看你对做事情的思考. 

​        改写这块: (1) 先做了高频相似query; (2) 覆盖不够, 做了长尾; (3) 效果不好控制, 做了更加精细的同义词改写

​        我认为这个是可以的, 今年要多做一些技术深度的东西. 



jq: 但是QA这个我担心明年还是会被argue. 而纠错也是老的套路, 包装下也是能包装, 但是影响太小

xlb: 我不知道为啥hb一直看中纠错, 我感觉这个不是重点, 也没必要让实习生来搞. 最后也上不了线



jq: 嗯呢, 不过我有个想法. 或许可以拉徐往过来搞纠错. 实习生来搞一些研究型的东西

xlb: 这个可以, 我前面每次和hb聊都会提到, 要在你这边加一个hc, 纠错可以让一个新人来搞, 又能熟悉业务和开发



--------------

jq: 担心今年做的事情和前面比较重复, 考虑后面换个做个新的

xlb: 再换新的方向, 不一定能快速的拿到效果. 改写这块可以先粗暴搞下, 拿到效果. 你懂的



jq: 那你感觉明年ppt会不会太单薄

xlb: 两三件事情就可以了, 而且除了事情, 评委看的是你做事情的思考. 

改写这块: (1) 先做了高频相似query; (2) 覆盖不够, 做了长尾; (3) 效果不好控制, 做了更加精细的同义词改写. 

这个我认为可以. 不过今年要做一些有技术深度的事情. 



jq: 但是还是担心明年QA被argue, 而纠错也是老的套路, 包装能包装, 但是也影响比较小

xlb: 我不知道为啥hb一直看中纠错, 我感觉这个不是重点, 也没必要让实习生来搞. 最后也上不了线

jq: 嗯呢, 不过我有个想法. 或许可以拉徐往过来搞纠错. 实习生来搞一些研究型的东西

xlb: 这个可以, 我前面每次和hb聊都会提到, 要在你这边加一个hc, 纠错可以让一个新人来搞, 又能熟悉业务和开发

