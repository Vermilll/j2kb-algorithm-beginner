<h2>2630</h2>
const fs = require("fs");
const input = fs.readFileSync("dev/stdin").toString().trim().split("\n");

const size = +input[0]; //길이
const paper = input //중첩 배열로 저장
  .filter((v, i) => i > 0)
  .map((v) => v.split(" ").map((v) => +v));

let zerocnt = 0;
let onecnt = 0;

// [[1,1,0,0],[1,0,0,0],[1,0,0,1],[1,1,1,1]]

const cutPaper = (row, col, size) => {
  let zero = 0;
  let one = 0;

  for (let i = row; i < row + size; i++) {
    for (let j = col; j < col + size; j++) {
      if (paper[i][j] === 0) zero++;
      else one++;
    }
  }

  if (zero === size * size) {
    zerocnt++; //모두 0일때
  } else if (one === size * size) {
    onecnt++; //모두 1일때
  } else {
    cutPaper(row, col, size / 2);
    cutPaper(row + size / 2, col, size / 2);
    cutPaper(row, col + size / 2, size / 2);
    cutPaper(row + size / 2, col + size / 2, size / 2);
  }
};

cutPaper(0, 0, size);

console.log(`${zerocnt}\n${onecnt}`);
