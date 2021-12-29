# 연필 개수

> ## 문제

```
연필 1 다스는 12자루입니다. 학생 1인당 연필을 1자루씩 나누어 준다고 할 때 N명이 학생수를 입력하면 필요한 연필의 다스 수를 계산하는 프로그램을 작성하세요.
```
***

> ## 풀이

Math의 메소드 사용한다. [Math](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math)

`Math.ceil()` : 올림<br/>
`Math.floor()` : 내림<br/>
`Math.round()` : 반올림<br/>
`Math.sqrt()` : 제곱근<br/>


***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>연필 개수</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = Math.ceil(n / 12);
      return answer;
    }
    console.log(solution(178));
  </script>
</body>

</html>
```