```java
import java.util.*;

class Solution {
    int[] row = new int[] {1, 0, -1, 0};
    int[] column = new int[] {0, 1, 0, -1};
    
    public int solution(int[][] land) {
        int answer = 0;
        int[] count = new int[land[0].length];
        boolean[][] visited = new boolean[land.length][land[0].length];
        for(int i = 0; i < land.length; i++) {
            for(int j = 0; j < land[0].length; j++) {
                if(!visited[i][j] && land[i][j] == 1) {
                    Queue<int[]> queue = new LinkedList<>();
                    queue.add(new int[] {i, j});
                    visited[i][j] = true;
                    
                    Set<Integer> cSet = new HashSet<>();
                    cSet.add(j);
                    int cnt = 1;
                    while(!queue.isEmpty()) {
                        int[] poll = queue.poll();
                        for(int k = 0; k < 4; k++) {
                            int nr = poll[0] + row[k];
                            int nc = poll[1] + column[k];
                            
                            if(nr < 0 || nc < 0 || nr >= land.length || nc >= land[0].length) continue;
                            if(visited[nr][nc] || land[nr][nc] != 1) continue;
                            queue.add(new int[] {nr, nc});
                            cnt++;
                            cSet.add(nc);
                            visited[nr][nc] = true;
                        }
                    }
                    
                    for(int s : cSet) {
                        count[s] += cnt;
                    }
                }
            }
        }
        for(int c : count) {
            answer = Math.max(answer, c);
        }
        
        return answer;
    }
    
}
```
