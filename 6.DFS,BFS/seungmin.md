*1260. DFS와 BFS*
```java
import java.io.*;
import java.util.*;

public class Main {
	static StringBuilder sb = new StringBuilder();
	static boolean[] check;
	static int[][] arr;
	
	static int top, line, start;
	static Queue<Integer> q = new LinkedList<>();

	public static void main(String[] args) throws Exception{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		top = Integer.parseInt(st.nextToken());
		line = Integer.parseInt(st.nextToken());
		start= Integer.parseInt(st.nextToken());
		
		arr = new int[top+1][top+1];
		check = new boolean[top+1];
		
		for(int i=0;i<line;i++) {
			StringTokenizer st1 = new StringTokenizer(br.readLine());
			
			int a = Integer.parseInt(st1.nextToken());
			int b = Integer.parseInt(st1.nextToken());
			
			arr[a][b] = arr[b][a] =  1;	
		}
		dfs(start);
		sb.append("\n");
        
		check = new boolean[top+1];
		bfs(start);
		System.out.println(sb);
	}
    
	public static void dfs(int start) {
		check[start] = true;
		sb.append(start + " ");
		
		for(int i=0;i<top+1;i++) {
			if(arr[start][i] == 1 && !check[i])
				dfs(i);
		}
	}
	
	public static void bfs(int start) {
		q.add(start);
		check[start] = true;
		
		while(!q.isEmpty()) {
			start = q.poll();
			sb.append(start + " ");
			
			for(int i=1;i<top+1;i++) {
				if(arr[start][i] == 1 && !check[i]) {
					q.add(i);
					check[i] = true;
				}
			}
		}
	}
}
```
