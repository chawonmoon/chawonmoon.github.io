---
layout: post
title: "React Basic #1 - JSX"
date: 2019-02-14
image: '/assets/img/'
description: 'VELOPERT님의 React 동영상 강좌와 블로그로 스터디를 하며 개인적으로 정리한 포스트'
tags:
- react
- JSX
- VELOPERT
categories:
- Blog
---

# React Basic #1  
> 정리 내용들은 [VELOPERT.LOG](https://velopert.com/reactjs-tutorials) 님의 동영상 강좌와 블로그 강좌를 기반으로 스터디를 하며 정리한 내용 입니다.  

## JSX

### 작성 기본 규칙
```javascript
// src/App.js
import React, { Component, Fragment } from 'react';

class App extends Component {
  render() {
    return (
        <fragment>        
            <div>
                '...내용1'<br/>
                '...내용2'
            </div>
            <div>
                '...내용3'
            </div>
        </fragment>
    );
  }
}

export default App;
```
* 태그는 꼭 닫혀있어야 한다
* 두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸져 있어야 한다.
* 16.2버전부터 `<Fragment />`의 추가로 불필요한 Wrap엘리먼트를 더 추가하지 않아도 된다. 

### 조건부 렌더링
```javascript
import React, { Component, Fragment } from 'react';

class App extends Component {
  render() {
    return (
        {/* 삼항연산자일 경우 */}
        <div> { 1 + 1 === 2 ? (<div>맞아요!</div>) : (<div>틀려요!</div>) } </div>
        
        {/* 삼항연산자 단순 AND연산일 경우 */}
        <div> { 1 + 1 === 2 && (<div>맞아요!</div>) } </div>
        
        {/* 복잡한 조건식으로 길게 작성해야할 경우 IIFE 사용(화살표 함수로 사용하는것이 좋음)  */}
        <div>
        {
          (() => {
            if (value === 1) return (<div>하나</div>);
            if (value === 2) return (<div>둘</div>);
            if (value === 3) return (<div>셋</div>);
          })()
        }
        </div>
    );
  }
}

export default App;
```
> [IIFE](https://developer.mozilla.org/ko/docs/Glossary/IIFE)  
> 즉시 실행 함수 표현

> [화살표 함수란?](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/%EC%95%A0%EB%A1%9C%EC%9A%B0_%ED%8E%91%EC%85%98)   
> this, arguments, super 개념이 없는 익명 함수, ES6의 새로운 함수 표현식

### Style 과 ClassName

#### 인라인 스타일
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    const style = {
      backgroundColor: 'black',
      padding: '16px',
      color: 'white',
      fontSize: '12px'
    };

    return (
      <div style={style}>
        hi there
      </div>
    );
  }
}

export default App;
```

#### 외부 스타일
```css
.App {
  background: black;
  color: aqua;
  font-size: 36px;
  padding: 1rem;
  font-weight: 600;
}
```

```javascript
import React, { Component, Fragment } from 'react';
import './App.css' // import 구문으로 css를 불러옴

class App extends Component {
  render() {
    return (
      <div className="App">
        리액트
      </div>
    );
  }
}

export default App;
```

#### 주석
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    return (
      <div>
        {/* 주석은 이렇게 */}
        <h1
          // 태그 사이에
        >리액트</h1>
      </div>
    );
  }
}

export default App;
```
&nbsp;
> [VELOPERT님의 "누구든지 하는 리액트 3편: JSX"](https://velopert.com/3626) 참조

&nbsp;
## I think...
* 인라인 스타일을 넣는 방식은 그냥 지금도 쓰지 않는데, 앞으로 쓸일이 있을까 싶다
* 이놈의 [ES6](https://jsdev.kr/t/es6/2944)...

## TODO
* 컴포넌트에 전달해주는 값인 props 와, 컴포넌트 내부적으로 들고있는 값인 state 알아보기