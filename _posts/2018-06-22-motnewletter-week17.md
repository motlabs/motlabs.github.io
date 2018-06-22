---
layout: post
title: MoT Weekly News Letters (16-17th weeks)
description: "16-17th Weeks, MoT summary"
author: jwkang
date: 2018-06-22
tags: [MoTLabs Study]
comments: true
subdir: motnewletter-week17
thumbnail: mot_logo.jpg
share: true
---


## MOT News
- (6/9):  [강재욱, 양서연, 곽도영, 백윤범 Tensorflow Pattern Design Study day1](https://motlabs.github.io/2018-06-11/tfpattern-week2/)
- (6/12): 강재욱, ETRI에서 "Mobile Vision Learning" 주제로 발표 (Host 이용주 책연구원님, [발표자료 링크](https://goo.gl/4H3X1q))
- (6/15): 정겨울님 블로그 추가 포스팅 
- (6/16): [강재욱, 양서연, 곽도영, 백윤범 Tensorflow Pattern Design Study day2](https://motlabs.github.io/2018-06-19/tfpattern-week3/)
- (6/18): 김택민, 이용근 CVPR 2018 학회 참석



## MOT Study
**1. 거북목 프로젝트 UI/UX 초안 공유 + Convolutional Pose Machine을 활용한 안드로이드 tflite 톺아보기  (발표자 신정아)**
- [추천 깃헙링크:https://github.com/edvardHua/PoseEstimationForMobile](https://github.com/edvardHua/PoseEstimationForMobile)
- 

**2. Object Detection Tech Tree** (발표자 이성진)
- [Facebook Tech] - YOLO, 모바일 -> Tiny YOLO
- [Google Tech] - SSD(VGG), 모바일 -> SSD + MobileNet / TinySSD
- 우리 프로젝트 bounding box detection에는 SSD + MobileNet의 조합을 적용해 볼 수 있음
    

**3. iOS에서 ML Kit 핥아보기 (발표자 곽도영)** [(발표자료 링크)](https://goo.gl/2jms43)
- ML Kit DEMO
- ML Kit 이란?
- DEMO 프로젝트 설명
- 거북목 프로젝트 진행사항 – iOS
- 이 후 별도 포스팅 예정!

**4. 거북목 프로젝트 진행사항 (발표자 강재욱)**
- 모델 아키텍쳐 관련
- Tf to tflite 호환성 관련 
- Tf slim api use
- Mobile app implementation related
- Dataset collection status
- Off the record (It will be announced later !!)


## Lab Notices
- [프로젝트 모델 아키텍처 + 코드 UML 확인 요망](https://docs.google.com/document/d/1cOC9CZJv02WEz-v17FCQ-Up19kYP1ZtoadvpC_nLPPM/edit#heading=h.lv5patfw1lss)
- 텐서보드 대신에 더 간단하게 그래프 아키텍쳐를 보는 링크  
    - [https://lutzroeder.github.io/Netron/](https://lutzroeder.github.io/Netron/) 
    - .pb / .tflite 파일 로드 가능
- 텐서플로 코딩할때 tflite ops가 지원하는지 신경쓸 것 [(관련 링크)](https://goo.gl/EPqsXV)    
- TF 모듈 코딩해서 PR 날릴때 테스트코드도 같이 제출할 것
- 다음주(6/28)는 제주도 가기전에 한번 정리하는 모임이므로 모바일앱 + 모델 데모 필요
- 지표 설정
    - 모바일 앱 지표: fps, acc/time
    - 모델 지표: Top1-accuracy
- 6/28 자율주행 랩이 개포동 방문 


## Issues
- 훈련데이터 이미지 가로세로 비율에 대한 논의 ( 3x4 or 1x1)
- 텐서플로우 4D tensor 포맷은 NHWC를 따라야 함
- 테스트 모델 활용해서 앱 빨리 만들어보기(MVP)
- 모델 사이즈 줄이는 연구 지속 필요
- 모바일 앱 매주 데모 하기 (애자일!)


## Last Weekly Reports in MoT
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
