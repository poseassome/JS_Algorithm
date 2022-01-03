# 학급 확장

> ## 문제

```
학급 회장을 뽑는데 후보로 기호 A, B, C, D, E 후보가 등록을 했습니다.
투표용지에는 반 학생들이 자기가 선택한 후보의 기호(알파벳)가 쓰여져 있으며 선생님은 그 기호를 발표하고 있습니다.
선생님의 발표가 끝난 후 어떤 기호의 후보가 학급 회장이 되었는지 출력하는 프로그램을 작성하세요. 
반드시 한 명의 학급회장이 선출되도록 투표결과가 나왔다고 가정합니다.
```
***

> ## 풀이

Hash를 사용하기 위해 Map()을 사용한다.

`new` : 객체 생성 연산자<br/>
`Map()` 객체를 생성한다.
```jsx
let sH = new Map();
```
sH는 <u>key: value</u> 한 쌍으로된 객체로 이루어져 있다.

`sH.set()`을 이용해서 알파벳은 key, 갯수를 value로 하여 설정한다.
```jsx
sH.set('B', 1)
```
이미 입력한 알파벳을 만나면 value를 +1 증가시킨다.
```jsx
sH.set('D', sH.get('D')+1)
```
최종적으로 value가 최대값인 알파벳을 출력한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>학급 확장</title>
</head>

<body>
  <script>
    function solution(s) {
      let answer;
      let sH = new Map();
      for (let x of s) {
        // sH에 x가 존재하는지 확인
        if (sH.has(x)) sH.set(x, sH.get(x) + 1);
        else sH.set(x, 1);
      }
      let max = Number.MIN_SAFE_INTEGER;
      for (let [key, val] of sH) {
        if (val > max) {
          max = val;
          answer = key;
        }
      }
      return answer;
    }

    let str = "BACBACCACCBDEDE";
    console.log(solution(str));
  </script>
</body>

</html>
```