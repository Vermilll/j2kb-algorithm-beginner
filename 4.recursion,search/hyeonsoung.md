## 10870. 피보나치 수 5
https://www.acmicpc.net/problem/10870

### 코드

```java
import java.util.Scanner;

public class Sol10870 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		
		int [] arr = new int[n + 1];
		
		for(int i = 0; i <= n; i++) {
			if(i == 0) {
				arr[i] = 0;
			}
			else if(i == 1) {
				arr[i] = 1;
			}
			else {
				arr[i] = arr[i - 1] + arr[i - 2];
			}
		}
		System.out.println(arr[n]);
	}
}
```

## 2750. 수 정렬하기
https://www.acmicpc.net/problem/2750

### 코드

```java
import java.util.Arrays;
import java.util.Scanner;

public class Sol2750 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int [] arr = new int [n];
		for(int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		for(int i = 0; i < n; i++) {
			System.out.println(arr[i]);
		}
	}
}

```

## 10989. 수 정렬하기 3
https://www.acmicpc.net/problem/10989

### 코드

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Arrays;

public class Sol10989 {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int n = Integer.parseInt(br.readLine());
		
		int [] arr = new int[n];
		
		for(int i = 0; i < n; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		Arrays.sort(arr);
		for(int i = 0; i < n; i++) {
			bw.write(arr[i] + "\n");
		}
		bw.flush();
		bw.close();
	}
}
```

## 10814. 나이순 정렬
https://www.acmicpc.net/problem/10814

### Comparator와 Comparable
https://st-lab.tistory.com/243

### 코드

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Sol10814 {

	public static void main(String[] args) throws IOException{
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int n = Integer.parseInt(br.readLine());
		
		String [][] str = new String[n][2];
		
		for(int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			str[i][0] = st.nextToken();
			str[i][1] = st.nextToken();
		}
		Arrays.sort(str, (o1, o2) -> Integer.parseInt(o1[0]) - Integer.parseInt(o2[0]));
		for(int i = 0; i < n; i++) {
			System.out.print(str[i][0] + " ");
			System.out.println(str[i][1]);
		}	
	}
}
```

## 1427. 소트인사이드
https://www.acmicpc.net/problem/1427

## Arrays.Sort Collections.Sort
https://codingnojam.tistory.com/38


### 코드

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Sol1427 {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		
		List<Integer> list = new ArrayList<>();
		
		for(int i = 0; i < str.length(); i++) {
			list.add(str.charAt(i) - 48);
		}
		
		Collections.sort(list, Comparator.reverseOrder());
		
		for(int i = 0; i < str.length(); i++) {
			System.out.print(list.get(i));
		}
	}	
}
```
