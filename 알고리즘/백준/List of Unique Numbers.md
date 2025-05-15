```java
import java.util.*;
import java.io.*;

class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] nums = new int[N];
        int[] cnt = new int[100001];
        long answer = 0;

        StringTokenizer st = new StringTokenizer(br.readLine());
        for(int i = 0; i < N; i++) {
            nums[i] = Integer.parseInt(st.nextToken());
        }
        int point1 = 0;
        int point2 = -1;
        while(point1 < N) {
            while(point2 + 1 < N && cnt[nums[point2 + 1]] == 0) {
                point2++;
                cnt[nums[point2]]++;
            }
            answer += point2 - point1 + 1;
            cnt[nums[point1]]--;
            point1++;
        }
        System.out.println(answer);
    }
}
```
