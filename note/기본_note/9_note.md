# A를 #으로

> ## 문제

```
대문자로 이루어진 영어단어가 입력되면 단어에 포함된 ‘A'를 모두 ’#‘으로 바꾸어 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이(1)

string으로 단어를 받아서 문자 하나하나를 for문으로 돌려서<br/>
조건문으로 대문자 'A'를 찾아 answer에 추가한다.
```jsx
let answer = "";
for(x of s){
  if(x ==="A") answer+="#";
  else answer+=x;
}
```

> ## 풀이(2)

`replace(정규식, 바꿀 문자)`를 사용한다.
```jsx
let answer = s;
answer = answer.replace(/A/g, "#");
// 정규식에 g를 붙이지 않으면 첫 번째 'A'만 바뀐다. 
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>A를 #으로</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "";
      for (x of s) {
        if (x === "A") {
          answer += "#";
        } else {
          answer += x;
        }
      }
      return answer;
    }

    let str = "BANANA";
    console.log(solution(str));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>A를 #으로</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = s;
      answer = answer.replace(/A/g, "#");
      return answer;
    }

    let str = "BANANA";
    console.log(solution(str));
  </script>
</body>

</html>
```