```java
import java.util.*;
import java.io.*;

class Solution
{
    static int max;
    static Set<String> visited;
    public static void main(String args[]) throws Exception
    {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(br.readLine());
        StringTokenizer st;

        for(int test_case = 1; test_case <= T; test_case++)
        {
            st = new StringTokenizer(br.readLine());
            String str = st.nextToken();
            int count = Integer.parseInt(st.nextToken());

            char[] nums = new char[str.length()];
            nums = str.toCharArray();

            max = 0;
            visited = new HashSet<>();
            DFS(count, nums);

            System.out.println("#" + test_case + " " + max);
        }
    }

    private static void DFS(int cnt, char[] nums) {
        if(cnt == 0) {
            max = Math.max(max, Integer.parseInt(new String(nums)));
            return;
        }

        String state = new String(nums) + " " + cnt;
        if(visited.contains(state)) return;
        visited.add(state);

        for(int i = 0; i < nums.length - 1; i++) {
            for(int j = i + 1; j < nums.length; j++) {
                swap(nums, i, j);
                DFS(cnt - 1, nums);
                swap(nums, j, i);
            }
        }

    }

    private static void swap(char[] nums, int i, int j) {
        char tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
}
```
