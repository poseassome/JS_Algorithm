# 중복문자 제거

> ## 문제

```
소문자로 된 한개의 문자열이 입력되면 중복된 문자를 제거하고 출력하는 프로그램을 작성하세요.
제거된 문자열의 각 문자는 원래 문자열의 순서를 유지합니다.
```
***

> ## 풀이

특정 문자의 인덱스를 찾아주는 `indexOf()`를 사용한다.<br/>
(발견을 못 하면 -1 return함 / 가장 빠른 위치의 문자 인덱스를 반환함)

두 번째 인자가 없으면 [0]부터 특정 문자를 찾아가는데,<br/> 
인자를 작성해주면 해당 숫자의 인덱스 자리를 시작 기준으로 특정 문자를 찾는다.

문자 하나하나를 탐색해야하니 for 반복문 사용한다.
```jsx
for(i=0;i<s.length;i++){
  if(s.indexOf(s[i])===i) answer+=s[i];
}
```

### 응용

`indexOf()`를 사용해서 특정 문자의 갯수 구하기

while로 index값이 반환되면 시작 기준을 옮겨서 다시 index를 반환하는 반복문을 작성한다.
```jsx
let pos = s.indexOf('k');
while(pos != -1){
  answer++;
  pos=s.indexOf('k', pos+1);
}
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>중복문자 제거</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "";
      for (i = 0; i < s.length; i++) {
        if (s.indexOf(s[i]) === i) {
          answer += s[i];
        }
      }
      return answer;
    }
    console.log(solution("ksekkset"));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>중복문자 제거</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = 0;
      let pos = s.indexOf('k');
      while (pos != -1) {
        answer++;
        pos = s.indexOf('k', pos + 1);
      }
      return answer;
    }
    console.log(solution("ksekkset"));
  </script>
</body>

</html>
```