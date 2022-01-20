# 결혼식

> ## 문제

```
현수는 다음 달에 결혼을 합니다.
현수는 결혼식 피로연을 장소를 빌려 3일간 쉬지 않고 하려고 합니다.
피로연에 참석하는 친구들 N명의 참석하는 시간정보를 현수는 친구들에게 미리 요구했습니다. 각 친구들은 자신이 몇 시에 도착해서 몇 시에 떠날 것인지 현수에게 알려주었습니다.
현수는 이 정보를 바탕으로 피로연 장소에 동시에 존재하는 최대 인원수를 구하여 그 인원을 수용할 수 있는 장소를 빌리려고 합니다. 여러분이 현수를 도와주세요.
만약 한 친구가 오는 시간 13, 가는시간 15라면 이 친구는 13시 정각에 피로연 장에 존재하는 것이고 15시 정각에는 존재하지 않는다고 가정합니다.
```
***

> ## 풀이

하나의 사람을 두 개의 이벤트로 쪼갠다. => 온 시간과 간 시간으로
```
[14, 18] 이라면 14를 s, 18을 e로
```
그리고 s, e 구분없이 시간으로 정렬을 한다.<br/>
s를 만나면 ++하고, e를 만나면 --를 한다.

s와 e가 동일하다면 e를 먼저 정렬한다.

***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>결혼식</title>
</head>

<body>
  <script>
    function solution(times) {
      let answer = Number.MIN_SAFE_INTEGER;
      let T_line = [];
      // 시간 분리
      for (let x of times) {
        T_line.push([x[0], 's']);
        T_line.push([x[1], 'e']);
      }
      // 시간 정렬
      T_line.sort((a, b) => {
        if (a[0] === b[0]) return a[1].charCodeAt() - b[1].charCodeAt();
        else return a[0] - b[0];
      })
      // 인원 파악
      let cnt = 0;
      for (let x of T_line) {
        if (x[1] === "s") cnt++;
        else cnt--;
        answer = Math.max(answer, cnt);
      }
      return answer;
    }

    let arr = [[14, 18], [12, 15], [15, 20], [20, 30], [5, 14]];
    console.log(solution(arr));
  </script>
</body>

</html>
```