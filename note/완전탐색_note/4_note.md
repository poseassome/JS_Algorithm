# 졸업선물

> ## 문제

```
선생님은 올해 졸업하는 반 학생들에게 졸업선물을 주려고 합니다.
학생들에게 인터넷 쇼핑몰에서 각자 원하는 상품을 골라 그 상품의 가격과 배송비를 제출하라 고 했습니다. 선생님이 가지고 있는 예산은 한정되어 있습니다.
현재 예산으로 최대 몇 명의 학생에게 선물을 사줄 수 있는지 구하는 프로그램을 작성하세요. 선생님은 상품 하나를 50% 할인해서(반 가격) 살 수 있는 쿠폰을 가지고 있습니다. 배송비는 할인에 포함되지 않습니다.
```
***

> ## 풀이

각 상품에 대해 할인을 적용했을 때의 경우를 모두 구해본다.

카운팅해야되니까 answer는 0으로 초기화한다.<br/>
m은 예산, product.length는 학생수이다.<BR/>

`sort()`를 사용하여 비용을 정렬한다.
```jsx
product.sort((a,b)=>((a[0]+a[1])-(b[0]+b[1]));
// 상품가격과 배송비를 합한 비용
```
각 상품에 할인을 적용한 경우를 구해야되기 때문에 for문을 사용한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>졸업선물</title>
</head>

<body>
  <script>
    function solution(m, product) {
      let answer = 0;
      let n = product.length;
      product.sort((a, b) => (a[0] + a[1]) - (b[0] + b[1]));
      for (let i = 0; i < n; i++) {
        let money = m - (product[i][0] / 2 + product[i][1]); // 남은 예산
        let cnt = 1;
        for (let j = 0; j < n; j++) {
          if (j !== i && (product[j][0] + product[j][1]) > money) break; // 예산초과
          if (j !== i && (product[j][0] + product[j][1]) <= money) {
            money -= (product[j][0] + product[j][1]);
            cnt++;
          }
        }
        answer = Math.max(answer, cnt);
      }
      return answer;
    }

    let arr = [[6, 6], [2, 2], [4, 3], [4, 5], [10, 3]];
    console.log(solution(28, arr));
  </script>
</body>

</html>
```