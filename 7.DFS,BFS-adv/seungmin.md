*7576. 토마토*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    static int[][] arr, day;
    static boolean[][] check;
    static int w,h;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] s = br.readLine().split(" ");
        w = Integer.parseInt(s[0]);
        h = Integer.parseInt(s[1]);
        
        arr = new int[w+2][h+2];
        check = new boolean[w+2][h+2];
        day = new int[w+2][h+2];
        
        for(int i=1;i<h+1;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=1;j<w+1;j++){
                arr[j][i] = Integer.parseInt(st.nextToken()) + 1;
            }
        }
        bfs();
        
        int ans = 0;
        loop:
        for(int i=1;i<h+1;i++){
            for(int j=1;j<w+1;j++){
                if(!check[j][i]){
                    ans = -1;
                    break loop;
                }else{
                    ans = Math.max(ans, day[j][i]);
                }
            }
        }
        
        System.out.println(ans);
    }
    
    public static void bfs(){
        Queue<int[]> q = new LinkedList<>();
        
        for(int i=1;i<h+1;i++){
            for(int j=1;j<w+1;j++){
                if(arr[j][i] == 2){
                    q.add(new int[] {j,i});
                    check[j][i] = true;
                }
                if(arr[j][i] == 0){
                    check[j][i] = true;
                }
            }
        }
        
        while(!q.isEmpty()){
            int[] now = q.poll();
            int nowx = now[0];
            int nowy = now[1];
            
            if(arr[nowx-1][nowy] == 1 && !check[nowx-1][nowy]){
                check[nowx-1][nowy] = true;
                day[nowx-1][nowy] = day[nowx][nowy] + 1;
                q.add(new int[] {nowx-1,nowy});
            }
            if(arr[nowx+1][nowy] == 1 && !check[nowx+1][nowy]){
                check[nowx+1][nowy] = true;
                day[nowx+1][nowy] = day[nowx][nowy] + 1;
                q.add(new int[] {nowx+1,nowy});
            }
            if(arr[nowx][nowy-1] == 1 && !check[nowx][nowy-1]){
                check[nowx][nowy-1] = true;
                day[nowx][nowy-1] = day[nowx][nowy] + 1;
                q.add(new int[] {nowx,nowy-1});
            }
            if(arr[nowx][nowy+1] == 1 && !check[nowx][nowy+1]){
                check[nowx][nowy+1] = true;
                day[nowx][nowy+1] = day[nowx][nowy] + 1;
                q.add(new int[] {nowx,nowy+1});
            }
        }
    }
}
```

*1916. 최소비용 구하기*
```java
import java.util.*;
import java.io.*;
import java.math.*;

public class Main{
    static int[][] arr;
    static int[] price;
    static boolean[][] able;
    static boolean[] check;
    static int cityC, start, end;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        cityC = Integer.parseInt(br.readLine());
        int busC = Integer.parseInt(br.readLine());
        able = new boolean[cityC+1][cityC+1];
        check = new boolean[cityC+1];
        arr = new int[cityC+1][cityC+1];
        price = new int[cityC+1];
        
        for(int i=0;i<busC;i++){
            StringTokenizer st1 = new StringTokenizer(br.readLine());
            int a = Integer.parseInt(st1.nextToken());
            int b = Integer.parseInt(st1.nextToken());
            int c = Integer.parseInt(st1.nextToken());
            if(able[a][b]){
                arr[a][b] = Math.min(arr[a][b], c);
            }else{
                arr[a][b] = c;
            }
            able[a][b] = true;
        }
        
        StringTokenizer st = new StringTokenizer(br.readLine());
        start = Integer.parseInt(st.nextToken());
        end = Integer.parseInt(st.nextToken());
        
        bfs(start);
        System.out.println(price[end]);
    }
    
    public static void bfs(int num){
        check[num] = true;
        Queue<Integer> q = new LinkedList<>();
        q.add(num);
        
        while(!q.isEmpty()){
            int now = q.poll();
            for(int i=1;i<cityC+1;i++){
                if(able[now][i]){
                    if(!check[i]){
                        check[i] = true;
                        price[i] = price[now] + arr[now][i];
                        q.add(i);
                    }else if(price[i] > price[now] + arr[now][i]){
                        price[i] = price[now] + arr[now][i];
                        q.add(i);
                    }
                }
            }
        }
    }
}
```

*4485. 녹색 옷 입은 애가 젤다지?*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int[][] arr, money;
    static boolean[][] check;
    static int count, m;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int m = 0;
        while(true){
            m++;
            count = Integer.parseInt(br.readLine());
            if(count == 0){
                break;
            }
            arr = new int[count][count];
            money = new int[count][count];
            check = new boolean[count][count];
            for(int i=0;i<count;i++){
                StringTokenizer st = new StringTokenizer(br.readLine());
                for(int j=0;j<count;j++){
                    arr[j][i] = Integer.parseInt(st.nextToken());
                }
            }
            bfs();
            System.out.println("Problem " + m + ": " + money[count-1][count-1]);
        }
    }
    
    public static void bfs(){
        check[0][0] = true;
        Queue<int[]> q = new LinkedList<>();
        q.add(new int[] {0,0});
        money[0][0] = arr[0][0];
            
        while(!q.isEmpty()){
            int[] now = q.poll();
            int nowx = now[0];
            int nowy = now[1];
            
            if(nowx-1 >= 0){
                if(!check[nowx-1][nowy]){
                    check[nowx-1][nowy] = true;
                    money[nowx-1][nowy] = money[nowx][nowy] + arr[nowx-1][nowy];
                    q.add(new int[] {nowx-1,nowy});
                }else if(money[nowx-1][nowy] > money[nowx][nowy] + arr[nowx-1][nowy]){
                    money[nowx-1][nowy] = money[nowx][nowy] + arr[nowx-1][nowy];
                    q.add(new int[] {nowx-1,nowy});
                }
            }
            
            if(nowy-1 >= 0){
                if(!check[nowx][nowy-1]){
                    check[nowx][nowy-1] = true;
                    money[nowx][nowy-1] = money[nowx][nowy] + arr[nowx][nowy-1];
                    q.add(new int[] {nowx,nowy-1});
                }else if(money[nowx][nowy-1] > money[nowx][nowy] + arr[nowx][nowy-1]){
                    money[nowx][nowy-1] = money[nowx][nowy] + arr[nowx][nowy-1];
                    q.add(new int[] {nowx,nowy-1});
                }
            }
            
            if(nowx+1 < count){
                if(!check[nowx+1][nowy]){
                    check[nowx+1][nowy] = true;
                    money[nowx+1][nowy] = money[nowx][nowy] + arr[nowx+1][nowy];
                    q.add(new int[] {nowx+1,nowy});
                }else if(money[nowx+1][nowy] > money[nowx][nowy] + arr[nowx+1][nowy]){
                    money[nowx+1][nowy] = money[nowx][nowy] + arr[nowx+1][nowy];
                    q.add(new int[] {nowx+1,nowy});
                }
            }
            
            if(nowy+1 < count){
                if(!check[nowx][nowy+1]){
                    check[nowx][nowy+1] = true;
                    money[nowx][nowy+1] = money[nowx][nowy] + arr[nowx][nowy+1];
                    q.add(new int[] {nowx,nowy+1});
                }else if(money[nowx][nowy+1] > money[nowx][nowy] + arr[nowx][nowy+1]){
                    money[nowx][nowy+1] = money[nowx][nowy] + arr[nowx][nowy+1];
                    q.add(new int[] {nowx,nowy+1});
                }
            }
        }
    }
}
```
