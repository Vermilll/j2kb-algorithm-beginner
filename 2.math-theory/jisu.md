## 8393.합

```jsx
const readline = require('readline').createInterface({
    input: process.stdin,
    output: process.stdout,
});

let input = [];

readline.on('line', function(line) {
    input = line.split(' ').map(el => parseInt(el));
}).on('close', function(){ 
    solution(input);
    process.exit();
});

const solution = input => {
    const A = parseInt(input[0]);
    console.log(A*(A+1)/2);
};
```

## 1929. 소수 구하기

에라토스테네스의 체
https://ko.wikipedia.org/wiki/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98_%EC%B2%B4
1)2부터 N까지의 모든 자연수를 나열한다.
2)남은 수 중에서 아직 처리하지 않은 가장 작은 수 i를 찾는다.
3)남은 수 중에서 i의 배수를 모두 제거한다. (i는 제거하지 않는다.)
4)더 이상 반복할 수 없을 때까지 2번과 3번의 과정을 반복한다.

```jsx
const fs = require('fs');
const input = fs.readFileSync('/dev/stdin').toString().trim().split(' ');

let N = Number(input[0]);
let M = Number(input[1]);
let isPrimeNumber = Array(M + 1).fill(true); // 0부터 M까지 true로 채운배열
isPrimeNumber[0] = isPrimeNumber[1] = false; // 0 과 1은 소수가 아니므로 false로 바꿔준다.

function result() {
  // 2부터 시작. 주어진값 N의 제곱근까지 i의 배수들을 모두 false로 만들어준다(i는 여전히 true)
  for (let i = 2; i <= Math.ceil(Math.sqrt(M)); i++) {
    if(isPrimeNumber[i]) {
      let m = 2; // 배수들을 구하기위해 곱해줄 수.
      while(i * m <= M) { 
        isPrimeNumber[i * m] = false; // i의 배수들을 false로 바꾼다.
        m++;  // i * m은 초기에 2 * 2 이고 m++ 해줌으로써 i + m은 2 * 3으로 바뀐다.
      }
    }
  }
  
  const results = []; // 결과값을 담을 배열.
  for(let i = N; i <= M; i++) { // N부터 M까지의 숫자 i가 소수인지 아닌지 확인하는 for문
    if(isPrimeNumber[i]) { 
		results.push(i); // i가 소수라면 results배열에 추가시켜준다.
    }
  }
  console.log(results.join('\n');
}

result();

```

## 1978. 소수찾기

```jsx
const input = require('fs').readFileSync('/dev/stdin').toString().trim();
const [c, nums] = input.split("\n");

const isPrime = (n) => {
    if (n == 1) {
      return false;
    }
    
    for (let i = 2; i <= Math.sqrt(n); i++) {
      if (n % i === 0) {
        return false;
      }
    }

    return true;
}
console.log(nums.split(" ").filter(v => isPrime(v)).length);
```

## 4948. 베르테랑 공준

```jsx
let input = require('fs').readFileSync('/dev/stdin').toString().split('\n').map(Number);

function isPrime(num) {
        if(num===1) return false;
        for(let i=2; i<=parseInt(Math.sqrt(num)); i++){
            if(num%i===0) return false;
        }
        return true;
    };

for(let i=0; i<input.length; i++){
    if(input[i]===0) break;
    
    let count = 0;
    for(let j=input[i]+1; j<=input[i]*2; j++){
        if(isPrime(j)) count++;
    };
    console.log(count);
}
```
