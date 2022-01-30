# 송아지찾기 (BFS:상태트리탐색)

> ## 문제

```
현수는 송아지를 잃어버렸다. 다행히 송아지에는 위치추적기가 달려 있다. 현수의 위치와 송아 지의 위치가 수직선상의 좌표점으로 주어지면 현수는 현재 위치에서 송아지의 위치까지 다음 과 같은 방법으로 이동한다. 송아지는 움직이지 않고 제자리에 있다.
현수는 스카이 콩콩을 타고 가는데 한 번의 점프로 앞으로 1, 뒤로 1, 앞으로 5를 이동할 수 있다. 최소 몇 번의 점프로 현수가 송아지의 위치까지 갈 수 있는지 구하는 프로그램을 작성하세요.
```
***

> ## 풀이

첫 출발지점에서 갈 수 있는 가지 수는 3가지이다. (-1, +1, +5)<br/>
다음 레벨에서도 동일하게 이동하지만 `ch`배열을 만들어서 이미 간 적 있는 지점에 대해서는 못가도록 표시한다.

배열로 풀이하면, `dis`배열에서 0~숫자가 있다고하면 처음 출발지점을 0으로 둔다. (dis[v])<br/>
이동 후 가능한 위치의 숫자의 값을 dis[nv]=dis[v]+1 이라고 한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>송아지 찾기</title>
</head>

<body>
  <script>
    function solution(s, e) {
      let answer = 0;
      let ch = Array.from({ length: 10001 }, () => 0);
      let dis = Array.from({ length: 10001 }, () => 0);
      let queue = [];
      ch[s] = 1;    // 출발 위치 방문 표시
      queue.push(s);
      dis[s] = 0;
      while (queue.length) {
        let x = queue.shift();    // 첫 출발지점 좌표
        for (let nx of [x - 1, x + 1, x + 5]) {
          if (nx === e) return dis[x] + 1;
          if (nx > 0 && nx <= 10001 && ch[nx] === 0) {
            ch[nx] = 1;
            queue.push(nx);
            dis[nx] = dis[x] + 1;
          }
        }
      }
      return answer;
    }

    console.log(solution(8, 3));
  </script>
</body>

</html>
```
```html
<!-- 레벨 풀이 -->

<head>
  <meta charset="UTF-8">
  <title>송아지 찾기</title>
</head>

<body>
  <script>
    function solution(s, e) {
      let answer = 0;
      let ch = Array.from({ length: 10001 }, () => 0);
      let queue = [];
      queue.push(s);
      ch[s] = 1;
      let L = 0;
      while (queue.length) {
        let len = queue.length;
        for (let i = 0; i < len; i++) {
          let x = queue.shift();
          for (let nx of [x - 1, x + 1, x + 5]) {
            if (nx === e) return L + 1;
            if (nx > 0 && nx <= 10000 && ch[nx] === 0) {
              ch[nx] = 1;
              queue.push(nx);
            }
          }
        }
        L++;
      }
      return answer;
    }

    console.log(solution(5, 14));
  </script>
</body>

</html>
```