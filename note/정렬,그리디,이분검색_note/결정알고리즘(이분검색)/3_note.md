# 마구간 정하기 (결정 알고리즘)

> ## 문제

```
N개의 마구간이 수직선상에 있습니다. 각 마구간은 x1, x2, x3, ......, xN의 좌표를 가지며, 마 구간간에 좌표가 중복되는 일은 없습니다.
현수는 C마리의 말을 가지고 있는데, 이 말들은 서로 가까이 있는 것을 좋아하지 않습니다. 각 마구간에는 한 마리의 말만 넣을 수 있고, 가장 가까운 두 말의 거리가 최대가 되게 말을 마구간에 배치하고 싶습니다.
C마리의 말을 N개의 마구간에 배치했을 때 가장 가까운 두 말의 거리가 최대가 되는 그 최대 값을 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

lt는 최소 거리 1, rt는 최대 거리로 좌표 배열의 끝

첫 번째 말은 첫 번째 좌표 마구간에 배치한다. 그 말이 들어간 마구간의 위치는 `ep`에 저장한다.

`ep`가 그 다음 말을 배칠할 마구간과의 거리가 `mid`보다 크거나 같은지 비교한다.<br/>
만약 크다면 그 위치에 말을 배치하고 `ep`를 해당 좌표로 재할당한다.

그리고 다시 그 다음 마구간의 좌표에서 `ep`를 뺀 값이 `mid`보다 큰지 비교한다.<br/>
크지 않다면 rt가 (mid-1)이 된다. <Br/>
그리도 다시 `ep`는 최근에 들어간 말의 위치, 첫 번째 말이 들어간 위치로 reset된다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>마구간 정하기</title>
</head>

<body>
  <script>
    function count(stable, dist) {
      // cnt : 말의 개수
      let cnt = 1, ep = stable[0];
      for (let i = 1; i < stable.length; i++) {
        if (stable[i] - ep >= dist) {
          cnt++;
          ep = stable[i];
        }
      }
      return cnt;
    }
    function solution(c, stable) {
      let answer;
      stable.sort((a, b) => a - b);
      let lt = 1;
      let rt = stable[stable.length - 1];
      while (lt <= rt) {
        let mid = parseInt((lt + rt) / 2);
        if (count(stable, mid) >= c) { // count() : 말을 몇 마리 배치할 수 있는지 return
          answer = mid;
          // 해당 거리로 배치할 수 있으면 그것보다 더 큰 거리는 무조건 가능한거니까
          // 더 좁은 거리를 찾기위해 lt를 옮긴다.
          lt = mid + 1;
        }
        else rt = mid - 1;
      }
      return answer;
    }

    let arr = [1, 2, 8, 4, 9];
    console.log(solution(3, arr));
  </script>
</body>

</html>
```