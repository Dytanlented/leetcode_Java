### Algorithm

We group the continuous same characters as a block and count their number. Then we check if the name group numbers are less or equal than the typed one's respectively.

### Solutions

```java
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        char[] chn = name.toCharArray();
        char[] cht = typed.toCharArray();
        ArrayList<Integer> cntn = new ArrayList();
        ArrayList<Integer> cntt = new ArrayList();
        char ch = chn[0];
        int count = 0;
        for(int i = 0;i < chn.length;i++){
            if(ch == chn[i]){
                count++;
                if(i == chn.length - 1){
                    cntn.add(count);
                }
            }else{
                cntn.add(count);
                count = 0;
                ch = chn[i];
                i--;
            }
        }
        count = 0;
        ch = cht[0];
        for(int i = 0;i < cht.length;i++){
            if(ch == cht[i]){
                count++;
                if(i == cht.length - 1){
                    cntt.add(count);
                }
            }else{
                cntt.add(count);
                count = 0;
                ch = cht[i];
                i--;
            }
        }
        if(cntn.size() != cntt.size()){
            return false;
        }
        for(int i = 0;i < cntt.size();i++){
            if(cntn.get(i) > cntt.get(i)){
                return false;
            }
        }

        return true;
    }
}
```

### Complexity Analysis

+ Time Complexity: O(N + T), where N and T is the length of `name` and `typed` respectively.

+ Space Complexity: O(N + T).