```java
import java.util.*;
import java.io.*;

class Main {
    static int N, R, C, answer = 0;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        N = Integer.parseInt(st.nextToken());
        R = Integer.parseInt(st.nextToken());
        C = Integer.parseInt(st.nextToken());
        recur((int) Math.pow(2, N), 0, 0);
    }

    private static void recur(int size, int r, int c) {
        if(size == 1) {
            System.out.println(answer);
            return;
        }

        int newSize = size / 2;
        if(R < r + newSize && C < c + newSize) {
            recur(newSize, r, c);
        }
        if(R < r + newSize && C >= c + newSize) {
            answer += (size * size) / 4;
            recur(newSize, r, c + newSize);
        }
        if(R >= r + newSize && C < c + newSize) {
            answer += ((size * size) / 4 ) * 2;
            recur(newSize, r + newSize, c);
        }
        if(R >= r + newSize && C >= c + newSize) {
            answer += ((size * size) / 4 ) * 3;
            recur(newSize, r + newSize, c + newSize);
        }
    }
}
```
