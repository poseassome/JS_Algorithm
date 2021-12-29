# 등수 구하기

> ## 문제

```
N(1<=N<=100)명의 학생의 국어점수가 입력되면 각 학생의 등수를 입력된 순서대로 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

for을 중첩하여 사용한다.
바깥쪽 for에서 i가 각 학생들의 국어점수를 나타내고,
그 안에 for에서 j가 돌면서 arr배열의 요소 하나와 요소 전체의 점수를 비교한다.
```jsx
for(i=0;i>arr.length;i++){
  for(j=0;j>arr.length;j++){
  
  }
}
```
answer는 배열로 출력되며, 초기에 arr배열의 길이와 동일하고 모든 요소는 1로 만든다.
```jsx
let n = arr.length;
let answer = Array.from({length:n}, ()=>1);
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>등수 구하기</title>
</head>

<body>
  <script>
    function solution(arr) {
      let n = arr.length;
      let answer = Array.from({ length: n }, () => 1);
      for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
          if (arr[j] > arr[i]) answer[i]++;
        }
      }
      return answer;
    }

    // let arr = [87, 89, 92, 100, 76];
    let arr = [92, 92, 92, 100, 76];
    console.log(solution(arr));
  </script>
</body>

</html>
```