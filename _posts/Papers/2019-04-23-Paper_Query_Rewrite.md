---
layout: post
title: Paper&#58 Paper Query
categories: [Paper]
tags: Query
score: 
---

[TOC]



## Synonym



SynonymNet: Multi-context Bilateral Matching for Entity Synonyms

An enhanced computational feature selection method for medical synonymidentification via bilingualism and multi-corpus training



Improving Information Retrieval Results for Persian Documents using FarsNet

Unsupervised Sense-Aware Hypernymy Extraction

Enhanced Word Representations for Bridging Anaphora Resolution

Calculated attributes of synonym sets

Path-Based Function Embedding and its Application to Specification Mining

Can Network Embedding of Distributional Thesaurus be Combined with Word Vectors for Better Representation?

Synonym Discovery with Etymology-based Word Embeddings

Word Sense Disambiguation using WSD specific Wordnet of Polysemy Words

Semantic Composition and Decomposition: From Recognition to Generation

Massive Query Expansion by Exploiting Graph Knowledge Bases

Unsupervised antonym-synonym discrimination in vector space

Self-Supervised Synonym Extraction from the Web.

[When similarity becomes opposition: Synonyms and antonyms discrimination in dsms](http://colinglab.humnet.unipi.it/wp-content/uploads/2012/12/IJCoL01_01-04-Santus-Lu-Lenci-etal.pdf)



2019 AAAI Mining Entity Synonyms with Efficient Neural Set Generation

EACL2017 Distinguishing Antonyms and Synonyms in a Pattern-based Neural Network

ACL2016 Integrating Distributional Lexical Contrast into Word Embeddings for Antonym-Synonym Distinction

Semantic Word Clusters Using Signed Normalized Graph Cuts

IJCAI 2015 Medical Synonym Extraction with Concept Space Models

IJCNLP2013 Uncovering distributional differences between synonyms and antonyms in a word space model

WWW-2016 [Automatic discovery of attribute synonyms using query logs and table corpora](https://dl.acm.org/citation.cfm?id=2874816)

WWW-2013 [Graded relevance ranking for synonym discovery](https://dl.acm.org/citation.cfm?id=2487855)

AAAI-2015 [Unsupervised phrasal near-synonym generation from text corpora](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/viewPaper/9473)

WWW-2015 [Synonym discovery for structured entities on heterogeneous graphs](https://dl.acm.org/citation.cfm?id=2745396)

LREC-2018 Word Embedding Approach for Synonym Extraction of Multi-Word Terms

KDD_2017_[Automatic Synonym Discovery with Knowledge Bases](http://hanj.cs.illinois.edu/pdf/kdd17_mqu.pdf)



## Rewrite

Query Expansion , Query Reformulation, Query Rewrite



Learning to Coordinate Multiple Reinforcement Learning Agents for Diverse QueryReformulation

On the Equilibrium of Query Reformulation and Document Retrieval



Query Expansion Techniques for Information Retrieval: a Survey

EMNLP-2017 Task-Oriented Query Reformulation with Reinforcement Learning

CIKM-2012 Structured Query Reformulations in Commerce Search

WWW-2018 Beyond Keywords and Relevance: A Personalized Ad Retrieval Framework in E-Commerce Sponsored Search

CIKM-2017 Learning to Attend, Copy, and Generate for Session-Based Query Suggestion

AAAI-2019 Sequence to Sequence Learning for Query Expansion

EMNLP-2013 Identifying Web Search Query Reformulation using Concept based Matching

2014 Query Expansion Strategy based on Pseudo Relevance Feedback and Term Weight Scheme for Monolingual Retrieval

CIKM-2009 Analyzing and evaluating query reformulation strategies in web search logs

CIKM-2013 Beyond clicks: query reformulation as a predictor of search satisfaction

Unsupervised Graph-based Rank Aggregation for Improved Retrieval

SIGIR_2017_Embedding-based query Expansion for Weighted Sequential Dependence Retrieval Model



绉纱连衣裙女士米白色裙子2019春



word2vec在词的相似度任务上的性能不如SVD这样的方法，具体可以看一下Levy的论文；另外我认为，鉴于word2vec的Skip-gram模型实际上是在分解PMI矩阵，NS的步骤也可以看成是一种NCE采样的简化，本质上还是归结于统计模型基于统计假设，只有分析出其中work的结构才能更进一步

作者：珙成胧
链接：https://www.zhihu.com/question/29426311/answer/128504882


Levy, Omer, and Yoav Goldberg. &quot;Neural word embedding as implicit matrix factorization.&quot; Advances in neural information processing systems. 2014.

一个问题是要找近义词。
还有一个问题是为什么这些词是近义词而不是同义词。
在RNNLM能够证明自己能够拳打脚踢各种问题（个人猜测这基本不可能）之前。
传统方法肯定还能在一些问题上存活很久……



word2vec学出来的模型可解释性太差；基于context统计的distributional representation，每个维度都容易理解，这是一大优势。此外，distributional representation的代表模型之一explicit semantic analysis（ESA），在很多任务上性能不比word2vec差，当然计算效率是ESA的主要问题。

作者：刘知远
链接：https://www.zhihu.com/question/29426311/answer/44321156




如果需要含义基本一致的同义词，主要有以下几类：

一：中文英文对应的同义词。比如：摩拜，对应英文：Mobike。饿了吗，英文：ele。 

二：在搜索引擎中用户使用基本一致的词语。比如：儿童，宝宝。女孩，女生。跑酷，酷跑。打扮，装扮。

三：全称/简称，例如：招商银行，简称：招行。上海交通大学，简称：上海交大。

四：别名，例如：西红柿，番茄。

作者：吴斌
链接：https://www.zhihu.com/question/40777785/answer/226765870



在电商搜索环境中，同义词分成好几类：

     1. 品牌同义词：nokia=诺基亚，Adidas=阿迪达斯
    
     2. 产品同义词：投影仪≈投影机，电话≈cell phone; automobile 和car。
    
     3.旧词和新词：自行车  -> 脚踏车
    
     4.南方用词和北方用词：番茄-> 西红柿。
    
     5.传统的同义词：储物柜和收纳柜。
    
     6.错别字同义词：瑜伽和瑜珈（错误写为斜王旁）
     
     7. 对应英文来说，还有词干提取，如单复数、动词原形和ing形式
        英文还有一个特殊的现象，例如两个单词可以分开写，也可以合并在一起，例如keychain和key chian（钥匙链），boyfriend 和boy friend。






### Automatic Synonym Discovery with Knowledge Bases









- 目前concept基本来源是宝贝title和一些内容中抽取, concept下挂载的商品中基于文本匹配以及对concept进行同义/上下位 扩展来挂载对应的商品占比比较多(保证准确率). 
- 这样就导致concept召回的宝贝和目前主搜已有的query改写 overlap比较重( 即线上已有的改写已经能cover这批concept带来的大部分的增益宝贝) 





数英切分只更新了q_final_cn, 没更新k

分词模块使用了q_final_cn, 只更新了ori_k



1: 改写, 类目预测用的是q_final_cn

2: 扩召回用的是k

3: 在线pidvid改写, 使用的是分词结果







**天猫店铺**

* 冠能旗舰店狗粮    —> proplan冠能官方旗舰店
* 圣罗兰旗舰店官网  ---> YSL圣罗兰美妆官方旗舰店
* 城野医生旗舰店官方旗舰  —>   DrCiLabo海外旗舰店 (同义词是dr.ci.labo)
* 安踏儿童官方旗舰店童装  —> anta安踏童装旗舰店
* 小米手机官网旗舰             —> 小米官方旗舰店
* 口红香奈儿限量版官网 正品 



**淘宝店铺**

* 大头家0728 --> 大头家0728 (一钻店铺)

* 大姗姗家  --> 大姗姗家 FASHION SHOP大码女装独家定制

* 晚安宇宙  --> 晚安宇宙wan

* 卡哈特  --> carhartt卡哈特

* 江南e柜 --> 江南e柜北京店

* wassup  --> wassup中国

  
  
  
  
  
  
* 高频query

    * 相似query
    * 类目&意图改写

* 低频query
    * 低质量&少结果 —> i2i改写(同款&标题相似) (i2i, u2i, s2i) 
    * 相似query
    * 向量召回
    * 类目&意图改写

  



w1 w2 w3 红色  —> OR ( w1 w2 )



title: w1 w2 * * * *      + 属性 (红色) + 类目 + 扩充字段(算法)  ==== > TODO: 图像 

title + 图像 + 属性 —> 向量召回(中低频),  中高频—> 个性化向量召回(全类目覆盖)





* 宝贝生成新的字段: 卖家没填写的, 又比较关键的一些term (tmall brandphrase, )
* 搜索了query但是在全网成交的宝贝占据的比例
* 





 w1 w2 

* 生成式改写: 
    * 客厅 空调 2p —> 柜式 空调 2p
* 点击反馈改写
    * bert对候选进行判别—> 线上+user进行效率筛选
* 纠错
    * 技术点. bert or deep model + 行为电商知识(pv, pv, 召回量. 片段),  问题: 电商纠错 & 数英错误纠正
    * 模型思路. 上线(离线搞)方案, 数据效果(举一些难的例子)



