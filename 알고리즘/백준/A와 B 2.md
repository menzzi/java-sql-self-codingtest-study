```java
import java.util.*;
import java.io.*;

class Main {
    static String s, p;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        s = br.readLine();
        p = br.readLine();

        make(p);
        System.out.println(0);
    }
    private static void make(String str) {
        if(str.length() == s.length()) {
            if(str.equals(s)) {
                System.out.println(1);
                System.exit(0);
            }
            return;
        }

        if(str.charAt(str.length() - 1) == 'A') {
            make(str.substring(0, str.length() - 1));
        }

        if(str.charAt(0) == 'B') {
            make(new StringBuilder(str.substring(1)).reverse().toString());
        }
    }
}

```
