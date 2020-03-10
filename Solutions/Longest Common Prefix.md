### Algorithm

We compare every string to the first string on the same column.

### Solutions

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs == null || strs.length == 0) return "";
        for(int i = 0;i < strs[0].length(); i++){
            char ch = strs[0].charAt(i);
            for(String str : strs){
                if(i >= str.length() || ch != str.charAt(i)){
                    return strs[0].substring(0, i);
                }
            }

        }
        return strs[0];
    }
}
```

### Complexity Analysis

+ Time Complexity: O(S), where S is sum of all characters in all strings.

+ Space Complexity: O(1), the space is for `ch`.