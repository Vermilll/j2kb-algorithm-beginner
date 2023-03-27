*2961. 도영이가 만든 맛있는 음식*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int[][] arr;
    static int ans = Integer.MAX_VALUE;
    static boolean[] check;
    static int all;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        all = Integer.parseInt(br.readLine());
        arr = new int[all][2];
        check = new boolean[all];
        
        for(int i=0;i<all;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            arr[i][0] = Integer.parseInt(st.nextToken());
            arr[i][1] = Integer.parseInt(st.nextToken());
        }
        a(0);
        System.out.println(ans);
    }
    
    public static void a(int num){
        if(num == all){
            int s = 1;
            int b = 0;
            int count = 0;
            for(int i=0;i<all;i++){
                if(check[i]){
                    count++;
                    s *= arr[i][0];
                    b += arr[i][1];
                }
            }
            if(count == 0) return;
            ans = Math.min(ans, Math.abs(s - b));
	    	return;      
        }
        
        check[num] = true;
        a(num+1);
        check[num] = false;
        a(num+1);
    }
}
```

