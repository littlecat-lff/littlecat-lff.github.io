---
layout: post
title: Paper&#58 Query Expansion with Locally-Trained Word Embeddings
categories: [Paper]
tags: Query
score: 70
---


> In general, these approaches provide global representations of words; each word has a fixed representation, regardless of any discourse context.

# 任务
* 使用topic限制的语料进行word embedding, 在全局word embedding 的基础上, 加强topic领域的信息.
* 主要假设是, 相同的word,在不同的语境或者topic下,会有不同的表示.(topic-specific representation)
> Documents on subtopics in a collection have very different unigram distributions compared to the whole corpus

# Local Word Embedding
* 文章的做法是, 根据用户的query, 首先选出该query相关的document集合, 然后在这个document集合上进行local word embedding, 而不再是在整个corpus上进行trian.
* 针对一个query, 选择相关的document, 文章是根据基于语言模型的KL 散度作为指标进行选取. 计算query下各个document的KL散度, 然后进行softmax选择document.

* 剩下的Query Expansion就没有看懂了, 写的太晦涩了, 全是文字描述. 而且和我们接下来的工作不相关.
