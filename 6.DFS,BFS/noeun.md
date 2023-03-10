## 2026 번

```java

public class b2606 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int cnt = Integer.parseInt(br.readLine());
    int connect = Integer.parseInt(br.readLine());
    StringTokenizer st;
    Queue<Integer> que = new LinkedList<>();
    
    int[][] arr = new int[cnt+1][cnt+1];
    
    for(int i=0; i<connect; i++) {
      st = new StringTokenizer(br.readLine());
      int x = Integer.parseInt(st.nextToken());
      int y = Integer.parseInt(st.nextToken());
      
      arr[x][y] = 1;
      arr[y][x] = 1;
    }
    
    boolean[] visited = new boolean[cnt+1];
    visited[1] = true;
    que.add(1);
    int result = 0;
    
    while(!que.isEmpty()) {
      int now = que.poll();
      for(int i=1; i<=cnt; i++) {
        if(arr[now][i] ==1 && !visited[i]) {
          que.add(i);
          visited[i] = true;
          result++;
        }
      }
    }
    
    System.out.println(result);
    
    br.close();
    
  }
}


```

<br/>

## 11724 번

```java

public class b11724 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    StringTokenizer st = new StringTokenizer(br.readLine());
    
    int N = Integer.parseInt(st.nextToken());
    int M = Integer.parseInt(st.nextToken());
    int[][] arr = new int[N+1][N+1];
    boolean[] visited = new boolean[N+1];
    Queue<Integer> que = new LinkedList<>();
    int result = 0;
    
    for(int i=0; i<M; i++) {
      st = new StringTokenizer(br.readLine());
      int x = Integer.parseInt(st.nextToken());
      int y = Integer.parseInt(st.nextToken());
      arr[x][y] = 1;
      arr[y][x] = 1;
    }
    
    for(int i=1; i<=N; i++) {
      if(!visited[i]) {
        visited[i] = true;
        que.add(i);
        result++;
      }
      
      while(!que.isEmpty()) {
        int now = que.poll();
        for(int j=1; j<=N; j++) {
          if(arr[now][j] == 1 && !visited[j]) {
            que.add(j);
            visited[j] = true;
          }
        }
      }
    }
    
    System.out.println(result);
    br.close();
    
  }
}


```

<br/>

## 10451 번

```java

public class b10451 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int T = Integer.parseInt(br.readLine());
    StringTokenizer st;
    Queue<Integer> que = new LinkedList<>(); 
    int result = 0;
    
    for(int i=0; i<T; i++) {
      int N = Integer.parseInt(br.readLine());
      st = new StringTokenizer(br.readLine());
      result = 0;
      que.clear();
      int[][] arr = new int[N+1][N+1];
      boolean[] visited = new boolean[N+1];
      
      for(int j=1; j<=N; j++) {
        int next = Integer.parseInt(st.nextToken());
        arr[j][next] = 1; 
      }
      
      for(int j=1; j<=N; j++) {
        if(!visited[j]) {
          visited[j] = true;
          que.add(j);
          result++;
        }
        
        while(!que.isEmpty()) {
          int now = que.poll();
          for(int k=1; k<=N; k++) {
            if(arr[now][k]==1 && !visited[k]) {
              visited[k] = true;
              que.add(k);
            }
          }
        }
        
      }
    
      System.out.println(result);
    }
    
    br.close();
  }
}


```

<br/>

## 1012 번

```java

public class b1012 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    Queue<Pos> que = new LinkedList<>();
    
    int T = Integer.parseInt(br.readLine());
    int result;
    
    for(int i=0; i<T; i++) {
      que.clear();
      result = 0;
      StringTokenizer st = new StringTokenizer(br.readLine());
      int M = Integer.parseInt(st.nextToken());
      int N = Integer.parseInt(st.nextToken());
      int K = Integer.parseInt(st.nextToken());
    
      int[][] arr = new int[N+1][M+1];
      boolean[][] visited = new boolean[N+1][M+1];
    
      for(int j=0; j<K; j++) {
        st = new StringTokenizer(br.readLine());
        int x = Integer.parseInt(st.nextToken());
        int y = Integer.parseInt(st.nextToken());
        arr[y][x] = 1;
      }
      
      for(int j=0; j<N; j++) {
        for(int k=0; k<M; k++) {
          if(arr[j][k] == 1 && !visited[j][k]) {
            que.add(new Pos(k,j));  
            visited[j][k] = true;    
            result++;      
          }
          
          while(!que.isEmpty()) {
            Pos pos = que.poll();
            int x = pos.x;
            int y = pos.y;
          
            if(y<N-1 && arr[y+1][x]==1 && !visited[y+1][x]) { // N=10 y<9. 접근은 9까지 가능. arr[9]
              visited[y+1][x] = true;
              que.add(new Pos(x, y+1));
            }
            if(x<M-1 && arr[y][x+1]==1 && !visited[y][x+1]) {
              visited[y][x+1] = true;
              que.add(new Pos(x+1, y));
            }
            
            if(y>0 && arr[y-1][x]==1 && !visited[y-1][x]) { // N=10 y<9. 접근은 9까지 가능. arr[9]
              visited[y-1][x] = true;
              que.add(new Pos(x, y-1));
            }
            
            if(x>0 && arr[y][x-1]==1 && !visited[y][x-1]) {
              visited[y][x-1] = true;
              que.add(new Pos(x-1, y));
            }
            
          }
          
        }
      }
      System.out.println(result);
    }
    
    br.close();
  }
  
  static class Pos {
    int x;
    int y;
    
    Pos(int x, int y) {
      this.x = x;
      this.y = y;
    }
  }
  
}



```



