### Algorithm

1. Memorize the initial color.
2. Apply DFS to the starting pixel.
3. If the pixel's color equals to the origin color and not equals to new color, do DFS and so on.

### Solutions

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        int color = image[sr][sc];
        dfs(image, sr, sc, color, newColor);
        return image;
    }
    private void dfs(int[][] image, int r, int c, int color, int newColor){
        if(image[r][c] != newColor && image[r][c] == color){
            image[r][c] = newColor;
            if(r >= 1) dfs(image, r-1, c, color, newColor);
            if(c >= 1) dfs(image, r, c-1, color, newColor);
            if(r < image.length - 1) dfs(image, r+1, c, color, newColor);
            if(c < image[0].length - 1) dfs(image, r, c+1, color, newColor);
        }
    }
}
```