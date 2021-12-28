# 가장 긴 문자열

> ## 문제

```
N개의 문자열이 입력되면 그 중 가장 긴 문자열을 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

`length`을 사용한다.<br/>

긴 길이를 구해야 하니까 max를 가장 작은 수를 가지는 안전한 변수로 선언한다.<br/>
max와 배열의 문자열을 비교해가며 답을 찾는다.
```jsx
let answer, max = Number.MIN_SAFE_INTEGER;
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>가장 긴 문자열</title>
</head>

<body>
  <script>
    let answer, max = Number.MIN_SAFE_INTEGER;
    function solution(s) {
      for (let x of s) {
        if (x.length > max) {
          max = x.length;
          answer = x;
        }
      }
      return answer;
    }
    let str = ["teacher", "time", "student", "beautiful", "good"];
    console.log(solution(str));
  </script>
</body>

</html>
```