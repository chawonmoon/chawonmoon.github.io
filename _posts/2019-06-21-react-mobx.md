---
layout: post
title: "CRA에 MobX 설치&셋팅"
date: 2019-06-21
image: '/assets/img/'
description: 'CRA에 MobX 설치와 셋팅하기'
tags:
- React
- CRA
- Code
- MobX
- 상태관리
categories:
- Code
---
## CRA에서 MobX 설치 & 셋팅

### MobX 모듈과 Decorator 설치 및 셋팅
* mobX / mobx-react 모듈 설치  

```text
$ yarn add mobx mobx-react
```

* Decorator를 Babel에 설정하기위해 `yarn eject` 
    - eject 하기전에 git에 push 되어야한다. 안되있으면 애러!!!
    - eject 후에는 꼭 `yarn` 또는 `yarn install` 실행
    - 또한 `yarn start` 하면 애러가 날것이다. `@babel/plugin-transform-react-jsx-source` 와 `@babel/plugin-transform-react-jsx-self` 모듈 추가 설치
    
* Babel 플러그인 설치

```text
$ yarn add @babel/plugin-proposal-class-properties @babel/plugin-proposal-decorators
```

* `package.json` 파일의 Babel 설정 추가

```json
"babel": {
    "presets": [
      "react-app"
    ],
    "plugins": [
        ["@babel/plugin-proposal-decorators", { "legacy": true}],
        ["@babel/plugin-proposal-class-properties", { "loose": true}]
    ]
  }
```
* 개발서버 reboot!!


&nbsp;
## I think...
* Mobx를 사용할때 꼭 Decorator를 사용해야하는건 아니다
* 다만 편하니까...

## TODO
* Mobx 문법 및 스토어 사용해보기
* Decorator 설정하면서 튀어나온 미루고 미뤄둔 `webpack`