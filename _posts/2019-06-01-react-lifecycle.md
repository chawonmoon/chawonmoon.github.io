---
layout: post
title: "React Lifecycle"
date: 2019-06-01
image: '/assets/img/'
description: 'React Lifecycle 정리'
tags:
- React
- Code
- Lifecycle
categories:
- Code
---
## React Lifecycle 정리

### Component Mount (초기화시)
React 컴포넌트 객체가 DOM에 실제로 삽입되기 전까지의 API호출 순서,  
일명 마운팅(Mounting) 과정
1. __contructor() {}__
- 생성자 함수, 컴포넌트가 새로 만들어질 때마다 호출됨
1. __componentWillMount() {}__
- 원래는 주로 브라우저가 아닌 환경(서버사이드)에서도 호출하는 용도
- 컴포넌트가 화면에 나가기 직전 호출됨 
- __v16.3__ 부터 __Deprecate__
- 이후부터 `UNSAFE_componentWillMount()` 로 변경
1. __render() {}__
- 실제 컴포넌트를 그리는 함수
1. __componentDidMount() {}__  
- 컴포넌트가 모두 구성된 직후 호출
- 통상적으로 API / 외부 라이브러리등을 연동은 여기서 이루어짐  
        - 외부 라이브러리 연동: D3, masonry, etc
        - 컴포넌트에서 필요한 데이터 요청: Ajax, GraphQL, etc
        - DOM 에 관련된 작업: 스크롤 설정, 크기 읽어오기 등
&nbsp;  
&nbsp;

### Component Update (데이터 변경이 있을시)
props / state 의 변화에 따라 특정한 변화를 렌더링하기 까지의 API호출 순서
2. __componentWillReceiveProps(`nextProps`) {}__  
- props가 업데이트가 발생했을시(변경 감지)
-  __v16.3__ 부터 __Deprecate__
- 이후부터 `UNSAFE_componentWillReceiveProps()` 변경
- 상황에 따라 __v16.3__ 에 생긴 `getDerivedStateFromProps()` 대체
> __getDerivedStateFromProps( `prevProps`, `prevState` )__  
> props 로 받아온 값을 state 로 동기화 하는 작업을 해줘야 하는 경우에 사용
2. __shouldComponentUpdate( `nextProps`, `nextState` ) {}__
- 컴포넌트 최적화에 주로 사용됨
- 기본적으로 `true` 를 반환
- 조건에 따라 `false` 를 반환하면 `render` 를 하지 않음
2. __componentWillUpdate( `nextProps`, `nextState` ) {}__
-  `shouldComponentUpdate` 에서 `true` 를 반환했을때만 호출
-  __v16.3__ 부터 __Deprecate__
- 이후부터 `getSnapshotBeforeUpdate()` 대체
> __getSnapshotBeforeUpdate( `prevProps`, `prevState` )__  
> - DOM 업데이트가 일어나기 직전 DOM 상태를 반환
> - 리턴값은 `componentDidUpdate` 에서 3번째 파라미터(`snapshot`)로 받음
> - API 발생시점
>   - `render()`  
>   - `getSnapshotBeforeUpdate()`
>   - 실제 DOM 에 변화 발생  
>   - `componentDidUpdate`  
2. __render() {}__
- 실제 컴포넌트를 그리는 함수
2. __componentDidUpdate( `prevProps`, `prevState`, `snapshot` ) {}__
- `render()` 를 호출하고난 다음에 발생
- `this.props` 와 `this.state` 가 바뀌어있는 상태
- 파라미터를 통해 이전의 값인 `prevProps` 와 `prevState` 조회 가능
- 파라미터를 통해 `getSnapshotBeforeUpdate` 에서 반환한 `snapshot` 값 조회가능
&nbsp;  
&nbsp;

### Component Unmount (컴포넌트 제거 시)
3. __componentWillUnmount() {}__
- 컴포넌트를 사용하지 않을 때(제거되기 직전) 발생하는 이벤트
- 주로 등록했었던 이벤트를 제거하는데 사용
- 외부 라이브러리를 사용한게 있고 해당 라이브러리에 `dispose` 기능이 있다면 여기서 호출
&nbsp;  
&nbsp;

### Component Error (컴포넌트 에러발생 시)  
4. __componentDidCatch( `error`, `info` ) {}__
- 컴포넌트 자신의 `render()` 에서 발생하는 에러는 잡아낼 수는 없음
- 자식 컴포넌트 내부에서 발생하는 에러를 잡아낼 수 있음  

&nbsp;
## I think...
* 일종의 React의 이벤트 같지만 이벤트의 개념은 아닌것 같다
* 뭐랄까 중간중간 사건이나 사고 발생때마다 알려주는 방송국의 개념???   

## TODO
* Router / Mobx / ~~Redux~~ 남았다...