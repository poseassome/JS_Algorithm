# 동전 교환 (냅색알고리즘)

> ## 문제

```
다음과 같이 여러 단위의 동전들이 주어져 있을때 거스름돈을 가장 적은 수의 동전으로 교환 해주려면 어떻게 주면 되는가? 각 단위의 동전은 무한정 쓸 수 있다.

첫 번째 줄에는 동전의 종류개수 N(1<=N<=12)이 주어진다. 두 번째 줄에는 N개의 동전의 종 류가 주어지고, 그 다음줄에 거슬러 줄 금액 M(1<=M<=500)이 주어진다.
각 동전의 종류는 100원을 넘지 않는다.
```
***

> ## 풀이

dy배열을 큰 숫자로 초기화한다.

dy[i]는 i 금액을 거슬러주는데 사용된 동전의 최소 개수이다.

dy 배열을 돌면서 가진 동전의 종류로 해당 금액을 만들 수 있는 최소 개수를 변경해간다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>동전교환</title>
</head>

<body>
  <script>
    function solution(m, coin) {
      let answer = 0;
      let dy = Array.from({ length: m + 1 }, () => 1000);
      dy[0] = 0;
      for (let i = 0; i < coin.length; i++) {
        for (let j = coin[i]; j <= m; j++) {
          // 대체할 금액을 빼고 사용한 동전 1개를 더해줌
          dy[j] = Math.min(dy[j], dy[j - coin[i]] + 1);
        }
      }
      answer = dy[m];
      return answer;
    }

    let arr = [1, 2, 5];
    console.log(solution(15, arr));
  </script>
</body>

</html>
```