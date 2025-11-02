```java
import java.util.*;

class Solution {
    public long solution(int[] diffs, int[] times, long limit) {
        long answer = Integer.MAX_VALUE;
        long left = Integer.MAX_VALUE;
        long right = 0;
        
        for(int d : diffs) {
            left = Math.min(left, d);
            right = Math.max(right, d);
        }
        
        
        while(left <= right) {
            long mid = (left + right) / 2;
            long time = 0;
            for(int i = 0; i < diffs.length; i++) {
                if(mid >= diffs[i]) {
                    time += times[i];
                } else {
                    long t = times[i];
                    if(i != 0) {
                        t += times[i - 1];
                    }
                    time += t * (diffs[i] - mid) + times[i];
                }
                if(time > limit) break;
            }
            if(time > limit) {
                left = mid + 1;
            } else {
                answer = Math.min(answer, mid);
                right = mid - 1;
            }
        }
        return answer;
    }
}
```
