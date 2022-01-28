# 조합 구하기

> ## 문제

```
1부터 N까지 번호가 적힌 구슬이 있습니다. 이중 M개를 뽑는 방법의 수를 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

`DFS(L, s)`로 `DFS(0,1)`에서 시작한다. (처음에 뽑은 수는 다음에 뽑을 수 없으니까)<br/>
(s는 for문이 시작되는 숫자다.)

다음 레벨은 `DFS(1, s+1)`이 된다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>조합 구하기</title>
</head>

<body>
  <script>
    function solution(n, m) {
      let answer = [];
      // tmp에 조합의 배열을 만들 것
      let tmp = Array.from({ length: m }, () => 0);
      function DFS(L, s) {
        if (L === m) {
          answer.push(tmp.slice());
        } else {
          for (let i = s; i <= n; i++) {
            // i를 뽑았다고 tmp에 기록
            tmp[L] = i;
            DFS(L + 1, i + 1);
          }
        }
      }
      DFS(0, 1);
      return answer;
    }

    console.log(solution(4, 2));
  </script>
</body>

</html>
```