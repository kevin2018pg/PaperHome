# PaperHome（weekly）
## Rank
### LTR
1. LTR:Learning Groupwise Multivariate Scoring Functions Using Deep
    - from Google，使用tf ranking框架实现，核心是Groupwise分组，通过超参数控制。本人实践基于自己数据上线效果弱于基于xgb实现的lambdaMART。
2. LTR:SERank Optimize Sequence wise Learning to Rank Using
    - from 知乎，核心点是加入se block结构做特征重要性表达，类似于ResNet；本人实践基于自己数据上线效果与基于xgb实现的lambdaMART基本一致。
3. LTR:Learning Query and Document Relevance from a Web-scale Click Graph
    - 用于构造样本

### CTR
1. FM:
    - 转化为 <vi, vj> 向量点积，正定阵转化为上三角阵。<vi, vj>表示xi与xj这两个bit在embedding空间的相似程度；
    - 目标是更新vi，参数量从o(n^2)降解为o(n*k)(k<<n)，通过直接建模V来间接建模W，避免了LR样本中二阶交叉稀疏导致的W难以学习的问题。
2. wide&deep:Wide & Deep Learning for Recommender Systems
    - wide&deep模型中如何确定哪些特征适用于wide侧哪些特征适用于deep侧？
    个人理解：需要凭借业务理解， 把强特/人工交叉的特征/id类特征放入wide侧，但是实践效果可能会出现w&d效果与只用deep效果一致甚至更差
    - Wide侧为什么用L1 FTRL 训练？不用SGD系列？
    wide侧人工交叉特征维度空间较大，需要稀疏解，压缩权重大小和特征维度。Deep侧数值特征或者类别特征的embedding，都不稀疏，所以沿用SGD系优化算法即可。
    - Wide部分中为什么要将连续特征离散化？
    增加非线性+增强对于异常特征值work
3. DeepFM:
    - 本人实践加入LHUC结构，对重要特征进行单独建模表征，效果有明显提升。
4. xDeepFM

### MTL
1. MMOE:
    ###### Highlights
    - 模型集成思想： 类似bagging的思路，即训练多个模型进行决策，从泛化能力，表达能力，学习能力上，应该都强于一个模型
    - 注意力思想: 为了增加灵活性， 为不同的模型还学习了重要性权重，这可能考虑到了在学习任务的共性模式上， 不同的模型学习的模式不同，那么聚合的时候，显然不能按照相同的重要度聚合，所以为各个专家学习权重，默认了不同专家的决策地位不一样
    - multi-head机制: 类似transformer， 多个专家其实代表了多个不同head, 而不同的head代表了不同的非线性空间，把输入特征映射到了不同的空间中去学习任务之间的共性模式。可以理解成从多个角度去捕捉任务之间的共性特征模式
2. youtube-multitask（MMoE-PosBias）:
    ###### Highlights
    - 模型基于wide&deep结构，加入浅层position bias消偏网络，降低位置偏差对模型
    - 输入特征包括position信息和device type，不同的机型位置偏差不同，FC输出cat到交互目标（如点击任务，时长任务）中，再过顶层sigmoid
    - 训练时，防止此特征过拟合，另外防止分布式训练gate网络陷入局部最优，加入dropout机制（0.1），推理时取默认缺失值
    - 实验位置特征加入input输入share DNN，无效果；gate网络从share DNN输入切换至底层embedding输入，无效果；
3. PLE:

## LanguageModel
1. QT-sim：sentence-bert  Sentence Embeddings using Siamese BERT-Networks