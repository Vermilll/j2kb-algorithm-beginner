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

```jsx
const input = require('fs').readFileSync('/dev/stdin').toString().trim();
const [n, m] = input.split(" ").map(v => Number(v));
    
    var count = 0;
    for (var i=1; i<n+1; i++) {
    count = 0;
    for (var j=1; j<=n/2; j++) {
    
    if ( i % j === 0 ) {
        count ++;
    }
        count +=1;
}   

    if( count == 2 && i >= m) {
    console.log(i);
    }
    
    
}
    process.exit();
});
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
