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
