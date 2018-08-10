## 문제 1

두 수 `x`, `y`를 입력받아 큰 수를 반환하는 함수(larger)를 작성하세요.

호출 예시:

```js
larger(4, 12); // 결과: 12
```

답:

```js
function larger(x, y) {
  if (x > y) {
    return x;
  } else {
    return y;
  }
}
```

```js
function larger(x, y) {
  return x > y ? x : y;
}
```

## 문제 2

세 수 `x`, `y`, `z`를 입력받아 그 곱이 양수이면 `true`, 0 혹은 음수이면 `false`, 둘 다 아니면 에러를 발생시키는 함수(isPositive)를 작성하세요.

호출 예시:

```js
isPositive(1, 2, 10) // 반환값: true
isPositive(-1, 4, 5) // 반환값: false
isPositive('열다섯', 10, 2) // 에러: Error: 입력값이 잘못되었습니다.
```

에러를 발생시키는 코드는 다음과 같습니다.

```js
throw new Error('입력값이 잘못되었습니다.');
```

답:

```js
function isPositive(x, y, z) {
  const result = x * y * z;
  if (typeof result !== 'number' || Number.isNaN(result)) {
    throw new Error('입력값이 잘못되었습니다.');
  }
  return result > 0;
}
```

## 문제 3

어떤 숫자(num)가 짝수인지 홀수인지 출력하는 함수(printEvenOdd)를 작성하세요.

호출 예시:

```js
printEvenOdd(5) // 출력: '5: 홀수'
printEvenOdd(10) // 출력: '10: 짝수'
```

## 문제 3-1

문제 3번의 함수(printEvenOdd)를 이용해서, 1부터 20까지의 수가 각각 짝수인지 홀수인지 출력하는 함수(printEvenOdd20)를 작성하세요.

호출 예시:

```js
printEvenOdd20();

/*
출력:
1: 홀수
2: 짝수
3: 홀수
4: 짝수
5: 홀수
6: 짝수
7: 홀수
8: 짝수
9: 홀수
10: 짝수
11: 홀수
12: 짝수
13: 홀수
14: 짝수
15: 홀수
16: 짝수
17: 홀수
18: 짝수
19: 홀수
20: 짝수
*/
```

답: 

```js
function printEvenOdd(x) {
  if (x %  2 === 0) {
    console.log(`${x}는 짝수입니다.`);
  } else {
    console.log(`${x}는 홀수입니다.`);
  }
}

function printEvenOdd20() {
  for (let i = 1; i <= 20; i++) {
    printEvenOdd(i);
  }
}
```

## 문제 4

세 수를 입력받아 큰 것부터 차례대로 출력하는 함수(printLargerFirst)를 작성하세요.

호출 예시:

```js
printLargerFirst(5, 15, -2) // 출력: 15, 5, -2
```

답:

```js
function printLargerFirst(x, y, z) {
  if (x < y) {
    const temp = x;
    x = y;
    y = temp;
  }
  if (y < z) {
    const temp = y;
    y = z;
    z = temp;
  }
  if (x < y) {
    const temp = x;
    x = y;
    y = temp;
  }
  console.log(x);
  console.log(y);
  console.log(z);
}
```

## 문제 5

두 문자열 `str1`, `str2`를 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수(insensitiveEqual)를 작성하세요.

호출 예시:

```js
insensitiveEqual('hello', 'hello'); // 반환값: true
insensitiveEqual('hello', 'Hello'); // 반환값: true
insensitiveEqual('hello', 'world'); // 반환값: false
```

답:

```js
function insensitiveEqual(s1, s2) {
  return s1.toLowerCase() === s2.toLowerCase();
}
```

## 문제 6

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수(hideId)를 작성하세요.

호출 예시:

```js
hideId('ksh@fastcampus.co.kr') // 반환값: '***@fastcampus.co.kr'
```

답:

```js
function hideId(s) {
  let idLength = 0;
  let domain = '';
  let isAfterAtSign = false;
  for (let c of s) {
    if (c === '@') {
      isAfterAtSign = true;
      continue;
    }
    if (isAfterAtSign) {
      domain += c;
    } else {
      idLength++;
    }
  }
  return '*'.repeat(idLength) + '@' + domain;
}
```

```js
function hideId(s) {
  const [id, domain] = s.split('@');
  return '*'.repeat(id.length) + '@' + domain;
}
```

## 문제 7

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수(insertHyphen)를 작성하세요.

호출 예시:

```js
insertHyphen('1122334455'); // 반환값: '112-2334-455'
insertHyphen('437027423'); // 반환값: '4370-274-23'
```

답:

```js
const EVENS = ['0', '2', '4', '6', '8'];

function insertHyphen(s) {
  let previous;
  let sum = '';
  for (let c of s) {
    if (EVENS.includes(previous) && EVENS.includes(c)) {
      sum += '-';
    }
    sum += c;
    previous = c;
  }
  return sum;
}
```

## 문제 8

두 정수 `start`, `end`를 입력받아, `start`부터 `end`까지의 모든 정수를 배열로 반환하는 함수(range)를 작성하세요.

호출 예시:

```js
range(3, 6); // 반환값: [3, 4, 5, 6]
range(-4, 0); // 반환값: [-4, -3, -2, -1, 0]
```

답:

```js
function range(start, end) {
  const result = [];

  for (let i = start; i <= end; i++) {
    result.push(i);
  }

  return result;
}
```

## 문제 9

수 타입의 값으로만 이루어진 배열 `arr`를 입력받아, 그 값들의 합을 구하는 함수(sum)를 작성하세요.

호출 예시:

```js
sum([1, 2, 3]); // 반환값: 6
```

답:

```js
function sum(arr) {
  let result = 0;
  for (let item of arr) {
    result += item;
  }
  return result;
}
```

## 문제 10

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수(randomInteger)를 작성하세요.

호출 예시:

```js
randomInteger(1, 7); // 반환값: 1, 2, 3, 4, 5, 6 중 임의의 수 하나
```

답:

```js
function randomInteger(min, max) {
  return min + Math.floor(Math.random() * (max - min));
}
```
