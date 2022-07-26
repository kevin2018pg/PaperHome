# PaperHome（weekly）
1. LTR：Learning Groupwise Multivariate Scoring Functions Using Deep
2. LTR：SERank Optimize Sequencewise Learning to Rank Using
3. QT-sim：sentence-bert  Sentence Embeddings using Siamese BERT-Networks
4. LTR：Learning Query and Document Relevance from a Web-scale Click Graphpdf
5. MMOE:
    ###### Highlights
    - 模型集成思想： 类似bagging的思路，即训练多个模型进行决策，从泛化能力，表达能力，学习能力上，应该都强于一个模型
    - 注意力思想: 为了增加灵活性， 为不同的模型还学习了重要性权重，这可能考虑到了在学习任务的共性模式上， 不同的模型学习的模式不同，那么聚合的时候，显然不能按照相同的重要度聚合，所以为各个专家学习权重，默认了不同专家的决策地位不一样
    - multi-head机制: 类似transformer， 多个专家其实代表了多个不同head, 而不同的head代表了不同的非线性空间，把输入特征映射到了不同的空间中去学习任务之间的共性模式。可以理解成从多个角度去捕捉任务之间的共性特征模式
6. youtube-multitask（MMoE-PosBias）：
    ###### Highlights
    - 模型基于wide&deep结构，加入浅层position bias消偏网络，降低位置偏差对模型
    - 输入特征包括position信息和device type，不同的机型位置偏差不同，FC输出cat到交互目标（如点击任务，时长任务）中，再过顶层sigmoid
    - 训练时，防止此特征过拟合，另外防止分布式训练gate网络陷入局部最优，加入dropout机制（0.1），推理时取默认缺失值
    - 实验位置特征加入input输入share DNN，无效果；gate网络从share DNN输入切换至底层embedding输入，无效果；
    
