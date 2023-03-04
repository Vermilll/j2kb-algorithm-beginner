### 1991 트리순회

- 이진트리 / 각각의 노드가 최대 두개의 자식 노드를 갖는 트리 자료 구조
- tree[부모] = [왼쪽 자식, 오른쪽 자식]
- [https://velog.io/@brian_kim/JavaScript-트리-순회#3-후위-순회](https://velog.io/@brian_kim/JavaScript-%ED%8A%B8%EB%A6%AC-%EC%88%9C%ED%9A%8C#3-%ED%9B%84%EC%9C%84-%EC%88%9C%ED%9A%8C)

```jsx
let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().trim().split("\n");

const N = Number(input.shift());
let result = '';

const tree = {};
for (let i = 0; i < N; i++) {
  const [node, left, right] = input[i].split(" ");
  tree[node] = [left, right]; //부모 노드를 key 값으로 자식 노드를 value 값으로 저장.
}

function preorder(node) {
  if (node === ".") return; //자식 노드가 없는 경우 ; 재귀의 종료 조건
  const [left, right] = tree[node];
  result += node;
  preorder(left);
  preorder(right); // 전위순회: 루트부터 기록 시작함
}

function inorder(node) {
  if (node === ".") return;
  const [left, right] = tree[node];
  inorder(left);
  result += node;
  inorder(right); // 중위순회: 왼쪽-루트-오른쪽 순 , 왼쪽의 재귀가 끝난 시점에서 기록함
}

function postorder(node) {
  if (node === ".") return;
  const [left, right] = tree[node];
  postorder(left);
  postorder(right);
  result += node; // 후위순회: 왼쪽-오른쪽-루트순, 왼쪽과 오른쪽 재귀가 끝난 시점에서 기록함
}

preorder("A");
result += "\n";
inorder("A");
result += "\n";
postorder("A");

console.log(result);
```

### 11725 / 트리의 부모 찾기

- bfs를 이용하고 check 배열 인덱스(자식 노드)에 값(부모 노드)를 입력한다.
- [https://velog.io/@dark6ro/백준-11725번-트리의-부모-찾기](https://velog.io/@dark6ro/%EB%B0%B1%EC%A4%80-11725%EB%B2%88-%ED%8A%B8%EB%A6%AC%EC%9D%98-%EB%B6%80%EB%AA%A8-%EC%B0%BE%EA%B8%B0)
- BFS의 동작 방식
1) 탐색 시작 노드를 큐에 삽입하고 방문 처리한다.
2) 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리한다.
3) 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.


```jsx
let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().trim().split("\n");

const solution = (input) => {
  const n = +input.shift();
  const tree = Array.from(Array(n + 1), () => []);
  const check = new Array(n + 1).fill(0);
  
for (let [from, to] of input.map((e) => e.split(" ").map(Number))) {
    tree[from].push(to);
    tree[to].push(from); // 무방향 트리이므로 A->B, B->A 정보를 모두 넣음
  }

  const queue = [];
  check[1] = 1;
  for (let next of tree[1]) {
    // 1이 시작이고 child 노드를 넣고 check[child]엔 부모노드의 값을 넣음
    check[next] = 1;
    queue.push(next);
  }
  while (queue.length) {
    const cur = queue.shift();
    for (let next of tree[cur]) { // 노드를 순회하면서, 방문한 노드라면 건너뜀
      if (!check[next]) {
        check[next] = cur; // next 인덱스에는 node(부모 노드)값을 넣음
        queue.push(next);
      }
    }
  }
  // console.log(check);
  return check.slice(2).join("\n"); 체크 배열의 2번 인덱스(2번 노드)부터 출력
};

console.log(solution(input));
```

