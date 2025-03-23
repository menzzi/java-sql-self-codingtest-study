```java
import java.util.*;
import java.io.*;

class Main {
    static int S, P;
    static int answer = 0;
    static int[] checkArr = new int[4];
    static int[] myArr = new int[4];

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        S = Integer.parseInt(st.nextToken());
        P = Integer.parseInt(st.nextToken());
        String[] str = br.readLine().split("");

        st = new StringTokenizer(br.readLine());
        for(int i = 0; i < 4; i++) {
            checkArr[i] = Integer.parseInt(st.nextToken());
        }

        for(int i = 0; i < P; i++) {
            if(str[i].equals("A")) myArr[0]++;
            else if(str[i].equals("C")) myArr[1]++;
            else if(str[i].equals("G")) myArr[2]++;
            else if(str[i].equals("T")) myArr[3]++;
        }
        if(isCollect())answer++;

        for(int j = P; j < S; j++) {
            int i = j - P;
            if(str[i].equals("A")) myArr[0]--;
            else if(str[i].equals("C")) myArr[1]--;
            else if(str[i].equals("G")) myArr[2]--;
            else if(str[i].equals("T")) myArr[3]--;

            if(str[j].equals("A")) myArr[0]++;
            else if(str[j].equals("C")) myArr[1]++;
            else if(str[j].equals("G")) myArr[2]++;
            else if(str[j].equals("T")) myArr[3]++;

            if(isCollect())answer++;
        }

        System.out.println(answer);
    }

    private static boolean isCollect() {
        for(int i = 0; i < 4; i++) {
            if(myArr[i] < checkArr[i]) return false;
        }
        return true;
    }
}
```
