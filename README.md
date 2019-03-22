# 论文<<Tacotron: Towards End-to-End Speech Synthesis>>阅读

## 1.模型介绍
tacotron的主干架构是基于seq2seq的attention机制的模型,由encoder-decoder机制和post-processing的网络组成,结构如下;

![tacotron](https://github.com/sysu16340234/tacotron_reading/blob/master/tacotron.png?raw=true)
### seq2seq模型
seq2seq模型的意义是Sequence to Sequence,目的是将一个输入序列转化为一个输出序列,seq2seq由两部分组成,encoder和decoder,encoder的作用是将一个输入序列X转换为一个语义向量c,decoder使用语义向量c作为输入产生输出序列Y,其中encoder和decoder都由RNN实现
### attention模型
attention模型是为了解决提取语义焦点的问题而产生的,将encoder输出的特征向量进行加权求和后作为decoder的输入;
### CBHG模型
CBHG模型的结构如下:

![CBHG](https://github.com/sysu16340234/tacotron_reading/blob/master/CGBG.png?raw=true)
第一层由K个长度从1到k的一维卷积核组成,输入序列在这一层被提取在不同长度上具有的特征,下一层为池化层,池化后需要经过两层一维的卷积层进一步提取特征,经过两层卷积之后有一个residual connection将第一层输出的结果和两次卷积结果相加进入下一层highwaylayer,得到的输出进入一个双向RNN得到输出结果;
### pre-net
pre-net结构的作用是对输入进行一系列非线性变换,使模型有更强的泛化能力;
### post-processing
后处理网络的目的是将RNN的输出转化为可合成的目标波形,由于它能够得到所有解码后的序列因此它有向前和向后的信息来纠正每一帧的预测误差,在文中使用的后处理网络是CBHG;

## 2.相关参数
![param](https://github.com/sysu16340234/tacotron_reading/blob/master/param.png?raw=true)
