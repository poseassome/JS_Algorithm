# 일곱 난쟁이

> ## 문제

```
왕비를 피해 일곱 난쟁이들과 함께 평화롭게 생활하고 있던 백설공주에게 위기가 찾아왔다. 일과를 마치고 돌아온 난쟁이가 일곱 명이 아닌 아홉 명이었던 것이다.
아홉 명의 난쟁이는 모두 자신이 "백설 공주와 일곱 난쟁이"의 주인공이라고 주장했다. 뛰어난 수학적 직관력을 가지고 있던 백설공주는, 다행스럽게도 일곱 난쟁이의 키의 합이 100이 됨을 기억해 냈다.
아홉 난쟁이의 키가 주어졌을 때, 백설공주를 도와 일곱 난쟁이를 찾는 프로그램을 작성하시오.
```
***

> ## 풀이

두 수`(i, j)`를 제외한 모든 숫자의 합을 구해봐야한다.<br/>
9개의 수를 더한 **sum**에서 **(arr[i]+arr[j])**를 뺐을 때 100이 되는 지 확인한다.
확인 후 배열을 자르기 위해 `splice(자를 위치 index, 자를 갯수)`를 사용한다. 
```jsx
let answer = arr;
let sum = arr.reduce((a,b)=>a+b, 0);
```
`reduce()`에서 두 번째 인자(<u>0</u>)은 a값을 0으로 초기화한다.<br/>
콜백함수 b는 arr의 요소들이다.

for문에서 i는 j가 있으니까 끝까지 갈 필요 없고 8번째 요소까지 가면 된다.
```jsx
for(i=0;i<8;i++)
```
j는 i+1로 정의하고 9번째 요소까지 가면 된다. (반복문 중첩)
```jsx
for(i=0;i<8;i++){
  for(j=i+1;i<9;j++){
    if((sum-(arr[i]+arr[j]))===100){
      arr.splice(j,1);
      arr.splice(i,1);
      // i 인덱스를 먼저 지우게 되면 j의 인덱스가 한 칸씩 당겨져서 엉뚱한 숫자가 지워진다.
    }
  }
}
```
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>일곱 난쟁이</title>
</head>

<body>
  <script>
    function solution(arr) {
      let answer = arr;
      let sum = arr.reduce((a, b) => a + b, 0);
      for (i = 0; i < 8; i++) {
        for (j = i + 1; j < 9; j++) {
          if ((sum - (arr[i] + arr[j])) === 100) {
            arr.splice(j, 1);
            arr.splice(i, 1);
          }
        }
      }
      return answer;
    }

    let arr = [20, 7, 23, 19, 10, 15, 25, 8, 13];
    console.log(solution(arr));
  </script>
</body>

</html>
```