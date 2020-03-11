### Algorithm

1. Use char array to store wheather copy this character, if not then set to `0`. Start from left to right, if character is `)` and  the number of `)` is greater or equal to `(`, set to '0'. 
2. We then got the number of `(` and `)`, start from right to left and set the extra `(` to '0'.
3. Copy the resulting char array.

### Solutions

```java
class Solution {
    public String minRemoveToMakeValid(String s) {
        char[] str = s.toCharArray();
        int left = 0, right = 0;
    
        for(int i = 0;i < s.length(); i++){
            if(s.charAt(i) == ')' && right >= left){
                str[i] = '0';
            }else if( s.charAt(i) == ')'){
                right++;
            }
            if(s.charAt(i) == '('){
                left++;
            }
            
        }
        int count = left - right;
        for(int j = s.length()-1; j >= 0; j--){
            if(count == 0) break;
            if(s.charAt(j) == '('){
                str[j] = '0';
                count--;
            }
        }
        StringBuilder ans = new StringBuilder();
        for( char ch : str){
            if(ch != '0'){
                ans.append(ch);
            }
        }
        return ans.toString();
        
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N), `N` is the length of String s.

+ Space Complexity: O(N), for the char array.