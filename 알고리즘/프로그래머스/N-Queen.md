```java
import java.util.*;

class Solution {
    static int answer = 0;
    public int solution(int n) {
        int[] queen = new int[n];
        boolean[] visited = new boolean[n];
        Arrays.fill(queen, -1);
        findQ(0, queen, visited, n);
        return answer;
    }
    
    private void findQ(int cnt, int[] queen, boolean[] visited, int n) {
        if(cnt == n) {
            answer++;
            return;
        }
        
        for(int i = 0; i < n; i++) {
            queen[cnt] = i;
            if(isRight(queen, cnt)) {
                findQ(cnt + 1, queen, visited, n);
            }
        }
    }
    
    private boolean isRight(int[] queen, int cnt) {
        for(int i = 0; i < cnt; i++) {
            if(queen[i] == queen[cnt]) return false;
            if(Math.abs(queen[i] - queen[cnt]) == cnt - i) return false;
        }
        return true;
    }
}
```
