# 경로탐색 (DFS-인접리스트: 노드개수가 많을 때)

> ## 문제

```
방향그래프가 주어지면 1번 정점에서 N번 정점으로 가는 모든 경로의 가지 수를 출력하는 프 로그램을 작성하세요. 아래 그래프에서 1번 정점에서 5번 정점으로 가는 가지 수는 총 6 가지입니다.
```
![경로탐색(인접행렬)](../../img/경로탐색(인접행렬).png)
***

> ## 풀이

정점이 많을 때는 행렬로 풀면 메모리, 시간 낭비라서 인접리스트를 사용한다.<br/>
인덱스 번호는 중요하지 않다.
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
      let graph = Array.from(Array(n + 1), () => Array());
      let ch = Array.from({ length: n + 1 }, () => 0);
      for (let [a, b] of arr) {
        // a 정점에서 갈 수 있는 정점 b를 push 한다.
        graph[a].push(b);
      }
      function DFS(v) {
        if (v === n) answer++;
        else {
          for (let i = 0; i < graph[v].length; i++) {
            if (ch[graph[v][i]] === 0) {
              ch[graph[v][i]] = 1;
              DFS(graph[v][i]);
              ch[graph[v][i]] = 0;
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