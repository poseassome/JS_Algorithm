# 후위식 연산 (postfix) (스택)

> ## 문제

```
후위연산식이 주어지면 연산한 결과를 출력하는 프로그램을 작성하세요.
만약 3*(5+2)-9 을 후위연산식으로 표현하면 352+*9- 로 표현되며 그 결과는 12입니다.
```
***

> ## 풀이

받은 문자열 중 숫자를 만나면 stack에 `push`하고<br/>
연산자를 만나면 연산자를 기준으로 왼쪽을 lt, 오른쪽은 rt라 하면,<br/>
rt는 stack의 가장 마지막으로 `push`된 숫자/ lt는 그 전에 `push`된 숫자를 대입한다.

그리고 연산의 결과를 stack에 다시 `push`한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>후위식 연산</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer;
      let stack = [];
      for (let x of s) {
        if (!isNaN(x)) stack.push(Number(x));
        else {
          let rt = stack.pop();
          let lt = stack.pop();
          if (x === '+') stack.push(lt + rt);
          else if (x === '-') stack.push(lt - rt);
          else if (x === '/') stack.push(lt / rt);
          else if (x === '*') stack.push(lt * rt);
        }
      }
      answer = stack[0];
      return answer;
    }

    let str = "352+*9-";
    console.log(solution(str));
  </script>
</body>

</html>
```