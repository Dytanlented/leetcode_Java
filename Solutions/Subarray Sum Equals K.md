### Algorithm

1. Start from the first element, we compute the sum as we go. And use a hash map to store the sum. The value is the occurance of the sum(including subsets'). If the sum upto two indices, say `i` and `j`, is at a difference `k`, that means the sum from `nums[i+1]` to `nums[j]` equals to `k`.
2. If the hash map contains key which is subtraction of sum at index `i` between target `k`, that means there exists subset equals to `k`, then update count by increasing by the key's value. Finally update the key's value by increasing one. 
3. Return count.

### Solutions

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap<Integer,Integer> map = new HashMap<>();
        map.put(0,1);
        int count = 0;
        int sum = 0;
        for(int i = 0;i<nums.length;i++){
            sum += nums[i];
            if(map.containsKey(sum - k)){
                count += map.get(sum - k);
            }
            map.put(sum, map.getOrDefault(sum,0) + 1);
        }
        return count;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(n), we traverse the nums array only once.

+ Space Complexity: O(n), hash map can contain `n` different sums. 