# 문자 찾기

> ## 문제

```
한 개의 문자열을 입력받고, 특정 문자를 입력받아 해당 특정문자가 입력받은 문자열에 몇 개 존재하는지 알아내는 프로그램을 작성하세요.
문자열의 길이는 100을 넘지 않습니다.
```
***

> ## 풀이(1)

counting해야 하니까 answer의 초기값은 0으로 선언한다.<br/>
받은 단어 하나하나를 특정 문자와 일치하는지 반복문과 조건문을 사용하여 찾아낸다.
```jsx
let answer = 0;
for(x of s){
  if(x===t) answer++;
}
```

> ## 풀이(2)

내장함수 `split(자를 기준이 될 문자열)`을 사용한다.
`split( )`은 잘려진 문자열을 요소로 하여 배열을 반환한다.

반환된 배열의 길이가 4라면 자를 기준이 된 문자열의 수는 3개가 있었다는 것을 알 수 있다.
```jsx
let answer = s.split(t).length;
return answer-1;
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>문자 찾기</title>
</head>

<body>
  <script>
    function solution(s, t) {
      let answer = 0;
      for (x of s) {
        if (x === t) {
          answer++;
        }
      }
      return answer;
    }

    let str = "COMPUTERPROGRAMMING";
    console.log(solution(str, 'R'));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>문자 찾기</title>
</head>

<body>
  <script>
    function solution(s, t) {
      let answer = s.split(t).length;
      return answer - 1;
    }

    let str = "COMPUTERPROGRAMMING";
    console.log(solution(str, 'R'));
  </script>
</body>

</html>
```