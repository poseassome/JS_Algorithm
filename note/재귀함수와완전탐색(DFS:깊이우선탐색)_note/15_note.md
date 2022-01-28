# 수들의 조합

> ## 문제

```
N개의 정수가 주어지면 그 숫자들 중 K개를 뽑는 조합의 합이 임의의 정수 M의 배수인 개수는 몇 개가 있는지 출력하는 프로그램을 작성하세요.
예를 들면 5개의 숫자 2 4 5 8 12가 주어지고, 3개를 뽑은 조합의 합이 6의 배수인 조합을 찾으면 4+8+12 2+4+12로 2가지가 있습니다.
```
***

> ## 풀이

인덱스 번호로 수를 선택해서 가지를 뻗어나간다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>수들의 조합</title>
</head>

<body>
  <script>
    function solution(n, k, arr, m) {
      let answer = 0;
      function DFS(L, s, sum) {
        if (L === k) {
          if (sum % m === 0) answer++;
        } else {
          for (let i = s; i < n; i++) {     // i는 인덱스 번호
            DFS(L + 1, i + 1, sum + arr[i]);
          }
        }
      }
      DFS(0, 0, 0);
      return answer;
    }

    let arr = [2, 4, 5, 8, 12];
    console.log(solution(5, 3, arr, 6));
  </script>
</body>

</html>
```