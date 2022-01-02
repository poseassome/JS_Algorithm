# 공통 원소 구하기

> ## 문제

```
A, B 두 개의 집합이 주어지면 두 집합의 공통 원소를 추출하여 오름차순으로 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

각 배열을 오름차순으로 정렬한다. p1, p2를 0 인덱스부터 비교하면서 answer에 push한다.<br/>
`sort()`는 기본적으로 문자열로 변환한 다음에 오름차순 정렬한다.<br/>
한 자리 숫자면 문제가 되지않지만, 두 자리 숫자면 문자 사전 기준으로 정렬되서 문제가 된다.<Br/>
=> 정렬 기준을 줘야한다. `sort((a,b)=>a-b)`

비교한 값이 같지 않을 경우 값이 작은 pointer의 인덱스를 증가시킨다.<br/>
비교한 값이 같으면 pointer 두 개 모두 증가시킨다.

하나의 배열 탐색이 끝나면 전체 탐색이 끝난다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>공통원소 구하기</title>
</head>

<body>
  <script>
    function solution(arr1, arr2) {
      let answer = [];
      arr1.sort((a, b) => a - b);
      arr2.sort((a, b) => a - b);
      let p1 = p2 = 0;
      while (p1 < arr1.length && p2 < arr2.length) {
        if (arr1[p1] === arr2[p2]) {
          answer.push(arr1[p1++]);
          p2++;
        }
        else if (arr1[p1] < arr2[p2]) p1++;
        else p2++;
      }
      return answer;
    }

    let a = [1, 3, 9, 5, 2];
    let b = [3, 2, 5, 7, 8];
    console.log(solution(a, b));
  </script>
</body>

</html>
```