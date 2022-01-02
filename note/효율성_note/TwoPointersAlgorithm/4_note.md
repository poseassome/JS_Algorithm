# 연속 부분수열2

> ## 문제

```
N개의 수로 이루어진 수열이 주어집니다.
이 수열에서 연속부분수열의 합이 특정숫자 M이하가 되는 경우가 몇 번 있는지 구하는 프로그램을 작성하세요.
만약 N=5, M=5이고 수열이 다음과 같다면
13123
합이 5이하가 되는 연속부분수열은 {1}, {3}, {1}, {2}, {3}, {1, 3}, {3, 1}, {1, 2}, {2, 3}, {1, 3, 1}로 총 10가지입니다.
```
***

> ## 풀이

lt와 rt로 pointer를 지정하고 0으로 초기화한다.

sum값이 M보다 같거나 작으면 rt++하여 가리키는 값을 더하는데,<Br/>
이 때 새롭게 추가된 값을 포함하는 sum이 M보다 작다면 더한 수의 부분 배열도 M보다 작다.
```
예를 들어 M=5일 때,
[1 3 1 2 3]에서 1 3 1 까지 더해도 M을 초과하지 않는다.

이 때 가능한 부분수열은 1 / 3 / 1 3 / 1 3 1 / 3 1 / 1 이 있다.

rt - li + 1로 각 인덱스에서 가리키는 숫자를 더했을 때 가능한 부분 수열의 갯수를 구할 수 있다.
```
sum이 M보다 커지면 li를 증가시키고 가리키는 값을 뺀다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>연속부분 수열2</title>
</head>

<body>
  <script>
    function solution(m, arr) {
      let answer = 0, lt = 0, sum = 0;
      for (let rt = 0; rt < arr.length; rt++) {
        sum += arr[rt];
        while (sum > m) {
          sum -= arr[lt++];
        }
        answer += (rt - lt + 1);
      }
      return answer;
    }

    let a = [1, 3, 1, 2, 3];
    console.log(solution(5, a));
  </script>
</body>

</html>
```