# 최솟값 구하기

> ## 문제

```
7개의 수가 주어지면 그 숫자 중 가장 작은 수를 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

최솟값을 구할 때 아주 큰 숫자로 초기화하는 것도 좋다. <br/>
`Number.MAX_SAFE_INTEGER` : 안정적인 가장 큰 정수
```jsx
let min = Number.MAX_SAFE_INTEGER;
```
배열의 인덱스를 사용하여 for 반복문을 사용한다.

가장 큰 정수르 지정한 min과 비교하게 되면 무조건 **TRUE**이고,<br/>
비교 후 비교한 배열의 값을 min으로 다시 선언한다.
```jsx
for(i=o;i<arr.length;i++){
  if(arr[0]<min){
    min = arr[i];
  };
}
```

아니면 min을 배열의 첫 번째 값으로 선언하고,
반복문의 시작 배열 인덱스를 1로 시작한다.
```jsx
let min = arr[0];

for(i=i;i<arr.length;i++){
  if(arr[0]<min){
    min = arr[i];
  };
}
```

***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>출력결과</title>
</head>

<body>
  <script>
    function solution(arr) {
      // let answer, min = Number.MAX_SAFE_INTEGER;
      let answer, min = arr[0];
      for (i = 1; i < arr.length; i++) {
        if (arr[i] < min) {
          min = arr[i];
        }
      }
      answer = min;
      return answer;
    }

    let arr = [5, 7, 1, 3, 2, 9, 11];
    console.log(solution(arr));
  </script>
</body>

</html>
```
***

> ## 풀이 (내장함수 사용)

`Math.min()` : 인자값들 중에 최솟값을 구함 / 하지만 배열을 넣으면 구해지지 않음.
=> 배열을 전개해야 한다. `...` 사용
`Math.max()` : 인자값들 중에 최댓값 구함
```
(...arr) --> (arr[0], arr[1], arr[2], ...)
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>최솟값 구하기 (내장함수 사용)</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = Math.min(...arr);
      return answer;
    }

    let arr = [5, 7, 1, 3, 2, 9, 11];
    console.log(solution(arr));
  </script>
</body>

</html>
```

배열을 전개하지 않으려면,
`Math.min.apply()` : 첫 번째 인자는 객체를 넘기고, 두 번째 인자는 배열을 넘긴다.<br/>
첫 번째 인수는 해당 함수 내의 this에 연결되는 값으로 만약 this가 상관없는 함수라면 별 의미가 없기 때문에 null이나 undifined를 넣어 주는 것
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>최솟값 구하기 (내장함수 사용)</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = Math.min.apply(null, arr);
      return answer;
    }

    let arr = [5, 7, 1, 3, 2, 9, 11];
    console.log(solution(arr));
  </script>
</body>

</html>
```