---
layout: archive
classes: wide
title: "화살표 함수(Arrow Function) 기초"
date: 2021-01-27 23:45:36 +0900
author_profile: true
toc: true
---

ES5에서 등장한 화살표 함수(Arrow Function)의 기초에 대해서

# 화살표 함수(Arrow Function)

화살표 함수는 ES5에서 등장했으며, 기존 함수 작성법을 보다 간결하게 할 수 있다.

이 외에도 몇가지 추가적인 기능이 있는데, 우선은 기초적인 작성법만 기술하고자 한다.

## 화살표 함수의 작성법

코드를 보면 기존 자바스크립트의 함수 작성법과의 차이점이 즉시 느껴질 것이다.

**기존 자바스크립트**

```javascript
let multiply = function(x, y) {
  return x * y;
}

console.log(multiply(3, 5)) // 15
```

**ES5**

```javascript
let multiply = (x, y) => x * y;

console.log(multiply(3, 5)) // 15
```

훨씬 간결하지 않은가?

그러나 화살표 함수는 익명 함수로만 사용이 가능하다.
이를 호출하고 싶다면, 함수 표현식을 사용하여 호출할 수 있다.

때문에 이해를 돕기 위해 기존 자바스크립트의 코드도 함수 표현식으로 작성했다.

화살표 함수는 인자를 하나만 받을 경우, 괄호를 생략할 수 있다.

```javascript
let pow = n => n * n;

console.log(pow(5)) // 25
```

위 코드는 아래 코드와 같은 동작을 한다.

```javascript
function pow(n) {
  return n * n;
}

console.log(pow(5)) // 25
```

### 화살표 함수 사용 시의 주의점

기본적으로 화살표 함수는 표현식이 한 줄일때 사용하기 가장 편하다.

그러나 함수의 표현식이 길어진다면, `return`을 직접 입력 해줘야한다.

예시를 보자.

```javascript
let sum = (x, y) => {
  let result = x + y;
  return result;
}

console.log(sum(1, 1)) // 2
```

함수의 본문이 두 줄 이상이면 기존 함수 작성과 동일하게 중괄호로 내용을 묶어주어야 하며, `return`을 직접 입력해줘야 한다는 점에 유의하자.

## 요약

1. 화살표 함수는 ES5에서 등장했으며, 기존의 함수 작성법을 조금 더 간결하게 해줄 수 있다.
2. 함수가 받는 인자가 하나라면 괄호는 생략 가능하지만, 두 개 이상이라면 생략이 불가능하다.
3. 함수 본문이 한 줄이라면 암묵적으로 `return`이 있는 것 처럼 동작하지만, 두 줄 이상이라면 `return` 지시자를 입력해줘야 한다.

더 자세한 내용을 배우기 위해선 `this` 등 선행지식이 있어야 한다.
추후 `this`에 대해서 포스팅 하고, 심화 내용에 대해 기술해보려 한다.

## References

> [Arrow function expressions MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)