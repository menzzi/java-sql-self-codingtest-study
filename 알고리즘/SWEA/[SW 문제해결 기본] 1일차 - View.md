```java
import java.util.*;
import java.io.*;

class Solution
{
	public static void main(String args[]) throws Exception
	{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		for(int test_case = 1; test_case <= 10; test_case++)
		{
			int N = Integer.parseInt(br.readLine());
            int[] building = new int[N];
            String[] input = br.readLine().split(" ");
            for(int i = 0; i < N; i++) {
                building[i] =  Integer.parseInt(input[i]);
            }
            
            int totalCnt = 0;
            for(int i = 2; i < N - 2; i++) {
                int maxLH = Math.max(building[i - 2], building[i - 1]);
                int maxRH = Math.max(building[i + 2], building[i + 1]);
                int maxH = Math.max(maxLH, maxRH);
                
                if(maxH < building[i]) totalCnt += building[i] - maxH;
		    }
            System.out.println("#" + test_case + " " + totalCnt);
        }  
	}
}
```
