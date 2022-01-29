# 경로탐색 (DFS-인접행렬: 노드개수가 적을 때)

> ## 문제

```
방향그래프가 주어지면 1번 정점에서 N번 정점으로 가는 모든 경로의 가지 수를 출력하는 프 로그램을 작성하세요. 아래 그래프에서 1번 정점에서 5번 정점으로 가는 가지 수는 총 6 가지입니다.
```
![경로탐색(인접행렬)](../../img/경로탐색(인접행렬).png)
***

> ## 풀이

`ch`배열을 만들어서 방문한 노드를 표시한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>경로탐색</title>
</head>

<body>
  <script>
    function solution(n, arr) {
      let answer = 0;
      // 1번 인덱스부터 사용할 거니까 행과 열의 개수는 n+1개
      let graph = Array.from(Array(n + 1), () => Array(n + 1).fill(0));
      let ch = Array.from({ length: n + 1 }, () => 0);
      // 인접행렬 생성
      for (let [a, b] of arr) {
        graph[a][b] = 1;
      }
      function DFS(v) {
        if (v === n) answer++;
        else {
          for (let i = 1; i <= n; i++) {
            // v라는 정점에서 i라는 정점까지 갈 수 있느냐
            if (graph[v][i] === 1 && ch[i] === 0) {
              ch[i] = 1;
              DFS(i);
              ch[i] = 0;
            }
          }
        }
      }
      ch[1] = 1;
      DFS(1);
      return answer;
    }

    let arr = [[1, 2], [1, 3], [1, 4], [2, 1], [2, 3], [2, 5], [3, 4], [4, 2], [4, 5]];
    console.log(solution(5, arr));
  </script>
</body>

</html>
```