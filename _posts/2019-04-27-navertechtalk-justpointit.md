---
layout: post
title: "짚으면 찾아주는 사전 - JUST POINT IT과 모바일 머신러닝 (NAVER TechTalk)"
description: "Core ML과 ML Kit을 사용한 Pose Estimation + OCR 앱 개발기"
author: dygwak
date: 2019-04-27
tags: [presentation, NAVER, TechTalk]
comments: true
subdir: presentation
thumbnail: mot_logo.jpg
share: true
---
발표자 : 곽도영<br>
발표날짜 : 2019-03-15

<br><br>
감사하게도 이번에 네이버 테크톡에 초대를 받아 제가 만들었던 **[JUST POINT IT 앱](https://itunes.apple.com/app/id1438598958)**에대해 소개하고 경험을 공유할 수 있는 기회가 있었습니다.

JUST POINT IT은 여러가지 머신러닝을 사용한 모바일 앱 프로젝트로써 모바일 위에서 **실시간**으로 추론하고 여러 모델을 **연속적**으로 실행시키는 특징을 가지고 있습니다. 이러한 문제들을 어떻게 정의하고 어떻게 해결하였는지 설명합니다.

<img style="width:240px; display: block; margin-left: auto; margin-right: auto;" src="/assets/images/navertechtalk-justpointit/justpointit-demo2-4-3.gif">
<div style="text-align:center;">JUST POINT IT 데모</div>

## Presentation

### Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/Jq5L_5bRBR0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<div style="margin-bottom:5px"> <strong> <a href="https://youtu.be/Jq5L_5bRBR0" title="Just point it" target="_blank">짚으면 찾아주는 사전 - Just Point It와 모바일 머신러닝</a> </strong> from <strong><a href="https://www.youtube.com/channel/UCNrehnUq7Il-J7HQxrzp7CA" target="_blank">Youtube</a></strong>
</div>

### Slide
<iframe src="//www.slideshare.net/slideshow/embed_code/key/d6VZJLKmHLOJtC" width="560" height="400" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>
<div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/NaverEngineering/just-point-it" title="Just point it" target="_blank">JUST POINT IT</a> </strong> from <strong><a href="https://www.slideshare.net/NaverEngineering" target="_blank">ShareSlide</a></strong>
</div>

### Presentation Recap
1. DEMO
2. Motivation
3. 없으면 만들자!<br>1. OCR(학습없이)<br>2. Finger Detection(직접학습)<br>3. Majority Voting(인식률개선)
4. 앞으로...

## Related links
- [App Store 다운로드 링크 - JUST POINT IT](https://itunes.apple.com/app/id1438598958)
- [Google Play 다운로드 링크 - JUST POINT IT](https://play.google.com/store/apps/details?id=jeongari.com.just_point_it)
- [Youtube 발표 영상](https://youtu.be/Jq5L_5bRBR0)
- [NAVER TV 발표 영상](https://tv.naver.com/v/6001189)
- [ShareSlide 발표 자료](https://www.slideshare.net/NaverEngineering/just-point-it)
- [JUST POINT IT 소개 - TensorFlow KR 공유](https://www.facebook.com/groups/TensorFlowKR/permalink/842354062772320/)
