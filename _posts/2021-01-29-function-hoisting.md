---
layout: single
title: "함수 표현식과 함수 선언문의 차이"
date: 2021-01-29 16:17:36 +0900
author_profile: true
toc: true
---

var와 마찬가지로, 함수도 **호이스팅(Hoisting)**이 일어난다.

# 함수의 생성 방법

크게 함수의 생성 방법은 세 가지로 나뉜다.

1. 함수 선언문(function statement)
2. 함수 표현식(function expression)
3. Function() 생성자 함수

3번의 생성자 함수는 거의 사용되지 않는 방법으로 본 글에서는 다루지 않는다.

살펴볼 것은 함수 선언문과 함수 표현식의 차이이다.

## 함수 선언문(function statement)

함수 선언문은 다음과 같이 작성한다.

```javascript
function sum(x, y) {
  return x + y;
}

console.log(sum(1, 2)); // 3
```

## 함수 표현식(function expression)

함수 표현식은 다음과 같이 작성한다.

```javascript
let sum = function(x, y) {
  return x + y;
};

console.log(sum(1, 2)); // 3
```

## 함수 호이스팅

다음 예시를 보자.

```javascript
console.log(sum(1, 2)) // 3

function sum(x, y) {
  return x + y;
}

console.log(sum(1, 2)) // 3
```

분명히 함수가 선언되기 이전인데 오류를 뿜지 않는다. 이를 **함수 호이스팅**이라고 한다.
함수 호이스팅은 함수 선언식으로 생성된 함수에서만 일어난다.

이제 함수 표현식으로 함수를 생성할 시 어떻게 되는지 다음 예시를 통해 살펴보자.

```javascript
console.log(sum(1, 2)) // ERROR

let sum = function(x, y) {
  return x + y;
};

console.log(sum(1, 2)) // 3
```

함수 표현식으로 생성된 함수에서는 함수 호이스팅이 일어나지 않는다.
이는 `let`을 `var`로 바꾸어도 동일하다.

### 요약

함수 표현식으로 생성된 함수는 함수 호이스팅이 일어나지 않고, 함수 선언문으로 생성된 함수는 함수 호이스팅이 일어난다.

이러한 특성을 이해하고 있어야, 본인이 예상치 못한 결과가 발생하는 일이 줄어들 것이다.

이러한 특성 때문에, 일반적으로 함수 표현식을 이용해 함수를 생성할 것이 권장되고 있으나, 특성을 이해하고 제어할 수 있다면 함수 선언문으로 함수를 생성해도 바람직한 결과를 얻을 수 있을 것이다.

