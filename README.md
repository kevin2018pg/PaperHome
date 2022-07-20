# PaperHome（weekly）
1. LTR：Learning Groupwise Multivariate Scoring Functions Using Deep
2. LTR：SERank Optimize Sequencewise Learning to Rank Using
3. QT-sim：sentence-bert  Sentence Embeddings using Siamese BERT-Networks
4. LTR：Learning Query and Document Relevance from a Web-scale Click Graphpdf
5. MMOE:
    - 模型集成思想： 类似bagging的思路，即训练多个模型进行决策，从泛化能力，表达能力，学习能力上，应该都强于一个模型
    - 注意力思想: 为了增加灵活性， 为不同的模型还学习了重要性权重，这可能考虑到了在学习任务的共性模式上， 不同的模型学习的模式不同，那么聚合的时候，显然不能按照相同的重要度聚合，所以为各个专家学习权重，默认了不同专家的决策地位不一样
    - multi-head机制: 类似transformer， 多个专家其实代表了多个不同head, 而不同的head代表了不同的非线性空间，把输入特征映射到了不同的空间中去学习任务之间的共性模式。可以理解成从多个角度去捕捉任务之间的共性特征模式
