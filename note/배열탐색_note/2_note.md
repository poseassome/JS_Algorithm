# 보이는 학생

> ## 문제

```
선생님이 N(1<=N<=1000)명의 학생을 일렬로 세웠습니다. 일렬로 서 있는 학생의 키가 앞에 서부터 순서대로 주어질 때, 
맨 앞에 서 있는 선생님이 볼 수 있는 학생의 수를 구하는 프로그 램을 작성하세요. (앞에 서 있는 사람들보다 크면 보이고, 작거나 같으면 보이지 않습니다.)
```
***

> ## 풀이

i번째 사람이 있을 때, i번째 앞에 있는 수들 중 최대값과 비교하여
i번째 수가 그 최대값보다 크면 보이는 학생이다.

max라는 변수에 배열의 가장 앞 요소를 넣는다.
반복문을 도는 배열 요소와 max를 비교하며 max가 변화하는 방식
```jsx
let answer = 1, max = arr[0];

if(arr[i]>max){
  answer++;
  max = arr[i];
}
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>보이는 학생</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = 1, max = arr[0];
      for (i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
          answer++;
          max = arr[i];
        }
      }
      return answer;
    }

    let arr = [130, 135, 148, 140, 145, 150, 150, 153];
    console.log(solution(arr));
  </script>
</body>

</html>
```