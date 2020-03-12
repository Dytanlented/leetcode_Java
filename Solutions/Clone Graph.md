### Algorithm

1. Use dfs and clone node as we go. Start traversing the graph from the given node.

2. Take a hash map to to store the nodes we have already visited. The key is the node from original graph, the value is the correspongding cloned node. If the node is already visited, return the cloned one.

3. If the node is not in the visited hash map, create a copy of it and put it in the map. Then make recursive calls for the neighbors of the node. Each recursive call would return a cloned neighbor. And create a list where store these neighbors. This way we will have cloned the given graph's node and its' neighbors.


### Solutions

```java
class Solution {
    private HashMap<Node, Node> visited = new HashMap();

    public Node cloneGraph(Node node) {
        if(node == null) return node;

        if(visited.containsKey(node)){
            return visited.get(node);
        }

        Node cloneNode = new Node(node.val, new ArrayList());
        visited.put(node, cloneNode);
        for(Node neighbor : node.neighbors){
            cloneNode.neighbors.add(cloneGraph(neighbor));
        } 
        return cloneNode;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), since we process each node exactly once.

+ Space Complexity: O(N), the space is occupied by the `visited` hash map and recursion  stack. The space of recursion stack is O(H) where H is the height of the graph. Overall, the space comlexity is O(N).