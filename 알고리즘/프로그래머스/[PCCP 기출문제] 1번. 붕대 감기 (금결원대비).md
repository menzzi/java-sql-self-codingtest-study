```java
class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
        int answer = health;
      
        for(int i = 1; i < attacks.length; i++) {
            answer -= attacks[i - 1][1];
            if(answer <= 0) return -1;
            
            int time = attacks[i][0] - attacks[i - 1][0] - 1;
            answer += time * bandage[1];
            answer += (time / bandage[0]) * bandage[2];
            if(answer > health) answer = health;
        }
        answer -= attacks[attacks.length - 1][1];
        if(answer == 0) return -1;
        return answer;
    }
}
```
