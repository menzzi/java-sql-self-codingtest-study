```java
import java.util.*;
import java.io.*;

class Main {
    static int N, Q;
    static List<int[]>[] list;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        N = Integer.parseInt(st.nextToken());
        Q = Integer.parseInt(st.nextToken());

        list = new ArrayList[N + 1];
        for(int i = 1; i <= N; i++) {
            list[i] = new ArrayList<>();
        }

        for(int i = 0; i < N - 1; i++) {
            st = new StringTokenizer(br.readLine());
            int p = Integer.parseInt(st.nextToken());
            int q = Integer.parseInt(st.nextToken());
            int r = Integer.parseInt(st.nextToken());
            list[p].add(new int[] {q, r});
            list[q].add(new int[] {p, r});
        }

        for(int i = 0; i < Q; i++) {
            st = new StringTokenizer(br.readLine());
            int k = Integer.parseInt(st.nextToken());
            int v = Integer.parseInt(st.nextToken());

            boolean[] visited = new boolean[N + 1];
            visited[v] = true;
            Queue<Integer> queue = new LinkedList<>();
            queue.add(v);

            int answer = 0;
            while(!queue.isEmpty()) {
                int poll = queue.poll();

                for(int[] arr : list[poll]) {
                    if(!visited[arr[0]] && arr[1] >= k) {
                        queue.add(arr[0]);
                        visited[arr[0]] = true;
                        answer++;
                    }
                }
            }
            System.out.println(answer);
        }
    }
}
```
