---
layout: post
title: Paper&#58 A Neural Attention Model for Sentence Summarization
categories: [Paper]
tags: Query
score: 
---


> Summarization based on text extraction is inherently limited, but generation-style abstractive methods have proven challenging to build.

# 任务

* Our method utilizes a local attention-based model that generates each word of the summary conditioned on the input sentence.
* 原先的文本摘要一般是通过抽取原文中的term来生成的, 本篇文章尝试了生成模型来生成摘要(文本不一定出现在原文中)
* 把文章x压缩成摘要(标题)y, 把原文x encoding后和标题中词的context concat后用NNLM来预测下一个词， 且可以把x和NNLM里的context窗口来做attention
* 感觉这种方法没有和NMT比较，是一个比较大的遗憾，需要比较多的已经有摘要或标题的文章做训练数据


