---
layout: archive
title: "스위프트 Nil Coalescing(Nil 병합)"
date: 2021-02-14 17:00:36 +0900
author_profile: true
classes: wide
---

스위프트 연산자 중 하나인 Nil Coalescing Operator에 대해서

옵셔널은 스위프트 언어에서 굉장히 중요한 역할을 담당한다.<br>
`nil` 이라는 특수한 값을 저장할 수 있게 하기 때문인데, 이러한 특성 때문에 Optional 변수/상수는 그 자체로는 활용이 제한적이다.(값이 없을 수도 있기 때문에)<br>
그렇기 때문에 우리는 옵셔널을 활용하기 전에 가공하는 절차를 통해 옵셔널을 일반 밸류로 변경시킨 후에 사용하게 되는데, 이전에도 서술했지만 그 방법은 여러가지가 있다.
- 옵셔널 바인딩
- 강제 언래핑
- if != nil을 사용한 방법

오늘은 상술 내용에 추가적으로 Nil Coalescing Operator를 활용하여 옵셔널 값을 가공할 수 있는 방법에 대해서 포스팅을 하려고 한다.

## Nil Coalescing Operator ( Nil 합병/병합 연산자 )

Nil Coalescing Operator란, 옵셔널 변수/상수에 대해서 값이 `nil`인지 확인 후에 참이라면 미리 정해둔 값을 할당시키는 연산자다.<br>

`A ?? B`의 형태로 사용하며, 여기서 A가 옵셔널, B는 A가 nil일 때 할당되는 값이 되겠다.<br>
예시를 통해서 살펴보면 이러한 형태이다.

```swift
let defaultValue: Int = 1 // 1

var someOptionalInt: Int? // nil

var myNum = someOptionalInt ?? defaultValue // 1
/*
myNum 변수에 someOptionalInt 옵셔널을 할당하려고 시도한다.
하지만 현재 someOptionalInt는 초기화가 이루어지지 않았기 때문에 nil이다.
그렇기 때문에, defaultValue가 할당되어 myNum은 1이 된다.
*/

someOptionalInt = 3 // Optional(3)

var myNum2 = someOptionalInt ?? defaultValue // 3
/*
myNum2 변수에 someOptionalInt 옵셔널을 할당하려고 시도한다.
현재 someOptionalInt의 값은 Optional(3)이므로 nil이 아니다. 
따라서 myNum2에는 someOptionalInt의 값이 할당되는데,
이 때 Optional이 일반 값으로 가공된다. 
따라서 myNum2의 값은 3이 된다.
*/
```

nil 병합연산자의 특이한 점은, 옵셔널 값이 nil이 아니라면, 해당 옵셔널 값을 일반 값으로 가공시켜주는 것에 있다.<br>
따라서 사용하기가 매우 편리하고, 안전성도 보장된다.(기본값을 할당하기 때문에)<br><br>

이러한 점 때문에 상당히 자주 쓰이는 연산자다. 꼭 기억해두자.