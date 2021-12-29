# 대문자로 통일

> ## 문제

```
대문자와 소문자가 같이 존재하는 문자열을 입력받아 대문자로 모두 통일하여 문자열을 출력 하는 프로그램을 작성하세요.
```
***

> ## 풀이(1)

소문자를 찾아서 대문자로 바꿔준다.<br/>
`toLowerCase( )`

> ## 풀이(2)

ASCII코드를 사용한다.
소문자 범위는 97 ~ 122이므로 대문자로 바꾸기 위해 32를 뺀다. (대문자 코드와 32차이 난다.)

`String.fromCharCode( )` : ASCII코드를 문자로 변환해준다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>대문자로 통일</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "";
      for (x of s) {
        if (x === x.toLowerCase()) {
          answer += x.toUpperCase();
        } else {
          answer += x;
        }
      }
      return answer;
    }

    let str = "ItisTimeToStudy";
    console.log(solution(str));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>대문자로 통일</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "";
      for (x of s) {
        let num = x.charCodeAt();
        if (num >= 97 && num <= 122) {
          answer += String.fromCharCode(num - 32);
        } else {
          answer += x;
        }
      }
      return answer;
    }

    let str = "ItisTimeToStudy";
    console.log(solution(str));
  </script>
</body>

</html>
```