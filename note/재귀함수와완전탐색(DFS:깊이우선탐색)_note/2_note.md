# 이진수 출력

> ## 문제

```
10진수 N이 입력되면 2진수로 변환하여 출력하는 프로그램을 작성하세요. 단 재귀함수를 이용해서 출력해야 합니다.
```
***

> ## 풀이

입력된 N을 2로 몫이 0이 될 때까지 나눈다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>이진수 출력</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = "";
      function DFS(n) {
        // n이 0이 됐을 때 멈춰야 한다.
        if (n === 0) return;
        else {
          DFS(parseInt(n / 2));     // 여기까지 실행하고 line 12로 이동한다.
          answer += String(n % 2);        // 이 위치에 있으면 나중에 실행된 수의 나머지부터 출력된다.
        }
      }
      DFS(n);
      return answer;
    }

    console.log(solution(11));
  </script>
</body>

</html>
```