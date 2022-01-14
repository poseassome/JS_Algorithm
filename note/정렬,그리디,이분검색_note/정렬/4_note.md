# 삽입 정렬

> ## 문제

```
N개의 숫자가 입력되면 오름차순으로 정렬하여 출력하는 프로그램을 작성하세요. 정렬하는 방법은 삽입정렬입니다.
```
***

> ## 풀이

arr이 주어지면 arr[0]은 냅두고 i가 arr[1]부터 돈다.
```
i는 arr의 --> 방향으로 돌고
j는 i에서부터 <-- 방향으로 돈다.
```

j가 돌기 전에 tmp라는 공간에 arr[i]를 임시 저장하고<br/>
j = i-1 ~ 0 까지 이며 arr[j]가 tmp보다 크면 `arr[j+1] = arr[j]`로 뒤로 복사한다.

j가 끝나는 지점은 -1이다. -1 뒤에 자리는 j+1이 된다.<br/>
arr[j+1]자리에 tmp를 넣는다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>삽입정렬</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = arr;
      for (let i = 0; i < arr.length; i++) {
        let tmp = arr[i], j;
        for (j = i - 1; j >= 0; j--) {
          if (arr[j] > tmp) arr[j + 1] = arr[j];
          else break; // arr[j]가 tmp보다 작다.
        }
        arr[j + 1] = tmp;
      }
      return answer;
    }

    let arr = [11, 7, 5, 6, 10, 9];
    console.log(solution(arr));
  </script>
</body>

</html>
```