```java
import java.util.*;
import java.io.*;

class Main {
    static long A, B;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        A = Long.parseLong(st.nextToken());
        B = Long.parseLong(st.nextToken());

        Queue<long[]> queue = new LinkedList<>();
        queue.add(new long[]{A, 1});

        while(!queue.isEmpty()) {
            long[] poll = queue.poll();

            if(poll[0] == B) {
                System.out.println(poll[1]);
                return;
            }

            long num1 = poll[0] * 2;
            long num2 = poll[0] * 10 + 1;

            if(num1 <= B) {
                queue.add(new long[] {num1, poll[1] + 1});
            }

            if(num2 <= B) {
                queue.add(new long[] {num2, poll[1] + 1});
            }
        }
        System.out.println(-1);
    }
}
```
