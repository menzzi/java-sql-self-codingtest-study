```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        Arrays.sort(citations);
        int length = citations.length;
        if(citations[0] >= length) return length;
        
        for(int i = 0; i <= length / 2; i++) {
            int start = citations[i] + 1;
            while(start <= citations[i + 1]) {
                if(length - (i + 1) >= start) answer = Math.max(answer,start);
                start++;
            }
        }
        return answer;
    }
}
```
