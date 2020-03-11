## Approach 1

### Algorithm

Use DFS to find the value which has minimum differcence from target, and use hashmap to store the difference and the node's value. Update `dif` while traversing the tree. 

### Solutions

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    double dif = Double.MAX_VALUE;
    HashMap<Double,Integer> map = new HashMap<>();
    public int closestValue(TreeNode root, double target) {
        dfs(root,target);
        return map.get(dif);
    }
    
    private void dfs(TreeNode node,double tar){
        if(node == null) return;
        if(Math.abs(tar - node.val) < dif){
            dif = (double)Math.abs(tar - node.val);
            map.put(dif, node.val);
        }
        dfs(node.left,tar);
        dfs(node.right,tar);
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), where `N` is number of tree nodes.

+ Space Complexity: O(d), where `d` is the maximum length of tree branch.


## Approach 2

### Algorithm

We can use binary search to reduce the time complexity.

### Solutions

```java
class Solution {
    public int closestValue(TreeNode root, double target) {
        int val, closest = root.val;
        while(root != null){
            val = root.val;
            closest = Math.abs(val - target) < Math.abs(closest - target) ? val : closest;
            root = root.val < target ? root.right : root.left;
        }
        return closest;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(H), where `H` is the tree level.

+ Space Complexity: O(1), for storing the closest value.