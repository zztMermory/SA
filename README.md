# SA
---
## 思路
* 不同于以往将attention层增加在分类器层，提出新的基于注意力的情感分类模型，在embeddings层增加注意力，学习单词对情感分类的重要程度。
* 传统模型： input layer-> embeddings layer -> LSTM layer -> attention layer -> predict layer.
* 新模型：    input layer-> embeddings layer + attention layer -> sum layer  -> predict layer.

### sentiment and attention
* sentiment + attention.ipynb
    * 实验（模型及结果），实验1为新模型，其他为对比模型，结果如下表：

model | acc（%） | total params | 说明
---|:---:|:---:|---
实验2：baseline(new method 减去 attention)|85.47|6,000,301|baseline，去掉新模型中的注意力机制后的模型
实验3：baseline(LSTM)|86.09|6,219,777 |LSTM模型
实验4：baseline(LSTM+Attention)|89.08|6,232,777|LSTM+attention
实验1：__new method__(embeddings+Attention)|__89.12__|6,020,251 |提出的新模型，结果最优，参数少

* results__attention-weights.md
    * attention层的结果，即，每个单词对情感分类任务的权重大小。<br/> __从结果可以看出，对于大多数单词，可学习到对情感分类重要的单词具有较大的权重，而影响较小的具有较小的权重。__

### data
* imdb.npz SA数据集 25000 trainset,25000 testset.
