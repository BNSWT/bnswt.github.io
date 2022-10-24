---
title: '论文笔记(Learning functional properties of proteins with language models)'
date: 2022-10-24
permalink: /posts/2022/10/note-for-paper-1/
tags:
  - Protein Language Model
  - Functional property learning
---

蛋白质数据的表征，是解决当前生物医学问题的一大关键，比较好的方法是从优秀的语言模型汲取灵感，以构建类似的生信模型，这些模型最近已经在`序列-结构-功能`关系提取上获得了很大的成功。这篇论文对蛋白质表征学习做了深入的调研，分类并解释每一种方法，依次在如下预测目标中对他们进行评估：

1. 蛋白质间的语义相似性
1. ontology-based protein function
1. 药物靶蛋白族
1. 突变对蛋白质-蛋白质亲和性的改变

> Ontology(https://en.wikipedia.org/wiki/Ontology_(information_science))
> 在计算机科学和信息科学中，本体是指对概念、数据和实体之间的类别、属性和关系的表示、命名和定义，这些概念、数据和实体构成了一个、大量或所有的论域[1]。本体提供的是特定领域之中那些存在着的对象类型或概念及其属性和相互关系[2]；或者说，本体就是一种特殊类型的术语集，具有结构化的特点，且更加适合于在计算机系统之中使用；或者说，本体实际上就是“对特定领域之中某套概念及其相互之间关系的形式化表达（formal representation）”
> Ontology-based data integration(https://en.wikipedia.org/wiki/Ontology-based_data_integration)
> 使用一个或更多ontology去整合大量混杂的数据信息

## 背景知识

截至2021年5月，UniProt收录了大约215,000,000条蛋白质序列，然而只有560,000(~0.26%)条序列被人工检查、标记过。这是因为标记需要大量cost。为了进行自动标记，很多团队开始研究新的计算方法以预测蛋白质的：

+ 酶活动
+ 生物物理学特性
+ 蛋白质-受体交互
+ 3D结构
+ 各种功能

蛋白质功能预测(Protein function prediction, PFP)是蛋白质功能对蛋白质的自动化或半自动化的assignment。Gene Ontology(GO)系统是一个层次的概念网络，代表着从基因到蛋白质的映射，其底层逻辑则是蛋白质亚细胞定位和生物逻辑过程。

PFP任务中最具综合性的benchmark是Critical Assessment of Functional Annotation(CAFA)，需要对一个目标蛋白质set预测他们基于GO的功能联系，然后再进行人工检验核算结果。

## Overview

对不同方法根据技术特征和其application分类，然后进行评估。具体评估任务涵盖了：

1. 语义相似性推理
2. ontology-based蛋白质功能预测
3. 药物靶蛋白族
4. 蛋白质-蛋白质亲和性估计


