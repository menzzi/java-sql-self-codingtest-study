```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    static int answer = Integer.MAX_VALUE;
    static int[][] universe;
    static int N, M;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        N = Integer.parseInt(st.nextToken());
        M = Integer.parseInt(st.nextToken());
        universe = new int[N][M];
        for(int i = 0; i < N; i++) {
            st = new StringTokenizer(br.readLine());
            for(int j = 0; j < M; j++) {
                universe[i][j] = Integer.parseInt(st.nextToken());
            }
        }

        for(int i = 0; i < M; i++) {
            DFS(universe[0][i] + universe[1][i], 2, i, i);
            if(i - 1 >= 0) DFS(universe[0][i] + universe[1][i - 1], 2,  i, i - 1);
            if(i + 1 < M) DFS(universe[0][i] + universe[1][i + 1], 2, i,i + 1);
        }

        System.out.println(answer);
    }

    private static void DFS(int sum, int depth, int prevC, int c) {
        if(depth == N) {
            answer = Math.min(answer, sum);
            return;
        }

        for(int i = c - 1; i <= c + 1; i++) {
            if(i < 0 || i >= M) continue;
            if(prevC - c == c - i) continue;
            DFS(sum + universe[depth][i], depth + 1, c, i);
        }
    }
}
```
