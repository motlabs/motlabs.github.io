---
layout: post
title: "Quick Review of TF 2.0"
description: "Quick review of TF 2.0"
author: jwkang
date: 2019-01-12
tags: [TF2.0 Preview]
comments: true
subdir: tf2preview-review
thumbnail: tensorflow_logo.png
share: true
---

> Reviewed by MoTLab members

2019 1/11 에 Tensorflow 2.0 Preview가 Google 공개되었습니다. 
- [groups.google.com link](https://groups.google.com/a/tensorflow.org/forum/m/?fbclid=IwAR2PlRIzPb8yEAHrZaF4v4t4IbbnIMUfDPccJKgP1GG-hpF5vGLkeHL8G4A#!topic/developers/aKdmUOiyzGM/discussion)

TF2.0은 무엇보다도 사용성과 생산성 개선에 맞추어 설계되었다고 하네요. TF의 열성적인 사용자로써 매우 기대가 큽니다. 
개인적으로 사용성에 있어서 가장 중요한것은 얼마나 "사용자 친화적인 API를 제공하는가?"라고 생각합니다. 
본 포스트에서는 TF2.0의 다른 점을 제쳐두고 `API사용 관점`에서 빠르게 리뷰해봤습니다. 

아래 슬라이드를 보시고 다양한 의견을 댓글로 남겨주시면 감사하겠습니다. 
TF2.0에 대한 리뷰는 지속적으로 업데이트 하도록 하겠습니다. :-)

### 요약
---------------------------------------
- tf2.0의 대표 high-level APIs는 tf.keras이다.
- low-level APIs는 Eager mode와 Graph mode 두 가지로 제공된다.  
    - Eager mode가 디폴트 이다. 
    - Graph mode는 tf.function + autograph로 pythonic 하게 제공될 것이다. 하지만 아직 완전하지 않다. 
    - tf.Session()은 은폐된다. tf.function으로 decorate된 함수들이 call될때 내부적으로 실행된다. 
- 기존 High-level APIs(tf.layers 등)은 tf.keras namespace로 옮겨갈 것이다. 
- 그동안 존재하였던 많은 APIs의 중복은 사라진다. 
- tf2.0에서 Custom tf.Estimator의 사용은 장려되지 않는다. 
- tf2.0에서는 Custom 모델에 대해서 tf.keras.Model의 subclassing이 장려된다. 
- tf1.x 코드를 2.0으로 업데이트하는 스크립트가 제공될 것이나 아직 테스트 중이다.
- tf2.0에서도 tf1.x APIs에 대한 하위호환성은 유지 된다. 


### Keywords
---------------------------------------
- tf.keras
- tf.function + autograph
- tf.eager

### Slide
---------------------------------------
<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<!-- this is the embed code provided by Google -->
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSA7C55q2Q4VH8BpI-ze-POX8I-6BW1e93nr4X1chnIByu1h4xLWZLCtgAiLO4Qruobzl3qIFTmED1N/embed?start=true&loop=true&delayms=10000" frameborder="0" width="720" height="380" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>


