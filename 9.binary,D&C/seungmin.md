*2448. 별 찍기 - 11*
```java
import java.io.*;
import java.util.*;

public class Main{
    static boolean[][] star;
    public static void main(String[] args){
        StringBuilder sb = new StringBuilder();
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        star = new boolean[num*2][num];
        re(0,0,num);
        
        for(int i=0;i<num;i++){
            for(int j=0;j<num*2;j++){
                if(star[j][i]){
                    sb.append("*");
                }else{
                    sb.append(" ");
                }
            }
            sb.append("\n");
        }
        
        System.out.println(sb);
    }
    
    public static void re(int a, int b, int c){
        if(c == 3){
            star[a+2][b] = true;
            star[a+1][b+1] = star[a+3][b+1] = true;
            star[a][b+2] = star[a+1][b+2] = star[a+2][b+2] = star[a+3][b+2] = star[a+4][b+2] = true;
        }else{
            re(a+c/2, b, c/2);
            re(a, b+c/2, c/2);
            re(a+c, b+c/2, c/2);
        }
    }
}
```

*1780. 종이의 개수*
```java
import java.io.*;
import java.util.*;

public class Main{
    static int[][] arr;
    static int z, v, c;
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        arr = new int[count][count];
        
        for(int i=0;i<count;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=0;j<count;j++){
                arr[j][i] = Integer.parseInt(st.nextToken());
            }
        }
        
        z = v = c = 0;
        re(0,0,count);
        System.out.println(z);
        System.out.println(v);
        System.out.println(c);
    }
    
    public static void re(int x, int y, int num){
        int a = arr[x][y];
        for(int i=0;i<num;i++){
            for(int j=0;j<num;j++){
                if(arr[x+j][y+i] != a){
                    for(int q=0; q<=num/3*2; q+=num/3){
                        for(int w=0; w<=num/3*2; w+=num/3){
                            re(x+w, y+q, num/3);
                        }
                    }
                    return;
                }
            }
        }
        
        if(a == -1){
            z++;
        }else if(a == 0){
            v++;
        }else if(a == 1){
            c++;
        }
    }
}
```

*1992. 쿼드트리*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int[][] arr;
    static StringBuilder sb = new StringBuilder();
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        arr = new int[count][count];
        
        for(int i=0;i<count;i++){
            String[] s = br.readLine().split("");
            for(int j=0;j<count;j++){
                arr[j][i] = Integer.parseInt(s[j]);
            }
        }
        
        re(0,0,count);
        System.out.println(sb);
    }
    
    public static void re(int x, int y, int num){
        int a = arr[x][y];
        for(int i=0;i<num;i++){
            for(int j=0;j<num;j++){
                if(arr[x+j][y+i] != a){
                    sb.append("(");
                    re(x, y, num/2);
                    re(x+num/2, y, num/2);
                    re(x, y+num/2, num/2);
                    re(x+num/2, y+num/2, num/2);
                    sb.append(")");
                    return;
                }
            }
        }
        sb.append(a);
    }
}
```

*2512. 예산*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[count];
        int left = 0;
        int right = 0;
        StringTokenizer st = new StringTokenizer(br.readLine());
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
            right = Math.max(right, arr[i]);
        }
        int money = Integer.parseInt(br.readLine());
        
        while(left <= right){
            int mid = (left + right)/2;
            int a = 0;
            
            for(int i=0;i<count;i++){
                if(arr[i] > mid){
                    a += mid;
                }else{
                    a += arr[i];
                }
            }
            
            if(a <= money){
                left = mid+1;
            }else{
                right = mid-1;
            }
        }
        System.out.println(right);
    }
}
```

*2110. 공유기 설치*
```java
import java.io.*;
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int house = Integer.parseInt(st.nextToken());
        int count = Integer.parseInt(st.nextToken());
        int[] arr = new int[house];
        
        for(int i=0;i<house;i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        
        Arrays.sort(arr);
        
        int left = 1;
        int right = arr[house-1] - arr[0];
        int d = 0;
        int ans = 0;
        
        while(left <= right){
            int mid = (left + right)/2;
            int start = arr[0];
            int a = 1;
            
            for(int i=0;i<house;i++){
                d = arr[i] - start;
                if(d >= mid){
                    a++;
                    start = arr[i];
                }
            }
            
            if(a >= count){
                ans = mid;
                left = mid+1;
            }else{
                right = mid-1;
            }
        }
        System.out.println(ans);
    }
}
```

*2470. 두 용액*
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
        
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
        
        Arrays.sort(arr);
        int ans = Math.abs(arr[count-1] + arr[0]);
        int a = arr[0];
        int b = arr[count-1];
        int i = 0;
        int j = count-1;
        
        while(j != i){
            if(ans > Math.abs(arr[j] + arr[i])){
                ans = Math.abs(arr[j] + arr[i]);
                a = arr[i];
                b = arr[j];
            }
            if(arr[j] + arr[i] > 0){
                j--;
            }else{
                i++;
            }
        }
        
        System.out.println(a + " " + b);
    }
}
```
