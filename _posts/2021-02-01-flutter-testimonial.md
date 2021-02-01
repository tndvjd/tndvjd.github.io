---
layout: single
title: "플러터 사용 후기 및 스위프트 전향"
date: 2021-02-01 23:00:36 +0900
author_profile: true
---

리액트 네이티브와 같은 선상에 서있는 크로스플랫폼 프레임워크, 플러터를 잠깐 맛보고 스위프트로 전향하게 된 일기

당초 내가 개발을 시작한 목적은 앱 개발이었고, 프로그래밍 전반적인 지식이 전무한 상태에서 시작 언어로 많이 추천들 하는게 JS더라.

자바스크립트는 기본적으로 웹 브라우저에서 구동되는 프로그래밍 언어이고, 자연스레 웹 공부를 하게 됐었는데, 결과물이 조금씩 나올 때마다 뿌듯함도 있었으나,

빨리 앱 개발을 해보고 싶다는 생각이 조금씩 강해졌다. 

그래서 RN이라는 프레임워크를 알게 되고 깔짝대봤다.

RN은 아무래도 JS 기반이다 보니 이해하기 조금 수월했고, 이런 크로스플랫폼 프레임워크를 찾다 보니 비슷한 성격을 가지고 있는게 플러터라는 사실을 알게 됐다.

플러터와 RN의 비교분석을 보다 보니, RN은 자바스크립트 브리지라는걸 이용해서 화면을 그리지만, 플러터는 C계열로 컴파일하여 안정적 네이티브 성능을 낸다는 차이점이 있었다.

무엇보다 킹 구글에서 밀어준다는 프레임워크라는게...

성능상의 우위가 있다고 하니, 내가 만들 앱이 헤비한 앱이 아니더라도 추후를 위해 한번쯤 맛봐볼까 하고 시작했던 게 계기.

근데 이틀정도 공부해보고 바로 포기했다.

이 코드를 보라..

```dart
     body: Padding(
        padding: EdgeInsets.fromLTRB(30, 40.0, 0.0, 0.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Center(
              child: CircleAvatar(
                backgroundImage: AssetImage('assets/bio-pic.jpg'),
                radius: 80,
              ),
            ),
            Divider(
              height: 60,
              color: Colors.grey[850],
              thickness: 0.5,
              endIndent: 30,
            ),
            Text(
              'NAME',
              style: TextStyle(
                color: Colors.white,
                letterSpacing: 2.0,
              ),
            ),
            SizedBox(
              height: 10.0,
            ),
            Text(
              'HYPERIDIOT',
              style: TextStyle(
                  color: Colors.white,
                  letterSpacing: 2.0,
                  fontSize: 28.0,
                  fontWeight: FontWeight.bold),
            ),
            SizedBox(
              height: 30.0,
            ),
            Text(
              'YOUR SKILL LEVEL',
              style: TextStyle(
                color: Colors.white,
                letterSpacing: 2.0,
              ),
            ),
            SizedBox(
              height: 10.0,
            ),
            Text(
              'BEGINNER',
              style: TextStyle(
                  color: Colors.white,
                  letterSpacing: 2.0,
                  fontSize: 28.0,
                  fontWeight: FontWeight.bold),
            ),
            SizedBox(
              height: 30.0,
            ),
            Row(
              children: <Widget>[
                Icon(Icons.check_circle_outline),
                SizedBox(width: 10.0),
                Text(
                  'Learning OOP',
                  style: TextStyle(fontSize: 16, letterSpacing: 1.0),
                ),
              ],
            ),
            Row(
              children: <Widget>[
                Icon(Icons.check_circle_outline),
                SizedBox(width: 10.0),
                Text(
                  'Passion',
                  style: TextStyle(fontSize: 16, letterSpacing: 1.0),
                ),
              ],
            ),
            Row(
              children: <Widget>[
                Icon(Icons.check_circle_outline),
                SizedBox(width: 10.0),
                Text(
                  'Creativity',
                  style: TextStyle(fontSize: 16, letterSpacing: 1.0),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}
```

HTML 태그를 작성하고, 인라인 스타일로 스타일링을 하는 느낌을 강하게 받았는데, 
텍스트 한줄 입력하기 위해 들여야 하는 노력이 너무 컸다고 느껴졌다.
RN이 오히려 스타일링과 요소부분을 구별 가능해서 낫다고 생각이 들 정도였다.

아.. RN도 그렇고, 플러터도 그렇고, 앱 개발은 이런 플로우로 개발을 하는건가? 라는 생각이 문득 들었고, RN할 때 깔아둔 안드로이드 스튜디오, 그리고 엑스코드는 어떤 식으로 화면을 그리는 지 궁금했다.

근데 찾아보니까 신세계더라.

역시 풀네이티브라 그런지, 화면을 그리는 것에 대해서는 훨씬 직관적이게 되어 있었다.

다만 안스나 엑스코드를 고른다는 건, 택일을 해야한다는 의미였다. 살짝 망설였으나, 내 안에서 답을 찾았고 스위프트를 선택하게 됐다.

내가 안드로이드 개발을 할지 iOS 개발을 할지의 기로에서 iOS를 선택한 이유는 간단했다.

내가 앱등이니까. 난 내가 쓰고싶다고 느낄 만한 앱을 우선 만들어 보고 싶으니까.

이렇게 스위프트를 골랐으니 공부를 해야하는데,

세상에, 프로그래밍 처음 배울때랑 다른 게 없다. 아주 일부의 개념만 이해되고, Optional이라는 스위프트 고유의 개념을 포함하여 거의 대부분을 다 처음 배워야 했다.

심지어 안드로이드처럼 이용 풀이 넓은게 아니라 자료도 비교적 부족한 느낌적인 느낌? ㅜㅜ 

심지어 잘 정리된 건 영문이 많은데, 웹은 워낙 방대해서 국문으로 된 양질의 자료가 매우 많았으나...

스위프트의 경우는 버전이 바뀌면서 거의 대격변이라고 할 정도의 변화가 있었던 것 같은데, 국내강의 대부분 자료가 Outdated된 상태였다(스위프트 2 기준이라던지)

최근 자료는 대부분 영문이었다. ㅠㅠ 사실 영어 레퍼런스를 많이 봐야한다는 생각이 들면서도, 뭔가 문제에 직면했을 때 스택오버플로에 나온 글만 읽었으니 크게 영어실력 향상은 없던 듯 한데..

이번 기회에 영어도 같이 공부할 겸 개발 영어랑 좀 친해져봐야겠다.

