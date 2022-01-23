# 부분집합 구하기 (이진트리 DFS)

> ## 문제

```
자연수 N이 주어지면 1부터 N까지의 원소를 갖는 집합의 부분집합을 모두 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

부분집합은 2^n이 된다. (숫자 하나당 참여한다, 안한다.)
```
D(1)에서
D(2) o    D(2) x
D(3) o D(3) x   D(3) o D(3) x
...
```
배열을 만들어서 숫자에 1, 0 으로 표시하면서 부분집합을 구한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>부분집합 구하기</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = [];
      let ch = Array.from({ length: n + 1 }, () => 0);
      function DFS(v) {
        if (v === n + 1) {
          let tmp = "";
          for (let i = 1; i <= n; i++) {
            if (ch[i] === 1) tmp += i + " ";
          }
          if (tmp.length > 0) answer.push(tmp.trim());
        }
        else {
          ch[v] = 1;
          DFS(v + 1);
          ch[v] = 0;
          DFS(v + 1);
        }
      }
      DFS(1);
      return answer;
    }

    console.log(solution(3));
  </script>
</body>

</html>
```