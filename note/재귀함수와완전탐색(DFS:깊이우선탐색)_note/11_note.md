# 팩토리얼

> ## 문제

```
자연수 N을 입력하면 N!값을 구하세요. 
N! = n*(n-1)*(n-2)*.....*2*1입니다. 만약 N=5라면 5!=5*4*3*2*1=120입니다.
```
***

> ## 풀이

`DFS(n-1)`로 재귀함수를 이용한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>팩토리얼</title>
</head>

<body>
  <script>
    function solution(n) {
      let answer;
      function DFS(n) {
        if (n === 1) return 1;
        else return n * DFS(n - 1);
      }
      answer = DFS(n);
      return answer;
    }

    console.log(solution(5));
  </script>
</body>

</html>
```