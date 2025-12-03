```java
class Solution {
    public String solution(String video_len, String pos, String op_start, String op_end, String[] commands) {
        String answer = "";
        int current = convert(pos);
        int video = convert(video_len);
        int os = convert(op_start);
        int oe = convert(op_end);
        
        if(current >= os && current <= oe) current = oe;
        for(String command : commands) {
            if(command.equals("prev")) {
                current = Math.max(current - 10, 0);
            } else {
                current = Math.min(current + 10, video);
            }
            
            if(current >= os && current <= oe) current = oe;
        }
        int minute = current % 60;
        int hour = current / 60;
        answer = String.format("%02d:%02d", hour, minute);
        return answer;
    }
    
    private int convert(String str) {
        String[] s = str.split(":");
        return Integer.parseInt(s[0]) * 60 + Integer.parseInt(s[1]);
    }
    
}
```
