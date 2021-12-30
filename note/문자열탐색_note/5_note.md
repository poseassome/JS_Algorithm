# 문자열 압축

> ## 문제

```
알파벳 대문자로 이루어진 문자열을 입력받아 같은 문자가 연속으로 반복되는 경우 반복되는 문자 바로 오른쪽에 반복 횟수를 표기하는 방법으로 문자열을 압축하는 프로그램을 작성하시오. 
단 반복횟수가 1인 경우 생략합니다.
```
***

> ## 풀이

인덱스를 사용하여 `s[i] === s[i+1]` 이면 cnt++한다.<br/>
새로운 문자를 만나면 cnt=1 이다.<br/>

마지막 문자는 비교할 다음 문자가 없기 때문에 빈 문자열을 추가한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>문자열 압축</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "";
      let cnt = 1;
      s = s + " ";
      for (i = 0; i < s.length - 1; i++) {
        if (s[i] === s[i + 1]) cnt++;
        else {
          answer += s[i];
          if (cnt > 1) answer += String(cnt);
          cnt = 1;
        }
      }
      return answer;
    }

    let str = "KKHSSSSSSSE";
    console.log(solution(str));
  </script>
</body>

</html>
```