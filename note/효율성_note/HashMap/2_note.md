# 아나그램

> ## 문제

```
Anagram이란 두 문자열이 알파벳의 나열 순서를 다르지만 그 구성이 일치하면 두 단어는 아나그램이라고 합니다.
예를 들면 AbaAeCe 와 baeeACA 는 알파벳을 나열 순서는 다르지만 그 구성을 살펴보면 A(2), a(1), b(1), C(1), e(2)로 알파벳과 그 개수가 모두 일치합니다. 
즉 어느 한 단어를 재 배열하면 상대편 단어가 될 수 있는 것을 아나그램이라 합니다.
길이가 같은 두 개의 단어가 주어지면 두 단어가 아나그램인지 판별하는 프로그램을 작성하세요. 아나그램 판별시 대소문자가 구분됩니다.
```
***

> ## 풀이

`Map()`객체를 생성하여 sH에 key:value로 한 배열의 알파벳과 그의 갯수를 입력한다.

우선, 해당 알파벳 key가 존재하는 지 확인한다.<Br/>
key가 있으면 value를 -1 하는 방식으로 상쇄시킨다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>아나그램</title>
</head>

<body>
  <script>
    function solution(str1, str2) {
      let answer = "YES";
      let sH = new Map();
      for (let x of str1) {
        if (sH.has(x)) sH.set(x, sH.get(x) + 1);
        else sH.set(x, 1);
      }
      for (let x of str2) {
        if (!sH.has(x) || sH.get(x) === 0) return "NO";
        sH.set(x, sH.get(x) - 1);
      }
      return answer;
    }

    let a = "AbaAeCe";
    let b = "baeeACA";
    console.log(solution(a, b));
  </script>
</body>

</html>
```