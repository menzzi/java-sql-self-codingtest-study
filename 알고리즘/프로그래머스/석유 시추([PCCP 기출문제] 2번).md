```java
import java.util.*;

class Solution {
    private int[] column;
    private boolean[][] visited;
    
    private final int[] dx = {1, 0, -1, 0};
    private final int[] dy = {0, 1, 0, -1};

    public int solution(int[][] land) {
        int answer = 0;
        column = new int[land[0].length];
        visited = new boolean[land.length][land[0].length];
        
        for(int i = 0; i < land.length; i++) {
            for(int j = 0; j < land[0].length; j++) {
                if(land[i][j] == 1 && !visited[i][j]) {
                    visited[i][j] = true;
                    BFS(j, i, land);
                }
            }
        }
        
        for(int c : column) {
            answer = Math.max(answer, c);
        }
        
        return answer;
    }
    
    private void BFS(int x, int y, int[][] land) {
        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{x, y});
        visited[y][x] = true;
        int sum = 1;
        
        Set<Integer> colSet = new HashSet<>();
        colSet.add(x);
        
        while(!queue.isEmpty()) {
            int[] poll = queue.poll();
            for(int i = 0; i < 4; i++) {
                int nx = poll[0] + dx[i];
                int ny = poll[1] + dy[i];
                
                if(nx < 0 || ny < 0 || nx >= land[0].length || ny >= land.length) continue;
                
                if(land[ny][nx] == 1 && !visited[ny][nx]) {
                    visited[ny][nx] = true;
                    sum++;
                    colSet.add(nx);
                    queue.add(new int[]{nx, ny});
                }
            }
        }
        
        for(int c : colSet) {
            column[c] += sum;
        }
    }
}
```
