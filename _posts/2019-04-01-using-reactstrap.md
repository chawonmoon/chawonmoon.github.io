---
layout: post
title: "ReactStrap 사용기"
date: 2019-04-01
image: '/assets/img/'
description: 'ReactStrap 설치 방법 및 사용법 정리'
tags:
- React
- Reactstrap
- Bootstrap
categories:
- Blog
---
## 1. ReactStrap 관련 홈페이지
> ReactStrap : [https://reactstrap.github.io/](https://reactstrap.github.io/)  
> BootStrap4.~(공식) : [https://getbootstrap.com/](https://getbootstrap.com/)  
> (국문홈페이지는 버전 3.~으로 업뎃이 오래된듯, 참고만 하자)

## 2. 설치 (Yarn으로 진행)  


### 프로젝트 폴더 진입 후 CRA로 프로젝트 생성

```
yarn create react-app ./

```  
&nbsp;
### 부트스트랩 설치
ReactStrap과 BootStrap을 설치 해준다

```
yarn add bootstrap reactstrap
```
&nbsp;
### CSS/SCSS import
#### Case 1. src/index.js 파일에 css를 사용할 경우

```javascript
import 'bootstrap/dist/css/bootstrap.min.css'; //CSS일 경우
```
#### Case 2. src/index.js 파일에 scss를 사용할 경우
기본 CRA에서 `scss`를 사용하기 위해선 `node-sass` 모듈이 필요하므로 설치 ㄱㄱ

```
yarn add node-sass
```
그 후 `CSS`와 똑같이 `import`를 하면된다

```javascript
import 'bootstrap/scss/bootstrap.scss'; //SCSS일 경우
```
&nbsp;
### src/index.js 전체 소스
```javascript
import React from "react";
import ReactDOM from "react-dom";
import "./index.css";
import App from "./App";
import * as serviceWorker from "./serviceWorker";

import "bootstrap/scss/bootstrap.scss"; //SCSS 

ReactDOM.render(<App />, document.getElementById("root"));

serviceWorker.unregister();
```
&nbsp;
## 3. 사용방법
딱히 어려울건 없다 일반 컴포넌트 쓰듯이 `import` 하고 쓰면된다

### Breadcrumbs
```javascript
import React, { Component } from 'react';
import { Breadcrumb, BreadcrumbItem } from 'reactstrap';

class App extends Component {
    render(){
        return (
            <div>
            <Breadcrumb>
                <BreadcrumbItem active>Home</BreadcrumbItem>
            </Breadcrumb>
            <Breadcrumb>
                <BreadcrumbItem><a href="#">Home</a></BreadcrumbItem>
                <BreadcrumbItem active>Library</BreadcrumbItem>
            </Breadcrumb>
            <Breadcrumb>
                <BreadcrumbItem><a href="#">Home</a></BreadcrumbItem>
                <BreadcrumbItem><a href="#">Library</a></BreadcrumbItem>
                <BreadcrumbItem active>Data</BreadcrumbItem>
            </Breadcrumb>
            </div>
        );
    }  
};

export default App;
```

### Button
```javascript
import React, { Component } from "react";
import { Button } from "reactstrap";

class App extends Component {
  render() {
    return (
      <div className="text-center pt-5">
        <Button color="primary">primary</Button>{" "}
        <Button color="secondary">secondary</Button>{" "}
        <Button color="success">success</Button>{" "}
        <Button color="info">info</Button>{" "}
        <Button color="warning">warning</Button>{" "}
        <Button color="danger">danger</Button>{" "}
        <Button color="link">link</Button>
      </div>
    );
  }
}

export default App;

```

### Table
```javascript
import React, { Component } from 'react';
import { Table } from 'reactstrap';

class App extends Component {
  render() {
    return (
      <Table>
        <thead>
          <tr>
            <th>#</th>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Username</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">1</th>
            <td>Mark</td>
            <td>Otto</td>
            <td>@mdo</td>
          </tr>
          <tr>
            <th scope="row">2</th>
            <td>Jacob</td>
            <td>Thornton</td>
            <td>@fat</td>
          </tr>
          <tr>
            <th scope="row">3</th>
            <td>Larry</td>
            <td>the Bird</td>
            <td>@twitter</td>
          </tr>
        </tbody>
      </Table>
    );
  }
}

export default App;
```
#### 조금 더 자세한 사용법은...
아래 주소를 찾아 들어가자  
##### ReactStrap 컴포넌트 홈  
* [https://reactstrap.github.io/components/alerts/](https://reactstrap.github.io/components/alerts/)  

##### BootStrap 도큐멘트 홈  
* [https://getbootstrap.com/docs/4.3/getting-started/introduction/](https://getbootstrap.com/docs/4.3/getting-started/introduction/)

&nbsp;
## I think...
* 과거에 User 영역을 WebPublishing 할때는 이거 써달라는 만큼 괴로운 요구사항도 없었다. (뭐 물론 잘쓰는 사람들은 조율해서 다 잘 쓰긴하더라...)
* 딱히 디자인이 없이 프론트 개발이 필요할때는 이젠 이것만한것도 없는것 같다.
* 부트스트랩이 버전이 3.~에서 4.~로 올라가면서 이것저것 바뀐것 같은데 다 확인해볼 필요성이 있는것으로 판단됨.
* 앞으로 요긴하게 잘 써주마!!!

## TODO
* Styling관련 부분을 다뤄봐야겠다. SCSS 믹스인을 몇가지 살펴보던중 일반적으로 WebPublishing에도 충분히 쓰일 만한 것들이 보이더라