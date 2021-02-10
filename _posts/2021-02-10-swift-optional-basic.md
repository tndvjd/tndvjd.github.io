---
layout: archive
title: "스위프트 타입 옵셔널 기초 개념"
date: 2021-02-10 22:00:36 +0900
author_profile: true
classes: wide
---

스위프트 기본 문법 - 옵셔널에 대해서(기초개념)

## 옵셔널(Optional)

옵셔널은 스위프트 입문자에게 충공깽을 선물하며 나가떨어지게 해주는 문지기다. 나도 그렇다. 그래서 공부한 내용을 정리를 좀 해보고자 글을 쓴다.<br>

굉장히 생소한 개념이고 이해도 잘 안된다. 양자역학마냥 값이 있을 수도 있고, 없을 수도 있다라는 것을 표기할 때 나타낸다. 슈뢰딩거의 고양이냐?<br>

하지만 스위프트에서 매우 중요한 역할을 담당하므로 정상적으로 코드 작성을 하기 위해서는 꼭 넘어야 하는 산임은 분명하다.

---

- 옵셔널은 타입 어노테이션 시, 기본 자료형(Character, String, Int, Float, Double, etc..) 뒤에 ?나 !를 붙여서 표기할 수 있다.

```swift
print(10) // Int
print(Optional(10)) // Int? <<< 얘가 옵셔널

var someInt: Int = 10// Int
var someOptionalInt: Int? = 10// Int?

print(someInt) // 10
print(someOptionalInt) // Optional(10)
```

각 값을 콘솔에 찍어보면 옵셔널은 값에 옵셔널임을 명시하고 괄호 안에 값이 출력됨을 알 수 있다.<br>
옵셔널은 일반적인 형태로 변환해주지 않으면 멀쩡하게 사용할 수가 없다.

```swift
var myNumber: Int? = 10
print(myNumber - 5) 
//  error: value of optional type 'Int?' must be unwrapped to a value of type 'Int'
```

옵셔널의 가장 큰 특징은 값이 있을 수도 있고, 없을 수도 있다는 것이다.
- 옵셔널이 아닌 기본 자료형은 nil 값을 가질 수 없다.
선언만 이루어지고 초기값이 주어지지 않은 상태에서 각 변수를 호출하면 그 차이를 쉽게 알 수 있다.

```swift
var myNumber: Int
print(myNumber) // Error, initialize 되지 않았음

var myOptionalNumber: Int?
print(myOptionalNumber) // nil
```

마찬가지로, 옵셔널이 아닌 변수에 nil을 할당하려고 시도해도 오류가 발생한다. 하지만 옵셔널 값은 nil을 할당할 수 있다.(값이 없을 수 있기 때문에)

```swift
var myNumber: Int = 10
myNumber = nil // 'nil' cannot be assigned to type 'Int'

var myOptionalNumber: Int? = 10
myOptionalNumber = nil // nil
```

- 옵셔널은 값이 반환될 때 오류가 발생할 가능성이 있는 경우에 사용된다.
예를 들어서 String 타입의 값을 Int형으로 새로 생성할 때의 코드를 보자.

```swift
var stringNumToInt = Int("100") // Optional(100)
var stringStrToInt = Int("Hi") // nil
```

여기서 `Int()`의 타입을 확인해보면 옵셔널이다. 왜 그럴까?<br>
`Int("Hi")`의 출력 값을 보면 알겠지만, 정수로 반환될 수 없는 값이 들어올 수 있는 가능성을 내포하고 있기 때문이다.

## 옵셔널의 용도

- 옵셔널 타입은 변수/상수에 아무런 값이 할당되지 않는 상황을 안전하게 처리하기 위한 방법을 제공한다.

## 옵셔널 값을 일반형태로 변환시키기

- 옵셔널 변수에 값이 있으면 옵셔널로 래핑되었다(Wrapped)고 표현한다.
- 옵셔널에 래핑된 값은 몇가지 방법을 통하여 언래핑할 수 있다.

### 강제 언래핑(Forced Unwrapping)

강제 언래핑은 옵셔널 값에 !를 붙이면 된다. 매우 간단하다.

```swift
var x : Int? // 옵셔널 정수형 변수 x 선언
var y : Int = 0

x = 10 // Optional(10)
print(x) // Optional(10)
print(x!) // 10 
// !을 붙임으로 forced unwrapping이 이루어졌다.(일반 자료형으로 가공됨)
print(y) // 0
```

그러나 치명적인 단점이 있다.<br>
값이 nil인 변수를 강제 언래핑하게 되면, Fatal error를 던지며 프로그램은 죽어버린다.

```swift
var x : Int? // 옵셔널 정수형 변수 x 선언
// 초기화가 되지 않았으므로 값은 nil이다.

print(x) // nil
print(x!) // 으악! 값이 없어서 벗길 수가 없어요.
// Fatal error
```

따라서 주로 조건문을 활용하여 해당 변수의 값이 nil이 아닌지 확인 후에 강제 언래핑을 하는 경우가 많다.

```swift
var myOptionalInt: Int? // nil

if myOptionalInt != nil {
  print(myOptionalInt!)
} else {
  print(myOptionalInt)
}
// ---> nil

var myName: String? = "Hyperidiot" // Optional("Hyperidiot")

if myName != nil {
  print(myName!)
} else {
  print(myName)
}
// ---> "Hyperidiot"
```

### 옵셔널 바인딩(Optional Binding)

옵셔널 바인딩이란, 옵셔널이 할당된 값을 임시 변수 또는 상수에 할당하여 옵셔널을 언래핑하는 방법이다.<br>
강제 언래핑보다 안전하고, 옵셔널을 벗기는 가장 보편적인 방법이다. 단 처음에 볼때는 이해가 잘 안될 수 있다.

```swift
if let someConst = optionalName {
  // 옵셔널 변수가 값이 있다면 if문의 조건은 true가 됨. 
  // optionalName의 옵셔널을 언래핑하여 일반 상수 someConst에 대입시키고 if문을 실행시킨다.

  // 만약 값이 nil이라면 if문의 조건은 false가 되고 조건문은 실행되지 않는다.
}
```

if let 구문 자체는 이렇게 해석하면 되겠다.

```swift
if optionalName != nil {
  someConst = optionalName!
  // someConst에 optionalName이 할당된 이후에 if let 본체 코드가 실행된다.
  // *주의* optionalName은 여전히 optional이다. 가공된 값은 someConst에 할당된다.
} else {
  return
}
```

실제 실행 시에는 이런 모습이다.

```swift

var x: Int? = 10 // Optional(10)

if let unwrappedX = x {
  print(unwrappedX) // 10
} else {
  print(x) 
}
// ---> 10이 출력된다.

var y: Int? // nil

if let unwrappedY = y {
  print(unwrappedY)
} else {
  print(y) // nil
}
// ---> nil이 출력된다.

```

#### 여러 옵셔널을 동시에 언래핑하기

여러 옵셔널 변수를 콤마를 통해 동시에 언래핑할 수 있다.

```swift

var person1: String?
var person2: String?

person1 = "Chulsu"
person2 = "Minsu"

if let firstPerson = person1, let secondPerson = person2 {
  print("\(firstPerson) : Hello \(secondPerson)!")
} else {
  print("nil")
}

// ---> Chulsu : Hello Minsu!

```

단, 하나라도 nil값이 포함되어 있으면 if문의 조건은 false가 된다.

```swift

var person1: String?
var person2: String?

person1 = "Chulsu"
person2 = nil

if let firstPerson = person1, let secondPerson = person2 {
  print("\(firstPerson) : Hello \(secondPerson)!")
} else {
  print("nil")
}

// ---> nil

```

## 암묵적 언래핑(Implicitly Unwrapping)

옵셔널이 항상 유효한 값을 가질 경우(절대 nil이 될 일이 없는 경우)에는 옵셔널이 암묵적으로 언래핑을 하게끔 선언할 수도 있다.<br>
클래스의 아웃렛 변수 초기화에서 많이 사용된다.(자동 생성되는 코드)

이러한 방법으로 옵셔널이 선언된다면 강제 언래핑이나 옵셔널 바인딩을 하지 않아도 값에 접근할 수 있다.

암묵적 언래핑으로 옵셔널을 선언하기 위해선 선언부에 물음표 대신 느낌표를 사용하면 된다.

```swift

var x: Int? // 옵셔널 변수 선언방법 1. 이 경우 옵셔널을 벗겨줘야 함
var y: Int! // 옵셔널 변수 선언방법 2. 암묵적 언래핑이 된다.

```

위에서 말했지만 옵셔널 변수의 값이 nil일 때, 강제 언래핑을 시도하면 Fatal error를 던지며 프로그램이 죽어버린다.
따라서 절대로 nil이 들어갈 일이 없는 변수에만 암묵적 언래핑을 활용하도록 하는게 좋겠다.

다음 코드를 보면 암묵적 언래핑이 어떤 식으로 이뤄지는지 알 수 있다.

```swift

var a: Int! = 1
var b: Int = a // type annotation이 Optional이 아니기 때문에 암묵적으로 언래핑이 된다.
var c: Int = a!
var d = a // type annotation이 없다. 이 경우 a의 자료형을 가져오므로 d는 옵셔널이다.
var e = a + 1 
// 원래 옵셔널과 일반자료형은 연산이 불가능하지만 이 경우 암묵적 언래핑을 수행하여 연산된다.

print(a,b,c,d,e)
// ---> Optional(1) 1 1 Optional(1) 2

```

