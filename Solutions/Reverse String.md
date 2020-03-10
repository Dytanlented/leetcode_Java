### Algorithm

Set pointer `left` in the beginning and `end` at the end. Then move them while swapping characters until they meet.

### Solutions

```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0, right = s.length-1;
        while(left < right){
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;
            left++;
            right--;
        }
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), where N is the length of `s`.

+ Space Complexity: O(1), the space is for `temp` and pointers `left` and `right`.