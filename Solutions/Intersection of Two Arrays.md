### Algorithm

1. Since each element in the result must be unique, it is natural to come up with hashset.
2. Use two sets to store the arrays then iterate the smaller set to check the presence of each element in the larger set. 

### Solutions

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        for(Integer n : nums1) set1.add(n);
        HashSet<Integer> set2 = new HashSet<>();
        for(Integer n : nums2) set2.add(n);
        
        if(set1.size() < set2.size()){
            return set_intersection(set1,set2);
        }else{
            return set_intersection(set2,set1);
        }
    }
    
    private int[] set_intersection(HashSet<Integer> set1, HashSet<Integer> set2){
        int[] ans = new int[set1.size()];
        int idx = 0;
        for(Integer s : set1){
            if(set2.contains(s)) ans[idx++] = s;
        }
        return Arrays.copyOf(ans,idx);
    }
}
```

### Complexity Analysis

+ Time Complexity: O(m + n), where `n` and `m` are arrays' lengths.

+ Space Complexity: O(m + n), when all elements in arrays are unique. 