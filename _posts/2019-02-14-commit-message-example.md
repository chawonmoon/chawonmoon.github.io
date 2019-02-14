---
layout: post
title: "Commit Message 예제"
date: 2019-02-14
image: '/assets/img/'
description: 'Git / SVN 등의 형상관리툴 사용시 공유할 Commit 메세지 정리'
tags:
- Git
- SVN
categories:
- Blog
---

# Commit Message Example  

```
Type: 제목(Title)

본문(Body) - 본문은 한 줄에 72자 이내로 작성

꼬리말(Footer) - 꼬리말에는 이슈 트래커 ID를 추가
Resolves: #123
See also: #456, #789
```

## Type 종류
제목의 처음은 동사 원형으로 시작하고 첫 글자는 대문자로 작성

* `feat`: 새로운 기능을 추가할 경우
* `fix`: 버그를 고친 경우
* `docs`: 문서 수정한 경우
* `style`: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
* `refactor`: 프로덕션 코드 리팩터링
* `test`: 테스트 추가, 테스트 리팩터링 (프로덕션 코드 변경 없음)
* `chore`: 빌드 테스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)
* `ignore`: 예외 파일 추가


## TODO
* 공적/사적 프로젝트를 진행하면서 필요한 부분은 주기적으로 업데이트를 해나아가야함