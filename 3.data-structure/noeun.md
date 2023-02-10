 ## 10828 번 : 스택
 
 ```java
 public class b10828 {
  
  static List<Integer> list = new ArrayList<>();
  
  // push X: 정수 X를 스택에 넣는 연산이다.
  public static void pushX(int x) {
    list.add(x);
  }
  
  public static int popX() {
    int size = sizeX();
    if(size == 0) {
      return -1;
    } else {
      Integer popNum = list.get(size - 1);
      list.remove(size-1);
      return popNum.intValue();
    }
  }
  
  public static int sizeX() {
    int size = list.size();
    return size;
  }
  
  public static int emptyX() {
    int size = sizeX();
    if(size <= 0) {
      return 1;
    }
    return 0;
  }
  
  public static int topX() {
    int size = sizeX();
    if(emptyX() > 0) {
      return -1;
    }
    int topX = list.get(size-1);
    return topX;
  }
  
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    
    int N = Integer.parseInt(br.readLine());
    
    StringTokenizer st;
    
    for(int i=0; i<N; i++) {
      st = new StringTokenizer(br.readLine());
      String doin = st.nextToken();
      if(doin.equals("push")) {
        int num = Integer.parseInt(st.nextToken());
        pushX(num);
      } else if (doin.equals("pop")) {
        bw.write(popX() + "\n");
      } else if(doin.equals("size")) {
        bw.write(sizeX() + "\n");
      } else if(doin.equals("empty")) {
        bw.write(emptyX() + "\n");
      } else if(doin.equals("top")) {
        bw.write(topX() + "\n");
      } 
      
    }    
    bw.flush();
    bw.close();
    br.close();
    
  }
  
}
 
 ```
 
 <br/><br/>
 
 ## 10845 번 : 큐
 ```java
 public class b10845 {
  
  static List<Integer> list = new ArrayList<>();
  
   public static void pushX(int x) {
    list.add(x);
    
   }
   
   public static int popX() {
    if(emptyX() > 0) {
      return -1;
    }
    Integer popNum = list.get(0);
    list.remove(0);
    return popNum.intValue();
   }
   public static int sizeX() {
    return list.size();
   }
   public static int emptyX() {
    if(list.isEmpty()) {
      return 1;
    }
    return 0;
   }
   public static int frontX() {
    if(emptyX() > 0) {
      return -1;
    }
    Integer frontX = list.get(0);
    return frontX.intValue();
   }
   public static int backX() {
    if(emptyX() > 0) {
      return -1;
    }
    int size = sizeX();
    Integer backX = list.get(size-1);
    return backX.intValue();
   }
   
   
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    
    StringTokenizer st;
    int N = Integer.parseInt(br.readLine());
    
    for(int i=0; i<N; i++) {
      st = new StringTokenizer(br.readLine());
      String doin = st.nextToken();
      if(doin.equals("push")) {
        int x = Integer.parseInt(st.nextToken());
        pushX(x);
      }else if(doin.equals("pop")) {
        bw.write(popX() + "\n");
      }else if(doin.equals("size")) {
        bw.write(sizeX() + "\n");
      }else if(doin.equals("empty")) {
        bw.write(emptyX() + "\n");
      }else if(doin.equals("front")) {
        bw.write(frontX() + "\n");
      }else if(doin.equals("back")) {
        bw.write(backX() + "\n");
      }
      
    }
    bw.flush();
    bw.close();
    br.close();
    
  }
}

 ```
 
  <br/><br/>
 
 
 
 
 
 
 
 
 
 
