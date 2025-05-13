```java
import java.util.*;
import java.io.*;

class Main {

    static class Team {
        int id;
        Map<Integer, Integer> scores = new HashMap<>();
        int totalScore = 0;
        int submitCnt = 0;
        int lastSubmitTime = 0;

        Team(int id) {
            this.id = id;
        }

        public void addScore(int pid, int score, int time) {
            int prev = scores.getOrDefault(pid, 0);
            if(prev < score) {
                totalScore += (score - prev);
                scores.put(pid, score);
            }
            submitCnt++;
            lastSubmitTime = time;
        }
    }

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(br.readLine());
        StringTokenizer st;
        for(int i = 0; i < T; i++) {
            st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
            int k = Integer.parseInt(st.nextToken());
            int t = Integer.parseInt(st.nextToken());
            int m = Integer.parseInt(st.nextToken());
            Map<Integer, Team> teams = new HashMap<>();

            for(int j = 0; j < m; j++) {
                st = new StringTokenizer(br.readLine());
                int id = Integer.parseInt(st.nextToken());
                int num = Integer.parseInt(st.nextToken());
                int score = Integer.parseInt(st.nextToken());
                teams.computeIfAbsent(id, tid -> new Team(tid)).addScore(num, score, j);
            }

            List<Team> answer = new ArrayList<>(teams.values());
            Collections.sort(answer, (a,b) -> {
                if(a.totalScore == b.totalScore) {
                    if(a.submitCnt == b.submitCnt) return a.lastSubmitTime - b.lastSubmitTime;
                    else return a.submitCnt - b.submitCnt;
                } else return b.totalScore - a.totalScore;
            });

            for(int grade = 0; grade < answer.size(); grade++) {
                if(answer.get(grade).id == t) System.out.println(grade + 1);
            }
        }
    }
}
```
