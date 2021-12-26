# 1부터 N까지 합

> ## 문제

```
자연수 N이 입력되면 1부터 N까지의 합을 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

for 반복문을 사용한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>출력결과</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = 0;
      for (i = 1; i <= n; i++) {
        answer = answer + i;
      }
      return answer;
    }

    console.log(solution(10));
  </script>
</body>

</html>
```