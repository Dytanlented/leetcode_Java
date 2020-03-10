### Algorithm
1. Use two pointers `read` and `write` to mark where where we read and write. And another pointer `anchor` to indicate the character which to be compresses.
2. When `read` reaches the end of the `chars` or character ponited by `read` is not equal to the next character, we compute the compressed results.
3. Update `anchor` to `read + 1`.


### Solutions

```java
class Solution {
    public int compress(char[] chars) {
        int anchor = 0, write = 0;
        for(int read = 0; read < chars.length; read++){
            if(read == chars.length-1 || chars[read] != chars[read+1]){
                chars[write++] = chars[anchor];
                if(read > anchor){
                    for(char c : ("" + (read - anchor + 1)).toCharArray()){
                        chars[write++] = c;
                    }
                }
                anchor = read + 1;
            }
        }
        return write;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), where N is the length of `chars`.

+ Space Complexity: O(1), the space is for `anchor`, `write` and `read`. 