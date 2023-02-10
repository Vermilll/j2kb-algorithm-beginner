10828. 스택
```java
import java.io.*;
import java.util.*;

class Main{

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int n = Integer.parseInt(br.readLine());
        Stack<Integer> stack = new Stack<>();

        for(int i=0;i<n;i++){
            StringTokenizer st = new StringTokenizer(br.readLine(), " ");
            String command = st.nextToken();
            if(command.equals("push")){
                stack.push(Integer.parseInt(st.nextToken()));
            }else if(command.equals("pop")){
                if(stack.isEmpty()) {
                    sb.append(-1).append("\n");
                }else{
                    sb.append(stack.pop()).append("\n");
                }
            }
            else if(command.equals("size")) {
                sb.append(stack.size()).append("\n");
            }
            else if(command.equals("empty")){
                if(stack.isEmpty()) {
                    sb.append(1).append("\n");
                }else{
                    sb.append(0).append("\n"); 
                } 
            }
            else if(command.equals("top")){
                if (stack.isEmpty()) {
                    sb.append(-1).append("\n");
                }else{
                    sb.append(stack.peek()).append("\n");
                }
            }
        }

        System.out.println(sb);
    }
}
```

9012. 괄호
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        for(int i=0;i<a;i++){
            String s = sc.next();
            int count = 0;
            while(s.length()>0){
                String first = s.substring(0,1);
                count = first.equals("(") ? count+1 : count-1;
                s = s.substring(1);
                if(count<0){break;}
            }
            System.out.println(count == 0 ? "YES" : "NO");
        }
    }
}
```
10773. 제로
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Stack<Integer> stack = new Stack<>();
        Scanner sc = new Scanner(System.in);
        int count = sc.nextInt();
        
        for(int i=0;i<count;i++){
            int num = sc.nextInt();
            if(num != 0){stack.push(num);}
            else{stack.pop();}
        }
        count = stack.size();
        int ans = 0;
        for(int i=0;i<count;i++){
            ans += stack.pop();
        }
        System.out.println(ans);
    }
}
```

1935. 후위 표기식2
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int count = sc.nextInt();
        String s = sc.next();
        Stack<Double> stack = new Stack<>();
        Map<Character, Double> map = new HashMap<>();
        char c = 'A';
        
        for(int i=0;i<count;i++){
            map.put(c,Double.parseDouble(sc.next()));
            c++;
        }
        
        double ans;
        for(int i=0;i<s.length();i++){
            double a,b;
            if(s.substring(i,i+1).equals("+")){
                a = stack.pop();
                b = stack.pop();
                stack.push(a + b);
            }else if(s.substring(i,i+1).equals("-")){
                a = stack.pop();
                b = stack.pop();
                stack.push(b - a);
            }else if(s.substring(i,i+1).equals("*")){
                a = stack.pop();
                b = stack.pop();
                stack.push(a * b);
            }else if(s.substring(i,i+1).equals("/")){
                a = stack.pop();
                b = stack.pop();
                stack.push(b / a);
            }else{
                stack.push(map.get(s.charAt(i)));
            }
        }
        
		System.out.print(String.format("%.2f", stack.pop()));
    }
}
```
1406. 에디터
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        Stack<String> stack1 = new Stack<>();
        Stack<String> stack2 = new Stack<>(); 
        String s = br.readLine();
        int count = Integer.parseInt(br.readLine());
        
        while(s.length() != 0){
            stack1.push(s.substring(0,1));
            s = s.substring(1);
        }
        
        for(int i=0;i<count;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            String a = st.nextToken();
            if(a.equals("L") && !stack1.empty()){
                stack2.push(stack1.pop());
            }else if(a.equals("D") && !stack2.empty()){
                stack1.push(stack2.pop());
            }else if(a.equals("B") && !stack1.empty()){
                stack1.pop();
            }else if(a.equals("P")){
                stack1.push(st.nextToken());
            }
        }
        while(!stack1.empty()){
            stack2.push(stack1.pop());
        }
        while(!stack2.empty()){
            sb.append(stack2.pop());
        }
        System.out.println(sb);
    }
}
```

1874. 스택 수열
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        int push = 1;
        int pop = Integer.parseInt(br.readLine());
        int count = 0;
        
        Stack<Integer> stack = new Stack<>();
        String[] ans = new String[2*pop];
        
        for(int i=0;i<pop;i++){
            int num = Integer.parseInt(br.readLine());
            while(num >= push){
                ans[count++] = "+";
                stack.push(push++);
            }
            if(stack.pop() != num){
                ans = new String[0];
                count = 0;
                System.out.println("NO");
                break;
            }else{
                ans[count++] = "-";
            }
        }
        for(int i=0;i<count;i++){
            System.out.println(ans[i]);
        }
    }
}
```

10799. 쇠막대기
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args) throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String s = br.readLine();
        
        Stack<String> stack = new Stack<>();
        int count = 0;
        
        for(int i=0;i<s.length();i++){
            String next = s.substring(i,i+1);
            if(next.equals("(")){
                stack.push("(");
            }else if(next.equals(")")){
                    stack.pop();
                if(s.substring(i-1,i).equals("(")){
                    count += stack.size();
                }else{
                    count += 1;
                }
            }
        }
        System.out.println(count);
    }
}
```

2493. 탑
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        int poped = 0;
        StringTokenizer st = new StringTokenizer(br.readLine());
        Stack<Integer> stack = new Stack<>();
        int[] arr = new int[count];
        
        for(int i=0;i<count;i++){
            int num = Integer.parseInt(st.nextToken());
            int a = i;
            
            while(!stack.empty()){
                if(stack.peek() >= num){
                    break;
                }else{
                    a = arr[--a];
                    stack.pop();
                }
            }
            stack.push(num);
            sb.append(a + " ");
            arr[i] = a;
        }
        
        System.out.print(sb);
    }
}
```
17298. 오큰수
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        int[] arr = new int[count];
        Stack<Integer> stack1 = new Stack<>();
        Stack<Integer> stack2 = new Stack<>();
        Stack<Integer> ans = new Stack<>();
        
        for(int i=0;i<count;i++){
            int num = Integer.parseInt(st.nextToken());
            stack1.push(num);
        }
        
        for(int i=0;i<count;i++){
            int num = stack1.pop();
            int a;
            while(true){
                if(stack2.empty()){
                    a = -1;
                    stack2.push(num);
                    break;
                }else if(stack2.peek() > num){
                    a = stack2.peek();
                    stack2.push(num);
                    break;
                }
                stack2.pop();
            }
            ans.push(a);
        }
        while(!ans.empty()){
            sb.append(ans.pop() + " ");
        }
        System.out.println(sb);
    }
}
```

2812. 크게 만들기
```java
import java.io.*;
import java.util.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        StringBuilder sb = new StringBuilder();
        
        int count = Integer.parseInt(st.nextToken());
        int del = Integer.parseInt(st.nextToken());
        int l = count - del;
        String s = br.readLine();
        String[] arr = s.split("");
        LinkedList<Integer> q1 = new LinkedList<>();
        LinkedList<Integer> q2 = new LinkedList<>();
        
        for(int i=0;i<count;i++){
            q1.add(Integer.parseInt(arr[i]));
        }
    
        while(del != 0 && !q1.isEmpty()){
            if(q2.isEmpty() || q1.peek() <= q2.peekLast()){
                q2.add(q1.poll());
            }else{
                q2.pollLast();
                del--;
            }
        }
        
        while(!q1.isEmpty()){
            q2.add(q1.poll());
        }
        
        for(int i=0;i<l;i++){
            sb.append(q2.poll());
        }
        
        System.out.println(sb);
    }
}
```

18258. 큐2
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        
        Deque<String> queue = new LinkedList<>();
        int count = Integer.parseInt(br.readLine());
        
        for(int i=0;i<count;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            String s = st.nextToken();
            if(s.equals("push")){
                queue.add(st.nextToken());
            }else if(s.equals("pop")){
                if(queue.isEmpty()){
                    sb.append("-1").append("\n");
                }else{
                    sb.append(queue.poll()).append("\n");
                }
            }else if(s.equals("front")){
                if(queue.isEmpty()){
                    sb.append("-1").append("\n");
                }else{
                    sb.append(queue.peek()).append("\n");
                }                
            }else if(s.equals("back")){
                if(queue.isEmpty()){
                    sb.append("-1").append("\n");
                }else{
                    sb.append(queue.peekLast()).append("\n");
                }                
            }else if(s.equals("size")){
                sb.append(queue.size()).append("\n");
            }else if(s.equals("empty")){
                if(queue.isEmpty()){
                    sb.append("1").append("\n");
                }else{
                    sb.append("0").append("\n");
                }
            }
        }
        
        System.out.println(sb);
    }
}
```
2164. 카드2
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        Deque<Integer> q = new LinkedList<>();
        
        for(int i=1;i<=num;i++){
            q.add(i);
        }
        
        while(q.size() != 1){
            q.poll();
            q.add(q.poll());
        }
        System.out.println(q.poll());
    }
}
```

1021. 회전하는 큐
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int ans = 0;
        
        StringTokenizer st = new StringTokenizer(br.readLine());
        int deck = Integer.parseInt(st.nextToken());
        int count = Integer.parseInt(st.nextToken());
        Deque<Integer> q = new LinkedList<>();
        st = new StringTokenizer(br.readLine());
        for(int i=0;i<deck;i++){
            q.add(i+1);
        }
        
        for(int i=0;i<count;i++){
            int num = Integer.parseInt(st.nextToken());  
            int temp = 0;
            while(q.peekFirst() != num){
                q.add(q.pollFirst());
                temp++;
            }
            ans += temp < q.size()-temp ? temp : q.size() - temp;
            q.pollFirst();
        }
        System.out.println(ans);
    }
}
```

1966. 프린터 큐
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int a = Integer.parseInt(br.readLine());
        
        for(int i=0;i<a;i++){
            LinkedList<Integer> q = new LinkedList<>();
            LinkedList<Integer> r = new LinkedList<>();
            StringTokenizer st = new StringTokenizer(br.readLine());
            int count = Integer.parseInt(st.nextToken());
            int index = Integer.parseInt(st.nextToken());
            st = new StringTokenizer(br.readLine());
            int print = 0;
            
            for(int j=0;j<count;j++){
                q.add(Integer.parseInt(st.nextToken()));
                r.add(j);
            }
            
            while(!q.isEmpty()){
                boolean max = true;
                for(int k=1;k<q.size();k++){
                    if(q.get(k)>q.peek()){
                        q.add(q.poll());
                        r.add(r.poll());
                        max = false;
                        break;
                    }
                }
                
                if(max){
                    q.poll();
                    print++;
                    if(r.poll() == index){
                        System.out.println(print);
                        break;
                    }
                }
            }
        }
    }
}
```

11866. 요세푸스 문제 0
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        StringBuilder sb = new StringBuilder();
        int all = Integer.parseInt(st.nextToken());
        int num = Integer.parseInt(st.nextToken());
        Deque<Integer> q = new LinkedList<>();
        
        for(int i=1;i<=all;i++){
            q.add(i);
        }
        sb.append("<");
        
        while(q.size() > 1){
            for(int i=0;i<num-1;i++){
                q.add(q.poll());
            }
            sb.append(q.poll()).append(", ");
        }
        sb.append(q.poll()).append(">");
        
        System.out.println(sb);
    }
}
```

1927. 최소 힙
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        StringBuilder sb = new StringBuilder();
        PriorityQueue<Integer> q = new PriorityQueue<>();
        
        for(int i=0;i<count;i++){
            int num = Integer.parseInt(br.readLine());
            if(num == 0){
                if(q.isEmpty()){
                    sb.append(0).append("\n");
                }else{
                    sb.append(q.poll()).append("\n");
                }
            }else{
                q.add(num);
            }
        }
        System.out.println(sb);
    }
}
```

11286. 절댓값 힙
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        
		PriorityQueue<Integer> q = new PriorityQueue<Integer>(new Comparator<Integer>() {
			@Override
			public int compare(Integer o1, Integer o2) {
				if(Math.abs(o1) > Math.abs(o2)) {
					return Math.abs(o1) - Math.abs(o2);
				}else if(Math.abs(o1) == Math.abs(o2)) {
					return o1 - o2;
				}else {
					return -1;
				}
			}
        });
        
        for(int i=0;i<count;i++){
            int num = Integer.parseInt(br.readLine());
            if(num == 0){
                if(q.isEmpty()){
                    sb.append(0).append("\n");
                }else{
                    sb.append(q.poll()).append("\n");
                }
            }else{
                q.add(num);
            }
        }
        System.out.println(sb);
    }
}
```
