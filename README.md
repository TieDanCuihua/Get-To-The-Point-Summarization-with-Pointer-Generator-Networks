# Get-To-The-Point-Summarization-with-Pointer-Generator-Networks
通过指针网络生成abstract式摘要的学习与总结。

论文地址:https://arxiv.org/pdf/1704.04368.pdf, 利用指针网络以及覆盖机制，生成摘要。使用了CNN/Daily Mail dataset, 比其它基于attention的seq2seq发放提高了至少8 ROUGE points，比单纯使用指针网络提高了2ROUGE points。

代码实现参考了，https://github.com/becxer/pointer-generator/
Abstract式的摘要有一些问题：(1)生成词不准确(2)重复问题。

为了解决上述问题，(1)论文使用了指针网络，它可以从原文中直接复制关键词，从而解决了生成词不准确的问题。(2)使用了Coverage mechanism覆盖机制，它利用一个
Coverage向量c，其值为之前时间步的注意力a之和，然后在loss中加入了min(c,a),也就是说，如果之前某个词的注意力太高了，也就是c太高了，那么a，即现在的注意力就应该低一些，这样就避免了重复问题。

此代码的作者用以为卷积替代了全连接层，是因为快么？
