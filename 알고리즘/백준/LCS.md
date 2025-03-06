```java
import java.util.*;
import java.io.*;

class Main {
    static int[][] dp;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        char[] str1 = br.readLine().toCharArray();
        char[] str2 = br.readLine().toCharArray();
        int N = str1.length;
        int M = str2.length;

        dp = new int[N + 1][M + 1];

        for(int i = 1; i <= N; i++) {
            for(int j = 1; j <= M; j++) {
                if(str1[i - 1] == str2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i][j - 1], dp[i - 1][j]);
                }
            }
        }

        System.out.println(dp[N][M]);
    }
}
```
