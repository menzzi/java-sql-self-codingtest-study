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
        StringTokenizer st;

        for(int test_case = 1; test_case <= 10; test_case++)
        {
            int count = Integer.parseInt(br.readLine());
            Map<Integer, Integer> map = new HashMap<>();
            int min = Integer.MAX_VALUE;
            int max = 0;

            st = new StringTokenizer(br.readLine());
            while(st.hasMoreTokens()) {
                int num = Integer.parseInt(st.nextToken());
                map.put(num, map.getOrDefault(num, 0) + 1);
                min = Math.min(min, num);
                max = Math.max(max, num);
            }

            while(count > 0) {
                if(min == max) break;
                map.put(min, map.get(min) - 1);
                map.put(min + 1, map.getOrDefault(min + 1, 0) + 1);

                map.put(max, map.get(max) - 1);
                map.put(max - 1, map.getOrDefault(max - 1, 0) + 1);

                count--;

                if(map.get(min) == 0) {
                    map.remove(min);
                    min++;
                    while(!map.containsKey(min)) {
                        min++;
                    }
                }

                if(map.get(max) == 0) {
                    map.remove(max);
                    max--;
                    while(!map.containsKey(max)) {
                        max--;
                    }
                }
                
            }

            int answer = max - min;
            System.out.println("#" + test_case + " " + answer);
        }
    }
}
```
