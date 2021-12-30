# 숫자만 추출

> ## 문제

```
문자와 숫자가 섞여있는 문자열이 주어지면 그 중 숫자만 추출하여 그 순서대로 자연수를 만듭니다.
만약 “tge0a1h205er”에서 숫자만 추출하면 0, 1, 2, 0, 5이고 이것을 자연수를 만들면 1205 이 됩니다.
추출하여 만들어지는 자연수는 100,000,000을 넘지 않습니다.
```
***

> ## 풀이

`isNaN()`함수를 사용한다.
 - 숫자가 아니면 true
 - 숫자면 false

숫자만 추출했을 때 가장 맨 앞에 있는 숫자가 0이면 0은 생략해야 한다.<br/>
마지막 answer에 `parseInt()`처리 한다.

`parseInt()`을 사용못하면 `answer=answer*10+Number(x)`를 사용한다.
```jsx
let answer = 0;
answer=answer*10+Number(x)

// 맨 앞에 숫자가 0 일때는 answer도 0이다.
// 0이 아닌 숫자를 마주치면 해당 숫자를 가지게 되고
// 그 뒤에 오는 숫자도 0이 아니면 *10에 의해 그 전 숫자가 앞으로 이동한다.
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>숫자만 추출</title>
</head>

<body>
  <script>
    function solution(str) {
      let answer = "";
      for (x of str) {
        if (!isNaN(x)) answer += x;
      }
      return parseInt(answer);
    }

    let str = "g0en2T0s8eSoft";
    console.log(solution(str));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>숫자만 추출</title>
</head>

<body>
  <script>
    function solution(str) {
      let answer = 0;
      for (x of str) {
        if (!isNaN(x)) answer = answer * 10 + Number(x);
      }
      return answer;
    }

    let str = "g0en2T0s8eSoft";
    console.log(solution(str));
  </script>
</body>

</html>
```