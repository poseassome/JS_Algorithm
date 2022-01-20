# 이분 검색

> ## 문제

```
임의의 N개의 숫자가 입력으로 주어집니다. 
N개의 수를 오름차순으로 정렬한 다음 N개의 수 중 한 개의 수인 M이 주어지면 이분검색으로 M이 정렬된 상태에서 몇 번째에 있는지 구하는 프로그램을 작성하세요. 
단 중복값은 존재하지 않습니다.
```
***

> ## 풀이

이분 검색은 무조건 배열이 정렬되있어야 한다.

정렬 후 인덱스를 가리키는 변수로 lt, rt를 정의한다.
```
lt: 인덱스 시작
rt: 인덱스 끝
```
`mid = (lt+rt)/2`로 중앙지점을 확인한다.<br/>
그리고 그 값이 target 숫자가 맞는지 비교한다.

아니라면 arr[mid]이 target보다 크면 `rt`를 움직이고 `(mid-1)`,
반대면 `lt`를 움직인다 `(mid+1)`.

```
log_2로 계산하면 몇 번만에 나오는지 할 수 있다.
ex) log_2 8이면 
    8 / 2 = 4
    4 / 2 = 2
    2 / 2 = 1

3번만에 값을 구할 수 있다.
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>이분검색</title>
</head>

<body>
  <script>
    function solution(target, arr) {
      let answer;
      // arr.sort((a, b) => a - b);
      console.log(arr.sort((a, b) => a - b));
      let lt = 0; rt = arr.length - 1;
      while (lt <= rt) {
        let mid = parseInt((lt + rt) / 2);
        if (target === arr[mid]) {
          answer = mid + 1;
          break;
        } else if (target < arr[mid]) rt = mid - 1;
        else lt = mid + 1;
      }
      return answer;
    }

    let arr = [23, 87, 65, 12, 57, 32, 99, 81];
    console.log(solution(32, arr));
  </script>
</body>

</html>
```