### Algorithm

Just traverse the String `s`, and count the number of `A` and `L`, be careful of boundary conditions.

### Solutions

```java
class Solution {
    public boolean checkRecord(String s) {
        int cntA = 0;
        int cntL = 0;
        for(int i =0; i < s.length();i++){
            if(s.charAt(i)=='P'){
                cntL = 0;
                continue;
            }else if(s.charAt(i) == 'A'){
                cntL = 0;
                cntA++;
                if(cntA>1){
                    return false;
                }
            }else{
                cntL++;
                if(cntL > 2){
                    return false;
                }
            }
        }
        return true;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(n), traverse the String only once.

+ Space Complexity: O(1), constant space is used.