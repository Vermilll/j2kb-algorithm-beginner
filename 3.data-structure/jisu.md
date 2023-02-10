## 10828 스택

```jsx
const fs = require('fs');
const input =
fs.readFileSync("/dev/stdin").toString().trim().split('\n');
const N = parseInt(input.shift(),10);

let stack = [];
//출력을 명령어 각각일때마다 하면 시간초과 발생
//한 곳에 출력할 것들을 담아놓은다음 \n을 이용해서 출력해야 성공함
let answer = [];

for (let i=0; i < N; i++) {
    switch (input[i]) {
    //push 2 형식이므로 ' ' 공백 구분자로 나눠서 배열 삽입
    
    //pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
    case 'pop' :
        answer.push(stack.pop() || -1);
        break;
    
    //top : 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
    case 'top':
        answer.push(stack[stack.length-1] || -1);
        break;
    
    //size: 스택에 들어있는 정수의 개수를 출력한다.
    case 'size':
        answer.push(stack.length);
        break;
    
    //empty: 스택이 비어있으면 1, 아니면 0을 출력한다.
    case 'empty':
        if (stack.length === 0) {
            answer.push(1);
        }

        else {
            answer.push(0);
        }
        break;
    
    //push X: 정수 X를 스택에 넣는 연산이다.
    default:
        stack.push(Number(input[i].split(' ')[1]));
        break;
    }
}
console.log(answer.join('\n'));
```

## 18258 큐2

```jsx
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

    let queue = [];

    counter = Number(input[0]);

    for (let i = 0; i < counter + 1; i++) {
        const command = input[i].split(' ');
        if (command.length == 1) {
            
            if (command[0] === 'pop') {
                if (queue.length == 0) {
                    console.log(-1);
                } else {
                    console.log(queue[0]);
                    // console.log("qqq",queue[0]);
                    // console.log("www",queue[1]);
                    queue.shift();
                }
            }
            if (command[0] === 'size') {
                console.log(queue.length);
            }
            if (command[0] === 'empty') {
                if (queue.length == 0) {
                    console.log(1);
                } else {
                    console.log(0);
                }
            }
            if (command[0] === 'front') {
                if (queue.length == 0) {
                    console.log(-1);
                } else {
                    console.log(queue[0]);
                }
            }
            if (command[0] === 'back') {
                if (queue.length == 0) {
                    console.log(-1);
                } else {
                    console.log(queue[queue.length - 1]);
                }
            }
        } else {
            x = command[1];
            queue.push(x);
        }
    }
```

## 10845 큐

```jsx
// const fs = require('fs');
// const filePath = process.platform === 'linux' ? '/dev/stdin' : './input.txt';
// let input = fs.readFileSync(filePath).toString().split('\n');
// console.log(solution(input));

const input = [];
require("readline")
  .createInterface(process.stdin, process.stdout)
  .on("line", (line) => {
    input.push(line);
  })
  .on("close", () => {
    console.log(solution(input));
    process.exit();
  });

function solution(input) {
  const n = input.shift();
  const queue = [];
  const answer = [];
  // input = input.map(el => el.replace('\r', '')); // vscode에서 fs 모듈 사용시 개행문자 제거.
  for (let i = 0; i < n; i++) {
    const command = input[i].split(' ');
    switch (command[0]) {
      case 'push':
        queue.push(+command[1]);
        break;
      case 'pop':
        answer.push(queue[0] ? queue.shift() : -1); // queue가 비어있으면 -1, 아니면 맨 앞 queue에서 빼고 그 수를 출력
        break;
      case 'size':
        answer.push(queue.length);
        break;
      case 'empty':
        answer.push(queue.length ? 0 : 1); // queue가 비어있으면 1, 아니면 0 출력.
        break;
      case 'front':
        answer.push(queue[0] ? queue[0] : -1); // queue의 맨 앞 정수 출력, 비어있으면 -1 출력.
        break;
      case 'back':
        answer.push(queue[0] ? queue[queue.length - 1] : -1); // queue의 맨 뒤 정수 출력, 비어있으면 -1 출력.
        break;
    }
    // console.log('queue: ', queue);
  }
  return answer.join('\n');
}
```

## 10886 덱

```jsx
let input = [];
require("readline")
  .createInterface(process.stdin, process.stdout)
  .on("line", (line) => {
    input.push(line);
  })
  .on("close", () => {
    console.log(solution(input));
    process.exit();
  });

function solution(input) {
  const n = input.shift();
  const deque = [];
  // input = input.map((el) => el.replace('\r', '')); // vscode 사용시, fs모듈에서 개행 제거.

  const command = {
    push_front: (x) => deque.unshift(x),
    push_back: (x) => deque.push(x),
    pop_front: () => deque[0] ? deque.shift() : -1,
    pop_back: () => deque[0] ? deque.pop() : -1,
    size: () => deque.length,
    empty: () => deque.length ? 0 : 1,
    front: () => deque[0] ? deque[0] : -1,
    back: () => deque[0] ? deque[deque.length - 1] : -1,
  }
  const answer = [];

  for (let i = 0; i < n; i++) {
    const splitedI = input[i].split(' ');
    if (!command[input[i]]) {
      if (splitedI[0] === 'push_front') {
        command.push_front(splitedI[1]);
      } else if (splitedI[0] === 'push_back') {
        command.push_back(splitedI[1]);
      }
    } else {
      answer.push(command[input[i]]());
    }
  }
  return answer.join('\n');
}
```

## 1874 스택 수열

```jsx
const input = [];
require("readline")
  .createInterface(process.stdin, process.stdout)
  .on("line", (line) => {
    input.push(line);
  })
  .on("close", () => {
    console.log(solution(input));
    process.exit();
  });

function solution(input) {
  const n = input.shift();
  const answer = [];
  const stack = [];
  let start = 1;

  for (let i = 0; i < n; i++) { // input을 돌기 위한 for문.
    for (let j = start; j <= +input[i]; j++) { // stack에 input[i]를 넣기위한 for문.
      stack.push(j); // 추가 push
      answer.push('+');
    }
    if (stack[stack.length - 1] === +input[i]) {
      stack.pop(input[i]); // 제거 pop
      answer.push('-');
    } else { // stack의 맨 마지막 배열과 input[i]가 같지 않으면 'NO' 리턴.
      return 'NO';
    }
    // start보다 input[i] + 1 가 크면 input[i] + 1 로 초기화.
    start = start < +input[i] + 1 ? +input[i] + 1 : start;
  }

  return answer.join('\n');
}
```
