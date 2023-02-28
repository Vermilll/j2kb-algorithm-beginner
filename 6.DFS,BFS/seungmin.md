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
