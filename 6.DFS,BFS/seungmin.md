*1260. DFS와 BFS*
```java
import java.io.*;
import java.util.*;

public class Main {
	static StringBuilder sb = new StringBuilder();
	static boolean[] check;
	static boolean[][] arr;
	static int top, line, start;

	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		top = Integer.parseInt(st.nextToken());
		line = Integer.parseInt(st.nextToken());
		start= Integer.parseInt(st.nextToken());
		
		arr = new boolean[top+1][top+1];
		check = new boolean[top+1];
		
		for(int i=0;i<line;i++) {
			StringTokenizer st1 = new StringTokenizer(br.readLine());
			
			int a = Integer.parseInt(st1.nextToken());
			int b = Integer.parseInt(st1.nextToken());
			
			arr[a][b] = arr[b][a] =  true;	
		}
		dfs(start);
		sb.append("\n");
        
		check = new boolean[top+1];
		bfs(start);
		System.out.println(sb);
	}
    
	public static void dfs(int num) {
		check[num] = true;
		sb.append(num + " ");
		
		for(int i=1;i<top+1;i++) {
			if(arr[num][i] && !check[i])
				dfs(i);
		}
	}
	
	public static void bfs(int num) {
	    Queue<Integer> q = new LinkedList<>();
		q.add(num);
		check[num] = true;
		
		while(!q.isEmpty()) {
			num = q.poll();
			sb.append(num + " ");
			
			for(int i=1;i<top+1;i++) {
				if(arr[num][i] && !check[i]) {
					q.add(i);
					check[i] = true;
				}
			}
		}
	}
}
```

*11724. 연결 요소의 개수*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int top, line, count;
    static boolean check[];
    static boolean arr[][];
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        top = Integer.parseInt(st.nextToken());
        line = Integer.parseInt(st.nextToken());
        count = 0;
        check = new boolean[top+1];
        arr = new boolean[top+1][top+1];
        
        for(int i=0;i<line;i++){
            StringTokenizer st1 = new StringTokenizer(br.readLine());
            int a = Integer.parseInt(st1.nextToken());
            int b = Integer.parseInt(st1.nextToken());
            arr[a][b] = arr[b][a] = true;
        }
        
        for(int i=1;i<top+1;i++){
            if(!check[i]){
                dfs(i);
                count++;
            }
        }
        System.out.println(count);
    }
    
    public static void dfs(int num){
        if(check[num]){
            return;
        }else{
            check[num] = true;
            for(int i=1;i<top+1;i++){
                if(arr[num][i]){
                    dfs(i);
                }
            }
        }
    } 
}
```

*10451. 순열 사이클*
```java
import java.util.*;
import java.io.*;

public class Main{
    static boolean[][] arr;
    static boolean[] check;
    static int count, top;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        
        for(int i=0;i<all;i++){
            count = 0;
            top = Integer.parseInt(br.readLine());
            arr = new boolean[top+1][top+1];
            check = new boolean[top+1];
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=1;j<top+1;j++){
                int a = Integer.parseInt(st.nextToken());
                arr[j][a] = arr[a][j] = true;
            }
            
            for(int j=1;j<top+1;j++){
                if(!check[j]){
                    dfs(j);
                    count++;
                }
            }
            System.out.println(count);
        }
    }
    
    public static void dfs(int num){
        for(int i=1;i<top+1;i++){
            if(arr[num][i] && !check[i]){
                check[i] = true;
                dfs(i);
            }
        }
    }
}
```

*2606. 바이러스*
```java
import java.util.*;
import java.io.*;

public class Main{
    static boolean[] check;
    static boolean[][] arr;
    static int count = -1;
    static int top, line;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        top = Integer.parseInt(br.readLine());
        line = Integer.parseInt(br.readLine());
        check = new boolean[top+1];
        arr = new boolean[top+1][top+1];
        
        for(int i=0;i<line;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            int a = Integer.parseInt(st.nextToken());
            int b = Integer.parseInt(st.nextToken());
            arr[a][b] = arr[b][a] = true;
        }
        
        dfs(1);
        System.out.println(count);
    }
    
    public static void dfs(int num){
        check[num] = true;
        count++;
        for(int i=1;i<top+1;i++){
            if(!check[i] && arr[num][i]){
                dfs(i);
            }
        }
    }
}
```

*1012. 유기농 배추*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int ans;
    static boolean[][] arr;
    static boolean[][] check;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        
        for(int l=0;l<all;l++){
            ans = 0;
            StringTokenizer st = new StringTokenizer(br.readLine());
            int x = Integer.parseInt(st.nextToken());
            int y = Integer.parseInt(st.nextToken());
            int count = Integer.parseInt(st.nextToken());
            arr = new boolean[2501][2501];
            check = new boolean[2501][2501];
            
            for(int i=0;i<count;i++){
                StringTokenizer st1 = new StringTokenizer(br.readLine());
                int x1 = Integer.parseInt(st1.nextToken());
                int y1 = Integer.parseInt(st1.nextToken());
                arr[x1][y1] = true;
            }
            for(int i=0;i<x;i++){
                for(int j=0;j<y;j++){
                    if(!check[i][j] && arr[i][j]){
                        dfs(i,j);
                        ans++;
                    }
                }
            }
            System.out.println(ans);
        }
    }
    
    public static void dfs(int x, int y){
        check[x][y] = true;
        if(!check[x+1][y] && arr[x+1][y]){
            dfs(x+1,y);
        }
        if(!check[x][y+1] && arr[x][y+1]){
            dfs(x,y+1);
        }
        
        if(x!= 0 && !check[x-1][y] && arr[x-1][y]){
            dfs(x-1,y);
        }
        if(y!= 0 && !check[x][y-1] && arr[x][y-1]){
            dfs(x,y-1);
        }
    }
}
```

*1991. 트리순회*
```java
```

*11725. 트리의 부모 찾기*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int count;
    static ArrayList<Integer>[] list;
    static boolean[] check;
    static int[] parent;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        count = Integer.parseInt(br.readLine());
        
        list = new ArrayList[count+1];
        parent = new int[count+1];
        check = new boolean[count+1];
        
        for(int i=1;i<count+1;i++){
            list[i] = new ArrayList<Integer>();
        }
        
        for(int i=0;i<count-1;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            int a = Integer.parseInt(st.nextToken());
            int b = Integer.parseInt(st.nextToken());
            
            list[a].add(b);
            list[b].add(a);
        }
        
        for(int i=1;i<count+1;i++){
            if(!check[i]){
                dfs(i);
            }
        }
        
        for(int i=2;i<count+1;i++){
            System.out.println(parent[i]);
        }
    }
    
    public static void dfs(int num){
        if(!check[num]){
            check[num] = true;
            
            for(int a : list[num]){
                if(!check[a]){
                    parent[a] = num;
                    dfs(a);
                }
            }
        }
    }
}
```

*1697. 숨바꼭질*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int a = Integer.parseInt(st.nextToken());
        int b = Integer.parseInt(st.nextToken());
        int[] time = new int[100001];
        boolean[] check = new boolean[100001];
        Queue<Integer> q = new LinkedList<>();
        q.add(a);
        check[a] = true;
        time[a] = 0;
        
        while(!q.isEmpty()){
            int num = q.poll();
            int[] arr = {num-1,num+1,num*2};
            for(int i=0;i<3;i++){
                if(arr[i] < 0 || arr[i] > 100000 || check[arr[i]]){
                    continue;
                }else{
                    check[arr[i]] = true;
                    time[arr[i]] = time[num]+1;
                    if(check[b]){
                        break;
                    }
                    q.add(arr[i]);
                }
            }
        }
        System.out.println(time[b]);
    }
}
```

*5567. 결혼식*
```java
import java.util.*;
import java.io.*;

public class Main{
    static boolean[] check;
    static boolean[][] arr;
    static int answer = 0;
    static int count;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        count = Integer.parseInt(br.readLine());
        int a = Integer.parseInt(br.readLine());
        arr = new boolean[count+1][count+1];
        check = new boolean[count+1];
        check[1] = true;
        
        for(int i=0;i<a;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            int x = Integer.parseInt(st.nextToken());
            int y = Integer.parseInt(st.nextToken());
            arr[x][y] = arr[y][x] = true;
        }
        
        for(int i=1;i<count+1;i++){
            if(arr[1][i]){
                if(!check[i]){
                    answer++;
                    check[i] = true;
                }
                bfs(i);
            }
        }
        System.out.println(answer);
    }
    
    public static void bfs(int num){
        for(int i=1;i<count+1;i++){
            if(arr[num][i] && !check[i]){
                check[i] = true;
                answer++;
            }
        }
    }
}
```

*2667. 단지번호붙이기*
```java
import java.util.*;
import java.io.*;

public class Main{
    static boolean[][] arr;
    static boolean[][] check;
    static int num;
    static ArrayList<Integer> list = new ArrayList<>();
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        arr = new boolean[count+2][count+2];
        check = new boolean[count+2][count+2];
        
        for(int i=1;i<count+1;i++){
            String[] a = br.readLine().split("");
            for(int j=1;j<count+1;j++){
                if(a[j-1].equals("1")){
                    arr[j][i] = true;
                }
            }
        }
        
        for(int i=1;i<count+1;i++){
            for(int j=1;j<count+1;j++){
                if(arr[i][j] && !check[i][j]){
                    num = 0;
                    dfs(i,j);
                    list.add(num);
                }
            }
        }
        
        Collections.sort(list);
        System.out.println(list.size());
        for(int i=0;i<list.size();i++){
            System.out.println(list.get(i));
        }
    }
    
    public static void dfs(int x,int y){
        num++;
        check[x][y] = true;
        
        if(arr[x-1][y] && !check[x-1][y]){
            dfs(x-1,y);
        }
        if(arr[x+1][y] && !check[x+1][y]){
            dfs(x+1,y);
        }
        if(arr[x][y+1] && !check[x][y+1]){
            dfs(x,y+1);
        }
        if(arr[x][y-1] && !check[x][y-1]){
            dfs(x,y-1);
        }
    }
}
```

*4963. 섬의 개수*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int count;
    static boolean[][] arr;
    static boolean[][] check;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        while(true){
            count = 0;
            String[] a = br.readLine().split(" ");
            if(a[0].equals("0") && a[1].equals("0")){
                break;
            }
            int w = Integer.parseInt(a[0]);
            int h = Integer.parseInt(a[1]);
            arr = new boolean[52][52];
            check = new boolean[52][52];
            
            for(int i=1;i<h+1;i++){
                StringTokenizer st = new StringTokenizer(br.readLine());
                for(int j=1;j<w+1;j++){
                    if(st.nextToken().equals("1")){
                        arr[j][i] = true;
                    }
                }
            }
            
            for(int i=1;i<h+1;i++){
                for(int j=1;j<w+1;j++){
                    if(arr[j][i] && !check[j][i]){
                        count++;
                        dfs(j,i);
                    }
                }
            }
            System.out.println(count);
        }
    }
    
    public static void dfs(int x,int y){
        check[x][y] = true;
        
        for(int i=-1;i<2;i++){
            for(int j=-1;j<2;j++){
                if(arr[x+j][y+i] && !check[x+j][y+i]){
                    dfs(x+j,y+i);
                }
            }
        }
    }
}
```

*2178. 미로 탐색*
```java
import java.util.*;
import java.io.*;

public class Main{
    static boolean[][] check;
    static boolean[][] arr;
    static int[][] count;
    static int w,h;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        h = Integer.parseInt(st.nextToken());
        w = Integer.parseInt(st.nextToken());
        arr = new boolean[w+2][h+2];
        check = new boolean[w+2][h+2];
        count = new int[w+2][h+2];
        
        for(int i=1;i<h+1;i++){
            String[] a = br.readLine().split("");
            for(int j=1;j<w+1;j++){
                if(a[j-1].equals("1")){
                    arr[j][i] = true;
                }
            }
        }
        
        bfs(1,1);
        System.out.println(count[w][h]);
    }
    
    public static void bfs(int x,int y){
        check[x][y] = true;
        count[x][y] = 1;
        Queue<int[]> q = new LinkedList<>();
        q.add(new int[] {x,y});
        
        while(!q.isEmpty()){
            if(check[w][h]){
                return;
            }
            
            int[] now = q.poll();
            int nowx = now[0];
            int nowy = now[1];
            
            for(int i=-1;i<2;i++){
                if(arr[nowx+i][nowy] && !check[nowx+i][nowy]){
                    q.add(new int[] {nowx+i,nowy});
                    count[nowx+i][nowy] = count[nowx][nowy] + 1;
                    check[nowx+i][nowy] = true;
                }
                
                if(arr[nowx][nowy+i] && !check[nowx][nowy+i]){
                    q.add(new int[] {nowx,nowy+i});
                    count[nowx][nowy+i] = count[nowx][nowy] + 1;
                    check[nowx][nowy+i] = true;
                }
            }
        }
    }
}
```
