# 가운데 문자 출력

> ## 문제

```
소문자로 된 단어(문자열)가 입력되면 그 단어의 가운데 문자를 출력하는 프로그램을 작성하세요. 
단 단어의 길이가 짝수일 경우 가운데 2개의 문자를 출력합니다.
```
***

> ## 풀이

먼저 문자열의 길이를 먼저 구하고, 그 길이를 절반(2)으로 나눈 값을 내림처리 한다.
```jsx
let mid=Math.floor(s.length/2);
```

나눈 값의 나머지가 1이면 해당 문자열의 길이는 홀수이다.<br/>
`substring(시작 인덱스(부터), 끝날 인덱스(까지))`를 사용한다.
```jsx
if(s.length%2--1) answer=s.substring(mid, mid+1);
```

문자열의 길이가 짝수일 때는 mid-1한 인덱스 위치에서 잘라야 한다.
```jsx
else answer=s.substring(mid-1, mid+1);
```

<br/><br/>

`substr(인덱스 위치(부터), 범위(n개를))`을 사용할 수도 있다.
```jsx
answer=s.substr(mid,1); // 홀수
answer=s.substr(mid-1,2); // 짝수
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>가운데 문자 출력</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer, mid = Math.floor(s.length / 2);
      if (s.length % 2 == 1) {
        // answer = s.substring(mid, mid + 1);
        answer = s.substr(mid, 1);
      } else {
        // answer = s.substring(mid - 1, mid + 1);
        answer = s.substr(mid - 1, 2);
      }
      return answer;
    }
    console.log(solution("study"));
  </script>
</body>

</html>
```

```html

```