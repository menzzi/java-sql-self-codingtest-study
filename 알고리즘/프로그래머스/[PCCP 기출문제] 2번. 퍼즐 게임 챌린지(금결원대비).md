```java
import java.util.*;

class Solution {
    public int solution(int[] diffs, int[] times, long limit) {
        int answer = Integer.MAX_VALUE;
        int left = Integer.MAX_VALUE;
        int right = Integer.MIN_VALUE;
        for(int d : diffs) {
            left = Math.min(left, d);
            right = Math.max(right, d);
        }
        
        while(left <= right) {
            int mid = (left + right) / 2;
            if(calculate(mid, diffs, times) <= limit) {
                answer = Math.min(answer, mid);
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return answer;
    }
    
    private long calculate(int level, int[] diffs, int[] times) {
        long totalTime = 0;
        for(int i = 0; i < diffs.length; i++) {
            if(level >= diffs[i]) {
                totalTime += times[i];
            } else {
                if(i != 0) {
                    totalTime += (times[i - 1] + times[i]) * (diffs[i] - level) + times[i];
                } else {
                    totalTime += (times[i]) * (diffs[i] - level) + times[i];
                }
            }
        }
        return totalTime;
    }
}
```
