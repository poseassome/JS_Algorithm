# K번째 큰 수

> ## 문제

```
현수는 1부터 100사이의 자연수가 적힌 N장의 카드를 가지고 있습니다. 같은 숫자의 카드가 여러장 있을 수 있습니다. 현수는 이 중 3장을 뽑아 각 카드에 적힌 수를 합한 값을 기록하려고 합니다. 3장을 뽑을 수 있는 모든 경우를 기록합니다. 기록한 값 중 K번째로 큰 수를 출력 하는 프로그램을 작성하세요.
만약 큰 수부터 만들어진 수가 25 25 23 23 22 20 19......이고 K값이 3이라면 K번째 큰 값 은 22입니다.
```
***

> ## 풀이

3장을 뽑으니까 for문이 3번 중첩된다.<br/>
`Set()` 자료 구조로 중복을 제거한 새로운 객체를 만들어낸다.
```jsx
let tmp = new Set();
```
set에 자료를 취하는 메소드는 `add()`이다.

`sort()`
이 함수가 a, b 두개의 element를 파라미터로 입력받을 경우,<br/>
이 함수가 리턴하는 값이 0보다 작을 경우, a가 b보다 앞에 오도록 정렬하고,<br/>
이 함수가 리턴하는 값이 0보다 클 경우, b가 a보다 앞에 오도록 정렬한다.
```jsx
score.sort(function(a, b) { // 오름차순
    return a - b;
});

score.sort(function(a, b) { // 내림차순
    return b - a;
});
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>K번째 큰 수</title>
</head>

<body>
  <script>
    function solution(n, k, card) {
      let answer;
      let tmp = new Set();
      for (let i = 0; i < n; i++) {
        for (let j = i + 1; j < n; j++) {
          for (let k = j + 1; k < n; k++) {
            tmp.add(card[i] + card[j] + card[k]);
          }
        }
      }
      let a = Array.from(tmp).sort((a, b) => b - a);
      answer = a[k - 1];
      return answer;
    }

    let arr = [13, 15, 34, 23, 45, 65, 33, 11, 26, 42];
    console.log(solution(10, 3, arr));
  </script>
</body>

</html>
```