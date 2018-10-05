---
layout: post
title: Paper&#58 Distilling the Knowledge in a Neural Network
categories: [Paper]
tags: DeepLearning
score: 90
---

> Unfortunately, making predictions using a whole ensemble of models is cumbersome and may be too computationally expensive to allow deployment to a large number of users, especially if the individual models are large neural nets.

# 任务
* 机器学习提高指标的一种常见做法是Model Ensemble, 不过这个过程通常会很复杂而且耗时. 本文就尝试将ensemble model进行压缩为a single model. 术语叫做: distilling the knowledge in an ensemble model.

> Once the cumbersome model has been trained, we can then use a different kind of training, which we call “distillation” to transfer the knowledge from the cumbersome model to a small model that is more suitable for deployment.

