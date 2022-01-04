# 크레인 인형뽑기 (카카오 기출) (스택)

> ## 문제

[크레인 인형뽑기](https://programmers.co.kr/learn/courses/30/lessons/64061)
***

> ## 풀이

idx|0|1|2|3|4
---|---|---|---|---|---
0|0|0|0|0|0
1|0|0|1|0|3
2|0|2|5|0|1
3|4|2|4|4|2
4|3|5|1|3|1
크레인<br/>번호(위치)→|1|2|3|4|5

인형별로 숫자 부여하고 열번호와 행번호를 사용하여 해결한다.

게임 로직은 board라고 하고 크레인 위치를 pos라고 하면, for문으로 i가 돌 때<br/>
`board[i][pos-1]`가 안형의 위치가 된다. (이 값이 0이 아닐 때)

인형을 꺼내고 나서 해당 위치는 0으로 바꿔야 한다.

인형을 꺼내고나서는 stack의 가장 마지막 인형과 일치하는지 확인하고<br/>
일치하면 stack에 있는 인형을 제거한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>크레인 인형뽑기</title>
</head>

<body>
  <script>
    function solution(board, moves) {
      let answer = 0;
      let stack = [];
      moves.forEach(pos => {
        for (let i = 0; i < board.length; i++) {
          if (board[i][pos - 1] !== 0) {
            let tmp = board[i][pos - 1];
            board[i][pos - 1] = 0;
            if (tmp == stack[stack.length - 1]) {
              stack.pop();
              answer += 2;
            }
            else stack.push(tmp);
            break;
          }
        }
      })
      return answer;
    }

    let a = [[0, 0, 0, 0, 0],
    [0, 0, 1, 0, 3],
    [0, 2, 5, 0, 1],
    [4, 2, 4, 4, 2],
    [3, 5, 1, 3, 1]];

    let b = [1, 5, 3, 5, 1, 2, 1, 4];
    console.log(solution(a, b));
  </script>
</body>

</html>
```