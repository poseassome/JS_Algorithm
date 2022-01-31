# 돌다리 건너기

> ## 문제

```
철수는 학교에 가는데 개울을 만났습니다. 개울은 N개의 돌로 다리를 만들어 놓았습니다. 철수는 돌 다리를 건널 때 한 번에 한 칸 또는 두 칸씩 건너뛰면서 돌다리를 건널 수 있습니다. 
철수가 개울을 건너는 방법은 몇 가지일까요?
```
***

> ## 풀이

완전히 건너야 되므로 7번째 돌에서 멈추면 안된다. (21)

도착점으로 가는 방법은 6번째 돌 방법수+7번째 돌 방법수 이다. (34)
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>돌다리 건너기</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = 0;
      let dy = Array.from({ length: n + 1 }, () => 0);
      dy[0] = 1;
      dy[1] = 1;
      dy[2] = 2;
      for (let i = 3; i <= n + 1; i++) {
        dy[i] = dy[i - 2] + dy[i - 1];
      }
      answer = dy[n + 1];
      return answer;
    }

    console.log(solution(7));
  </script>
</body>

</html>
```