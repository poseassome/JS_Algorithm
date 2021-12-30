# 가장 짧은 문자 거리

> ## 문제

```
한 개의 문자열 s와 문자 t가 주어지면 문자열 s의 각 문자가 문자 t와 떨어진 최소거리를 출 력하는 프로그램을 작성하세요.
```
***

> ## 풀이

단어의 길이가 n이라면 for문이 n바퀴를 정방향으로 한번 돌고, 역방향으로 한번 돈다.

P라는 변수에 가장 큰 수를 할당한다.
```jsx
let p = 1000;
```
answer는 배열로 선언하여<br/>
t가 아닌 문자를 만나면 p++을 하고 문자 t를 만나면 P=0이 되어 answer에 push한다. <br/>
==> 각 문자열의 왼쪽에 있는 문자 t로부터의 거리가 구해진다.(정방향 for)<br/>
==> 반대로 각 문자열의 오른쪽에 있는 문자 t로부터의 거리를 구한다. (역방향 for)

역방향으로 구할 때는 index를 사용한다.

기존 answer[i]가 가지고 있는 값과 역방향으로 구했을 때의 값을 비교하여 작은 수를 선택한다.
```jsx
answer[i] = Math.min(answer[i], p);
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>가장 짧은 문자거리</title>
</head>

<body>
  <script>
    function solution(s, t) {
      let answer = [];
      let p = 1000;
      for (x of s) {
        if (x === t) {
          p = 0;
          answer.push(p);
        } else {
          p++;
          answer.push(p);
        }
      }

      p = 1000;
      for (i = s.length - 1; i >= 0; i--) {
        if (s[i] === t) {
          p = 0;
          answer[i] = 0;
        } else {
          p++;
          answer[i] = Math.min(answer[i], p);
        }
      }
      return answer;
    }

    let str = "teachermode";
    console.log(solution(str, 'e'));
  </script>
</body>

</html>
```