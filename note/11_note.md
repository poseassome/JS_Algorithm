# 대문자 찾기

> ## 문제

```
한 개의 문자열을 입력받아 해당 문자열에 알파벳 대문자가 몇 개 있는지 알아내는 프로그램 을 작성하세요.
```
***

> ## 풀이(1)

counting이니까 answer는 0으로 선언한다.<br/>

`toUpperCase( )`문자열의 대문자를 출력한다. x 자체의 값을 바꾸지않는다.(x를 출력하면 소문자 그대로 나옴)<br/>
원래의 x와 대문자을 출력한 값이 일치하는지 확인해서 대문자를 선별할 수 있다.
```jsx
let answer = 0;
for(x of s){
  if(x === x.toUpperCase()) answer++;
}
```

> ## 풀이(2)

ASCII문자 코드를 사용한다.<br/>
대문자 : 65 ~ 90 / 소문자 : 97 ~ 122<br/>
`charCodeAt( )` 문자의 ASCII 코드를 넘겨준다.
```jsx
for(x of s){
  let num = s.charCodeAt();
  if(num>=65 && num<=90) answer++;
}
```

***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>대문자 찾기</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = 0;
      for (x of s) {
        if (x === x.toUpperCase()) {
          answer++;
        }
      }
      return answer;
    }

    let str = "KoreaTimeGood";
    console.log(solution(str));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>대문자 찾기</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = 0;
      for (x of s) {
        let num = x.charCodeAt();
        if (num >= 65 && num <= 90) {
          answer++;
        }
      }
      return answer;
    }

    let str = "KoreaTimeGood";
    console.log(solution(str));
  </script>
</body>

</html>
```