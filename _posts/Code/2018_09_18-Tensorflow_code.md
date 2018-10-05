---
layout: post
title: Blog&#58 TensorFlow相关代码
categories: [TensorFlow]
tags: TensorFlow
---




## tf读取数据

### 循环读取

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


