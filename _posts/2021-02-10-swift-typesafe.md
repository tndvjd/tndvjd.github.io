---
layout: archive
classes: wide
title: "스위프트 타입 어노테이션과 타입 추론"
date: 2021-02-10 21:00:36 +0900
author_profile: true
---

스위프트 기본 문법 - 타입 어노테이션과 타입 추론에 대해서

# 타입 어노테이션과 타입 추론

Swift는 기본적으로 **타입 안전(type safe)** 프로그래밍 언어이다.

> Type Safe?
  - 변수의 데이터 타입이 식별되면 그 변수는 다른 타입의 데이터를 저장할 수 없다.
  - 변수가 선언된 후에도 다른 데이터 타입을 입력할 수 있는 느슨한 타입과 대조적임(내가 이전에 공부하던 JS가 이 타입에 속한다.)

상수와 변수의 타입을 식별하는 방법은 두가지가 있다.

1. 변수 / 상수가 선언되는 시점에 **타입 어노테이션(type annotation)**을 사용한다.
  - 변수 또는 상수 이름 다음에 타입 선언
  - Int 타입의 x라는 변수를 선언

```swift
var userCount: Int = 10 // Int가 type annotation임
```

2. 해당 상수 또는 변수에 값이 할당되는 시점에서 그 값의 타입을 확인하고 그와 같은 타입처럼 사용한다.

```swift
var signalStrength = 2.231 // 여기서 이 변수의 타입은 Double로 할당된다.(부동소수점 기본 값은 Float이 아닌 Double이다.)
let myName = "Hyperidiot" // String이 할당됨
```
- signalStrength라는 변수를 Double 타입으로 간주하고 이후에도 Double 타입의 값을 할당하면 정상적으로 사용 가능
- myName은 String으로 간주된다. 마찬가지로 이후에도 스트링 값을 넣어주면 정상적으로 사용할 수 있다.

> 변수 또는 상수의 선언 시점에서 초기값이 할당되지 않는 경우, 자료형의 명시가 필요하지만 초기값이 할당되는 경우에는 스위프트 컴파일러가 타입을 식별하기 위해서 **타입 추론(type inference)**을 한다. 따라서 위 예제코드에서 자료값을 할당하지 않았음에도 Double, String 타입이 할당된 것이다. 해당 상태에서 다른 타입의 값을 할당하려고 시도하면 오류가 발생한다.

3. 타입 추론

일반적으로 변수의 초기값이 존재하지 않는 경우에는 자료형을 명시하게 되는데(type annotation), 초기값이 존재하는 경우에는 자료형을 명시하지 않아도 스위프트 컴파일러가 자동적으로 값의 자료형을 추론하여 해당 변수에 자료형을 할당한다.

```swift
var someValue: Int // 초기값이 없기 때문에 자료형을 명시해준다.
print(someValue) // 이 상태에서는 nil을 뱉는 게 아니라 오류가 발생한다.
someValue = 10
print(someValue) // 10

var myName = "Hyperidiot"
print(myName) // Hyperidiot
print(type(of myName)) // String
// 자동으로 자료형이 할당되었다.
```



