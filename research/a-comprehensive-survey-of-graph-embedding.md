####Graph Embeding
#####Definition

By representing a graph as a (or a set of) low dimensional vector(s), graph algorithms can then be computed efficiently.
graph embedding aims to represent a graph in a low dimensional space which preserves as much graph property information as possible.

-The term graph embedding has been used in the literature in two ways: to represent an entire graph in vector space, or to represent each individual node in vector space. In this paper, we use the latter definition since such representations can be used for tasks like node classification, differently from the former representation.

-Challenge
-Obtaining a vector representation of each node of a graph is inherently difficult and poses several challenges
-1. Choice of property
A “good” vector representation of nodes should **preserve the structure of the graph** and **the connection between individual nodes**. The first challenge is choosing the property of the graph which the embedding should preserve.
-2. Scalability 
Most real networks are large and contain millions of nodes and edges — embedding methods should be scalable and able to process large graphs. 
-3. Dimensionality of the embedding: 
Finding the optimal dimensions of the representation can be hard. For example, higher number of dimensions may increase the reconstruction precision but will have high time and space complexity.

Types of Graph
homogeneous graph, heterogeneous graph, attribute graph, etc So 
The input of graph embedding: varies in different scenarios. 
The output of graph embedding: is a low-dimensional vector representing a part of the graph (or a whole graph).

The problem of graph embedding is related to two traditional research problems, 
1. i.e., graph analytics [8] and
2. representation learning [9]. 

graph embedding aims to represent a graph as low dimensional vectors while the graph structures are preserved.

graph analytics aims to mine useful information from graph data.

representation learning obtains data representations that make it easier to extract useful information when building classifiers or other predictors [9].

####2. Problem Formalization
#####2.1 Notation and Definition
Definition 1 Graph Embedding. 
A graph is G = (V, E), where v ∈ V is a node and e ∈ E is an edge. G is associated with a node type mapping function fv : V → Tv and an edge type mapping function fe : E → Te

    -(Graph embedding) Given a graph G = (V, E), a graph embedding is a mapping f : vi → yi ∈ R d ∀i ∈ [n] such that d << |V| and the function f preserves some proximity measure defined on graph G. 
    An embedding therefore maps each node to a low-dimensional feature vector and tries to preserve the connection strengths between vertices. 

Definition 2. 
A homogeneous graph Ghomo = (V, E) is a graph in which |Tv| = |Te| = 1

Definition 3. 
A heterogeneous graph Ghete = (V, E) is a graph in which |Tv| > 1 and/or |Te| > 1

Definition 4. 
A knowledge graph Gknow = (V, E) is a directed graph whose nodes are entities and edges are subject-property-object triple facts h, t ∈ V are entities and r ∈ E is the relation. call < h, r, t > a knowledge graph triplet

Note that the entities and relations in a knowledge graph are usually of different types [14], [15]. Hence, knowledge graph can be viewed as _an instance of the heterogeneous graph_.

Definition 5. 
The first-order proximity（edge weight sij） between node vi and node vj is the weight of the edge eij , i.e., Ai,j .
It compares _the direct connection strength between a node pair._
    
    -The edge weight sij is generally treated as a measure of similarity between the nodes vi and vj. The higher the edge weight, the more similar the two nodes are expected to be.

The second-order proximity compares _the similarity of the nodes’ neighbourhood structures._ The more similar two nodes’ neighbourhoods are, the larger the second-order proximity value between them. 
    -Let si = [si1, · · · , sin] denote the first-order proximity between vi and other nodes. Then, second-order proximity between vi and vj is determined by the similarity of si and sj.

####Probelm setting
problem setting consists of
**the embedding input** and **the embedding output.**

#####Four types input
######1. homogeneous graph
Definition 2. 
A homogeneous graph Ghomo = (V, E) is a graph in which |Tv| = |Te| = 1

1.1. the weighted (or directed)
Adv:  the weights and directions of the edges provide more information about the graph, and may help represent the graph more accurately in the embedded space.

1.2. unweighted (or undirected) graph

Challenge: How to capture the diversity of connectivity patterns observed in graphs?

    Since only structural information is available in homogeneous graphs, the challenge of homogeneous graph embedding lies in how to preserve these connectivity patterns observed in the input graphs during embedding.
######2. heterogeneous graph
2.1. Community-based Question Answering (cQA) sites

cQA is an Internet-based crowdsourcing service that enables users to post questions on a website, which are then answered by other users [29].

(i, j, k, o, p) denotes that the j-th answer provided by user k obtains more votes (i.e., thumb-ups) than the o-th answer of user p for question i.

2.2.Multimedia Networks
A multimedia network is a network containing multimedia data, e.g., image, text, etc.

It exploits user-image links to embed users and images into the same space so that they can be directly compared for image recommendation. In [36], a click graph is considered which contains images and text queries. The image-query edge indicates a click of an image given a query, where the click count serves as the edge weight.

2.3. Knowledge Graphs 
In a knowledge graph (Def. 4), the entities (nodes) and relations (edges) are usually of different types.

2.4. Other heterogeneous graphs

Challenge: How to explore global consistency between different types of objects, and how to deal with the imbalances of objects belonging to different types, if any?
Different types of objects (e.g., nodes, edges) are embedded into the same space in heterogeneous graph embedding. How to explore the globalconsistency between them is a problem. Moreover, there may exist imbalance between objects of different types. This data skewness should be considered in embedding.


######3. graph with auxiliary information
The third category of input graph contains auxiliary information of a node/edge/whole-graph in addition to the structural relations of nodes (i.e., E)

there are five different types of auxiliary information as listed in Table 3
3.1. Label 
Nodes with different labels should be embedded far away from each other 
3.2. Attribute: 
In contrast to a label, an attribute value can be discrete or continuous.

3.3. Node feature: 
Most node features are text, which are provided either as a feature vector for each node [56], [57] or as a document [58], [59], [60], [61]

3.4. Information propagation: 
An example of information propagation is “retweet” in Twitter

3.5. Knowledge base: 
The popular knowledge bases include Wikipedia [66], Freebase [37], YAGO [67], DBpedia [68], etc.

Other types of auxiliary information include:  user checkin data (user-location) [70], user item preference ranking list [71], etc. 

Note that the auxiliary information is not just limited to one type. 
For instance, [62] and [72] consider both label and node feature information. [73] utilizes node contents and labels to assist the graph embedding process.

Challenge: How to incorporate the rich and unstructured information so that the learnt embeddings are both representing the topological structure and discriminative in terms of the auxiliary information?
The auxiliary information helps to define node similarity in addition to graph structural information. The challenges of embedding graph with auxiliary information is how to combine these two information sources to define the node similarity to be preserved.

######4. constructed graph.
As the last category of input graph is not provided, but constructed from the non-relational input data by different strategies.


```
In most cases, the input is a feature matrix X ∈ R |V |×N where each row Xi is an N-dimensional feature vector for the i-th training instance. A similarity matrix S is constructed by calculating Sij using the similarity between (Xi, Xj ). 
```
Ways to construct a graph from S:
4.1.  A straightforward way is to directly treat S as the adjacency matrix A of an invisible graph [74].

However, [74] is based on the Euclidean distance and it does not consider the neighbouring nodes when calculating Sij . If X lies on or near a curved manifold, the distance between Xi and Xj over the manifold is much larger than their Euclidean distance [12].

4.2. To address these issues, other methods (e.g., [75], [76], [77] ) construct a K nearest neighbour (KNN) graph from S first and estimate the adjacency matrix A based on the KNN graph

4.3. Another way of graph construction is to establish edges between nodes based on the nodes’ co-occurrence. 

Challenge: How to construct a graph that encodes the pairwise relations between instances and how to preserve the generated node proximity matrix in the embedded space? 
The first challenge faced by embedding graphs constructed from non-relational data is how to compute the relations between the non-relational data and construct such a graph. After the graph is constructed, the challenge becomes the same as in other input graphs, i.e., how to preserve the node proximity of the constructed graph in the embedded space.

#####Output
The output of graph embedding is a (set of) low dimensional vector(s) representing (part of) a graph. Based on the output granularity, we divide graph embedding output into four categories. Different
types of embedding facilitate different applications. the embedding output is task driven.

the first challenge:  in terms of embedding output is how to **find a suitable type of embedding output **which meets the needs of the specific application task.

###### node embedding
Challenge: How to define the pairwise node proximity in various types of input graph and how to encode the proximity in the learnt embeddings? 
The challenges of node embedding mainly come from defining the node proximity in the input graph. In Sec 3.1, we have elaborated the challenges of node embedding with different types of input graphs.

###### edge embedding
In contrast to node embedding, edge embedding aims to represent an edge as a low-dimensional vector.

Scenarios
1. knowledge graph embedding (e.g., [90], [91], [92]) learns embedding for both nodes and edges. Each edge is a triplet < h, r, t > (Def. 4).
2. some work (e.g., [28], [64]) embeds a node pair as a vector feature to either make the node pair comparable to other nodes or predict the existence of a link between two nodes.
In summary, edge embedding benefits edge (/node pairs) related graph analysis, such as link prediction, knowledge graph entity/relation prediction, etc.

Challenge: How to define the edge-level similarity and how tomodel the asymmetric property of the edges, if any? 
The edge proximity is different from node proximity as an edge contains a pair of nodes and usually denotes the pairwise node relation. Moreover, unlike nodes, edges may be directed. This asymmetric property should be encoded in the learnt edge representations


###### hybrid embedding
Hybrid embedding is the embedding of a combination of different types of graph components, e.g, node + edge (i.e., substructure), node + community.

1. Substructure embedding 

2. community embedding

The embedding of substructure or community can also be derived by aggregating the individual node and edge embedding inside it

Challenge: How to generate the target substructure and how to embed different types of graph components in one common space?
In contrast to other types of embedding output, the target to embed in hybrid embedding (e.g., subgraph, community) is not given. Hence the first challenge is how to generate such kind of embedding target structure. Furthermore, different types of targets (e.g., community, node) may be embedded in one common space simultaneously. How to address the heterogeneity of the embedding target types is a problem.


###### whole-graph embedding. 
the embedding of a whole graph usually for small graphs, such as proteins, molecules, etc.
In this case, a graph is represented as one vector and two similar graphs are embedded to be closer

Whole-graph embedding benefits the graph classification task by providing a straightforward and efficient solution for calculating graph similarities [49], [55], [95].

Challenge: How to capture the properties of a whole graph and how to make a trade-off between expressiveness and efficiency?
Embedding a whole graph requires capturing the property of a whole graph and is thus more time consuming compared to other types of embedding. The key challenge of whole-graph embedding is how to make a choice between the expressive power of the learnt embedding and the efficiency of the embedding algorithm.

####Graph Embedding techniques
The differences between different graph embedding algorithms lie in **how they define the graph property** to be preserved.

#####  Tech 1：Matrix Factorization
Matrix factorization based graph embedding represent graph property (e.g., node pairwise similarity) in the form of a matrix and factorize this matrix to obtain node embedding [11]

######Type 1: Graph Laplacian Eigenmaps

Insight: The graph property to be preserved can be interpreted as pairwise node similarities. Thus, a larger penalty is imposed if two nodes with **larger similarity** are embedded far apart.

Based on the above insight, the optimal embedding y can be derived by the below objective function [99].

The differences of existing studies mainly lie in 
1. how they calculate the pairwise node similarity Wij , 
2. and whether they use a linear function y = XT a or not


######Type 2:  Node Proximity Matrix Factorization

Insight: Node proximity can be approximated in a lowdimensional space using matrix factorization. The objective of preserving node proximity is to **minimize the loss of approximation**

#####Tech 2: Deep Learning
DL based graph embedding applies DL models on graphs.
we divide the DL based graph embedding into two categories based on **whether random walk is adopted to sample paths from a graph**

######Type 1: DL based Graph Embedding with Random Walk
Insight: The second-order proximity in a graph can be preserved in the embedded space by maximizing the probability of observing the neighbourhood of a node conditioned on its embedding. 

A graph is represented as a set of random walk paths sampled from it. The deep learning methods are then
applied to the sampled paths for graph embedding which preserves graph properties carried by the paths

1. DeepWalk
adopts a neural language model (SkipGram) for graph embedding. SikpGram [111] aims to maximize the co-occurrence probability among the words that appear within a window w.

Long-Short Term Memory (LSTM) [115]

######Tpye 2:  DL based Graph Embedding without Random Walk
Insight:The multi-layered learning architecture is a robust and effective solution to encode the graph into a low dimensional space.

The second class of deep learning based graph embedding methods applies deep models on a whole graph (or aproximity matrix of a whole graph) directly. Below are some popular **deep learning models** used in graph embedding.

1. Autoencoder: An autoencoder aims to minimize the reconstruction error of the output and input by its encoder and decoder. 
2. Deep Neural Network: As a popular deep learning model, Convolutional Neural Network (CNN) and its variants have been widely adopted in graph embedding
3. Others: There are some other types of deep learning based graph embedding methods. We summarize all deep learning based graph embedding
methods (random walk free) in Table 7

####Tech 3:  Edge Reconstruction based Optimization
Overall Insight: The edges established based on node embedding should be as similar to those in the input graph as possible.

The third category of graph embedding techniques directly optimizes an edge reconstruction based objective functions, by either **maximizing edge reconstruction probability** or minimizing edge reconstruction loss. The later is further divided into **distance-based loss** and **margin-based ranking loss**. Next, we introduce the three types one by one.

#####Type 1: Maximizing Edge Reconstruction Probability
Insight: Good node embedding maximizes the probability of generating the observed edges in a graph.

#####Type 2: Minimizing Distance-based Loss
Insight: The node proximity calculated based on node embedding should be as close to the node proximity calculated based on the observed edges as possible.

#####Type 3: Minimizing Margin-based Ranking Loss
In the margin-based ranking loss optimization, the edges of the input graph indicate the relevance between a node pair. Some nodes in the graph are usually associated with a set of relevant nodes. E.g., in a cQA site, a set of answers are marked as relevant to a given question. The insight of theloss is straightforward.
Insight: A node’s embedding is more similar to the embedding of relevant nodes than that of any other irrelevant node.

#####Tech 4: Graph Kernel
Insight: The whole graph structure can be represented as a vector containing the counts of elementary substructures that are decomposed from it.

#####Tech 5: Generative Model
A generative model can be defined by specifying the joint distribution of the input features and the class labels, conditioned on a set of parameters [139].

######Type 1: Embed Graph Into The Latent Semantic Space
Insight: Nodes are embedded into a latent semantic space where the distances among nodes explain the observed graph structure.

######Type 2: Incorporate Latent Semantics for Graph Embedding
Insight: Nodes which are close in the graph and having similar semantics should be embedded closer. The node semantics can be detected from node descriptions via a generative model.

#### Application
#####Node Related Applications
######Type 1: Node Classification
Node classification is to assign a class label to each node in a graph based on the rules learnt from the labelled nodes.

######Type 2: Node Clustering
Node clustering aims to group similar nodes together, so that nodes in the same group are more similar to each other than those in other groups.

######Type 3: Node Recommendation/Retrieval/Ranking
The task of node recommendation is to recommend top K nodes of interest to a given node based on certain criteria such as similarity [3], [16], [43], [45], [47], [106].

#####Edge Related Applications
######Type 1: Link Prediction
Graph embedding aims to represent a graph with low-dimensional vectors, but interestingly its output vectors can also help infer the graph structure. In practice, graphs are often incomplete; 

######Type 2: Triple Classification
Triplet classification [14], [15], [38], [51], [52], [53], [61], [142] is a specific application for knowledge graph.

#####Graph Related Applications
######Type 1: Graph Classification
Graph classification assigns a class label to a whole graph. This is important when the graph is the unit of data. For example, in [50], each graph is a chemical compound, an organic molecule or a protein structure 

######Type 2: Visualization
Graph visualization generates visualizations of a graph on a low dimensional space [20], [23], [48], [55], [58], [73]


####Future Direction
#####Computation
Problem: The deep architecture, which takes the geometric input (e.g., graph), suffers the low efficiency problem.
Directon: [117] suggested that the computational paradigms developed for large-scale graph processing can be adopted to facilitate efficiency improvement in deep learning models for graph embedding.

#####Problem Setting
Problem: The dynamic graph is one promising setting for graph embedding.
Direction: How to design effective graph embedding methods in dynamic domains remains an open question

#####Techniques 
Structure awareness is important for edge reconstruction based graph embedding.
Problem: However, most of them use deep learning models ( [38], [40], [142]) which suffer the low efficiency issue as discussed earlier.
Direction: How to design the non-deep learning based methods that can take advantage of the expressive power of graph structure is a question.

#####Applications 
Graph embedding has been applied in many different applications. It is an effective way to learn there presentations of data with **consideration of their relations**. Moreover, it can convert **data instances from different sources/platforms/views into one common space** so that they are directly comparable













