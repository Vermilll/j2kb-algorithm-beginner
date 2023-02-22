*1003. 피보나치 함수*
```java
import java.io.*;

public class Main{
    static int[][] arr = new int[41][2];
    public static void main(String[] args)throws Exception{
        arr[0][0] = 1;
        arr[1][0] = 0;
        arr[0][1] = 0;
        arr[1][1] = 1;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        
        for(int i=0;i<count;i++){
            int[] s = def(Integer.parseInt(br.readLine()));
            sb.append(s[0] + " " + s[1]).append("\n");
        }
        
        System.out.println(sb);
    }
    
    public static int[] def(int a){
        if(arr[a][0] == 0 && arr[a][1] == 0){
            arr[a][0] = def(a-1)[0] + def(a-2)[0];
            arr[a][1] = def(a-1)[1] + def(a-2)[1];
        }
        
        return arr[a];
    }
}
```
*9461. 파도반 수열*
```java
import java.io.*;
import java.math.*;

public class Main{
    static BigInteger[] arr = new BigInteger[101];
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        arr[0] = new BigInteger("0");
        arr[1] = new BigInteger("1");
        arr[2] = new BigInteger("1");
        arr[3] = new BigInteger("1");
        arr[4] = new BigInteger("2");
        
        for(int i=0;i<count;i++){
            sb.append(def(Integer.parseInt(br.readLine()))).append("\n");
        }
        
        System.out.println(sb);
    }
    
    public static BigInteger def(int a){
        if(a > 4 && arr[a] == null){
            arr[a] = def(a-5).add(def(a-1));
        }
        return arr[a];
    }
}
```
*11726.2xn 타일링*
```java
import java.io.*;

public class Main{
    static int[] arr = new int[1001];
    public static void main(String[] args)throws Exception{
        arr[0] = 0;
        arr[1] = 1;
        arr[2] = 2;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println(def(Integer.parseInt(br.readLine())));
    }
    
    public static int def(int a){
        if(a > 2 && arr[a] == 0){
            arr[a] = (def(a-1) + def(a-2))%10007;
        }
        return arr[a];
    }
}
```

*11727.2xn 타일링 2*
```java
import java.io.*;

public class Main{
    static int[] arr = new int[1001];
    public static void main(String[] args)throws Exception{
        arr[0] = 0;
        arr[1] = 1;
        arr[2] = 3;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println(def(Integer.parseInt(br.readLine())));
    }
    
    public static int def(int a){
        if(a > 2 && arr[a] == 0){
            arr[a] = (def(a-1) + 2*def(a-2))%10007;
        }
        return arr[a];
    }
}
```

*9095. 1, 2, 3 더하기*
```java
import java.io.*;

public class Main{
    static int[] arr = new int[12];
    public static void main(String[] args)throws Exception{
        arr[1] = 1;
        arr[2] = 2;
        arr[3] = 4;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        for(int i=0;i<count;i++){
            sb.append(def(Integer.parseInt(br.readLine()))).append("\n");
        }
        System.out.println(sb);
    }
    
    public static int def(int a){
        if(a > 3 && arr[a] == 0){
            arr[a] = def(a-1) + def(a-2) + def(a-3);
        }
        return arr[a];
    }
}
```

*1463. 1로 만들기*
```java
import java.io.*;
import java.util.*;
import java.math.*;

public class Main{
    static int[] arr = new int[1000001];
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(System.in);
        arr[1] = 0;
        arr[2] = 1;
        arr[3] = 1;
        System.out.println(def(sc.nextInt()));
    }
    
    public static int def(int a){
        if(a > 3 && arr[a] == 0){
            if(a%3 == 0 && a%2 == 0){
                arr[a] = 1 + Math.min(Math.min(def(a/3), def(a/2)), def(a-1));
            }else if(a%3 == 0){
                arr[a] = 1 + Math.min(def(a/3), def(a-1));
            }else if(a%2 == 0){
                arr[a] = 1 + Math.min(def(a/2), def(a-1));
            }else{
                arr[a] = 1 + def(a-1);    
            }
        }
        return arr[a];
    }
}
```

*2193. 이친수*
```java
import java.util.*;
import java.math.*;

public class Main{
    static BigInteger[] arr = new BigInteger[91];
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(System.in);
        arr[0] = new BigInteger("0");
        arr[1] = new BigInteger("1");
        System.out.println(def(sc.nextInt()));
    }
    
    public static BigInteger def(int a){
        if(arr[a] == null){
            arr[a] = def(a-1).add(def(a-2));
        }
        return arr[a];
    }
}
```

*11053. 가장 긴 증가하는 부분 수열*
```java
import java.io.*;
import java.math.*;
import java.util.*;

public class Main{
    static int[] ref;
    static int[] arr;
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        arr = new int[count];
        ref = new int[count];
        ref[0] = 1;
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        for(int i=0;i<count;i++){
            ref[i] = 1;
            for(int j=0;j<i;j++){
                if(arr[i] > arr[j] && ref[i] < ref[j]+1){
                    ref[i] = ref[j] + 1;
                }
            }
        }
        int max = 1;
		for(int i=0;i<count;i++) {
			max = Math.max(max,ref[i]);
		}
		System.out.println(max);
    }
}
```

*11722. 가장 긴 감소하는 부분 수열*
```java
import java.io.*;
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        int[] arr = new int[count];
        int[] ref = new int[count];
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        for(int i=0;i<count;i++){
            ref[i] = 1;
            for(int j=0;j<i;j++){
                if(arr[i] < arr[j] && ref[i] <= ref[j]){
                    ref[i] = ref[j] + 1;
                }
            }
        }
        
        int ans = ref[0];
        for(int i=1;i<count;i++){
            ans = Math.max(ans, ref[i]);
        }
        
        System.out.println(ans);
    }
}
```

*11055. 가장 큰 증가 부분 수열*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        int[] arr = new int[count];
        int[] ref = new int[count];
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        for(int i=0;i<count;i++){
            ref[i] = arr[i];
            for(int j=0;j<i;j++){
                if(arr[i] > arr[j]){
                    ref[i] = Math.max(ref[i], ref[j] + arr[i]);
                }
            }
        }
        
        int ans = ref[0];
        for(int i=1;i<count;i++){
            ans = Math.max(ref[i], ans);
        }
        System.out.println(ans);
    }
}
```

*1912. 연속합*
```java

```

*10844. 쉬운 계단 수*
```java

```

*11057. 오르막 수*
```java

```

*2579. 계단 오르기*
```java

```

*1932. 정수 삼각형*
```java

```

*9465. 스티커*
```java

```

*2156. 포도주 시식*
```java

```
