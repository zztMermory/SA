# SA
---
## 思路

### sentiment and attention
* sentiment + attention.ipynb
    * 基于attention机制的sentiment classification 初步模型及实验对比

model | acc（%） | total params |
---|---|---|
实验2：baseline(new method - attention)|85.47|6,000,301
实验3：baseline(LSTM)|86.09|6,219,777
实验4：baseline(LSTM+Attention)|89.08|6,232,777
实验1：__new method__(embeddings+Attention)|__89.12__|6,020,251

1. 实验1是提出的新模型，结果最优，参数少；<br/>实验2是去掉新模型中的注意力机制后的模型，baseline；<br/>实验3是LSTM模型,实验4是LSTM+attention模型，准确率和新模型不相上下，但是比新模型参数多200,000个左右。<br/>ps:实验3结果不稳定：出现过84%，87.22%.

* sentiment + attention.ipynb
    * attention层的结果，即，每个单词对情感分类任务的权重大小。__从结果可以看出，对于大多数单词，可学习到对情感分类重要的单词具有较大的权重，而影响较小的具有较小的权重。__

### data
* imdb.npz SA数据集 25000 trainset,25000 testset.
