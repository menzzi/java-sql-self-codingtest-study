```java
import java.util.*;
import java.io.*;

class Main {
    static int N;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        N = Integer.parseInt(br.readLine());

        int[] numbers = new int[N + 1];
        for(int i = 0; i < N; i++) {
            numbers[i] = Integer.parseInt(br.readLine());
        }

        int num = (int) Math.round((N * 0.3) / 2);
        Arrays.sort(numbers);
        double sum = 0;
        for(int i = num + 1; i <= N - num; i++) {
            sum += numbers[i];
        }
        sum /= (N - (num * 2));
        System.out.println(Math.round(sum));
    }
}
```
