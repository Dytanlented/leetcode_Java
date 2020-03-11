### Algorithm

Just brute force. But there is a little trick to speed up. The outer loop is `A`'s row, the second loop is `A`'s column, and the third loop is `B`'s coloumn. We can check if `A[i][j]` equals zero, if so, continue. That saves a lot of time and makes it faster than 100%.

### Solutions

```java
class Solution {
    public int[][] multiply(int[][] A, int[][] B) {
        int[][] ans = new int[A.length][B[0].length];
        for(int i = 0;i < A.length; i++){
            for(int j = 0; j < A[0].length; j++){
                if(A[i][j] == 0) continue;
                for(int k = 0; k < B[0].length;k++){
                    ans[i][k] += A[i][j]*B[j][k];
                }
            }
        }
        return ans;
    }
}
```
