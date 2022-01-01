# 자리수의 합

> ## 문제

```
N개의 자연수가 입력되면 각 자연수의 자릿수의 합을 구하고, 그 합이 최대인 자연수를 출력 하는 프로그램을 작성하세요. 
자릿수의 합이 같은 경우 원래 숫자가 큰 숫자를 답으로 합니다. 만약 235 와 1234가 동시에 답이 될 수 있다면 1234를 답으로 출력해야 합니다.
```
***

> ## 풀이(1)

최대값을 구해야되니까 max라는 변수에 가장 작은 수를 할당한다.

각 수를 10으로 나눈 나머지를 구하다보면 각 한 자리씩의 수를 구할 수 있다. 구한 나머지를 계속 구하다가 더하고 최종값을 max와 비교한다.
```jsx
while(tmp){
  sum+=(tep%10);
  tmp=Math.floor(tmp/10);
}
```

> ## 풀이(2)

숫자를 문자화하여 split으로 각 하나하나씩 분리한다.<br/>
해당 숫자는 더하면 문자로 더해지기 때문에 `reduce()`를 사용한다.
```
reduce()메소드는 배열의 모든 요소들을 순회하면서 주어진 리듀서 함수(콜백 함수)를 실행시킨다. 콜백함수의 필수 파라미터로 accumulator, currentValue과 있는데, 
함수에서 반환된 값은 accumulator에 할당된다. 
accumulator는 배열 순회 중 유지되며, 모든 배열의 요소의 순회가 끝났을 때 최종적으로 반환된다.

reduce() 메소드의 파라미터로는 
첫 번째(필수)로 reducer함수(콜백)를, 두 번째(선택)로 initialValue를 받는다.

만약 initialValue가 별도로 할당이 되어있다면, 
reducer 함수의 accumulator initialValue, currentValue는 배열의 첫 번째요소부터 시작한다.
initialValue가 별도로 할당되어 있지 않다면 accumulator는 배열의 첫 번째 요소, currentValue는 배열의 두 번째 요소부터 시작한다.
```
```jsx
let sum = x.toString().split('').reduce((a,b)=>a+Number(b),0);
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>자리수의 합</title>
</head>

<body>
  <script>
    function solution(n, arr) {
      let answer, max = Number.MIN_SAFE_INTEGER;
      for (x of arr) {
        let sum = 0, tmp = x;
        while (tmp) {
          sum += (tmp % 10);
          tmp = Math.floor(tmp / 10);
        }
        if (sum > max) {
          max = sum;
          answer = x;
        } else if (sum === max) {
          if (x > answer) answer = x;
        }
      }
      return answer;
    }

    let arr = [128, 460, 603, 40, 521, 137, 123];
    console.log(solution(7, arr));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>자리수의 합</title>
</head>

<body>
  <script>
    function solution(n, arr) {
      let answer, max = Number.MIN_SAFE_INTEGER;
      for (x of arr) {
        let sum = x.toString().split('').reduce((a, b) => a + Number(b), 0);
        if (sum > max) {
          max = sum;
          answer = x;
        } else if (sum === max) {
          if (x > answer) answer = x;
        }
      }
      return answer;
    }

    let arr = [128, 460, 603, 40, 521, 137, 123];
    console.log(solution(7, arr));
  </script>
</body>

</html>
```