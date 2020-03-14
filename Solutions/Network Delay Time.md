
### Algorithm

1. Use hash map `graph` to transform the input to a graph. The key is the `node`, and the value is its' corresponding nodes it can reach to. To speed up, we sort each each value array by the distance.
2. Use another hash map `dist` to store the distance to get to each node. Initialize them as `Integer.MAX_VALUE`.
3. Apply dfs, and update the `dist`. To speed up, if the current distance is greater or equal than value in `dist`, return.
4. After dfs, if there exists a disctance to be Integer.MAX_VALUE, return false, else true.

### Solutions

```java
class Solution {
    Map<Integer,Integer> dist = new HashMap<>();   
    public int networkDelayTime(int[][] times, int N, int K) {

        int mintime = -1;
        HashMap<Integer,List<int[]>> graph = new HashMap<>();
        for(int[] time : times){
            if(!graph.containsKey(time[0])){
                graph.put(time[0], new ArrayList<int[]>());
            }
            graph.get(time[0]).add(new int[]{time[1],time[2]});
        }
        for(int node : graph.keySet()){
            Collections.sort(graph.get(node), (a,b) -> a[1] - b[1]);
        }
        for(int i = 1;i<=N;i++){
            dist.put(i,Integer.MAX_VALUE);
        }
        dfs(K,graph,0);
        int ans = 0;
        for(int cand : dist.values()){
            if(cand == Integer.MAX_VALUE) return -1;
            ans = Math.max(cand, ans);
        }
        return ans;
        
    }
    
    public void dfs(int node, HashMap<Integer,List<int[]>> graph, int curr){
        if(curr >= dist.get(node)){
            return;
        }
        dist.put(node, curr);
        if(graph.containsKey(node)){
            for(int[] neighbor : graph.get(node)){
                dfs(neighbor[0],graph,curr + neighbor[1]);
            }
        }
    }
}
```
