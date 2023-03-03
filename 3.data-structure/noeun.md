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
 
 ## 9012 번 : 괄호
 
 ```java
 public class b9012 {
  
  static List<Integer> list = new ArrayList<>();
   
  public static void pushX() {
    list.add(1);
  }
  public static int popX() {
    int size = sizeX();
    if(size <= 0) {
      return 0;
    }
    list.remove(size-1);
    return 1;
  }
  public static int sizeX() {
    if(list.isEmpty()) {
      return 0;
    }
    return list.size();
  }
   
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    
    int T = Integer.parseInt(br.readLine());
    int popNum = 1;
    for(int i=0; i<T; i++) {
      list.clear();
      String input = br.readLine();
      for(int j=0; j<input.length(); j++) {
        popNum = 1;
        if(input.charAt(j) == '(') {
          pushX();
        } else if(input.charAt(j) == ')') {
          popNum = popX();
        }
        
        if(j == input.length()-1 && list.isEmpty() && popNum == 1) {
          bw.write("YES" + "\n");
          break;
        }
        if(j == input.length()-1 && !list.isEmpty()) {
          bw.write("NO" + "\n");
          break;
        }
        if(popNum == 0 ) {
          bw.write("NO" + "\n");
          break;
        }
        
      }
    }    

    bw.flush();
    bw.close();
    br.close();
    
  }
}

 ```
 
 
 <br/><br/>
 
 ## 10773 번 : 제로
 
 ```java
 public class b10773 {
  
  static List<Integer> list = new ArrayList<>();
  
  public static void pushX(int x) {
    list.add(x);
  }
  
  public static void popX() {
    list.remove(sizeX()-1);
  }
  
  public static int sizeX() {
    if(list.isEmpty()) {
      return 0;
    }
    return list.size();
  }
   
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    // BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    
    int N = Integer.parseInt(br.readLine());
    
    for(int i=0; i<N; i++) {
      int num = Integer.parseInt(br.readLine());
      if(num != 0) {
        pushX(num);
      } else {
        popX();
      }
    }
    
    int sum =0;
    for(int i=0; i < list.size(); i++) {
      sum += list.get(i).intValue();
    }
    
    System.out.println(sum);
    
    br.close();
  
    
  }
}

 ```
 
 <br/><br/>
 
 ## 2164 번 : 카드2
 while문으로 구현시 시간초과
 

 ```java
 public class b2164 {  
  
  // 맨앞의 숫자 삭제
  // 그 다음의 맨앞 숫자를 맨뒤에 넣기
  public static int card_game(List<Integer> current) {
    
    if(current.size() == 1) {
      return current.get(0);
    }
    else {
      List<Integer> keep = new ArrayList<>();
    
      for(int i=0; i<current.size(); i++) {
        if((i+1) % 2 == 0) keep.add(current.get(i));
      }
    
      if(current.size() % 2 == 1) {
        int num = keep.remove(0);
        keep.add(num);
      } 
      
      return card_game(keep);
    }
  }
  
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int N = Integer.parseInt(br.readLine());
    
    List<Integer> list = new ArrayList<>();
    
    for(int i=1; i<=N; i++) {
      list.add(i);
    }
    
    int result = card_game(list);
    
    System.out.println(result);
    
    br.close();
  }
}

 ```
 
 ## 1406 번
 
 ```java
 
 public class Main{
 
	// L : 커서를 왼쪽으로 옮김
	// D : 커서를 오른쪽으로 옮김 
	// B : 커서 왼쪽에 있는 문자를 삭제함
	// P $ : $라는 문자를 커서 왼쪽에 추가함
	
	static LinkedList<String> li = new LinkedList<>();
	
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		String str = br.readLine();
		int times = Integer.parseInt(br.readLine());
		
		// 초기 링크드리스트 입력 
		for(int i=0; i<str.length(); i++) {
			li.add(str.charAt(i)+"");
		}

		ListIterator<String> iter = li.listIterator();
		
		while(iter.hasNext()) {
			iter.next();
		}
		
		
		for(int i=0; i<times; i++) {
			String lin = br.readLine();
			Character comm = lin.charAt(0);
			
			switch(comm) {
			case 'P':
				char lcp = lin.charAt(2);
				iter.add(lcp+"");
				break;
			case 'L' :
				if(iter.hasPrevious())
					iter.previous();
				break;
			case 'D' :
				if(iter.hasNext())
					iter.next();
				break;
			case 'B' :
				if(iter.hasPrevious()) {
					iter.previous();
					iter.remove();	
				}
				break;
				
			default:
					break;
				
			}
			
			
			
		}
		
		System.out.println(String.join("", li));
	
	}
}
 
 ```
 
 
 
