# 삼각형 판별하기

> ## 문제

```
길이가 서로 다른 A, B, C 세 개의 막대 길이가 주어지면 이 세 막대로 삼각형을 만들 수 있으면 “YES"를 출력하고, 만들 수 없으면 ”NO"를 출력한다.
```
***

> ## 풀이

우선 가장 긴 막대의 길이를 구한다. => max
```jsx
if(a>b) max=a;
else max=b;
if(c>max) max=c;
```

짧은 막대 두 개의 합을 구해야하는데,<br/>
짧은 막대가 어떤 것인지 모르니까 a, b, c의 합을 구한다.
```jsx
let sum = a+b+c;
```

합에서 max를 빼면 짧은 막대 두 개의 합이다. <br/>
짧은 막대 두 개의 합과 긴 막대의 값을 비교한다.
```jsx
if((sum-max)<=max) answer="NO"; 
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>삼각형 판별하기</title>
</head>

<body>
  <script>
    function solution(a, b, c) {
      let answer = "YES";
      let sum = a + b + c;
      if (a > b) {
        max = a;
      } else {
        max = b;
      }
      if (c > max) {
        max = c;
      }
      if ((sum - max) <= max) {
        answer = "NO";
      }
      return answer;
    }
    console.log(solution(13, 33, 17));
  </script>
</body>

</html>
```