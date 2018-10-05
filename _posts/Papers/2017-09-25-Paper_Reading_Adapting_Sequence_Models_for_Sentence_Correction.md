---
layout: post
title: Paper&#58 Adapting Sequence Models for Sentence Correction
categories: [Paper]
tags: Query
score: 
---



we find that character based models are generally more effective than word-based models.
and models that encode subword information via convolutions, and that modeling the output data as a series of diffs improves effectiveness over standard approaches.

subword information: We model morphology by considering subword units, and representing words by a sum of its character n-grams. 中文也有对应的subword操作, 笔画的embedding.

