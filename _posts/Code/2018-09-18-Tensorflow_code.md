---
layout: post
title: Blog&#58 TensorFlow相关代码
categories: [TensorFlow]
tags: TensorFlow
---



[TOC]



## tf基本概念

 在 Python 语言中, 返回的 tensor 是 [numpy](http://www.numpy.org/) `ndarray` 对象; 在 C 和 C++ 语言中, 返回的 tensor 是`tensorflow::Tensor` 实例.

TensorFlow 程序通常被组织成**一个构建阶段和一个执行阶段**. 在构建阶段, op 的执行步骤 被描述成一个图. 在执行阶段, 使用会话执行执行图中的 op.



创建**源 op (source op)**. 源 op 不需要任何输入, 例如 `常量 (Constant)`. 源 op 的输出被传递给其它 op 做运算.

计算图中, 操作间传递的数据都是 tensor.







##tf 变量

### tf.split

```python
# Split 'value' into 3 tensors with sizes [4, 15, 11] along dimension 1
split0, split1, split2 ``=` `tf.split(value, [``4``, ``15``, ``11``], ``1``)
tf.shape(split0)  ``# [5, 4]
tf.shape(split1)  ``# [5, 15]
tf.shape(split2)  ``# [5, 11]
# Split 'value' into 3 tensors along dimension 1
split0, split1, split2 ``=` `tf.split(value, num_or_size_splits``=``3``, axis``=``1``)
tf.shape(split0)  ``# [5, 10]
```



### tf.string_split

```python
tf.string_split(
    source,
    sep=None,
    skip_empty=True,
    delimiter=None,
    result_type='SparseTensor',
    name=None
)
```





### tf.FixedLenFeature

FixedLenFeature在处理特征时，会根据输入的shape来得到相应的输出tensor的shape。
当输入shape = []时，输出tensor的shape=（batch_size,)，
当输入shape=[k]时，输出tensor的shape= （batch_size,k）



###print 权重值

* self.sess.run(self.w)  # 返回值 'result' 是一个 numpy `ndarray` 对象.

### tf 常量

```python
# 构造器的返回值代表该常量 op 的返回值. 产生一个 1x2 矩阵
matrix1 = tf.constant([[3., 3.]])

# 创建另外一个常量 op, 产生一个 2x1 矩阵.
matrix2 = tf.constant([[2.],[2.]])
```



###权重初始化

```python
w = tf.Variable(tf.random_normal([self.n_input_size, self.n_hidden_size_1]))
```



## tf optimizer 



### 自动调整Learning rate的值

```python
learning_rate = tf.placeholder(tf.float32, shape=[])
optimizer     = tf.train.GradientDescentOptimizer(learning_rate=learning_rate).minimize(mse)


sess.run(train_step, feed_dict={learning_rate: 0.1})
```







##tf summary相关

### 常见summary用法

* **tf.summary.scalar**

    * 用来显示标量信息

    * tf.summary.scalar(name, tensor, collections=None)

    * ```python
        tf.scalar_summary('learning_rate', lr)
        ```

* **tf.summary.merge_all**

    * merge_all 可以将所有summary全部保存到磁盘，以便tensorboard显示。



###summary 汇总writer的一般代码

```python
# summary 汇总代码
summary_op = tf.summary.merge_all()
summary_writer = tf.summary.FileWriter(FLAGS.train_dir, sess.graph)

summary_str = sess.run(summary_op, feed_dict=feed_dict)
summary_writer.add_summary(summary_str, step)

# 最后释放write
summary_writer.close()
```

###summary自动化函数
```python
def variable_summaries(var):
  """Attach a lot of summaries to a Tensor (for TensorBoard visualization)."""
  with tf.name_scope('summaries'):
    mean = tf.reduce_mean(var)
    tf.summary.scalar('mean', mean)
    with tf.name_scope('stddev'):
      stddev = tf.sqrt(tf.reduce_mean(tf.square(var - mean)))
    tf.summary.scalar('stddev', stddev)
    tf.summary.scalar('max', tf.reduce_max(var))
    tf.summary.scalar('min', tf.reduce_min(var))
    tf.summary.histogram('histogram', var)
```

##tensorboard
* 启动
    *  tensorboard --logdir=logs --port=6099





## tf矩阵操作

### tf.multiply tf.matmul 区别

1.tf.multiply（）实现的是元素级别的相乘，也就是两个相乘的数元素各自相乘，而不是矩阵乘法. 返回Tensor

2.tf.matmul（）将矩阵a乘以矩阵b，生成a * b  返回Tensor



### np.dot 与 np.matmul 区别

1.二者都是矩阵乘法。
2.np.matmul中禁止矩阵与标量的乘法。
3.在矢量乘矢量的內积运算中，np.matmul与np.dot没有区别。





##tf 输入输出

### decode_csv

tf.decode_csv(records, record_defaults, field_delim=None, name=None)

* 首先records为reader读到的内容，这里为CSV (TXT)的一行。一般一行里面的值会用逗号或者空格隔开，
* 这里第三个输入参数就是指定用什么来进行分割，默认为逗号。
* 第二个输入参数是指定分割后每个属性的类型，比如分割后会有三列，那么第二个参数就应该是[['int32'], [], ['string']], 可见不指定类型（设为空[]）也可以。
* 如果分割后的属性比较多，比如有100个，可以用[ [] *100 ]来表示, 返回的col是长度为100的list。
    * col= tf.decode_csv(records, record_defaults=[ [ ] * 100 ], field_delim=‘ ’, name=None) 



###循环读取

``` python
match_data_path = tf.train.match_filenames_once(data_path + "/*.json" )
filename_queue = tf.train.string_input_producer(match_data_path, num_epochs=1)
reader = tf.TextLineReader()
key, value = reader.read(filename_queue)
with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())
    sess.run(tf.local_variables_initializer())
    coord = tf.train.Coordinator()
    threads = tf.train.start_queue_runners(coord=coord)

    try:
        while True:
            name, line = sess.run([key, value])
            sample = self._process_line(line, train)
            if sample is not None:
                data_set.append(sample)
                except tf.errors.OutOfRangeError:
                    self.logger.info('finish reading data path[{}]'.format(data_path))

                    coord.request_stop()
                    coord.join(threads)
```







##tf 常见问题



### tf tensor shape里面的问号

It means that first dimension is not fixed in the graph and it can vary between run calls





###ValueError: setting an array element with a sequence.

* 原因: 因为feed_dict里面的key是placeholder, 而value需要是list. 因此如果feed_dict的value是numpy的array, 需要首先转为list(narray)

### Tensorboard could not bind to unsupported address family ::

```
tensorboard --logdir=/tmp/mnist/log/ --port 51691 --post 本机ip
```



### AttributeError: seq_length







## word2vec basic 使用



### 明文embedding转换成distance程序使用的bin格式

```python
import numpy as np
import struct
import sys

if len(sys.argv) < 3:
    print "Usage: python ./convert_txt_to_bin.py infile outfile sep"
    sys.exit(-1)

infile = sys.argv[1]
outfile = sys.argv[2]
sep = ","
if len(sys.argv) > 3:
    sep = sys.argv[3]

index = 0
token2id = {}
id2token = {}
embeddings = {}

with open(infile, "r") as f1:
    for line in f1:
        sp = line.rstrip('\n').split(sep)
        word = sp[0]
        embed = sp[1].split(',')
        token2id[word] = index
        id2token[index] = word
        embeddings[index] = []
        for i,v in enumerate(embed):
            if len(v) < 1:
                break
            embeddings[index].append(float(v))
        index += 1

with open(outfile, "wb") as f:
    n_input = len(embeddings[0])
    f.write(str(len(embeddings))+" "+str(n_input))
    for i in range(len(embeddings)):
        f.write(id2token[i]+" ")
        vec = embeddings[i]
        s = struct.pack('f'*len(vec), *vec)
        f.write(s)
```

