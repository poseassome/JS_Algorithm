# 홀수

> ## 문제

```
7개의 자연수가 주어질 때, 이들 중 홀수인 자연수들을 모두 골라 그 합을 구하고, 고른 홀수들 중 최소값을 찾는 프로그램을 작성하세요.
예를 들어, 7개의 자연수 12, 77, 38, 41, 53, 92, 85가 주어지면 이들 중 홀수는 77, 41, 53, 85이므로 그 합은

            77 + 41 + 53 + 85 = 256 
이 되고,
            41 < 53 < 77 < 85

이므로 홀수들 중 최소값은 41이 된다.
```
***

> ## 풀이

홀수를 찾기 위해 for반복문으로 나머지값을 구하여 선별한다.<br/>
조건문으로 선별된 값을 합하고, 그 안에서도 최솟값을 찾기위해 if문을 중첩한다.
```jsx
for(x of arr){
  if(x%2==1){
    sum+=x;
    if(x<min) min=x;
  };
}
```
홀수의 합과, 최솟값을 answer 배열에 push해서 출력한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>홍수</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = [];
      let sum = 0, min = Number.MAX_SAFE_INTEGER;
      for (x of arr) {
        if (x % 2 == 1) {
          sum += x;
          if (x < min) {
            min = x;
          }
        }
      }
      answer.push(sum);
      answer.push(min);
      return answer;
    }

    arr = [12, 77, 38, 41, 53, 92, 85];
    console.log(solution(arr));
  </script>
</body>

</html>
```