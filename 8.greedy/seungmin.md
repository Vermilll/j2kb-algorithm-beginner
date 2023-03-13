*1783. 병든 나이트*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int y = Integer.parseInt(st.nextToken());
        int x = Integer.parseInt(st.nextToken());
        int ans = 1;
        
        if(y == 1){
            ans = 1;
        }else if(y == 2){
            ans = Math.min(4, (x+1)/2);
        }else if(y >= 3){
            if(x <= 3){
                ans = x;
            }else if(x >= 7){
                ans = x-2;
            }else{
                ans = 4;
            }
        }
        
        System.out.println(ans);
    }
}
```

*11501. 주식*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        for(int i=0;i<all;i++){
            int count = Integer.parseInt(br.readLine());
            int[] arr = new int[count];
            int max = 0;
            long ans = 0;
            
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=0;j<count;j++){
                arr[j] = Integer.parseInt(st.nextToken());
            }
            
            for(int j=count-1;j>=0;j--){
                if(arr[j]<max){
                    ans += max-arr[j];
                }else{
                    max = arr[j];
                }
            }
            System.out.println(ans);
        }
    }
}
```
