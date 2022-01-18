# 좌표 정렬

> ## 문제

```
N개의 평면상의 좌표(x, y)가 주어지면 모든 좌표를 오름차순으로 정렬하는 프로그램을 작성하세요. 
정렬기준은 먼저 x값의 의해서 정렬하고, x값이 같을 경우 y값에 의해 정렬합니다.
```
***

> ## 풀이

`sort()`함수로 정렬한다. 

만약 x 위치인 `a[0] === b[0]`이면 y값에 의해 정렬되기때문에 `a[1] - b[1]`을 return한다. 아닐 경우는 원래대로 x값에 의해 return한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>좌표정렬</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = arr;
      arr.sort((a, b) => {
        if (a[0] === b[0]) return a[1] - b[1];
        else return a[0] - b[0];
      })
      return answer;
    }

    let arr = [[2, 7], [1, 3], [1, 2], [2, 5], [3, 6]];
    console.log(solution(arr));
  </script>
</body>

</html>
```