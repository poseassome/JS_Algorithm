# 회문 문자열

> ## 문제

```
앞에서 읽을 때나 뒤에서 읽을 때나 같은 문자열을 회문 문자열이라고 합니다.
문자열이 입력되면 해당 문자열이 회문 문자열이면 "YES", 회문 문자열이 아니면 “NO"를 출력 하는 프로그램을 작성하세요.
단 회문을 검사할 때 대소문자를 구분하지 않습니다.
```
***

> ## 풀이(1)

주어진 문자는 대문자나 소문자로 모두 바꾼다.

문자열의 길이를 절반으로 나눴을 때 절반만큼 인덱스를 사용해서 반대쪽 문자와 비교하면 된다.<br/>
(문자열의 길이가 홀수여도 가운데 숫자는 단독이기 때문에 상관없다.)

우선 answer는 "YES"로 할당한다.

> ## 풀이(2)

메소드를 사용한다.<br/>
`split()`을 사용하면 문자 하나하나가 배열이 된다.<br/>
배열이 되어야만 `reverse()`를 사용할 수 있다.<br/>
`join('')`으로 배열을 문자열로 다시 묶어준다.
```jsx
s.split('').reverse().join('');
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>회문 문자열</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "YES";
      s = s.toLowerCase();
      let len = s.length;
      for (i = 0; i < Math.floor(len / 2); i++) {
        if (s[i] !== s[len - i - 1]) return "NO";
      }
      return answer;
    }

    let str = "goooG";
    console.log(solution(str));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>회문 문자열</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "YES";
      s = s.toLowerCase();
      if (s.split('').reverse().join('') !== s) return "NO";
      return answer;
    }

    let str = "gooG";
    console.log(solution(str));
  </script>
</body>

</html>
```