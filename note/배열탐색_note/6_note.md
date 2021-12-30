# 격자판 최대 합

> ## 문제

```
5*5 격자판에 아래롸 같이 숫자가 적혀있습니다.
```
10|13|10|12|15
---|---|---|---|---
12|39|30|23|11
11|25|50|53|15
19|27|29|37|27
19|13|30|13|19
```
N*N의 격자판이 주어지면 각 행의 합, 각 열의 합, 두 대각선의 합 중 가 장 큰 합을 출력합니다.
```
***

> ## 풀이

arr은 2차원 배열로, arr[행][열]을 나타낸다.
최대값을 구해야하니까 안전한 가장 작은 수를 answer에 할당한다.

sum1은 행의 합, sum2는 열의 합으로 지정한다.
```jsx
let answer = Number.MIN_SAFE_INTEGER;
let sum1=sum2=0;
```
for문을 중첩해서 사용하고, i=0은 첫 번째 행을 나타내고 arr[0][j] j가 내부 배열 인덱스를 반복한다. 그러면 첫 번째 행의 모든 수를 더할 수 있다.
```jsx
for(i=0;i<n;i++){
  for(j=0;j<n;j++){
    sum1 += arr[i][j];
    sum1 += arr[j][i];
  }
}
```
여기서 sum1, sum2값은 변하기 때문에 j 반복문 시작전에 0으로 초기화 해줘야한다.
```jsx
sum1=sum2=0;
```
대각선의 합 구할 때도 똑같이 초기화 해준다.
```jsx
  sum1=sum2=0;

for(i=0;i<n;i++){
  sum1 += arr[i][i];
  sum2 += arr[i][n-i-1];
}
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>격자판 최대합</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = Number.MIN_SAFE_INTEGER;
      let n = arr.length;
      let sum1 = sum2 = 0;
      for (i = 0; i < n; i++) {
        sum1 = sum2 = 0;
        for (j = 0; j < n; j++) {
          sum1 += arr[i][j];
          sum2 += arr[j][i];
        }
        answer = Math.max(answer, sum1, sum2);
      }

      sum1 = sum2 = 0;
      for (i = 0; i < n; i++) {
        sum1 += arr[i][i];
        sum2 += arr[i][n - i - 1];
      }
      answer = Math.max(answer, sum1, sum2);
      return answer;
    }

    let arr = [[10, 13, 10, 12, 15],
    [12, 39, 30, 23, 11],
    [11, 25, 50, 53, 15],
    [19, 27, 29, 37, 27],
    [19, 13, 30, 13, 19]];
    console.log(solution(arr));
  </script>
</body>

</html>
```