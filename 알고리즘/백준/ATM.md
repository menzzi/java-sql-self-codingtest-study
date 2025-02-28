```java
import java.util.*;
import java.io.*;

class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        int[] numbers = new int[N];
        for(int i = 0; i < N; i++) {
            numbers[i] = Integer.parseInt(st.nextToken());
        }

        Arrays.sort(numbers);

        int sum = numbers[0];

        for(int i = 1; i < N; i++) {
            numbers[i] = numbers[i - 1] + numbers[i];
            sum += numbers[i];
        }

        System.out.println(sum);
    }
}
```
