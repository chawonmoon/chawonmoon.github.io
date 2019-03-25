---
layout: post
title: "Windows10 환경에서 Git-ssh로 접속 설정하기"
date: 2019-03-22
image: '/assets/img/'
description: 'Windows10 환경에서 Git-ssh로 접속 설정하는 방법을 정리한다.'
tags:
- Windows10
- Git
- SSH
- PuTTY
categories:
- Blog
---

# Windows10환경 SSH 인증설정 
> 원래 알고있으면 별거 아닐수있으나 처음접할때나 오랜만에 접할때는 정말 많은 시행착오를 겪어야하는 상황일듯 싶어 정리해놓는다.

## 문제 해결 과정
1. MAC환경에서 문제없이 돌아가던 VSCode의 Git 기능이 Windows10에서 돌아가지 않는다. 소스트리나 투토라이즈는 됨 (검색해보면 SSH인증 어쩌구저쩌구...)
2. Google검색을 미친듯이 해도 돌아오는 결과는 의역해보면 Windows10의 SSHAgent가 문제라는 이야기들이 즐비
3. 이런저런 검색을 하다보니 Windows10의 고유 SSHAgent를 사용할때 터미널을 닫게되면 인증세션도 같이 끊어진다는 문서발견
4. 테스트 해보니 실제로 SSHAgent를 실행한 터미널을 닫지 않고 그상태 그대로 터미널에서 VSCode를 실행시키면 Git이 실행됨
5. 찾다 찾다 [`PuTTY`](https://www.putty.org/)를 대안으로 찾아 테스트 해봄
6. 컴을 켜서 `PuTTY Agent`에 맨 처음 한번 암호를 넣고 실행시키면 컴끌때까지 잘 유지됨
7. 해결!!! 짝~짝~짝~

### Windows10의 SSH-Keygen으로 나온 SSH키를 PuTTY로 포팅 및 실행
1. Windows10 SSH-Keygen 실행방법은 검색하면 수백가지가 나오니 검색 ㄱㄱ~
2. 설치된 `PuTTY Key Generator`를 실행하여 상단 메뉴의 `Conversions` > `Import Key` 선택 후 Keygen으로 나온 Key선택
3. 여기서 절대 프로그램 가운데 있는 `Load`버튼으로 Key를 불러오면 안된다!!! 꼭 주의!!!
4. 이후에는 `Save public key`로 퍼블릭 키를 생성하고 `Save private key`로 프라이빗 키를 생성해서 사용하면 된다
5. 기본적으로 `PuTTY`를 설치하면 여러 프로그램들이 설치되는데 그중 `Pageand`라는 'PuTTY`용 SSHAgent가 같이 설치되며 Windows화면 하단 우측 시스템트레이에 등록된다.
6. 이제 생성된 `private key`를 `Pageand`에 `Add Key`하면 비밀번호를 최초 한번 입력하여 사용하면된다.

&nbsp;
## I think...
* Mac환경과 비슷하다고 치부하고 생각하는 바람에 이것때문에 1주일을 낭비했다. 생각을 닫고 고만큼만 보지 말자.
* Windows환경에서의 SSH Key사용은 그냥 기승전 `PuTTY`다!!!

## TODO
* 관련 사진은 귀찮기도하고 현재 포샵이 없어 편집이 힘들어 못올렸다. 시간날때 사진도 첨부하자!!!