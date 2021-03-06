# chawonmoon.github.io

## will-jekyll 테마 적용

이 테마는 블로그 포스트는 쓰고 싶지만 Front-end에는 신경쓰고 싶지 않은 개발자들을 위해 고안된 간단하고 미니멀리즘한 템플릿이다.

테마에 포함된 기능은 아래 목록과 같다 :

- Gulp
- Stylus (Jeet, Rupture, Kouto Swiss)
- Smoothscroll
- Live Search
- Offcanvas Menu
- SVG icons
- Shell Script to create posts
- Tags page
- Series page
- About Me page
- Feed RSS
- Sitemap.xml
- Color Customization
- Info Customization

## Basic Setup

1. [RubyInstaller 설치](https://rubyinstaller.org/)
2. [Jekyll 설치](http://jekyllrb.com)
3. Github의 [Will Jekyll Template](https://github.com/willianjusten/will-jekyll-template/fork) 테마 Fork(예의상 꼭 하자)
4. [Will Jekyll Template](https://github.com/willianjusten/will-jekyll-template/fork) Clone
5. `_config.yml` 파일을 자신에게 맞게 수정
6. 카테고리 및 태그 지정에 대한 예제를 보려면 `_posts`의 샘플 게시물과 기타 YAML 데이터를 확인
7. 자세한 사용자 지정 포인터 및 설명서는 아래 설명서를 참조

## Site and User Settings

사이트의 기본설정을 바꾸려면 `_config.yml`에 몇 가지 정보를 수정해야 한다.

```ruby
# Site settings
description: A blog about lorem ipsum dolor sit amet
baseurl: "" # the subpath of your site, e.g. /blog/
url: "http://localhost:3000" # the base hostname & protocol for your site 

# User settings
username: Lorem Ipsum
user_description: Anon Developer at Lorem Ipsum Dolor
user_title: Anon Developer
email: anon@anon.com
twitter_username: lorem_ipsum
github_username:  lorem_ipsum
gplus_username:  lorem_ipsum
disqus_username: lorem_ipsum
```

## Color customization

모든 색상변수는 `src/styl/_variables.styl`에 작성되어 있다. 메인 색상을 변경하려면 `main` 변수에 새 값을 설정하기만 하면 된다. 다른 색은 텍스트와 코드 배경색을 위한 것이다.

## Creating posts

`initpost.sh` 명령을 이용하여 새로운 post를 생성할수있다.  
아래 명령 참고

```bash
./initpost.sh -c Post Title
```

이때 생성되는 새로운 포스트는 `yyyy-mm-dd-title.md` 형식의 이름으로 `_posts`폴더에 생성된다.

## Front-matter 

새 게시물을 작성할 때, 작성하는 문서 최상단에 게시 정보를 입력해야 한다.  
아래 예시 참고

```ruby
layout: post
title: "How to use"
date: 2015-08-03 03:32:44
image: '/assets/img/post-image.png'
description: 'First steps to use this template'
tags:
- jekyll 
- template 
categories:
- I love Jekyll
twitter_text: 'How to install and use this template'
```


## Running the blog in local

Gulp로 컴파일 하고 로컬에서 Jekyll을 실행해서 화면을 확인하려면 아래의 단계를 참고 

- [NodeJS](https://nodejs.org/) 설치
- `npm install` 실행 
- `gulp` 실행

## Questions

작업하는데 문제가 있거나, 궁금한 내용이 있을시에는 [@willian_justen](https://twitter.com/willian_justen), [GitHub Issue](https://github.com/willianjusten/will-jekyll-template/issues/new)를 통하면 됩니다.  

## License

이 테마는 MIT License에 따라 배포되는 무료 오픈 소스 소프트웨어 입니다.    
자유롭게 이 테마를 이용하십시오.