### Algorithm

1. Use two pointers `start` and `end` starting from head and tail respectively.
2. Find the first two character which are not equal. If cannot find then return true, else there are two posibilities. 
3. Let's ignore character at the index of `start` or `end`, check the resulting string to see if it is palindrom.

### Solutions

```java
class Solution {
    public boolean validPalindrome(String s) {
        int start = 0, end = s.length() - 1;
        while(start < end){
            if(s.charAt(start)!=s.charAt(end)){
                if(helper(s,start + 1,end) || helper(s,start,end-1)){
                    return true;
                }else{
                    return false;
                }
            }
            start++;
            end--;
        }
        return true;
    }
    private boolean helper(String s, int l, int r){
        while(l < r){
            if(s.charAt(l) != s.charAt(r)){
                return false;
            }
            l++;
            r--;
        }
        return true; 
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), where N is the length of String `s`.

+ Space Complexity: O(1), the space is for pointers `start` and `end`.