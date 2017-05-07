---
layout: post
title: Blog&#58 bias_term(偏置项,截距项)在ML和DL中的作用,为什么正则化不限制bias_term
categories: [Paper]
tags: ML,DL,Math
score: 90
---

> 忘记什么时候被人问了一句, 在ML和DL的L1和L2中为什么只对weight进行惩罚, 不对bias term进行惩罚呢. 瞬间愣住了, 还真没有想到过这个问题. 

回来仔细做了下功课, 总结下. Try to Explain in My Own Language.

# bias term的作用
* w只能在y轴方向上压缩或者拉长函数曲线, 而bias term能够让函数曲线左右移动, 这样w和b的组合就能够拟合平面区间上的任何曲线.
* 为了简单起见, 就拿线性回归的方程式(eg: Y = w * x + b. )来解释下. 如果没有bias, 那么方程的形式 Y = w * x, 这个假设空间中的所有函数图像都是经过原点的直线, 但是更多的情况下, 最优的拟合曲线并不是经过原点的曲线,此时就需要bias来调整拟合的函数曲线. 



# bias term的正则化

* 正则化的目的是为了防止参数过于复杂导致的过拟合情况, 参数复杂情况是和 w 参数的个数直接相关的, 而bias并不会提高函数的复杂性, 只是对网络做了一个线性的平移. 因此bias term的存在并不会影响函数的复杂性情况. 因此正则项并不需要针对bias进行惩罚
* 如果对bias进行惩罚, 那么模型会偏向于选择距离原点进的函数曲线, 但是这没有任何意义..反而有可能会导致偏离了最优的函数曲线.

# 参考
* 下面是一些参考问答
    - 偏置单元（bias unit），在有些资料里也称为偏置项（bias term）或者截距项（intercept term），它其实就是函数的截距，与线性方程 y=wx+b 中的 b 的意义是一致的。
    - 在 y=wx+b中，b表示函数在y轴上的截距，控制着函数偏离原点的距离，其实在神经网络中的偏置单元也是类似的作用。
    - wx+b的b: 打个比方 有点(1,1) 属于1类  点(2,2)属于2类，请问是否能从原点画一条线把他们分开. --> 不可以，所以需要偏置值b，这样线段就不从(0,0)点出发了
    - 从数学层面上讲，偏置项可以将激活函数做横向平移。对于输入信号，可以通过乘以权重值将激活函数进行压缩或拉伸，但无法实现左右平移.
* 关于正则化
    - Moreover, in case a large offset is needed for whatever reason, regularizing it will prevent finding the correct relationship.
    - What's the purpose of regularisation? Isn't it to keep weight values as small as possible? Thus, what sense does it make to keep the discriminant function close to the origin when the data may well be strongly biased? Doing so (bias regularisation) clearly limits the learning expressiveness of the NN.