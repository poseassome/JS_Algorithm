# 계단 오르기

> ## 문제

```
철수는 계단을 오를 때 한 번에 한 계단 또는 두 계단씩 올라간다. 
만약 총 4계단을 오른다면 그 방법의 수는
1+1+1+1, 1+1+2, 1+2+1, 2+1+1, 2+2 로 5가지이다.
그렇다면 총 N계단일 때 철수가 올라갈 수 있는 방법의 수는 몇 가지인가?
```
***

> ## 풀이

dy라는 배열을 만들어서 0~N의 길이를 가지고 0으로 초기화한다.

각 계단으로 갈 수 있는 방법의 수를 입력한다.
```
dy[1] = 1
dy[2] = 2
```
3계단으로 가기 위해서는 1계단에서 가는 방법 1가지, 2계단에서 가는 방법 2가지로,총 3가지이다.

다음 계단도 동일한 방법으로 구한다.

***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>계단오르기</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer = 0;
      let dy = Array.from({ length: n + 1 }, () => 0);
      dy[1] = 1;
      dy[2] = 2;
      for (let i = 3; i <= n; i++) {
        dy[i] = dy[i - 2] + dy[i - 1];
      }
      answer = dy[n];
      return answer;
    }

    console.log(solution(7));
  </script>
</body>

</html>
```