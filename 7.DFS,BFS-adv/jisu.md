
2178 미로탐색
첫째 줄에 두 정수 N, M(2 ≤ N, M ≤ 100)이 주어진다. 다음 N개의 줄에는 M개의 정수로 미로가 주어짐

- 현재 위치를 기준으로 상하좌우 이동 가능성을 조회하고, 이동
- 이미 지나온 곳을 다시 방문하지 않기 위해 체크배열을 조회하며 이동하면 최단경로로 도착

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d01cd4f-0546-4c25-9a66-bff9e71ff1b4/Untitled.png)

```jsx
const input = require('fs').readFileSync('/dev/stdin').toString().trim().split('\n');

const [N, M] = input.shift().split(' ').map(Number);
const map = input.map((row) => row.split('').map(Number));

function bfs(x,y) {
    const queue = [[x,y]];
    const result = []; 
    const visisted = { }; // vistied를 몇번째 방문했는지 판단하는 객체로 활용
    visisted[[x,y]] = 1;
    let dx = [0, 0, -1, 1]; // 상하좌우 x축 방향
    let dy = [-1, 1, 0, 0]; // 상하좌우 y축 방향

    while(queue.length) {
        for(let i=0; i<queue.length; i++) {
            let coord = queue.shift(); // 큐는 FIFO이므로, 맨 앞부터 꺼냄
            result.push(coord);
            for(let j=0; j<4; j++) {
                let nx = coord[0] + dx[j]; 
                let ny = coord[1] + dy[j]; // (nx, ny)는 이동 가능성이 있는 좌표

                if( nx >= 0 && ny >= 0 && nx < N && ny < M &&
                    !visisted[[nx,ny]] &&
                    map[nx][ny] === 1) { // 길이 있고, 방문하지 않았다면 방문
                        visisted[[nx,ny]] = visisted[coord]+1; // 해당 좌표에 도달할때마다 visited 객체값을 증가
                        queue.push([nx,ny]); BFS로 현재 위치에서 갈 수 있는 좌표를 모두 큐에 넣어줌
                    }
            }
        }
    }
    return visisted[[N-1,M-1]];
  // N, M 좌표에 도달했을 때 visited객체에 담겨져 있는 값을 리턴함
}

console.log(bfs(0,0));
```
