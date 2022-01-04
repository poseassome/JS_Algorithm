# 괄호 문자 제거 (스택)

> ## 문제

```
입력된 문자열에서 소괄호 ( ) 사이에 존재하는 모든 문자를 제거하고 남은 문자만 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

여는 괄호와 문자는 `push`한다.

닫는 괄호를 만나면 stack에 존재하는 여는 괄호를 찾는다.<br/>
닫는 괄호와 여는 괄호 사이를 모두 제거한다.
```jsx
while(stack.pop()!=="(");
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>괄호 문자 제거</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer;
      stack = [];
      for (let x of s) {
        if (x === ")") {
          while (stack.pop() !== "(");
        } else stack.push(x);
      }
      answer = stack.join('');
      return answer;
    }

    let str = "(A(BC)D)EF(G(H)(IJ)K)LM(N)";
    console.log(solution(str));
  </script>
</body>

</html>
```