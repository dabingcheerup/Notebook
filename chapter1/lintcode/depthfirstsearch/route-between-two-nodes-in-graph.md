![](/assets/Screen Shot 2017-08-29 at 5.13.47 PM.png)
#Analysis
####Idea：
和clone graph思路相似
1. 用stack实现 典型的DFS求解。用set来记录元素是否曾经被加入过
2. 用queue实现 


```
九章
public class Solution {
   /**
     * @param graph: A list of Directed graph node
     * @param s: the starting Directed graph node
     * @param t: the terminal Directed graph node
     * @return: a boolean value
     */
    public boolean hasRoute(ArrayList<DirectedGraphNode> graph,
                                 DirectedGraphNode s, DirectedGraphNode t) {
        if (s == t)
            return true;

        HashSet<DirectedGraphNode> visited = new HashSet<DirectedGraphNode>();
        Queue<DirectedGraphNode> queue = new LinkedList<DirectedGraphNode>();
        
        queue.offer(s);
        visited.add(s);
        while (!queue.isEmpty()) {
            DirectedGraphNode node = queue.poll();
            for (int i = 0; i < node.neighbors.size(); i++) {
                if (visited.contains(node.neighbors.get(i))) {
                    continue;
                }
                visited.add(node.neighbors.get(i));
                queue.offer(node.neighbors.get(i));
                if (node.neighbors.get(i) == t) {
                    return true;
                }
            }
        }
        
        return false;
    }
}
```
####知识点：
1. HashSet<> HashSet.contains() node.neighbors.get()
2. queue.offer()


####Reference
[解答](https://zhengyang2015.gitbooks.io/lintcode/route_between_two_nodes_in_graph_176.html)