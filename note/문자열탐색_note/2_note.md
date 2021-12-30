# 유효한 팰린드롬

> ## 문제

```
앞에서 읽을 때나 뒤에서 읽을 때나 같은 문자열을 팰린드롬이라고 합니다.
문자열이 입력되면 해당 문자열이 팰린드롬이면 "YES", 아니면 “NO"를 출력하는 프로그램을 작성하세요.
단 회문을 검사할 때 알파벳만 가지고 회문을 검사하며, 대소문자를 구분하지 않습니다. 알파벳 이외의 문자들의 무시합니다.
```
***

> ## 풀이

알파벳을 제외한 나머지 문자는 제외한다.
```jsx
s=s.toLowerCase().replace(/[^a-z]/g, '');
// ^는 부정
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>유효한 팰린드롬</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "YES";
      s = s.toLowerCase().replace(/[^a-z]/g, '');
      if (s.split('').reverse().join('') !== s) return "NO";
      return answer;
    }

    let str = "found7, time: study; Yduts; emit, 7Dnuof";
    console.log(solution(str));
  </script>
</body>

</html>
```