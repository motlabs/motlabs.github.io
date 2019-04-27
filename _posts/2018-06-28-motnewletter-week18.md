---
layout: post
title: MoT Weekly News Letters (18th weeks)
description: "18th Weeks, MoT summary"
author: jwkang
date: 2018-06-30
tags: [MoTLabs Study]
comments: true
subdir: motnewletter-week18
thumbnail: mot_logo.jpg
share: true
---


## MOT News
**There is Nothing new, but we are moving for a leap!**



## MOT Study
**1. 거북목 프로젝트 iOS 데모 (발표자: 곽도영)**
- [[mot-ios-tensorflow github repo]](https://github.com/motlabs/mot-ios-tensorflow)
- 해결한 이슈 및 구현된 기능

```
    - 입력 포맷의 타입 이슈 해결(unit8 ☞ float32)
    - PoseEstimationForMobile을 ML Kit으로 구현(이슈해결)
    - PoseEstimationForMobile을 Core ML으로 구현(Core ML 모델을 저장소 오너에게 받음)
    - 실시간 추론(PoseEstimationForMobile + 카메라)
```
- 새로 생긴 이슈

```
    - 이 모델(PoseEstimationForMobile)은 상반신만 찍은 사진(우리가 사용할 데이터)은 거의 인식을 못함
```
- 다음 할 일

```
    - 전처리시 리사이징 할때 인터폴레이션 방법 조사(CoreGraphic)
    - 밴치마크 기준 잡아서 평가해보기
    - 후처리 성능 측정, 개선방향 조사
    - point들을 점으로 연결해보기
```

**2. 거북목 프로젝트 Android 데모 (발표자: 신정아)**
- [[mot-android-tensorflow github repo]](https://github.com/motlabs/mot-android-tensorflow)

```
- Single pose estimation demo 앱 빌드
- fps 측정 api 구현
```
{% include image.html subdir=page.subdir name='demoapp-week18.jpg' caption='18주차 앱구현 현황 (오른쪽:Android, 왼쪽:iOS)' %}


**3. To TFRecord (발표자: 이준호)**, [[코드링크]](https://github.com/motlabs/dont-be-turtle/blob/feature/fb_dataio/tfmodules/tfrecord_converter.py)


**4. Single-shot detection TF API 소개 (발표자: 이성진)**, [[발표자료 링크]](https://drive.google.com/drive/folders/1TrdtYw9Hzo3ux80gjqXhkwnRb4lQOs6s)


**5. 거북목 프로젝트 진행사항 (발표자 강재욱)**
- [Hourglass 모델 아키텍쳐 설명](https://docs.google.com/document/d/1cOC9CZJv02WEz-v17FCQ-Up19kYP1ZtoadvpC_nLPPM/edit#heading=h.lv5patfw1lss)
- [tflite Copatibility 가이드](https://docs.google.com/document/d/1cOC9CZJv02WEz-v17FCQ-Up19kYP1ZtoadvpC_nLPPM/edit#heading=h.lv5patfw1lss)
- [tf slim api 가이드](https://docs.google.com/document/d/19ZiExIc-vdbGrauuRUPKDI_o3sbVTeYMifc_hzvULGA/edit)
- 데이터 셋 수집 현황
- [모바일 앱 요구사항 정리](https://docs.google.com/document/d/1eYztqAInoD-6CQTsen6_SV0xVEYO6FRgkO9Zvbsr8DY/edit#)



## Lab Notices
- 자율주행 랩 방문! (Welcome!)
- 강재욱 양서연 김택민 구글 제주캠로 참석 (7/1~)
    - 제주도에 오실 분들 일정 확인!
- 다음주 부터 스카이프 미팅 (제주캠프 진행 상황 생중계)
- 8월 중순에 새로운 프로젝트에 대한 아이디어 공모 중! 


## Issues
- 성능측정앱과 데모앱은 다른 프로젝트로 빌드하기 [(문서참)](https://docs.google.com/document/d/1eYztqAInoD-6CQTsen6_SV0xVEYO6FRgkO9Zvbsr8DY/edit#)
- 팀원들의 지속적인 서포트 필요


{% include image.html subdir=page.subdir name='motweek18.jpg' caption='열심히! 연구하는 MoT' %}


## Last Weekly Reports in MoT
- [16-17주차 리포트 blog](https://motlabs.github.io/2018-06-22/motnewletter-week17/)
- [14-15주차 리포트 blog](https://motlabs.github.io/2018-06-09/motnewletter-week15/)
- [13 주차 리포트 gslide]( https://goo.gl/SPKZUp )
- [9-12주차 리포트 gslide](https://goo.gl/SY6gHF)
- [7-8주차 리포트 gslide]( https://goo.gl/CYwZM2 )
- [6주차 리포트 gslide](https://goo.gl/GYPzzp)
- [5주차 리포트 gslide]( https://goo.gl/tBny5m )
- [4주차 리포트 gslide]( https://goo.gl/4JnQoc )
- [3주차 리포트 gslide]( https://goo.gl/JGSztP )
- [2주차 리포트 gslide]( https://goo.gl/T7o9tf )
- [1주차 리포트 gslide]( https://goo.gl/nNqMYg )
