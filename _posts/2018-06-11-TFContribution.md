---
layout: post
title: Tensorflow 커미터가 되자!
description: "Summary"
author: dygwak
date: 2018-06-11
tags: [TF Contribution]
comments: true
subdir: postformat
thumbnail: tensorflow_logo.png
share: true
---

> Reviewed by Jaewook Kang

🙆‍이 포스팅의 PR은 언제든 환영입니다!

#### Intro

이번에 Tensorflow에 PR했던게 통과되었습니다🎉. 그러고보니 그 날이 제 생일이었는데ㅋㅋ 의미있는 선물을 받은거 같아서 기분이 좋네요☺️. 사실 PR도 문서 읽다가 마크다운 포멧이 적용되지 않은 부분을 발견해서 점하나 찍고 올렸던게 이틀만에 머지되었습니다. 간단한 PR은 리뷰도 토론도 생략하고 쉽게쉽게 진행되는 느낌입니다.

이번 글에서는 Tensorflow에 PR을 날리고 머지된 경험을 바탕으로 Tensorflow에 기여하는 절차에대해 간단하게 소개합니다. 많은분들께서 Tensorflow에 기여를 하고싶어하지만 언어의 장벽이나 절차가 많아보이는 부담감때문에 쉽게 시도해보지 못하는 것 같은데, 조금이나마 도움이 되길 바라며 정리해봤습니다.

**※ git과 github에 어느정도 익숙해야 합니다.** 참고로 저는 아래 문서를 보면서 git과 github을 배웠어요!

- [공식 git 책(한국어)](https://git-scm.com/book/ko/v2)
- [[번역] Art of Clean Pull Requests - 클린한 Git PR의 기술](http://blog.sonim1.com/224)



#### 참고문헌:
- [Tensorflow github comtributing.md](https://github.com/tensorflow/tensorflow/blob/master/CONTRIBUTING.md)
- [[번역]Tensorflow CONTRIBUTING.md](https://gist.github.com/tucan9389/1a7d1910dfe8183df47a4fbc5ced1c03)

## 절차
1. [이슈 생성](#1-%EC%9D%B4%EC%8A%88-%EC%83%9D%EC%84%B1%EF%B8%8F)❗️ (간단한 기여는 생략 가능)
1. [저장소 포크](#2-%EC%A0%80%EC%9E%A5%EC%86%8C-%ED%8F%AC%ED%81%AC)🍴
1. [소스코드 변경](#3-%EC%86%8C%EC%8A%A4%EC%BD%94%EB%93%9C-%EB%B3%80%EA%B2%BD)💻
1. [새너티 체크, 유닛 테스트](#4-%EC%83%88%EB%84%88%ED%8B%B0-%EC%B2%B4%ED%81%AC-%EC%9C%A0%EB%8B%9B-%ED%85%8C%EC%8A%A4%ED%8A%B8)🚦
1. [풀 리퀘스트](#5-%ED%92%80-%EB%A6%AC%ED%80%98%EC%8A%A4%ED%8A%B8)🙇
1. ([컨트리뷰터 라이센스에 서명하기](#6-%EC%BB%A8%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%84%B0-%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4%EC%97%90-%EC%84%9C%EB%AA%85%ED%95%98%EA%B8%B0%EF%B8%8F)✍️)
1. [리뷰어와 열띤 토론](#7-%EB%A6%AC%EB%B7%B0%EC%96%B4%EC%99%80-%EC%97%B4%EB%9D%A4-%ED%86%A0%EB%A1%A0)🗣
1. [리뷰 통과](#8-%EB%A6%AC%EB%B7%B0-%ED%86%B5%EA%B3%BC)💯
1. [코드 머지](#9-%EC%BD%94%EB%93%9C-%EB%A8%B8%EC%A7%80)🎊

### 1. [이슈](https://github.com/tensorflow/tensorflow/issues) 생성❗️
- 간단한 기여는 생략 가능
- 어디서 부터 기여를 해야할지 모르겠다면, 이슈에서 [contribution welcome](https://github.com/tensorflow/tensorflow/issues?q=is%3Aopen+is%3Aissue+label%3A%22stat%3Acontributions+welcome%22) 라벨을 찾아보기.
  - 코어 팀이 당장에 처리할 내용은 아니고
  - 특히 외부 컨트리뷰터에게 적합한 이슈들을 모아놓음
- 필요하면 언제든지 이슈 댓글에 도움을 요청하면 됨(누군가는 해주는듯)
- 혹은 평소에 생각하고 있던 부분을 이슈로 날리자
- 내가 작업하고 있는 이슈에 댓글로 남겨서 내가 작업중이라는 것을 알리기

### 2. 저장소 포크🍴
- 내 저장소에 포크하기
- 그리고 로컬에 `git clone` 하여 프로젝트 내려받기

### 3. 소스코드 변경💻
1. 필요시 새로운 브랜치 파기(다른 기능을 개발하는 경우 유용)
1. 소스코드를 변경/기능 추가

- 제시된 코딩 스타일 가이드라인(C/C++, Python, Objective-C...)을 지켜야함
- Tensorflow의 핵심 코드에 PR 할때는 이전 버전의 호환성에 신경써야 함
- 파일 헤더에 라이센스 문구를 포함해야함

### 4. 새너티 체크, 유닛 테스트🚦
- 코드 커버리지가 충분한 unit test를 포함해야함
- Sanity check?
- 유닛테스트<br>
  ☞ Docker와 Tensorflow의 CI 스크립트 사용<br>
  ☞ 혹은 직접 툴을 설치해서 세팅
### 5. 풀 리퀘스트🙇
- Pull Request(PR)
- 절차
  1. 내 로컬의 코드를 커밋
  2. 내 로컬의 커밋을 내 저장소에 Push!
  3. 내 저장소의 코드를 [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow/) 저장소에 PR!

### 6. 컨트리뷰터 라이센스에 서명하기✍️
- Contributor License Agreement(CLA)
- 커미터가 되기 위해서는 [컨트리뷰터 라이센스 동의 서약](https://cla.developers.google.com/)에 서명해야함
- 새로운 Pull Request를 만들면 댓글에서 봇이 자동으로 절차를 알려줌(신기)
  - 링크를 주면서 서명 절차를 알려줌
  - 서명 절차를 끝내고 나면 PR 페이지로 돌아가서 `I signed it!`이라고 댓글을 남기기
  - 그러면 자동으로 서명이 완료됨
- 개인용과 기업용이 따로 있음
- 이 절차를 거치지 않으면 PR을해도 반영되지 않으며, Tensorflow 저장소의 모든 코드는 CLA에 서명한 코드임

### 7. 리뷰어와 열띤 토론🗣
- 서명을 하고나면 하루/이틀 사이에 리뷰어가 할당됨
- 그 리뷰어에게 리뷰를 받고나면 

### 8. 리뷰 통과💯

### 9. 코드 머지🎊
- 리뷰어가 결정하고 노티피케이션으로 알림을 받습니다.


### PR:
※ [https://github.com/tensorflow/tensorflow/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Atucan9389+](https://github.com/tensorflow/tensorflow/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Atucan9389+)
