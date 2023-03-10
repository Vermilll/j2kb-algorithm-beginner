## 10828. 스택
https://www.acmicpc.net/problem/10828

### If Else vs Switch(https://aahc.tistory.com/6)
**특정 코드의 최적화를 위해선 if else문보다 switch구문을 쓰는게 더 적절하다.**   
if else구문은 각각의 조건문을 iterate하며 control flow를 결정한다.
N개의 if else구문이 있으면 N개의 조건문의 진위여부를 판단한다.
하지만 switch구문의 동작방식은 if else문과 다르다.
JVM에서는 switch구문안의 case 값들의 분포에 따라 내부적으로 각각의 상황에 최적화된 2개의 자바 바이트코드를 생성하는데, 공통적으로 두 경우 모두 HashTable이 연상되는 구조를 지니고 있다.
위의 예와 같이 case 값들이 서로 큰 차이가 없이 붙어있을 경우 TableSwitch형식의 컴파일을 수행하고, case의 값들이 서로 차이가 크게 날 경우 LookupSwitch형식을 사용한다. 
TableSwitch는 case의 값이 서로 큰 차이가 나지 않는 경우 case로 주어진 값과 case들 사이의 값들에 해당하는 case까지 전부 계산하여 바이트코드로 생성한다.
LookupSwitch는 TableSwitch 방식의 코드와는 다르게, case간의 값들이 서로 많이 차이나게되면 그 사이의 값들을 해시 형태로 계산해두지 않는다는 것을 알 수 있다.   
위의 링크 블로그에 예시가 있습니다.


### 코드

```java
import java.io.*;
import java.util.*;
public class Sol10828 {

	public static void main(String[] args) throws IOException{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		Stack<Integer> stack = new Stack<>();
		
		int n = Integer.parseInt(br.readLine());
		
		for(int i = 0; i < n; i++) {
			String str = br.readLine();
			if(str.contains("push")) {
				String [] spt = str.split(" ");
				stack.push(Integer.parseInt(spt[1]));
			}
			else if(str.equals("top")) {
				if(stack.isEmpty()) {
					System.out.println(-1);
				}
				else {
					System.out.println(stack.peek());
				}
			}
			else if(str.equals("empty")) {
				if(stack.isEmpty()) {
					System.out.println(1);
				}
				else {
					System.out.println(0);
				}
				
			}
			else if(str.equals("pop")) {
				if(stack.isEmpty()) {
					System.out.println(-1);
				}
				else {
					System.out.println(stack.pop());
				}
			}
			else {
				System.out.println(stack.size());
			}
		}	
	}
}

```

## 9012. 괄호
https://www.acmicpc.net/problem/9012

### next vs nextLine(https://devlog-wjdrbs96.tistory.com/80)
next(), nextLine()는 Scanner 클래스의 메소드이다. 공통점은 둘다 문자열로 반환을 시켜준다는 점이고 차이점은 개행문자를 무시하냐 안하냐의 차이이다.


### 코드

```java
import java.util.Scanner;
import java.util.Stack;

public class Sol9012 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		Stack<Character> stack = new Stack<>();
		
		for(int i = 0; i < n; i++) {
			String str = sc.next();
			for(int j = 0; j < str.length(); j++) {
				char ch = str.charAt(j);
				if(ch == '(') {
					stack.push(ch);
				}
				else {
					if(stack.isEmpty()) {
						stack.push(ch);
						break;
					}
					else {
						stack.pop();
					}
				}
			}
			if(stack.isEmpty()) {
				System.out.println("YES");
			}
			else {
				System.out.println("NO");
			}
			stack.clear();
		}

	}

}

```

## 1927. 최소 힙
https://www.acmicpc.net/problem/1927

### 코드

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.PriorityQueue;

public class Sol1927 {

	public static void main(String[] args) throws IOException{
		PriorityQueue<Integer> que = new PriorityQueue<>();
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int n = Integer.parseInt(br.readLine());
		for(int i = 0; i < n; i++) {
			int num = Integer.parseInt(br.readLine());;
			if(num == 0) {
				if(que.isEmpty()) {
					System.out.println(0);
				}
				else {
					System.out.println(que.poll());
				}
			}
			else {
				que.add(num);
			}
		}
	}
}
```

## 2164. 카드2
https://www.acmicpc.net/problem/2164

### 코드

```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Sol2164 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		Queue<Integer> que = new LinkedList<>();
		
		for(int i = 1; i <= n; i++) {
			que.offer(i);
		}
		while(que.size() != 1) {
			que.poll();
			que.add(que.poll());
		}
		System.out.println(que.poll());
	}
}
```

## 10773. 제로
https://www.acmicpc.net/problem/10773

### 코드

```java
import java.util.Scanner;
import java.util.Stack;

public class Sol10773 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		
		Stack<Integer> stack = new Stack<>();
		for(int i = 0; i < n; i++) {
			int add = sc.nextInt();
			if(add == 0) {
				stack.pop();
			}
			else {
				stack.add(add);
			}
		}
		int sum = 0;
		
		while(!stack.isEmpty()) {
			sum += stack.pop();
		}
		System.out.println(sum);
	}
}
```
