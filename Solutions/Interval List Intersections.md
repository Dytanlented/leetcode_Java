### Algorithm

1. Compare intervals `A[i]` and `B[j]` where i and j starts from 0 to its' boundary. If they don't have intersection, move the smaller interval to the next one.
2. If they have intersection, take the larger startpoint and smaller endpoint as their intersection.
3. Move the interval with smaller endpoint to the next interval. If they are equal, both move to the next one.

### Solutions

#### Initial
```java
class Solution {
    public int[][] intervalIntersection(int[][] A, int[][] B) {
        int i = 0, j = 0;
        List<int[]> ans = new ArrayList(); 
        while(i < A.length && j < B.length){
            if(A[i][1] < B[j][0]){
                i++;
                continue;
            }
            if(B[j][1] < A[i][0]){
                j++;
                continue;
            }
            int left = Math.max(A[i][0],B[j][0]);
            int right = Math.min(A[i][1],B[j][1]);
            ans.add(new int[]{left,right});
            if(A[i][1] < B[j][1]){
                i++;
            }else if(A[i][1] > B[j][1]){
                j++;
            }else{
                i++;
                j++;
            }
            
        }
        return ans.toArray(new int[ans.size()][]);
    }
}
```

#### Optimized

```java
class Solution {
    public int[][] intervalIntersection(int[][] A, int[][] B) {
        int i = 0, j = 0;
        List<int[]> ans = new ArrayList(); 
        while(i < A.length && j < B.length){
            int left = Math.max(A[i][0],B[j][0]);
            int right = Math.min(A[i][1],B[j][1]);
            if(left <= right){
                ans.add(new int[]{left, right});
            }
            if(A[i][1] < B[j][1]){
                i++;
            }else{
                j++;
            }
        }
        return ans.toArray(new int[ans.size()][]);
    }
}

```

### Complexity Analysis

+ Time Complexity: O(M + N), `M` and `N` are the length of `A` and `B` respectively.

+ Space Complexity: O(M + N), the maximum size of the answer.