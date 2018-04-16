
graph embedding是学习节点隐表示向量，在一个连续向量空间中对节点的关联关系进行编码，便于计算节点之间的关联关系，同时，graph具有传播能力，通过random walk可以挖掘多度关系，能有效的提升覆盖度，扩大召回。

Graph Embedding是学术界一个重要研究方向，比如
deep walk：是语言模型和无监督学习从单词序列扩展到图结构上的一个典型方法，该方法将截断游走的序列当成句子进行学习，之后采用word2vec中Skip-Gram模型进行训练，得到每个节点的embedding向量。Line只针对边进行采样，Node2vec可以调节参数来进行BFS或者DFS的抽样。

Graph Embedding的基本思路是，对graph进行采样（Sampling），采出来的序构建模型（Embedding）。

为什么我们还需要构建graph？
因为graph具有**传播能力**，它不仅能_有效的提取出来直接关联，而且可以通过**游走策略**，挖掘出来二度、三度的关系。_我们认为，朋友的朋友，也是朋友，也存在一定的弱关联，有效的利用这种传播能力，能解决购买数据的稀疏性，大大的提升覆盖。

####三步骤工作：

#####一、构建graph
基于用户购买行为构建graph，节点：商品，边：商品间同时购买的行为，权重：同时购买的比重，可以是购买次数、购买时间、金额等feature；

为什么需要带权重的Graph？
因为random walk等传统方法不适用商品网络，商品节点动辄上千万，其中大部分节点的关联性是很弱的，也就是冷门商品居多，只有少部分商品构建的graph是热点，如果采用random walk去采样，会采出很多冷门节点的序列，所以我们基于边的权重去采样（weighted walk），使采样尽量往热门节点方向游走，这样采样出来的样本置信度才更高。

```
因此，我们的输入是一个带weight的graph ，Graph定义：G = （V，E，W），V = vertex （顶点或者节点，在bundle的问题中，特指商品），E = edge（边，在bundle的问题中，特指共同购买） ，W = weight（边的权重，共同购买的次数、时间），如下图，接下来就要进行sampling。

```




#####二、weighted walk采样
基于权重Sampling（weighted walk）作为正样本的候选，负样本从用户非购买行为中随机抽样；

传统的方法，比如deep walk，它的Sampling本质上是有两部分，首先，通过random walk的方式进行游走截断，其次，在仍给word2vec中Skip-Gram模型进行embedding之前，用negative sampling的方式去构造样本；这种随机采样的方法会大概率的将热门节点采集为负样本，这种方式适用于语言模型，因为在自然语言中，热门的单词均为无用单词（比如he、she、it、is、the）。对于我们的商品网络，刚好相反，热门商品往往是最重要的样本，如果采用negative sampling的方式去构造样本，模型肯定是学不出来。因此，我们基于边的权重去采样（weighted walk），使采样尽量往热门节点方向游走


```
Algorithm 1 Weigted Walk(G,n,Walks)
Input: Graph G(V,E,W)
   Step n
Output: walk
Initialization: walk to empty
  For each vi ∈ V do
   Append vi to walk
   For j=1...n do
     vj=GetNeighbor(G,vi)
     Append vj to walk
   Return walk
Algorithm 2 GetNeighbor(G,vi)
Input: Graph G(V,E,W)
   Node vi
Output: next node vj
vj=WeightedSample(vi,w)
```
算法实现是在**odps graph平台**实现的，一个分布式的图计算平台，离线graph有2亿条边，3千万节点，10分钟跑完所有的数据，实时部分，我们实现了每分钟最高可更新10w的Graph边的结构


#####三、Embedding
embedding部分将无监督模型升级成有监督模型，将基于weighted walk采出来的序，构造成item-item的pair对，送给有**监督模型（DNN）**训练。

将基于weighted walk采出来的序，构造成item-item的pair对，送给embedding模型，我们构造了一个有监督embedding模型（DNN），规避无监督模型无法离线评估模型效果的问题。