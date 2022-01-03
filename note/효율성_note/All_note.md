# 모든 아나그램 찾기

> ## 문제

```
S문자열에서 T문자열과 아나그램이 되는 S의 부분문자열의 개수를 구하는 프로그램을 작성하세요.
아나그램 판별시 대소문자가 구분됩니다. 부분문자열은 연속된 문자열이어야 합니다.
```
***

> ## 풀이

각 배열에 대해 Hash map을 만든다.
```jsx
let sH = new Map();
let tH = new Map();
```
한 배열의 key: val를 모두 입력하고 다른 배열은 그 배열의 size만큼 key: val을 입력하고 아나그램인지 판별한다.<Br/>
판별 후 rt로 한 칸 이동하고 처음 추가한 key의 val는 -1한다.<br/>
어떤 key의 val이 0이되면 delete 지워줘야한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>모든 아나그램 찾기</title>
</head>

<body>
  <script>
    function compareMaps(map1, map2) {
      if (map1.size !== map2.size) return false;
      for (let [key, val] of map1) {
        if (!map2.has(key) || map2.get(key) !== val) return false;
      }
      return true;
    }
    function solution(s, t) {
      let answer = 0;
      let tH = new Map();
      let sH = new Map();
      // t배열 Hash 입력
      for (let x of t) {
        if (tH.has(x)) tH.set(x, tH.get(x) + 1);
        else tH.set(x, 1);
      }
      // t배열길이의 끝 한자리는 남기고 해쉬 앞 부분은 미리 세팅해놓는다.
      let len = t.length - 1;
      for (let i = 0; i < len; i++) {
        if (sH.has(s[i])) sH.set(s[i], sH.get(s[i]) + 1);
        else sH.set(s[i], 1);
      }
      // s배열에서 이제 오른쪽 방향의 알파벳을 추가하여 t배열과 아나그램인지 비교한다.
      let lt = 0;
      for (let rt = len; rt < s.length; rt++) {
        if (sH.has(s[rt])) sH.set(s[rt], sH.get(s[rt]) + 1);
        else sH.set(s[rt], 1);
        if (compareMaps(sH, tH)) answer++;
        sH.set(s[lt], sH.get(s[lt]) - 1);
        if (sH.get(s[lt]) === 0) sH.delete(s[lt]);
        lt++;
      }
      return answer;
    }

    let a = "bacaAacba";
    let b = "abc";
    console.log(solution(a, b));
  </script>
</body>

</html>
```