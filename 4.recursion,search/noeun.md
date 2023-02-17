## 10870 번

```java

public class b10870 {
  
  public static void main(String[] args) throws IOException {
   BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
   
   int N = Integer.parseInt(br.readLine());
   int result = fibo(N);
  
   System.out.println(result);
    
  }
  
  public static int fibo(int num) {
    if(num == 0) {
      return 0;
    }
    if(num == 1) {
      return 1;
    } 
    
    return fibo(num-1) + fibo(num-2);
  }
  
}


```

<br/><br/>


## 17478 번

```java

public class b17478 {
  static int N;
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    
    N = Integer.parseInt(br.readLine());
    System.out.println("어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.");
    fibo(0, "");
    
  }
  
  public static void fibo(int cnt, String under) {
    
    if(cnt == N) {
      System.out.println(under + "\"재귀함수가 뭔가요?\"");
      System.out.println(under + "\"재귀함수는 자기 자신을 호출하는 함수라네\"");
      System.out.println(under + "라고 답변하였지.");
      
      return;
    }

    System.out.println(under + "\"재귀함수가 뭔가요?\"");
    System.out.println(under + "\"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한 선인이 있었어.");
    System.out.println(under + "마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 모두 지혜롭게 대답해 주었지.");
    System.out.println(under + "그의 답은 대부분 옳았다고 하네. 그런데 어느 날, 그 선인에게 한 선비가 찾아와서 물었어.\"");
  
    
   fibo(cnt+1, under + "____");
   System.out.println(under + "라고 답변하였지.");
  }
  
}


```


<br/><br/>


## 10814 번

```java

public class b10814 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    
    int N = Integer.parseInt(br.readLine());
    Person[] p = new Person[N];
    for(int i=0; i<N; i++) {
      StringTokenizer st = new StringTokenizer(br.readLine());
    
      int age = Integer.parseInt(st.nextToken());
      String name = st.nextToken();
      p[i] = new Person(age, name);
    }
    
    Arrays.sort(p, new Comparator<Person>() {
      @Override
      public int compare(Person p1, Person p2) {
        return p1.age -p2.age;
      }
    });
    
    StringBuilder sb = new StringBuilder();
    for (int j=0; j<N; j++) {
      sb.append(p[j]); // 객체를 출력하면 해당 인덱스의 객체의 toString() 이 출력
    }
    System.out.println(sb);
    
  }
  
  public static class Person {
    int age;
    String name;
    
    public Person(int age, String name) {
      this.age = age;
      this.name = name;
    }
    
    @Override
		public String toString() {
			return age + " " + name + "\n";
		}
    
  }
}


```

<br/><br/>

## 1427 번

```java
public class b1427 {
  
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    
    String N = br.readLine();
    List<Integer> list = new ArrayList<>();
    for(int i=0; i<N.length(); i++) {
      int num = N.charAt(i) - '0';
      list.add(num);
    }
    
    Collections.sort(list, Collections.reverseOrder());
    
    for (Integer l : list) {
      bw.write(String.valueOf(l));
    }
    
    br.close();
    bw.flush();
    bw.close();
    
  }
}


```


<br/><br/>


## b2750 번


```java

public class b2750 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int N = Integer.parseInt(br.readLine());
    
    List<Integer> list = new ArrayList<>();
    for(int i=0 ;i<N; i++) {
      list.add(Integer.parseInt(br.readLine()));
    }
    
    Collections.sort(list);
    
    for (Integer i : list) {
      System.out.println(String.valueOf(i));
    }
    
    br.close();
    
  }
}


```












