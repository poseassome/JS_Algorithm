# 선택 정렬

> ## 문제

```
N개이 숫자가 입력되면 오름차순으로 정렬하여 출력하는 프로그램을 작성하세요. 정렬하는 방법은 선택정렬입니다.
```
***

> ## 풀이

arr의 인덱스 0의 위치를 i라고 하고 i를 해당 위치에 고정시킨다. j가 i위치에서부터 arr 배열의 끝까지 돈다.<br/>
i위치에서 arr배열 끝까지 존재하는 수 중 가장 작은 값을 i가 가리키는 위치에 갖다둔다.

i의 위치를 idx라고 하면 제일 처음에는 idx를 0으로 초기화한다.
```
arr[j] < arr[idx] 이면 idx = j 가 되도록 한다.
```
모든 배열의 요소와 비교했을 때 최종적으로 `idx`는 가장 작은 수의 인덱스를 가지고 있다.

```jsx
// arr[idx]이 가리키는 값이 arr[i] 위치로 가도록 한다.
[arr[i], arr[idx]] = [arr[idx], arr[i]]
```
그리고 i 가 1 증가하고 위의 과정을 반복한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>선택정렬</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = arr;
      for (let i = 0; i < arr.length; i++) {
        let idx = i;
        for (let j = i + 1; j < arr.length; j++) {
          if (arr[j] < arr[idx]) idx = j;
        }
        [arr[i], arr[idx]] = [arr[idx], arr[i]];
      }
      return answer;
    }

    let arr = [13, 5, 11, 7, 23, 15];
    console.log(solution(arr));
  </script>
</body>

</html>
```