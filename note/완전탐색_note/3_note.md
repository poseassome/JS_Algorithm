# 멘토링

> ## 문제

```
현수네 반 선생님은 반 학생들의 수학점수를 향상시키기 위해 멘토링 시스템을 만들려고 합니다. 멘토링은 멘토(도와주는 학생)와 멘티(도움을 받는 학생)가 한 짝이 되어 멘토가 멘티의 수학공부를 도와주는 것입니다.
선생님은 M번의 수학테스트 등수를 가지고 멘토와 멘티를 정합니다.
만약 A학생이 멘토이고, B학생이 멘티가 되는 짝이 되었다면, A학생은 M번의 수학테스트에서 모두 B학생보다 등수가 앞서야 합니다.
M번의 수학성적이 주어지면 멘토와 멘티가 되는 짝을 만들 수 있는 경우가 총 몇 가지 인지 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

멘토를 A, 멘티를 B라고 했을 때 (A, B)에 각각 들어갈 수 있는 수는 (1,2,3,4)이므로 경우의 수는 총 16(4*4)이다.<br/>
따라서 for문은 4개가 중첩된다.

(i, j) i가 멘토, j가 멘티가 되려면 i학생의 등수가 무조건 j보다 앞서야 한다.<br/>
=> i가 몇 번쨰 있고, j가 몇 번째에 있는지 확인해야한다.
||0|1|2|3
---|---|---|---|---
0|3|4|1|2
1|4|3|2|1
2|3|1|4|2

k는 수학테스트 횟수(↓), s는 한 테스트 당 등수(→)

예를 들어 (i,j) = (3,1)이 멘토링할 수 있는지 보려면<br/>
`test[k][s] = i` test[k][s]가 i인지 확인한다.<Br/>
pi는 i학생의 등수(=s인덱스번호) / pj는 j학생의 등수(=s인덱스번호)<br/>
pi=0, pj=2 이므로 가능하다.   <== k가 0일 때

pi < pj 이면 `cnt++` 한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>멘토링</title>
</head>

<body>
  <script>
    function solution(test) {
      let answer = 0, tmp = [];
      m = test.length; // 테스트 수
      n = test[0].length; // 학생 수

      for (let i = 1; i <= n; i++) {
        for (let j = 1; j <= n; j++) {
          let cnt = 0;
          for (let k = 0; k < m; k++) {
            let pi = pj = 0; // 초기화
            for (let s = 0; s < n; s++) {
              if (test[k][s] === i) pi = s;
              if (test[k][s] === j) pj = s;
            }
            if (pi < pj) cnt++;
          }
          if (cnt === m) {
            tmp.push([i, j]);
            answer++;
          }
        }
      }
      console.log(tmp);
      return answer;
    }

    let arr = [[3, 4, 1, 2], [4, 3, 2, 1], [3, 1, 4, 2]];
    console.log(solution(arr));
  </script>
</body>

</html>
```