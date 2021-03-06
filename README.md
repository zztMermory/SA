# SA
---
## 思路
* 不同于以往将attention直接加在分类器上，针对情感分类的特点：只有部分 __情感单词及副词__ 决定情感分类结果，提出新的基于注意力的情感分类模型，在embeddings层增加注意力机制，__学习单词对情感分类的重要程度__。
* 传统模型： input layer-> embeddings layer -> LSTM layer -> attention layer -> predict layer.
* 新模型：    input layer-> embeddings layer + attention layer -> sum layer  -> predict layer.

---
## sentiment and attention
* ### sentiment + attention.ipynb
    * 实验（模型及结果），实验1为新模型，其他为对比模型，结果如下表：

model | acc（%） | total params | 说明
---|:---:|:---:|---
实验1：__new method__(embeddings+Attention)|__89.12__|6,020,251 |提出的新模型，结果最优，参数少
实验2：baseline(new method 去掉 attention)|85.47|6,000,301|baseline，去掉新模型中的注意力机制后的模型
实验3：baseline(LSTM)|86.09|6,219,777 |LSTM模型
实验4：baseline(LSTM+Attention)|89.08|6,232,777|LSTM+attention

* ### results__attention-weights.md
    * attention层的结果，即，每个单词对情感分类任务的权重大小。<br/> __从结果可以看出，对于大多数单词，可学习到对情感分类重要的单词具有较大的权重，而影响较小的具有较小的权重。__

id |word | 翻译 | weights(前10个单词) | |id |word | 翻译 | weights(后10个单词) |
--- |:---:|:---:| ---|---|--- |:---:|:---:| ---
1 | unwatchable | 不能观看 | 1.4780544 |  |19999 | film | 电影 | -3.916907
2 | pointless | 无意义 | 1.4707756 | |19998 | people | 人 | -3.877606
3 | excellently | 出色 | 1.3945274| |19997 | big | 大 | -3.5991306
4 | poorly | 糟糕 | 1.3889633| |19996 | one | 一 | -3.5805032
5 | disappointing | 令人失望 | 1.3874675| |19995 | fact | 事实 | -3.5307567
6 | baldwin | 鲍德温 | 1.3558208| |19994 | never | 决不 | -3.4727523
7 | embarrassment | 困窘 | 1.3359343| |19993 | end | 结束 | -3.471965
8 | mildly | 温和 | 1.3224405| |19992 | comes | 来 | -3.461487
9 | refreshing | 清爽 | 1.3119076| |19991 | girl | 女孩 | -3.415614
10 | waste | 浪费 | 1.3099878| |19990 | sure | 当然 | -3.3848553

### data
* imdb.npz SA数据集 25000 trainset,25000 testset.
