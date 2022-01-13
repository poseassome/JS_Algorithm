# 버블 정렬

> ## 문제

```
N개의 숫자가 입력되면 오름차순으로 정렬하여 출력하는 프로그램을 작성하세요. 정렬하는 방법은 버블정렬입니다.
```
***

> ## 풀이

버블 정렬은 이웃한 두 수끼리 비교한다.

i는 배열의 인덱스 0 ~ (배열의 길이-1) 전 까지 반복한다. (마지막 끝 숫자까지 안간다고 생각하기)<br/>
그 안에서 j도 0 ~ (배열의 길이-2)까지 돌면서 `arr[j]`와 `arr[j+!]` 두 수를 비교한다.

처음 i=0일 때 배열 한 바퀴를 돌면 배열에서 가장 큰 숫자가 배열의 가장 끝 부분에 위치하게된다.<br/>
그러면 다음 j는 배열의 마지막 자리까지 갈 필요없이 그 두 칸 앞 자리까지 돌면 된다.<br/>
j는 0 부터 (배열의 길이 -i -1) 전 까지

***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>버블정렬</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = arr;
      for (let i = 0; i < arr.length - 1; i++) {
        for (let j = 0; j < arr.length - i - 1; j++) {
          if (arr[j] > arr[j + 1]) {
            [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
          }
        }
      }
      return answer;
    }

    let arr = [13, 5, 11, 7, 23, 15];
    console.log(solution(arr));
  </script>
</body>

</html>
```