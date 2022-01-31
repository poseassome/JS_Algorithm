# 최대점수 구하기

> ## 문제

```
이번 정보올림피아드대회에서 좋은 성적을 내기 위하여 현수는 선생님이 주신 N개의 문제를 풀려고 합니다. 각 문제는 그것을 풀었을 때 얻는 점수와 푸는데 걸리는 시간이 주어지게 됩니다. 제한시간 M안에 N개의 문제 중 최대점수를 얻을 수 있도록 해야 합니다. (해당문제는 해당시간이 걸리면 푸는 걸로 간주한다, 한 유형당 한개만 풀 수 있습니다.)
```
***

> ## 풀이

dy배열을 0~M개의 길이를 가지며 0으로 초기화한다.<br/>
dy[j]는 j시간 동안 얻을 수 있는 최대 점수이다.

동전교환처럼 dy배열을 돌면 중복적용이 되서 안 된다.

j를 m부터 pt[i] (i번째 문제에 걸리는 시간)해서 dy를 거꾸로 탐색한다.
```
[10, 5]면, 5분이 걸린 후 점수는 계속 10점이다. (dy[5]~dy[20]의 값은 모두 10)

[25, 12]면, (20-12=8) dy[8]에서 얻을 수 있는 점수는 10이고, dy[20]에서 얻는 최종 점수는 10+25로 35점이다.
16분에서 12분을 빼면 4분 동안 푼 문제가 없으므로 최종 점수는 25점이다.
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>최대점수구하기</title>
</head>

<body>
  <script>
    function solution(m, arr) {
      let answer = 0;
      let dy = Array.from({ length: m + 1 }, () => 0);
      for (let i = 0; i < arr.length; i++) {
        let ps = arr[i][0];
        let pt = arr[i][1];
        for (let j = m; j >= pt; j--) {
          dy[j] = Math.max(dy[j], dy[j - pt] + ps);
        }
      }
      answer = dy[m];
      return answer;
    }

    let arr = [[10, 5], [25, 12], [15, 8], [6, 3], [7, 4]];
    console.log(solution(20, arr));
  </script>
</body>

</html>
```