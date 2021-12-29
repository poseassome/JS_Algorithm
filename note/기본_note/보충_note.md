# forEach, map, filter, reduce

> ### forEach
a 배열이 있다.
```
a = [10, 11, 12, 13, 14, 15];
a.forEach();      // 함수 호출
```

`forEach()`는 매개변수가 2개이다.
첫 번째 변수는 함수를 전달받는다.
두 번째 변수는 함수 내부에서 사용할 this를 전달받는다.
```jsx
a.forEach(function());

원리는 a 배열 요소를 하나하나 가자다가 콜백함수를 계속 호출하는 것
function() --> predicate로 전달받아서 계속 호출하고
predicate는 a[i], i 를 인자로 넘긴다.

function forEach(predicate, thisArg){
  for(i=0;i<a.length;i++){
    predicate(a[i], i)
  }
}
```
```jsx
a.foreach(function(v, i){
  console.log(v, i, this);
}, [1, 2])

v는 a배열의 요소들 (=a[i]).
[1, 2]는 this.
```
***
> ### map
요소를 하나하나 탐색하면서 요소들을 사용하여 새로운 배열을 생성한다.

a 배열이 있다.
```
a = [10, 11, 12, 13, 14, 15];
a.map();      // 함수 호출
```

```jsx
let answer = a.map(function(v, i){
  return v*v;
}, [1, 2]);
```
map()을 호출하면 빈 배열을 만들고, for문으로 원본 배열 요소 하나하나를 탐색한다.<br/>
콜백함수 v*v라는 함수를 실행한 return값을 원소로 하는 새로운 배열 생성한다.
```jsx
// 원리를 설명하자면
function map(predicate, thisArg){
  let list = [];
  for(i=0;i<a.length;i++){
    list.push(predicate(a[i], i));
  }
  return list;
}
```
**새로운 배열은 무조건 원본 배열과 길이가 같다.**<br/>
return받지 못한 값은 undefined로 정의한다.

***
> ### filter
map과 동일하게 요소들을 사용하여 새로운 배열을 생성하지만 원본 배열과 길이가 같은 필요가 없다.

a 배열이 있다.
```
a = [10, 11, 12, 13, 14, 15];
a.map();      // 함수 호출
```

```jsx
let answer = a.filter(function(v, i){
  return v%2==0;
}, [1, 2]);
```
콜백함수가 TRUE를 return했을 때의 원소만 새로운 배열에 추가한다.
```jsx
// 원리를 설명하자면
function filter(predicate, thisArg){
  let list = [];
  for(i=0;i<a.length;i++){
    if(predicate(a[i], i)){
      list.push(a[i]);
    }
  }
  return list;
}
```
***
> ### reduce
첫 번째 인자는 콜백함수, 두 번째 인자는 초기화하는 값이다.<br/>
콜백함수의 인자도 앞 함수들과는 다르다.

reduce()는 배열을 생성해서 return하지 않고 어떤 값을 생성해서 return한다.

```
a = [10, 11, 12, 13, 14, 15];
a.map();      // 함수 호출
```
```jsx
let answer = a.reduce(function(acc, v){
  return acc+v;
}, 0);
```

```jsx
// 원리를 설명하자면
function reduce(predicate, val){
  let result = val;     // 값 초기화
  for(i=0;i<a.length;i++){
    result=predicate(result, a[i]);
  }
  return result;
}
```
acc(result)는 계속 누적된다.
***