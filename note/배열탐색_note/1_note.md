# 큰 수 출력하기

> ## 문제

```
N(1<=N<=100)개의 정수를 입력받아, 자신의 바로 앞 수보다 큰 수만 출력하는 프로그램을 작 성하세요.(첫 번째 수는 무조건 출력한다)
```
***

> ## 풀이

배열을 return해야 하니까 answer는 []로 선언한다.
첫 번째 수는 무조건 출력하므로 push()를 사용해서 배열에 넣어준다.
```jsx
let answer = [];
answer.push(arr[0]);
```
배열의 길이만큼 for반복문을 돌려서 비교하여 값을 찾는다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>큰 수 출력하기</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = [];
      answer.push(arr[0]);
      for (i = 0; i < arr.length; i++) {
        if (arr[i] > arr[i - 1]) answer.push(arr[i]);
      }
      return answer;
    }

    let arr = [7, 3, 9, 5, 6, 12];
    console.log(solution(arr));
  </script>
</body>

</html>
```