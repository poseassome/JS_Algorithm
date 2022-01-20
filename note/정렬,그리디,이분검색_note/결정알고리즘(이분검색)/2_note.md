# 뮤직 비디오 (결정 알고리즘)

> ## 문제

```
지니레코드에서는 불세출의 가수 조영필의 라이브 동영상을 DVD로 만들어 판매하려 한다. 
DVD에는 총 N개의 곡이 들어가는데, DVD에 녹화할 때에는 라이브에서의 순서가 그대로 유지 되어야 한다. 
순서가 바뀌는 것을 우리의 가수 조영필씨가 매우 싫어한다. 
즉, 1번 노래와 5번 노래를 같은 DVD에 녹화하기 위해서는 1번과 5번 사이의 모든 노래도 같은 DVD에 녹화해야 한다. 또한 한 노래를 쪼개서 두 개의 DVD에 녹화하면 안된다.
지니레코드 입장에서는 이 DVD가 팔릴 것인지 확신할 수 없기 때문에 이 사업에 낭비되는 DVD를 가급적 줄이려고 한다. 
고민 끝에 지니레코드는 M개의 DVD에 모든 동영상을 녹화하기로 하였다. 이 때 DVD의 크기(녹화 가능한 길이)를 최소로 하려고 한다. 
그리고 M개의 DVD는 모두 같은 크기여야 제조원가가 적게 들기 때문에 꼭 같은 크기로 해야 한다.
```
***

> ## 풀이

주어진 수 중 가장 큰 수를 lt로 두고, rt는 주어진 수 들의 합이다.

`mid = (lt + rt) / 2`를 해서 mid값이 곧 DVD 한 장의 용량이므로,<br/>
모든 내용이 담길 수 있는 지 확인한다. (장 수 상관없이)

이를 answer에 일단 저장하고, 우린 최소 용량을 찾아야되기 때문에<br/>
더 작은 용량으로도 담을 수 있는 지 확인하다. `rt = mid-1`

그렇게 다시 구한 DVD의 크기가 answer와 비교해서 더 작은 값인지 비교한다.


***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>뮤직비디오</title>
</head>

<body>
  <script>
    function count(songs, capacity) {
      // cnt : DVD 장 수, sum : DVD 한 장에 저장되는 용량(누적), capacity : DVD의 용량
      let cnt = 1, sum = 0;
      for (let x of songs) {
        if (sum + x > capacity) {
          cnt++;
          sum = x;
        }
        else sum += x;
      }
      return cnt;
    }
    function solution(m, songs) {
      let answer;
      let lt = Math.max(...songs);    // 가장 큰 값 찾기
      let rt = songs.reduce((a, b) => a + b, 0);    // 누적하여 더하기
      while (lt <= rt) {
        let mid = parseInt((lt + rt) / 2);
        // mid값을 DVD 한 장의 용량이라 했을 때 총 몇장이 필요한지 구함 --> count()
        if (count(songs, mid) <= m) {
          answer = mid;
          rt = mid - 1;
        }
        else lt = mid + 1;
      }
      return answer;
    }

    let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    console.log(solution(3, arr));
  </script>
</body>

</html>
```