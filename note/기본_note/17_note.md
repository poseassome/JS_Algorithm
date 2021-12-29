# 중복단어 제거

> ## 문제

```
N개의 문자열이 입력되면 중복된 문자열은 제거하고 출력하는 프로그램을 작성하세요.
출력하는 문자열은 원래의 입력순서를 유지합니다.
```
***

> ## 풀이

answer는 중복단어가 제거된 새로운 배열을 return한다.<br/>
`filter()`는 배열의 요소들 중 특정 조건을 만족하는 요소들만 모아서 새로운 배열을 반환한다.
`filter()`의 첫 번째 인자는 무조건 콜백함수.
```jsx
answer = s.filter(function(v,i){
  // v = 요소값, i = index
  if(s.indexOf(v)===i) return true;
  // true가 return되는 요소만 뽑아서 배열을 만든다.
});
```
*만약 good이 [1], [3] 위치에 있으면 <br/>*
*[3]위치의 good이 함수를 실행할 때,<Br/>*
*s.indexOf(v)는 1이라서 새로운 배열에 포함되지 않는다.*
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>중복단어 제거</title>
</head>

<body>
  <script>
    function solution(s) {
      answer = s.filter(function (v, i) {
        if (s.indexOf(v) === i) {
          return true;
        }
      })
      return answer;
    }
    let str = ["good", "time", "good", "time", "student"];
    console.log(solution(str));
  </script>
</body>

</html>
```