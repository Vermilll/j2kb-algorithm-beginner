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

*1946. 신입 사원*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        for(int l=0;l<all;l++){
            int count = Integer.parseInt(br.readLine());
            int ans = count;
            int[] arr = new int[count];
            
            for(int i=0;i<count;i++){
                StringTokenizer st = new StringTokenizer(br.readLine());
                int a = Integer.parseInt(st.nextToken());
                arr[a-1] = Integer.parseInt(st.nextToken());
            }
            
            int max = arr[0];
            
            for(int i=0;i<count;i++){
                if(max < arr[i]){
                    ans--;
                }else{
                    max = arr[i];
                }
            }
            System.out.println(ans);
        }
    }
}
```

*.11497. 통나무 건너뛰기*
```java
import java.io.*;
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        for(int i=0;i<all;i++){
            int count = Integer.parseInt(br.readLine());
            int[] arr = new int[count];
            int[] to = new int[count];
            StringTokenizer st = new StringTokenizer(br.readLine());
            
            for(int j=0;j<count;j++){
                arr[j] = Integer.parseInt(st.nextToken());
            }
            Arrays.sort(arr);
            
            for(int j=0;j<count;j++){
                if(j%2 == 0){
                    to[j/2] = arr[j];
                }else{
                    to[count-1-j/2] = arr[j];
                }
            }
            
            int ans = 0;
            for(int j=1;j<count;j++){
                ans = Math.max(ans, Math.abs(to[j-1]-to[j]));
            }
            System.out.println(ans);
        }
    }
}

```

*42883. 큰 수 만들기*
```java
class Solution {
    public String solution(String number, int k) {
        StringBuilder sb = new StringBuilder();
        int index = 0;
        
        for(int i=0;i<number.length()-k;i++) {
            int max = 0;
            for(int j=index;j<=k+i;j++) {
                if(max < number.charAt(j)-'0') {
                    max = number.charAt(j)-'0';
                    index = j+1;
                }
            }
            sb.append(max);
        }
        return sb.toString();
    }
}
```


*42862. 체육복*
```java
import java.util.*;

class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = 0;
        int[] arr = new int[n+1];
        Arrays.sort(lost);
        Arrays.sort(reserve);
        
        for(int i=0;i<reserve.length;i++){
            arr[reserve[i]]++;
        }
        
        for(int i=0;i<lost.length;i++){
            arr[lost[i]]--;
        }
        
        for(int i=0;i<lost.length;i++){
            int a = lost[i];
            if(arr[a] == 0){
                continue;
            }
            if(a-1 >= 0 && arr[a-1]>0){
                arr[a-1]--;
                arr[a]++;
            }else if(a+1 <= n && arr[a+1]>0){
                arr[a+1]--;
                arr[a]++;
            }
        }
        
        for(int i=1;i<n+1;i++){
            if(arr[i]>=0){
                answer++;
            }
        }
        
        return answer;
    }
}
```
