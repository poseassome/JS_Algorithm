# 세 수 중 최솟값

> ## 문제

```
100이하의 자연수 A, B, C를 입력받아 세 수 중 가장 작은 값을 출력하는 프로그램을 작성하세요.(정렬 사용 x)
```
***

> ## 풀이

세 수 a, b, c가 있으면, if문을 써서 최솟값을 찾는다.

### a와 b 비교
```jsx
  if(a<b) answer=a;
  else answer=b;
```
지금 `answer`에는 작은 값이 들어가 있다.

### c와 answer 비교
`c`가 더 작을 수도 있으니까 `c`와 `answer`를 비교한다.
```jsx
  if(c<answer) answer=c;
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>세 수 중 최솟값</title>
</head>

<body>
  <script>
    function solution(a, b, c) {
      let answer;

      if (a < b) {
        answer = a;
      } else {
        answer = b;
      }
      if (c < answer) {
        answer = c;
      }
      return answer;
    }

    console.log(solution(2, 5, 1));
  </script>
</body>

</html>
```