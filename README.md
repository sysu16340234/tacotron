# 论文<<Tacotron: Towards End-to-End Speech Synthesis>>阅读

## 1.模型介绍
tacotron的主干架构是基于seq2seq的attention机制的模型,由encoder-decoder机制和post-processing的网络组成,结构如下;
![tacotron](https://github.com/sysu16340234/tacotron_reading/blob/master/tacotron.png?raw=true)
### seq2seq模型
seq2seq模型的意义是Sequence to Sequence,目的是将一个输入序列转化为一个输出序列,seq2seq由两部分组成,encoder和decoder,encoder的作用是将一个输入序列X转换为一个语义向量c,decoder使用语义向量c作为输入产生输出序列Y,其中encoder和decoder都由RNN实现
### attention模型
attention模型是为了解决提取语义焦点的问题而产生的,将encoder输出的特征向量进行加权求和后作为decoder的输入;
### CBHG模型

