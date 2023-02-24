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
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[count];
        int[] ref = new int[count];
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        for(int i=0;i<count;i++){
            ref[i] = arr[i];
            if(i > 0){
                if(ref[i-1] > 0){
                   ref[i] += ref[i-1];
                }
            }
        }
        
        int ans = ref[0];
        for(int i=1;i<count;i++){
            ans = Math.max(ref[i] ,ans);
        }
        System.out.println(ans);
    }
}
```

*10844. 쉬운 계단 수*
```java
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        BigInteger[][] arr = new BigInteger[num+1][10];
        
        arr[1][0] = new BigInteger("0");
        for(int i=1;i<10;i++){
            arr[1][i] = new BigInteger("1");
        }
        
        for(int i=2;i<num+1;i++){
          for(int j=0;j<10;j++){
              if(j == 0){
                  arr[i][j] = arr[i-1][1];
              }else if(j == 9){
                  arr[i][j] = arr[i-1][8];
              }else{
                  arr[i][j] = arr[i-1][j-1].add(arr[i-1][j+1]);
              }
          }  
        }
        
        BigInteger ans = new BigInteger("0");
        for(int i=0;i<10;i++){
            ans = ans.add(arr[num][i]);
        }
        System.out.println(ans.remainder(new BigInteger("1000000000")));
    }
}
```

*11057. 오르막 수*
```java
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int count = sc.nextInt();
        BigInteger[][] arr = new BigInteger[count+1][10];
        
        for(int i=0;i<10;i++){
            arr[1][i] = new BigInteger("1");
        }
        
        for(int i=2;i<count+1;i++){
            for(int j=0;j<10;j++){
                arr[i][j] = new BigInteger("0");
                for(int k=0;k<j+1;k++){
                    arr[i][j] = arr[i][j].add(arr[i-1][k]);
                }
            }
        }
        
        BigInteger ans = new BigInteger("0");
        for(int i=0;i<10;i++){
            ans = ans.add(arr[count][i]);
        }
        System.out.println(ans.remainder(new BigInteger("10007")));
    }
}
```

*2579. 계단 오르기*
```java
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[301];
        int[] ref = new int[301];
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        
        ref[0] = arr[0];
        ref[1] = arr[0] + arr[1];
        ref[2] = Math.max(arr[0], arr[1]) + arr[2];
        for(int i=3;i<count;i++){
            ref[i] = Math.max(ref[i-3] + arr[i-1],ref[i-2]) + arr[i];
        }
        
        System.out.println(ref[count-1]);
    }
}
```

*1932. 정수 삼각형*
```java
import java.io.*;
import java.math.*;
import java.util.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[][] arr = new int[count][count];
        int[][] ref = new int[count][count];
        for(int i=0;i<count;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=0;j<i+1;j++){
                arr[i][j] = Integer.parseInt(st.nextToken());
            }
        }
        
        ref[0][0] = arr[0][0];
        for(int i=1;i<count;i++){
            ref[i][0] = ref[i-1][0] + arr[i][0];
            for(int j=1;j<i+1;j++){
                ref[i][j] = Math.max(ref[i-1][j-1],ref[i-1][j]) + arr[i][j];
            }
        }
        
        int ans = ref[count-1][0];
        for(int i=1;i<count;i++){
            ans = Math.max(ans, ref[count-1][i]);
        }
        System.out.println(ans);
    }
}
```

*9465. 스티커*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        StringBuilder sb = new StringBuilder();
        for(int i=0;i<all;i++){
            int count = Integer.parseInt(br.readLine());
            int[][] arr = new int[2][100001];
            int[][] ref = new int[2][100001];
            StringTokenizer st1 = new StringTokenizer(br.readLine());
            for(int j=0;j<count;j++){
                arr[0][j] = Integer.parseInt(st1.nextToken());
            }
            
            StringTokenizer st2 = new StringTokenizer(br.readLine());
            for(int j=0;j<count;j++){
                arr[1][j] = Integer.parseInt(st2.nextToken());
            }
            
            ref[0][0] = arr[0][0];
            ref[1][0] = arr[1][0];
            ref[0][1] = arr[1][0] + arr[0][1];
            ref[1][1] = arr[0][0] + arr[1][1];
            
            for(int j=2;j<count;j++){
                ref[0][j] = Math.max(Math.max(ref[0][j-2],ref[1][j-2]),ref[1][j-1]) + arr[0][j];
                ref[1][j] = Math.max(Math.max(ref[0][j-2],ref[1][j-2]),ref[0][j-1]) + arr[1][j];
            }
            sb.append(Math.max(ref[0][count-1],ref[1][count-1])).append("\n");
        }
        System.out.println(sb);
    }
}
```

*2156. 포도주 시식*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[10001];
        int[] ref = new int[10001];
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        
        ref[0] = arr[0];
        ref[1] = arr[0] + arr[1];
        ref[2] = Math.max(arr[0], arr[1]) + arr[2];
        ref[3] = Math.max(arr[0] + arr[2], ref[1]) + arr[3];
        for(int i=4;i<count;i++){
            ref[i] = Math.max(ref[i-4] + arr[i-1],Math.max(ref[i-3] + arr[i-1], ref[i-2])) + arr[i];
        }
        if(count == 1){
            System.out.println(ref[0]);
        }else{
            System.out.println(Math.max(ref[count-1],ref[count-2]));
        }
    }
}
```

*11052. 카드 구매하기*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        int[] arr = new int[1001];
        int[] ref = new int[1001];
        
        for(int i=1;i<count+1;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        for(int i=1;i<count+1;i++){
            for(int j=1;j<i+1;j++){
                ref[i] = Math.max(ref[i], ref[i-j] + arr[j]);
            }
        }
        
        System.out.println(ref[count]);
    }
}
```

*15486. 퇴사2*
```java
import java.util.*;
import java.math.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[] arr1 = new int[count+1];
        int[] arr2 = new int[count+1];
        int[] ref = new int[count+1];
        
        for(int i=1;i<count+1;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            arr1[i] = Integer.parseInt(st.nextToken());
            arr2[i] = Integer.parseInt(st.nextToken());
        }
        int ans = 0;
        for(int i=1;i<count+1;i++){
            if(i + arr1[i] <= count+1){
                ref[i+arr1[i]-1] = Math.max(ref[i+arr1[i]-1], ans + arr2[i]);
            }
            ans = Math.max(ans, ref[i]);
        }
        System.out.println(ans);
    }
}
```

*11058. 크리보드*
```javaimport java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int count = sc.nextInt();
        long[] arr = new long[101];
        arr[1] = 1;
        arr[2] = 2;
        arr[3] = 3;
        long num = 1;
        
        for(int i=4;i<count+1;i++){
            for(int j=3;j<i;j++){
                arr[i] = Math.max(arr[i-j]*(j-1), arr[i]);
            }
            
            arr[i] = Math.max(arr[i-1] + num, arr[i]);
            num = arr[i] - arr[i-1];
        }
        System.out.println(arr[count]);
    }
}

```

*12865. 평범한 배낭*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int count = Integer.parseInt(st.nextToken());
        int max = Integer.parseInt(st.nextToken());
        int[][] arr = new int[count+1][2];
        int[][] ref = new int[count+1][max+1];
        
        for(int i=1;i<count+1;i++){
            StringTokenizer st1 = new StringTokenizer(br.readLine());
            arr[i][0] = Integer.parseInt(st1.nextToken());
            arr[i][1] = Integer.parseInt(st1.nextToken());
        }
        
        for(int i=1;i<max+1;i++){
            for(int j=1;j<count+1;j++){
                ref[j][i] = ref[j-1][i];
                if(i - arr[j][0] >= 0){
                    ref[j][i] = Math.max(ref[j-1][i], arr[j][1] + ref[j-1][i-arr[j][0]]);
                }
            }
        }
        System.out.println(ref[count][max]);
    }
}
```

*9251. LCS*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] str1 = br.readLine().split("");
        String[] str2 = br.readLine().split("");
        int[][] ref = new int[str1.length+1][str2.length+1];
        
        for(int i=1;i<str1.length+1;i++){
            for(int j=1;j<str2.length+1;j++){
                ref[i][j] = Math.max(ref[i][j-1],ref[i-1][j]);
                if(str1[i-1].equals(str2[j-1])){
                    ref[i][j] = ref[i-1][j-1] + 1;
                }
            }
        }
        
        System.out.println(ref[str1.length][str2.length]);
    }
}
```

*2225. 합분해*
```java
import java.util.*;
import java.math.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(System.in);
        String[] a = sc.nextLine().split(" ");
        
        int num = Integer.parseInt(a[0]);
        int count = Integer.parseInt(a[1]);
        long[][] ref = new long[num+1][count+1];
        
        for(int i=0;i<count+1;i++){
            ref[0][i] = 1;
        }
        
        for(int i=1;i<num+1;i++){
            for(int j=1;j<count+1;j++){
                ref[i][j] = (ref[i-1][j] + ref[i][j-1])%1000000000;    
            }
        }
        System.out.println(ref[num][count]);
    }
}
```
