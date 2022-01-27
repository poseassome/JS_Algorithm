# 순열 구하기

> ## 문제

```
10이하의 N개의 자연수가 주어지면 이 중 M개를 뽑아 일렬로 나열하는 방법을 모두 출력합니다.
```
***

> ## 풀이

주어지는 N개의 자연수 `arr`과 중복사용을 확인할 배열 `ch`, M개를 뽑아 나열할 `tmp`이 필요하다.

`DFS(L)`로 `DFS(0)`에서 시작한다.<br/>
`ch`는 N개의 자연수만큼 length의 0을 가지고 사용한 수의 인덱스에는 1을 표시한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>순열 구하기</title>
</head>

<body>
  <script>
    function solution(m, arr) {
      let answer = [];
      let n = arr.length;
      let ch = Array.from({ length: n }, () => 0);
      let tmp = Array.from({ length: m }, () => 0);
      function DFS(L) {
        if (L === m) {
          answer.push(tmp.slice());
        } else {
          for (let i = 0; i < n; i++) {
            if (ch[i] === 0) {
              ch[i] = 1;
              tmp[L] = arr[i];
              DFS(L + 1);
              // 돌아오는 지점
              ch[i] = 0;
            }
          }
        }
      }
      DFS(0);
      return answer;
    }

    let arr = [3, 6, 9];
    console.log(solution(2, arr));
  </script>
</body>

</html>
```