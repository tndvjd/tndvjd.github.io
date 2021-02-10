---
layout: archive
classes: wide
title: "스위프트 Range에 대해서"
date: 2021-02-05 23:00:36 +0900
author_profile: true
---

스위프트의 특별한 자료형 Range에 대해서

스위프트를 공부하다 보니 조금 유별난 자료형을 찾았는데, 바로 range다.

일반적으로 Closed, Half-Open 등으로 나뉘는데, 여러가지 숫자를 한번에 취급할 수 있다는 점에서 튜플 등과 같이 사용했을 때 좋은 듯 하다.

```swift
let closedRange = 0...10
let halfClosedRange = 0..<10
```

이런 식으로 표현할 수 있다.

닫힌 레인지는 0에서 10까지의 수를 모두 포함하고, 반만 닫힌 레인지는 0에서 9까지의 수를 포함한다.

문자열의 count를 이용할 때나, 튜플 내의 자료를 꺼내올 때 유용하게 쓰이지 않을까 싶다.