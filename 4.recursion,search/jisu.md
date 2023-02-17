10870 피보나치수 5

```jsx
const fs = require("fs");
let input = fs.readFileSync("/dev/stdin");

solution(input);

function solution(N) {
  let answer;
  let fibo = [];
  fibo[0] = 0;
  fibo[1] = 1;
  fibo[2] = 1;
  if (N < 3) answer = fibo[N];
  else {
    for (let i = 2; i <= N; i++) {
      fibo[i] = fibo[i - 2] + fibo[i - 1];
    }
    answer = fibo[N];
  }
  console.log(answer);
}
```

11729 하노이탑 이동순서

```jsx
public static void hanoi(int n, int start, int mid, int to) {
        if (n == 1) {
            sb.append(start + " " + to + "\n");
            return;
        }
		
        // 1 -> 2로 n-1개를 옮김.
        hanoi(n - 1, start, to, mid);
		
        // 가장 큰 원판을 목적 지점으로 옮김
        sb.append(start + " " + to + "\n");
		
        // 2 -> 3으로 n-1개를 옮김.
        hanoi(n - 1, mid, start, to);
    }
```

2750 수 정렬하기

```jsx
const fs = require("fs");
const input = fs.readFileSync("./dev/stdin").toString().trim().split("\n");

let N = parseInt(input[0]);
let newInput = [];
for (let i = 1; i <= N; i++) newInput.push(parseInt(input[i]));

// 정렬 함수 구현(오름차순)
function sort(arr) {
  let tmp = 0;
  for (let i = 0; i < arr.length; i++)
    for (let j = i + 1; j < arr.length; j++)
      if (arr[i] > arr[j]) {
        tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
      }
  return arr;
}

function Solution(newInput) {
  newInput = sort(newInput);
  console.log(newInput.join("\n"));
}

Solution(newInput);
```
