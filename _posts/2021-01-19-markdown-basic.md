---
layout: archive
classes: wide
title: "마크다운 사용법"
toc: true
author_profile: true
---

본격적인 첫 포스팅을 위해서, 마크다운에 관해 앞서 설명하고자 한다.

---

# 마크다운에 관하여
[마크다운](https://whatismarkdown.com/)이란 텍스트 기반의 마크업 언어로, 2004년 존 그루버에 의해 만들어졌다.
마크다운의 가장 큰 특징으로는 문법이 매우 간단하며, 읽기에 편하다는 점이다. 주로 위키류의 페이지가 마크다운 방식을 채용하고 있는데, 매우 직관적인 구조이기 때문에 컨텐츠의 작성 및 인식에 있어 유리한 점이 많다는 것이다.

[GitHub](https://github.com/)을 사용하는 사람에게는 매우 친숙할 수 있는데, 깃헙의 레파지토리에 기본적인 정보를 표시해주는 README.md 파일이 바로 마크다운을 통해 작성된 문서이기 때문이다.

## 마크다운의 장점
문법이 매우 단순하고, 누구나 쉽게 익힐 수 있다.

## 마크다운의 단점
모든 HTML 문법을 대체할 수는 없다.


## 마크다운 문법
글 작성을 위해 필요한 기본적인 문법을 알아보도록 하자. 본 게시글에서는 모든 마크다운 문법을 다루지는 않고 아주 기초적인 마크다운 문법만을 다루고 있다.
나도 깃헙을 통해 마크다운을 처음 알게 되었고, 이제 막 사용하기 시작했으므로 복습 겸 남기는 의미가 크기 때문에..




### 1. 제목 Headers

`#` 으로 시작하는 텍스트. `HTML`에서 `<h1> ~ <h6>`과 동일한 역할을 수행한다.<br>
`#`의 갯수가 많아질 수록 크기가 줄어든다. **(중요도가 낮아진다)**

> <p style="font-size: 36px"> This is Heading 1. </p>
> <p style="font-size: 32px"> This is Heading 2. </p>
> <p style="font-size: 28px"> This is Heading 3. </p>
> <p style="font-size: 24px"> This is Heading 4. </p>
> <p style="font-size: 20px"> This is Heading 5. </p>
> <p style="font-size: 16px"> This is Heading 6. </p>



### 2. 강조 Emphasis

**볼드체**를 사용하거나 *이탤릭체*를 사용하여 강조를 표현할 수 있다.

| **Markdown** | **Output** |
-----|-----
| `볼드체는 **이렇게** 사용할 수 있다.` | 볼드체는 **이렇게** 사용할 수 있다. |
| `이탤릭체는 *이렇게* 사용할 수 있다.` | 이탤릭체는 *이렇게* 사용할 수 있다. | 
| `진짜 중요할땐 ***이렇게*** 써보자` | 진짜 중요할땐 ***이렇게*** 써보자 |


### 3. 인용 Blockquotes

단순히 `>` 를 입력한 후 글을 쓰면 인용문이 된다.

~~~
> 인용문을 이렇게 만들 수 있다.
~~~

> 인용문을 이렇게 만들 수 있다.



### 4. 코드 블럭 Code Blocks

`~~~` 블럭의 시작, 끝에 위 문자를 입력하여 물결표를 세개 입력하여 코드 블럭을 만들 수 있다.

~~~
코드 블럭은
이런 식으로
여러 줄로 쓸 수 있다.
~~~

코드 블럭의 타겟 언어를 지정해줄 수도 있다.

~~~html
<h1>This is HTML</h1>
<p>블럭의 시작 물결표 뒤에 프로그래밍 언어 명을 적음을 통해 syntax highlight 기능을
  사용할 수 있다.</p>
<span> ex : ~~~html
~~~


### 5. 하이퍼링크 Hyperlinks

문자에 하이퍼링크를 연결할 수 있다.

| **Markdown** | **Output** |
-----|-----
| `[구글](https://google.com)` | [구글](https://google.com) |


### 6. 이미지

| **Markdown** | **Output** |
-----|-----
| `![alt](/working_me.gif)` | ![alt](https://smilecounter.com/images/item/8.gif) |