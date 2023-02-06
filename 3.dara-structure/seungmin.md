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
