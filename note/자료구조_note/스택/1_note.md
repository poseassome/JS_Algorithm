# 올바른 괄호 (스택)

> ## 문제

```
괄호가 입력되면 올바른 괄호이면 “YES", 올바르지 않으면 ”NO"를 출력합니다.
(())() 이것은 괄호의 쌍이 올바르게 위치하는 거지만, (()()))은 올바른 괄호가 아니다.
```
***

> ## 풀이

`스택`의 자료구조를 사용하여 푼다.<br/>
=> 자료가 들어가는 입구와 나오는 출구가 동일하다.<br/>
=> Last In First Out (LIFO) /나중에 들어간 자료가 먼저 나온다.

스택과 반대되는 구조가 `큐`이다.<br/>
=> First In First Out (FIFO)

자바스크립트에서 스택은 배열처리 하면 된다.<br/>
`push`로 자료를 넣고 `pop`으로 자료를 뺀다.

여는 괄호를 만나면 `push`, 닫는 괄호를 만나면 `pop` 한다.<Br/>
--> 올바른 괄호는 최종 결과가 처음 배열의 형태와 동일하다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>올바른 괄호</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer = "YES";
      stack = [];
      for (let x of s) {
        if (x === "(") stack.push(x);
        else {
          if (stack.length === 0) return "NO";
          stack.pop();
        }
      }
      return answer;
    }

    let a = "(()(()))(()";
    console.log(solution(a));
  </script>
</body>

</html>
```