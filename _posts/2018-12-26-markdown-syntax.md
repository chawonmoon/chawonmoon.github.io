---
layout: post
title: "markdown-syntax"
date: 2018-12-26
image: '/assets/img/'
description: '마크다운(MarkDown) 문법(syntax) 정리'
tags:
- markdown
- syntax
categories:
- Blog
---

## 제목(Header)
* **`h1 ~ h6`** 태그
* **`h1`, `h2`** 태그는 두가지 방식으로 표현됨

#### 코드
```ruby
# h1
h1
==
## h2
h2
--
### h3
#### h4
##### h5
###### h6
```

#### 실제화면
# h1 (#)
## h2 (##)
### h3 (###)
#### h4 (####)
##### h5 (#####)
###### h6 (######)

## 강조(Emphasis) 
* **`<em>`, `<strong>`, `<del>`** 태그
* 밑줄 표현은 **`<u></u>`** 태그

#### 코드
```markdown
이텔릭체는 *별표(asterisks)* 혹은 _언더바(underscore)_를 사용하세요.
두껍게는 **별표(asterisks)** 혹은 __언더바(underscore)__를 사용하세요.
**_이텔릭체_와 두껍게**를 같이 사용할 수 있습니다.
취소선은 ~~물결표시(tilde)~~를 사용하세요.
<u>밑줄</u>은 `<u></u>`를 사용하세요.
```
#### 실제화면
이텔릭체는 *별표(asterisks)* 혹은 _언더바(underscore)_를 사용하세요.  
두껍게는 **별표(asterisks)** 혹은 __언더바(underscore)__를 사용하세요.  
**_이텔릭체_와 두껍게**를 같이 사용할 수 있습니다.  
취소선은 ~~물결표시(tilde)~~를 사용하세요.  
<u>밑줄</u>은 `<u></u>`를 사용하세요.  

## 목록(List) 
* **`<ol>`, `<ul>`, `<li>`** 태그

#### 코드
```markdown
1. 순서가 필요한 목록
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브) 
  - 순서가 필요하지 않은 목록(서브) 
1. 순서가 필요한 목록
  1. 순서가 필요한 목록(서브)
  1. 순서가 필요한 목록(서브)
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록에 사용 가능한 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)
```
#### 실제화면
1. 순서가 필요한 목록
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브) 
  - 순서가 필요하지 않은 목록(서브) 
1. 순서가 필요한 목록
  1. 순서가 필요한 목록(서브)
  1. 순서가 필요한 목록(서브)
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록에 사용 가능한 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)

## 이미지(Images) 
* **`<img>`** 태그

#### 코드
```markdown
![alt값(대체 텍스트)을 입력하세요.](https://via.placeholder.com/400x100 "링크 설명(title)을 입력하세요.")

![alt][dummy]

[dummy]: https://via.placeholder.com/400 "It's dummy images."
```
#### 실제화면
![alt값(대체 텍스트)을 입력하세요.](https://via.placeholder.com/400x100 "링크 설명(title)을 입력하세요.")

![alt][dummy]

[dummy]: https://via.placeholder.com/400 "It's dummy images."

## 링크(Links) 
* **`<a>`** 태그

#### 코드
```markdown
[GOOGLE](https://google.com)

[새창](https://google.com){: target="_blank" }

[NAVER](https://naver.com "링크 설명(title)을 작성하세요.")

[상대적 참조](../users/login)

[Dribbble][Dribbble link]

[GitHub][1]

문서 안에서 [참조 링크]를 그대로 사용할 수도 있습니다.

다음과 같이 문서 내 일반 URL이나 꺾쇠 괄호(`< >`, Angle Brackets)안의 URL은 자동으로 링크를 사용합니다.
구글 홈페이지: https://google.com
네이버 홈페이지: <https://naver.com>

[Dribbble link]: https://dribbble.com
[1]: https://github.com
[참조 링크]: https://naver.com "네이버로 이동합니다!"

[새창](https://google.com){: .btn.btn-default target="_blank" }
`{: 속성}` 를 뒤에 붙여 클래스나 id 원하는 테그에 원하는 속성이 추가 가능 
```
#### 실제화면
[GOOGLE](https://google.com)

[새창](https://google.com){: target="_blank" }

[NAVER](https://naver.com "링크 설명(title)을 작성하세요.")

[상대적 참조](../users/login)

[Dribbble][Dribbble link]

[GitHub][1]

문서 안에서 [참조 링크]를 그대로 사용할 수도 있습니다.  
다음과 같이 문서 내 일반 URL이나 꺾쇠 괄호(`< >`, Angle Brackets)안의 URL은 자동으로 링크를 사용합니다.  
구글 홈페이지: https://google.com  
네이버 홈페이지: <https://naver.com>

[Dribbble link]: https://dribbble.com
[1]: https://github.com
[참조 링크]: https://naver.com "네이버로 이동합니다!"

[새창/Class추가](https://google.com){: .btn.btn-default target="_blank" }  
`{: attr}` 를 뒤에 붙여 Class나 Id등 원하는 태그에 원하는 속성을 추가 가능 

## 이미지+링크(Images+Links) 
* 마크다운 이미지에 링크 걸기

#### 코드
```markdown
[![dummy](https://via.placeholder.com/200)](https://github.com/cchamang/markdown-template)
```
#### 실제화면
[![dummy](https://via.placeholder.com/200)](https://github.com/cchamang/markdown-template)

## 코드(Code) 강조  
* **`<pre>`**, **`<code>`** 태그

### 인라인(inline) 코드 강조
```markdown
`background`혹은 `background-image` 속성으로 요소에 배경 이미지를 삽입할 수 있습니다.
```

### 블록(block) 코드 강조
* `` 뒤에 각 언어의 명칭을 붙인다.  
`markdown` / `html` / `css` / `javascript` / `bash` / `python`

#### 코드
````markdown
```markdown
마크다운 블록(block) 코드 강조
```

```html
<!-- html -->
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```

```css
/* css */
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
// javascript
function foo() {
  var a = 'foo';
  return a;
}
```

```bash
# bash
$ vim ./~zshrc
```

```python
# python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```
````

#### 실제화면

```markdown
마크다운 블록(block) 코드 강조
```

```html
<!-- html -->
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```

```css
/* css */
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
// javascript
function foo() {
  var a = 'AAA';
  return a;
}
```

```bash
# bash
$ vim ./~zshrc
```

```python
# python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```

## 표(Table)  
* `<table>` 태그
* 헤더 셀을 구분할 때 3개 이상의 `-`(hyphen/dash) 기호가 필요  
* 헤더 셀을 구분하면서 `:`(Colons) 기호로 셀(열/칸) 안에 내용을 정렬  
* 가장 좌측과 가장 우측에 있는 `|`(vertical bar) 기호는 생략 가능

#### 코드
```markdown
| 값 | 의미 | 기본값 |
|---|:---:|---:|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |

값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |
```
#### 실제화면

값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |

## 인용문(BlockQuote)  
* `<blockquote>` 태그

#### 코드
```markdown
인용문(blockQuote)

> 남의 말이나 글에서 직접 또는 간접으로 따온 문장.
> _(네이버 국어 사전)_

BREAK!

> 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.
>>> 중중첩된 인용문 1  
>>> 중중첩된 인용문 2  
>>> 중중첩된 인용문 3  
```
#### 실제화면
인용문(blockQuote)

> 남의 말이나 글에서 직접 또는 간접으로 따온 문장.
> _(네이버 국어 사전)_

BREAK!

> 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.
>>> 중중첩된 인용문 1  
>>> 중중첩된 인용문 2  
>>> 중중첩된 인용문 3

## HTML  
* 일반 HTML 문법을 사용할수 있음  
* 마크다운에서 지원하지 않는 기능이 필요할때 사용

#### 코드
```markdown
<u>마크다운에서 지원하지 않는 기능</u>을 사용할 때 유용하며 대부분 잘 동작합니다.

<img width="100" src="https://via.placeholder.com/100" alt="dummy" title="100x100 dummy image">

![dummy](https://via.placeholder.com/400)
```
#### 실제화면
<u>마크다운에서 지원하지 않는 기능</u>을 사용할 때 유용하며 대부분 잘 동작합니다.

<img width="100" src="https://via.placeholder.com/100" alt="dummy" title="100x100 dummy image">

![dummy](https://via.placeholder.com/400)

## 수평선(Horizontal Rule)
* 수평/구분선 긋기

#### 코드
```markdown

---
(Hyphens)

***
(Asterisks)

___
(Underscores)
```

#### 실제화면

---
(Hyphens)

***
(Asterisks)

___
(Underscores)

## 줄바꿈(Line Breaks)  
#### 코드
```markdown
동해물과 백두산이 마르고 닳도록 
하느님이 보우하사 우리나라 만세   <!--띄어쓰기 2번-->
무궁화 삼천리 화려 강산<br>   <!--br태그도 사용가능--> 
대한 사람 대한으로 길이 보전하세
```

#### 실제화면
동해물과 백두산이 마르고 닳도록 
하느님이 보우하사 우리나라 만세   <!--띄어쓰기 2번-->   
무궁화 삼천리 화려 강산<br>
대한 사람 대한으로 길이 보전하세

## Repositories
[https://github.com/chawonmoon/markdown-template.git](https://github.com/chawonmoon/markdown-template.git){: target="_blank" }

## I Think...
문서화를 진행하거나 정리가 필요할때 개발자로서 확실히 이보다 좋은 문서 작성 포멧은 없을것같다  
PDF로 변환도 가능하다고 하던데 그 부분도 확인해봐야할 부분이다