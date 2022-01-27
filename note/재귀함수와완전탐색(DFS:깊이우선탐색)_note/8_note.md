# 중복 순열 구하기 (다중 for문과 재귀의 차이점)

> ## 문제

```
1부터 N까지 번호가 적힌 구슬이 있습니다. 이 중 중복을 허락하여 M번을 뽑아 일렬로 나열하는 방법을 모두 출력합니다.
```
***

> ## 풀이

`tmp`라는 M자리를 가지는 수가 있다고 가정한다.

처음에 `DFS(0)`이 호출되면, 1부터 N까지의 모든 번호가 올 수 있는 것이다.<br/>
여기서 N수 만큼 `DFS(1)` 가지가 만들어진다.

`DFS(1)`에서도 1부터 N까지의 모든 번호가 올 수 있으므로,<br/>
N수 만큼 `DFS(2)` 가지가 만들어진다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>중복순열</title>
</head>

<body>
  <script>
    function solution(n, m) {
      let answer = [];
      let tmp = Array.from({ length: m }, () => 0);
      // L이 몇 중 for문을 돌아야하는지 결정
      function DFS(L) {
        if (L === m) {
          answer.push(tmp.slice());     // 복사해서 새로 생성해서 추가해야되기 때문에 slice() 사용
        } else {
          for (let i = 1; i <= n; i++) {
            tmp[L] = i;
            DFS(L + 1);
          }
        }
      }
      DFS(0);
      return answer;
    }

    console.log(solution(3, 2));
  </script>
</body>

</html>
```