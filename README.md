# SA
---
### sentiment and attention
基于attention机制的sentiment classification 初步模型
sentiment attention的思想：从根部解决情感特征词选择问题，使用注意力机制自动学习各个单词对情感分类结果的影响程度。
__结果见 attention-weights-results.md ，从该文件可以看出，大多数对情感分类重要的单词，具有较大的权重，而影响较小的具有较小的权重。 __
### data
* imdb.npz SA数据集 25000 trainset,25000 testset.
