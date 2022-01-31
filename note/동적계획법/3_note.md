# 최대 부분 증가 수열 (LIS)

> ## 문제

```
N개의 자연수로 이루어진 수열이 주어졌을 때, 그 중에서 가장 길게 증가하는(작은 수에서 큰 수로) 원소들의 집합을 찾는 프로그램을 작성하라. 
예를 들어, 원소가 2, 7, 5, 8, 6, 4, 7, 12, 3 이면 가장 길게 증가하도록 원소들을 차례대로 뽑아내면 2, 5, 6, 7, 12를 뽑아내어 길이가 5인 최대 부분 증가수열을 만들 수 있다.
```
***

> ## 풀이

dy배열을 만들고 `dy[i]`를 arr의 i번째 숫자가 만드는 증가 수열의 마지막 숫자라 생각하고 최대 증가 수열을 만든다.

j는 i-1로 i 앞 숫자를 탐색한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>최대부분 증가수열 (LIS)</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = 0;
      let dy = Array.from({ length: arr.length }, () => 0);
      dy[0] = 1;
      for (let i = 1; i < arr.length; i++) {
        let max = 0;
        for (let j = i - 1; j >= 0; j--) {
          if (arr[j] < arr[i] && dy[j] > max) {
            max = dy[j];
          }
        }
        dy[i] = max + 1;
        answer = Math.max(answer, dy[i]);
      }
      return answer;
    }

    let arr = [5, 3, 7, 8, 6, 2, 9, 4];
    console.log(solution(arr));
  </script>
</body>

</html>
```