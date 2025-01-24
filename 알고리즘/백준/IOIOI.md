```java
import java.util.*;
import java.io.*;

class Main {
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int M = Integer.parseInt(br.readLine());
        String s = br.readLine();

        int answer = 0;
        int count = 0;
        for(int i = 0; i < M-2; i++) {
            if(s.charAt(i) == 'I' && s.charAt(i+1) == 'O' && s.charAt(i+2) == 'I') {
                count++;
                i++;

                if(count == N) {
                    answer++;
                    count--;
                }
            } else {
                count = 0;
            }
        }
        System.out.println(answer);
    }
}
```

### 아래 코드는 시간이 오래 걸려 50점짜리..!
```java
import java.util.*;
import java.io.*;

class Main {
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int M = Integer.parseInt(br.readLine());
        String s = br.readLine();

        String pn = makePn(N);

        int num = (N * 2) + 1;
        int answer = 0;
        for(int i = 0; i <= M - num; i++) {
            if(pn.equals(s.substring(i,i + num))) {
                answer++;
                i++;
            }
        }
        System.out.println(answer);
    }

    private static String makePn(int N) {
        StringBuilder sb = new StringBuilder();
        sb.append("I");
        String str = "OI";
        sb.append(str.repeat(N));
        return sb.toString();
    }
}
```
