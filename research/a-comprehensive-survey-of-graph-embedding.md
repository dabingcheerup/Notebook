####Graph Embeding
#####Definition

By representing a graph as a (or a set of) low dimensional vector(s), graph algorithms can then be computed efficiently.

Types of Graph
homogeneous graph, heterogeneous graph, attribute graph, etc So 
The input of graph embedding: varies in different scenarios. 
The output of graph embedding: is a low-dimensional vector representing a part of the graph (or a whole graph).

The problem of graph embedding 
is related to two traditional research problems, 
1. i.e., graph analytics [8] and
2. representation learning [9]. 

graph embedding aims to represent a graph as low dimensional vectors while
the graph structures are preserved.

graph analytics aims to mine useful information from graph data.

representation learning obtains data representations that make it easier to extract useful information when building classifiers or other predictors [9].

#####2. Problem Formalization
######2.1 Notation and Definition
Definition 1. 
A graph is G = (V, E), where v ∈ V is a node and e ∈ E is an edge. G is associated with a node type mapping function fv : V → Tv and an edge type mapping function fe : E → Te

Definition 2. 
A homogeneous graph Ghomo = (V, E) is a graph in which |Tv| = |Te| = 1

Definition 3. 
A heterogeneous graph Ghete = (V, E) is a graph in which |Tv| > 1 and/or |Te| > 1

Definition 4. 
A knowledge graph Gknow = (V, E) is a directed graph whose nodes are entities and edges are subject-property-object triple facts
h, t ∈ V are entities and r ∈ E is the relation. call < h, r, t > a knowledge graph triplet

Note that the entities and relations in a knowledge graph are usually of different types [14], [15]. Hence, knowledge graph can be viewed as _an instance of the heterogeneous graph_.

Definition 5. 
The first-order proximity between node vi and node vj is the weight of the edge eij , i.e., Ai,j .

The second-order proximity compares the similarity of the nodes’ neighbourhood structures. The more similar two nodes’ neighbourhoods are, the larger the second-order proximity value between them