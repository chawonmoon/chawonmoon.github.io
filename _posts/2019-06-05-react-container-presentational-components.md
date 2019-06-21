---
layout: post
title: "Container x Presentational Components"
date: 2019-06-01
image: '/assets/img/'
description: '대표적인 React 컴포넌트 디자인패턴'
tags:
- React
- Code
- Lifecycle
- Container
- Presentational
- Components
categories:
- Code
---
## Container x Presentational Components
&nbsp;

### 소개
이 패턴은 댄 아브라모프(Dan Abramov)가 Smart & Dumb 컴포넌트란 이름으로 사용하였다. 후에 더욱 정확한 의미 전달을 위해 명칭이 변경되었다.
    
컨테이너 컴포넌트와 프레젠테이션 컴포넌트는 로직 분리의 관점에서 구분하는 표현이다. 단순히 `props`, `state`로 화면을 그리는데 넘겨받는 것이 아니라 Ajax 요청이나 localStorage 등을 통해 데이터를 fetching 해야 할 경우 데이터까지 다루게 되므로 재사용성이 떨어진다. 이러한 상황에서 동작을 다루는 부분과 표현을 다루는 부분을 분리하여 작성하는 컴포넌트 패턴이다.
  
__`state` 존재 여부가 두 컴포넌트를 구분하는 것은 아니다. 또한 컴포넌트가 꼭 JSX를 출력하지 않아도 괜찮다.__

&nbsp;
### 장점
0. __관심사의 분리__  
    작성 하는 앱 과 UI 를 보다 이해하기 쉽게 만들 수 있다.
0. __재 사용성__  
    완전히 다른 곳으로부터 온 여러 상태(state) 라 할지라도, 이를 표현하기 위해 같은 Presentational Component 사용할 수 있는데 이때, 각 상태를 나타내는 Container Component 를 만들어 이를 또 재사용 할 수 있다.
0. __Markup__  
    작성시 Layout Component 를 별도로 추출하여 관리해야 하는데, 이렇게 Layout Component 를 추출하게 되면 똑같은 Layout 마크업을 여러 Container Component 에 작성하는 작업을 피할 수 있다.
    
&nbsp;
### 원본 컴포넌트
```javascript
import React, { Component } from 'react';

class Container extends Component {
  constructor() {
    super();
    this.state = { views: [] }
  }

  componentDidMount() {
    fetch("/views.json")
          .then(res => res.json())
          .then(views => this.setState({ views }))
  }

  redner() {
    return (
        <ul>
            {this.state.views.map(view => (
                <li>{view.name} - {view.contents}</li>
            ))}
        </ul>
        )
  } 
}

export default Container;
```

&nbsp;
### Container (컨테이너 컴포넌트)
1. 어떻게 동작해야 할지를 책임진다.
1. 내부에 Presentational Component 와 Container 컴포넌트 모두를 가질 수 있지만, 대게 전체를 감싸는 div를 제외하고 자체적인 JSX나 스타일을 갖고 있지 않다.
1. Ajax 요청, HOC 등을 이용해 render에 필요한 데이터를 Fetching 하여 다른 Presentational Component 와 Container Component 에게 제공한다.
1. Flux 의 Action 을 호출하는 작업을 Container Component 에서 작성하며, 이 Callback 들은 다른 Presentational Component 에게 넘겨준다.
1. 주로 데이터 저장소로 활용되며 데이터 Fetching 등을 위한 `state` 를 갖고 있는 경우가 많다.
1. 직접 작성되기 보다는 HOC(Higher-Order Components) 로 부터 생성되는 경우가 많다.
1. ex: UserPage, FollowersSlidebar, StoryContainer, FollowedUserList, 등등...

```javascript
import React, { Component } from 'react';

class Container extends Component {
  constructor() {
    super();
    this.state = { views: [] }
  }

  componentDidMount() {
    fetch("/views.json")
          .then(res => res.json())
          .then(views => this.setState({ views }))
  }

  redner() {
    return <Presentational views={this.state.views} />
  } 
}

export default Container;
```

&nbsp;
### Presentational (프레젠테이션 컴포넌트)  
2. 어떻게 보여지는 지를 책임진다.
2. 내부에 Presentational Component 와 Container 컴포넌트 모두를 가질 수 있고, 대게 JSX와 자체 스타일을 가진다.
2. this.props.children 을 통해 다른 컴포넌트 를 포함 하게끔 만들 수 있다.
2. 어플리케이션의 나머지 부분에 대해 아무런 의존성을 가지지 않는다. (예를 들면 Flux 의 Action 이나 Stroe) 즉, 단독적인 Component 가 된다.
2. 데이터를 불러오거나 변경하는 작업은 Presentational Component 에서 작성하지 않고, 이미 존재한다고 가정한다.
2. 데이터 및 데이터와 관련된 Callback 은 props 를 통해서 받는 작업만 한다.
2. UI 상태를 관리하기 위한 `state`가 존재할 수 있다.
2. state, LifeCycle, 성능 최적화가 필요없는 경우라면 Functional Component 로 작성된다.
2. ex: Page, Slidebar, Story, UserInfo, List, ..

```javascript
const Presentational = props => 
(<ul>
  {props.views.map(view => (
    <li>{view.name} - {view.contents}</li>
  ))}
</ul>)
```

&nbsp;
### Point
Presentational Component 와 Container Component 간의 차이점이 기술적인 부분에서 오는 것이 아니라 어떤 목적을 가지는지에 따라 분류 해야 한다는 것을 충분히 이해하는 것이 중요하다.

&nbsp;
>### 참고자료 
> [michael chan](https://medium.com/@chantastic)의 [gist](https://gist.github.com/chantastic/fc9e3853464dffdb1e3c)  
> [velog-리액트 교과서 - React 컴포넌트와 상태 객체](https://velog.io/@kyusung/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EA%B5%90%EA%B3%BC%EC%84%9C-React-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%99%80-%EC%83%81%ED%83%9C-%EA%B0%9D%EC%B2%B4)  
> [JeromeBaek님의 네이버 블로그](https://blog.naver.com/PostView.nhn?blogId=backsajang420&logNo=221368885149&categoryNo=77&parentCategoryNo=0)

&nbsp;
## I think...
* 도대체 뭘 기준으로 나누고 쪼개야하는지 기준이 서지않아 고민스럽던 때에 잘 정리한것 같다.
* "이 두가지 컴포넌트 에 대한 구분을 명확히 하기 위해 서로 다른 폴더에서 관리하는 것을 권한다." 고 한다. 훔...

## TODO
* Router / Mobx / Redux 해야되는데...