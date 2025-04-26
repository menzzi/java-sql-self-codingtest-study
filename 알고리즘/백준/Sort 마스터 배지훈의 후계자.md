```java
import java.util.*;
import java.io.*;

class Main {
    static int N, M;
    static int[] numbers;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        N = Integer.parseInt(st.nextToken());
        M = Integer.parseInt(st.nextToken());

        numbers = new int[N];
        for(int i = 0; i < N; i++) {
            numbers[i] = Integer.parseInt(br.readLine());
        }
        Arrays.sort(numbers);

        for(int i = 0; i < M; i++) {
            int num = Integer.parseInt(br.readLine());
            int index = binarySearch(num);
            System.out.println(index);
        }
    }

    private static int binarySearch(int num) {
        int right = N - 1;
        int left = 0;
        int answer = -1;
        while(left <= right) {
            int mid = (right + left) / 2;
            int value = numbers[mid];
            if(value == num) {
                answer = mid;
                right = mid - 1;
            } else if(value < num){
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return answer;
    }
}
```
