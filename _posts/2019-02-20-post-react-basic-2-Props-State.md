---
layout: post
title: "React Basic #2 - Props/State"
date: 2019-02-20
image: '/assets/img/'
description: 'VELOPERT님의 React 동영상 강좌와 블로그로 스터디를 하며 개인적으로 정리한 포스트'
tags:
- react
- Props
- State
- VELOPERT
categories:
- Blog
---

# React Basic #2  
> 정리 내용들은 [VELOPERT.LOG](https://velopert.com/reactjs-tutorials) 님의 동영상 강좌와 블로그 강좌를 기반으로 스터디를 하며 정리한 내용 입니다.  

## Props / State

### Props
```javascript
// src/MyName.js
import React, { Component } from 'react';

class MyName extends Component {
  render() {
    return (
      <div>
        안녕하세요! 제 이름은 <b>{this.props.name}</b> 입니다.
      </div>
    );
  }
}

export default MyName;


// src/App.js
import React, { Component } from 'react';
import MyName from './MyName';

class App extends Component {
  render() {
    return (
      <MyName name="리액트" />
    );
  }
}

export default App;
```
* MyName(자식컴포넌트)에서는 자신이 받아온 Props값을 `this.props`키워드를 통해 조회 할 수 있다.
* App(부모컴포넌트)에서 MyName(자식컴포넌트)을 불러와 랜더링을 해줄때 Props값을 전달해준다.
* 전달방식은 웹퍼블리싱 작업을 위해 마크업할때 속성(Attribute)을 지정해주듯이 `name="리액트"` 라고 Props값을 전달한다. 

### defaultProps
```javascript
// src/MyName.js
import React, { Component } from 'react';

class MyName extends Component {
  static defaultProps = {
    name: '기본이름'
  }
  render() {
    return (
      <div>
        안녕하세요! 제 이름은 <b>{this.props.name}</b> 입니다.
      </div>
    );
  }
}

export default MyName;


// src/App.js
import React, { Component } from 'react';
import MyName from './MyName';

class App extends Component {
  render() {
    return (
      <MyName />
    );
  }
}

export default App;
```
* 작업중의 실수 혹은 프로세스 진행상 Props값을 빠뜨리거나 빼야할때 기본적으로 자식 컴포넌트에 기본값을 설정해주는 방법이다.
* `defaultProps = {name:'기본이름'}`으로 자식 컴포넌트에 설정 한다.
* 당연히 App(부모컴포넌트)에서 전달해주는 값이 없더라도 MyName(자식컴포넌트)에서는 자신이 설정한 기본 props값을 `this.props`키워드를 통해 조회 할 수 있다.
  
> 추가로 함수형 컴포넌트 작성방식도 있는데 차이점은 `state` 와 `LifeCycle`이 빠져있다는 점이다.  
> 컴포넌트 초기 마운트가 아주 미세하게 빠르고, 메모리 자원을 미미하게 덜 사용한다.

```javascript
// src/MyName.js 파일을 함수형 컴포넌트로 작성한 예제
import React from 'react';

const MyName = ({ name }) => {
  return (
    <div>
      안녕하세요! 제 이름은 {name} 입니다.
    </div>
  );
};

export default MyName;
```

### State

```javascript
// State 기본 예제
import React, { Component } from 'react';

class Counter extends Component {
  state = {
    number: 0
  }

  handleIncrease = () => {
    this.setState({
      number: this.state.number + 1
    });
  }

  handleDecrease = () => {
    this.setState({
      number: this.state.number - 1
    });
  }

  render() {
    return (
      <div>
        <h1>카운터</h1>
        <div>값: {this.state.number}</div>
        <button onClick={this.handleIncrease}>+</button>
        <button onClick={this.handleDecrease}>-</button>
      </div>
    );
  }
}

export default Counter;
```

#### State 정의
* State 정의는 `class fields` 문법으로 정의하는 방식과, `constructor`를 작성하여 정의 해주는 두가지방식이 있다.
* 두종류를 한꺼번에 정의 할수도 있는데 이때의 실행 순서는 `class fields` 문법으로 정의하는 방식이 더 우선시 된다. (딱 봐도 그냥 `class fields`로 정의하는게 쉬워보인다.)

```javascript
// class fields 정의
import React, { Component } from 'react';

class Counter extends Component {
  state = {
    number: 0
  }
 ...  
}


// constructor 정의
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      number: 0
    }
  }
  ...
}
```

#### setState
* 리액트의 설계상 `setState`가 호출되면 리액트 내부에서 자체적으로 변경된 부분을 찾아 리렌더링 되도록 설계되어있기 때문에, state에 있는 값을 바꾸기 위해선 꼭 `setState`는 메서드를 사용해야 한다.
* 객체로 전달되는 값만 업데이트를 해준다.
* 복잡한 구조의 객체중 일부값만을 업데이트 해야할 때는 [`...`전개연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_operator)를 사용한다.

```javascript
this.setState({
  number: 0,
  foo: {
    ...this.state.foo, // 전개연산자(...) 사용
    foobar: 2
  }
});
```

#### setState에 함수를 이용한 값 업데이트
* 기존의 값을 참고하여 값을 업데이트 하거나 업데이트를 하기전 값을 가공해야할 경우 함수를 이용해 업데이트를 할 수 있다.

```javascript
handleIncrease = () => {
    const { number } = this.state;
    this.setState({
        number: number + 1
    });
}

handleDecrease = () => {
    this.setState(
        ({ number }) => ({
            number: number - 1
        })
    );
}
```
&nbsp;
> [VELOPERT님의 "누구든지 하는 리액트 4편: props 와 state"](https://velopert.com/3629) 참조

&nbsp;
## I think...
* 프론트엔드 프레임웍들(`Angular/React/Vue`)은 [비구조화 할당](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)과 [전개연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_operator)가 필수요소로 자리 잡은것 같다...
* 막연히 스터디를 진행하다보니 [ES6](https://jsdev.kr/t/es6/2944)문법에 대해서 내가 잘못 이해하고 있는 부분들이 있는것 같았다, 다시 한번 봐야겠다...

## TODO
* LifeCycle API로 넘어가기 전 이벤트 설정에 대해서 조금 파볼까 한다, 아무래도 이 부분은 인터렉션관련해서 필수요소니까 