---
layout: archive
classes: wide
title: "var 사용을 지양해야하는 까닭"
toc: true
author_profile: true
---

변수 선언을 위해 사용하는 `var`는 사용을 피하는 게 좋다. `var`의 특징을 알아보자.

---

# var

`var`는 초기 자바스크립트에서 등장했으며, `let`, `const`,와 상이한 점이 몇가지 존재한다.
구형 코드에서 `var`를 많이 볼 수 있는데, 이를 무턱대고 `let`으로 고치게 되면 코드가 엉망진창이 될 수 있다.

## 중복선언 가능

우선 가장 큰 특징으로는 **중복선언**이 가능하다는 것이다.

```javascript
var name = "Hyperidiot";
console.log(name); // Hyperidiot

var name = "Hamung";
console.log(name); // Hamung
```

분명 위에서 선언을 했음에도 불구하고 에러가 나오지 않는다.<br>
이는 유연한 변수 선언에는 도움이 될 수도 있지만, 대부분의 경우 우리를 괴롭힐 것이다.

_ex)_ 코드가 길어졌을 때, 실수로 같은 이름의 변수를 선언하면 어마어마한 에러를 내뱉을 것이다. 하지만 디버깅에는 오랜 시간이 걸릴 것이다.

## 블록 스코프의 부재

`var`는 블록 스코프가 없다. 함수 스코프거나 전역 스코프이다.
블록을 기준으로 스코프가 생기지 않기 때문에, 블록 밖에서 접근이 가능하다.

```javascript
if (true) {
  var greeting = "hello world!";
}

alert(greeting); // hello world!
```

`var`가 if문 밖에서도 동작을 하는 것을 볼 수 있다.

## var 호이스팅

[호이스팅(Hoisting)](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)이란 "끌어 올리기"라는 뜻이 있는데, 쉽게 풀어 말하면 **변수를 선언하기전에 사용할 수 있다**라는 것이다.<br> 코드를 보면 바로 이해할 수 있다.

```javascript
function greeting() {
  text = "Hello world!";

  alert(text);

  var text;
}
greeting();
```

위 코드는 다음과 같다.

```javascript
function greeting() {
  var text;

  text = "Hello world!";

  alert(text);
}
greeting();
```

이렇게 변수를 "끌어 올리는" 현상을 호이스팅이라고 부른다. `var`로 선언된 변수는 기본적으로 함수의 최상단으로 호이스팅된다.

변수는 _선언_ > _초기화_ > _할당_ 순서로 생성되는데, `var`로 선언된 변수는 선언과 초기화가 동시에 이루어진다.

**즉, 할당은 호이스팅 되지 않는다.**

```javascript
function greeting() {
  alert(text);

  var text = "Hello world!";
}
greeting();
```

이해가 되는가? `var phrase = "Hello world!"`에서는 다음과 같은 일이 벌어진다.

1. 변수 선언 + 초기화 (`var`)
2. 변수 할당 (`Hello world!`)

따라서 `alert(text)`의 값은 `undefind`가 된다.

위 코드는 아래 코드와 같은 코드처럼 동작한다.

```javascript
function greeting() {
  var text; // 선언은 호이스팅되므로 함수의 최상단으로 "끌어 올려진다."

  alert(text); // undefind, 값이 할당되지 않았음.

  text = "Hello world!";
}
greeting();
```

이렇게 `var`로 선언한 변수는 어디서든 참조 가능하지만, 실제 할당이 이루어지는 코드 행까지는 그 값이 `undefind`가 된다.

이러한 점이 혼란을 야기할 때가 종종 있기 때문에, 변수를 선언할 때엔 `let`과 `const`를 주로 사용한다.

# 요약

1. `var`로 선언한 변수는 블록 스코프를 무시한다.
2. `var`는 선언과 초기화가 함수 시작지점에서 처리된다.

**그러니 이러한 특성을 마스터하고 자유자재로 다룰 수 있는 수준이 아니라면 `var` 사용을 지양하자.**
