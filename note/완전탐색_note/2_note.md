# 뒤집은 소수

> ## 문제

```
N개의 자연수가 입력되면 각 자연수를 뒤집은 후 그 뒤집은 수가 소수이면 그 소수를 출력하는 프로그램을 작성하세요. 
예를 들어 32를 뒤집으면 23이고, 23은 소수이다. 그러면 23을 출력한다. 단 910를 뒤집으면 19로 숫자화 해야 한다. 첫 자리부터의 연속된 0은 무시한다.
```
***

> ## 풀이(1)

answer는 여러개가 나오니까 [] 배열 처리한다.

수를 10으로 나눈 나머지는 1의 자리 수가 된다. 그 수를 res에 할당하고
1의 자리가 아닌 숫자들도 똑같이 처리해주기 위해 수를 10으로 나누어 `parseInt()`처리 한다.
```jsx
while(x){
  let t=x%10;
  res = res*10+t;
  s=parseInt(x/10);
  // x가 0이되면 false가 되서 while문이 break된다.
}
```
최종적으로 뒤집은 수는 `isPrime()`이란 함수를 만들어서 소수를 판별한다.
```jsx
function isPrime(num){
  // 1은 소수가 아니다.
  if(num===1) return false;
  // for(let i=2;i<num/2;i++){
    // 자기 자신의 절반까지봐도 약수가 다 나온다.
  for(let i=2;i<=parseInt(Math.sqrt(num));i++){ // 제곱근까지 해도 상관없음
    if(num%i===0) return false;
  }
  return true;
}
```

> ## 풀이(2)

문자열로 변환하여 분리하고 reverse한 후 다시 붙여준다.
```jsx
let res=Number(x.toString().split('').reverse().join(''));
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>뒤집은 소수</title>
</head>

<body>
  <script>
    function isPrime(num) {
      if (num === 1) return false;
      for (let i = 2; i <= parseInt(Math.sqrt(num)); i++) {
        if (num % i === 0) return false;
      }
      return true;
    }
    function solution(arr) {
      let answer = [];
      for (let x of arr) {
        let res = 0;
        while (x) {
          let t = x % 10;
          res = res * 10 + t;
          x = parseInt(x / 10);
        }
        if (isPrime(res)) answer.push(res);
      }
      return answer;
    }

    let arr = [32, 55, 62, 20, 250, 370, 200, 30, 100];
    console.log(solution(arr));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>뒤집은 소수</title>
</head>

<body>
  <script>
    function isPrime(num) {
      if (num === 1) return false;
      for (let i = 2; i <= parseInt(Math.sqrt(num)); i++) {
        if (num % i === 0) return false;
      }
      return true;
    }
    function solution(arr) {
      let answer = [];
      for (let x of arr) {
        let res = Number(x.toString().split('').reverse().join(''));
        if (isPrime(res)) answer.push(res);
      }
      return answer;
    }

    let arr = [32, 55, 62, 20, 250, 370, 200, 30, 100];
    console.log(solution(arr));
  </script>
</body>

</html>
```