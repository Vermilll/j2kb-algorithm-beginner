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
