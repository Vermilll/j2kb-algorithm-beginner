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
