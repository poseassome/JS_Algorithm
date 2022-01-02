# 연속 부분수열1

> ## 문제

```
N개의 수로 이루어진 수열이 주어집니다.
이 수열에서 연속부분수열의 합이 특정숫자 M이 되는 경우가 몇 번 있는지 구하는 프로그램을 작성하세요.
만약 N=8, M=6이고 수열이 다음과 같다면
12131112
합이 6이 되는 연속부분수열은 {2, 1, 3}, {1, 3, 1, 1}, {3, 1, 1, 1}로 총 3가지입니다.
```
***

> ## 풀이

포인터 lt, rt를 0으로 초기화한다.(인덱스)<Br/>
rt가 증가하면서 숫자를 sum에 더하고 이것이 M이 되는지 확인한다.

값을 더했을 떄 M을 초과한다면 lt를 증가시키면서 lt가 가리키는 값을 빼준다.<br/>
(값을 빼고나서 lt도 증가한다.)

sum값이 M이 되면 카운팅을 한다.<br/>
그리고 lt를 증가시켜 가리키는 값을 뺸다.

M보다 sum값이 작으면 rt를 증가시켜 가리키는 값을 더한다.

모든 배열 탐색이 끝나면 전체가 끝난다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>연속부분 수열1</title>
</head>

<body>
  <script>
    function solution(m, arr) {
      let answer = 0, lt = 0, sum = 0;
      for (let rt = 0; rt < arr.length; rt++) {
        sum += arr[rt];
        if (sum === m) answer++;
        while (sum >= m) {
          sum -= arr[lt++];
          if (sum === m) answer++;
        }
      }
      return answer;
    }

    let a = [1, 2, 1, 3, 1, 1, 1, 2];
    console.log(solution(6, a));
  </script>
</body>

</html>
```