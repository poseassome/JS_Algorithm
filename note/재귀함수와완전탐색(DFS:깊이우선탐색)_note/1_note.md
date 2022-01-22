# 재귀함수와 스택프레임

> ## 문제

```
자연수 N이 입력되면 재귀함수를 이용하여 1부터 N까지를 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이

내가 자기자신을 호출하는 것이 재귀함수이다.<Br/>
계속 자기 자신을 호출하지 않게 조건문으로 멈춰야한다.
```jsx
function solution(n){
  function DFS(L){
    if(L===0) return;
    else{
      console.log(L);
      DFS(L-1);
    }
  }
  DFS(n);
}
```
`solution(3)`을 실행하면 콘솔창에 "3, 2, 1"로 출력이된다.

우리는 1부터 출력을 해야한다.
```jsx
function solution(n){
  function DFS(L){
    if(L===0) return;
    else{
      DFS(L-1);
      console.log(L);
    }
  }
  DFS(n);
}
```

`solution(3)`이 실행되면 `DFS(3)`의 정보가 `stack` 자료구조에 담긴다.
- 매개변수 L = 3
- 지역변수
- 복귀주소 (코드를 수행하고 자기가 호출된 위치로 돌아가기위한 주소)

위 코드에서 실행 중에 `DFS(L-1)`을 만나면서 stack에 `DFS(2)`가 쌓인다.<br/>
`DFS(3)`은 대기상태

```jsx
    if(L===0) return;
```
`return`이 되면서 `DFS(0)`이 호출된 시점으로 돌아가고,<br/>
stack에서 `DFS(1)`이 실행되면서 `console.log()`를 실행하면서 차례대로 결과가 나온다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>재귀함수와 스택프레임</title>
</head>

<body>
  <script>
    function solution(n) {
      function DFS(L) {
        if (L === 0) return;
        else {
          DFS(L - 1);
          console.log(L);
        }
      }
      DFS(n);
    }

    solution(3);
  </script>
</body>

</html>
```