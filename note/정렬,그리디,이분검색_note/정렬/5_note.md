# 삽입 정렬 응용 - Least Recently Used (카카오 캐시 문제 변형)

> ## 문제

```
캐시메모리는 CPU와 주기억장치(DRAM) 사이의 고속의 임시 메모리로서 CPU가 처리할 작업 을 저장해 놓았다가 필요할 바로 사용해서 처리속도를 높이는 장치이다. 
워낙 비싸고 용량이 작아 효율적으로 사용해야 한다. 철수의 컴퓨터는 캐시메모리 사용 규칙이 LRU 알고리즘을 따른다. 
LRU 알고리즘은 Least Recently Used의 약자로 직역하자면 가장 최근에 사용되지 않은 것 정도의 의미를 가지고 있습니다. 
캐시에서 작업을 제거할 때 가장 오랫동안 사용하지 않은 것을 제거하겠다는 알고리즘입니다.

만약 캐시의 사이즈가 5이고 작업이 2 3 1 6 7 순으로 저장되어 있다면, (맨 앞이 가장 최근에 쓰인 작업이고, 맨 뒤는 가장 오랫동안 쓰이지 않은 작업이다.)

1) Cache Miss : 해야할 작업이 캐시에 없는 상태로 위 상태에서 만약 새로운 작업인 5번 작업을 CPU가 사용한다면 Cache miss가 되고 모든 작업이 뒤로 밀리고 5번작업은 캐시의 맨 앞에 위치한다. 
5 2 3 1 6 (7번 작업은 캐시에서 삭제된다.)

2) Cache Hit : 해야할 작업이 캐시에 있는 상태로 위 상태에서 만약 3번 작업을 CPU가 사용한다면 Cache Hit가 되고, 63번 앞에 있는 5, 2번 작업은 한 칸 뒤로 밀리고, 3번이 맨 앞으로 위치하게 된다. 
5 2 3 1 6 ---> 3 5 2 1 6

캐시의 크기가 주어지고, 캐시가 비어있는 상태에서 N개의 작업을 CPU가 차례로 처리한다면 N개의 작업을 처리한 후 
캐시메모리의 상태를 가장 최근 사용된 작업부터 차례대로 출력하는 프로그램을 작성하세요.
```
***

> ## 풀이 (1)

i가 arr를 돌 떄 i는 배열의 마지막 인덱스에서 인덱스 1까지 돈다.<br/>
현재 위치해있는 숫자를 한 칸 씩 뒤로 복사한다. `arr[i] = arr[i-1]`

새로운 작업이 추가되면 해당 작업은 인덱스 0 자리에 위치시킨다.

존재하는 작업이 다시 실행되는 경우는 Hit 지점부터 인덱스 1까지 돈다.

> ## 풀이 (2)

내장 함수를 사용한다.

Cache Miss일 때,<br/>
`unshift()` 배열 맨 앞에 요소 추가한다.<br/>
하지만 이를 사용하면 배열의 크기가 커지기 때문에 크기를 벗어나는 마지막 요소를 지워버린다. => `pop()`

Cache Hit일 때,<br/>
`splice()` 로 존재하는 작업을 제거하고 `unshift()`로 맨 앞에 추가한다.
***

#### 전체 코드
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>삽입정렬 응용</title>
</head>

<body>
  <script>
    function solution(size, arr) {
      // answer을 캐시 공간으로 초기화
      let answer = Array.from({ length: size }, () => 0);
      arr.forEach(x => {
        // 주어진 작업이 Miss인지 Hit인지 판별
        let pos = -1;
        for (let i = 0; i < size; i++) if (x === answer[i]) pos = i;
        if (pos === -1) {
          for (let i = size - 1; i >= 1; i--) {
            answer[i] = answer[i - 1];
          }
          answer[0] = x;
        } else {
          for (let i = pos; i >= 1; i--) {
            answer[i] = answer[i - 1];
          }
          answer[0] = x;
        }
      });
      return answer;
    }

    let arr = [1, 2, 3, 2, 6, 2, 3, 5, 7];
    console.log(solution(5, arr));
  </script>
</body>

</html>
```
```html
<html>

<head>
  <meta charset="UTF-8">
  <title>삽입정렬 응용</title>
</head>

<body>
  <script>
    function solution(size, arr) {
      let answer = Array.from({ length: size }, () => 0);
      arr.forEach(x => {
        let pos = -1;
        for (let i = 0; i < size; i++) if (x === answer[i]) pos = i;
        if (pos === -1) {
          answer.unshift(x);
          answer.pop();
        } else {
          answer.splice(pos, 1);
          answer.unshift(x);
        }
      })
      return answer;
    }

    let arr = [1, 2, 3, 2, 6, 2, 3, 5, 7];
    console.log(solution(5, arr));
  </script>
</body>

</html>
```