---
layout: post
title: iOS 머신러닝 프레임워크 - Core ML
description: "Introduction"
author: dygwak
date: 2018-06-25
tags: [iOS, CoreML, Machine Learning for Mobile]
comments: true
subdir: postformat
thumbnail: "/assets/images/ios-ml-posting-01/1529830936112.png"
share: true
---

## 들어가며
올해 열린 WWDC 2018에서는 Core ML 2와 AR Kit 2, Create ML등 [머신러닝(ML)](https://developer.apple.com/kr/machine-learning/)과 [증강현실(AR)](https://developer.apple.com/kr/arkit/) 프레임워크를 업그레이드 시켜 발표했습니다. Core ML과 AR Kit은 작년 WWDC 2017에서 처음 발표한 프레임워크로 1년만에 버전 2를 낸다는것은 애플이 야심차게 준비해오고 있다는 의미이기도 합니다.

이러한 맥락에서 기계학습과 증강현실을 활용한 재밌있는 예제들도 많이 나오고 있습니다.

| [![Magic Sudoku](/assets/images/ios-ml-posting-01/magicsudoku.gif)](https://itunes.apple.com/us/app/magic-sudoku/id1286979959?ls=1&mt=8) | ![Core ML in AR Kit](/assets/images/ios-ml-posting-01/giphy.gif) |
| --- | --- |
| [CoreML+ARKit 예제1](https://magicsudoku.com/) | [CoreML+ARKit 예제2](https://github.com/hanleyweng/CoreML-in-ARKit) |

이번 글에서는 모바일에서 Core ML을 사용할 때 전체적인 흐름에대해 이야기하려고 하는데, 언제 기회가되면 AR Kit도 다뤄보도록 하겠습니다.

## Core ML이란?
iOS 환경에서 머신러닝을 실행하려면 Core ML에대해 먼저 알아야합니다. Core ML이란 학습된 모델을 애플 플랫폼 위에서 실행시킬 수 있는 머신러닝 프레임워크입니다. iOS는 물론이고 macOS, tvOS, watchOS에서도 Core ML을 사용할 수 있습니다.
보통 일반적인 머신러닝 툴은 TensorFlow, Caffe, PyTorch 등을 떠올릴텐데요. 다른 머신러닝 툴과 비교했을때 Core ML의 특징을 살펴보겠습니다.
- **모바일용** 머신러닝 프레임워크
- 애플 플랫폼 위에서만 동작<br>
  ☞ 애플의 모바일 기기에 최적화된 성능
- **추론**만 가능<br>
  ☞ 보통의 머신러닝 툴을 사용시 학습과 추론, 두 단계로 나뉩니다.
- **Core ML용 모델** 필요
- 편리한 **사용성**<br>
  ☞ 프로젝트에 모델을 넣는 방법
  ☞ 미리 제공된 전/후처리(특히 Vision 프레임워크의 이미지 변환)

### 모델 흐름도
아래 흐름도는 커스텀 모델을 사용할 때 머신러닝 모델이 Xcode 프로젝트까지 흘러가는 과정입니다. 최종적으로 Xcode에서 필요로하는 모델 포맷은 Core ML 모델(`.mlmodel`)입니다. 참고로 Core ML 프레임워크에서 제공하는 내장된 모델을 사용한다면 학습과정과 변환과정을 생략할 수 있습니다.

![Alt text](/assets/images/ios-ml-posting-01/1529830936112.png)

##### 1. TRAINING(학습)
준비된 데이터셋으로 학습을 시켜 모델을 만듭니다. 보통 모바일 개발자의 영역은 아니며 TensorFlow나 Caffe, turi 혹은 이번에 나온 Create ML 머신러닝 툴로 만들 수 있습니다. 사용한 툴에 따라서 각자 다른 포맷의 모델이 나오게 됩니다.
##### 2. CONVERSION(변환)
만들어진 모델을 Core ML 모델로 변환합니다. TensorFlow를 사용했다면 `.pb`나 `.ckpt` 확장자의 모델이 만들어집니다. 이 모델을 Core ML 모델(`.mlmodel`) 포맷의 모델로 변환시킵니다. 다양한 모델 변환기가 있는데, 아래 링크를 참고해서 필요한 변환기를 사용하면 되겠습니다. <br>
[![Alt text](/assets/images/ios-ml-posting-01/Screen Shot 2018-06-25 at 12.46.26 PM.png)](https://github.com/ysh329/deep-learning-model-convertor)<br>
[https://github.com/ysh329/deep-learning-model-convertor](https://github.com/ysh329/deep-learning-model-convertor)

저는 개인적으로 이 영역도 모델 개발 담당에서 해주셔야한다고 생각하지만, 모바일 개발자가 맡게된다면 여러 이슈에 부딪힐 수 있습니다(특히 머신러닝 도메인 지식이 부족해 생기는 이슈).
##### 3. INFERENCING(추론)
주로 하는 작업은 전처리/후처리입니다. 커스텀 모델을 사용할 경우 Core ML 모델이 필요하고, 내장된 모델을 사용할 경우  다음글에서 자세히 설명하도록 하겠습니다.

### Core ML 기능 
Core ML은 크게는 두가지 종류의 기능을 제공합니다.
1. 내장된 모델 사용
2. 커스텀 모델 사용

#### 내장된 모델

|             **Vision**             | **NLP**<br>(Natrual Language Framework) |
| :--------------------------------: | :-------------------------------------: |
|     Face Detection(얼굴 인식)      |   Language Identification(언어 식별)    |
| Face Landmarks(얼굴 랜드마크 인식) |          Tokenization(토큰화)           |
|  Image Registration(이미지 변환)   |             Part of Speech              |
|  Rectangle Detection(사각형 인식)  |              Lemmatization              |
|   Barcode Detection(바코드 인식)   |  Named Entity Recognition(개체명 인식)  |
|     Text Detection(글자 인식)      |                    -                    |
|     Object Tracking(물체 추적)     |                    -                    |

#### 커스텀 모델
내장된 모델을 사용하면 따로 모델을 준비할 필요가 없고, 제공된 API로 편리하게 사용할 수 있습니다. 하지만 커스텀 모델을 사용해야한다면 이야기는 조금 달라집니다. 모델 흐름도 부분에서 설명한 내용처럼 **1)모델을 준비**하고 **2)모델을 소스코드에 넣어서**, **3)전처리**를 한 뒤에 **4)추론을 실행**시키면 결과를 받아서 **5)후처리**를 해야하는 일련의 과정이 필요합니다. 

## 참고
- WWDC17에 Core ML 발표
	- [WWDC17 703 Session - Introducing Core ML](https://developer.apple.com/videos/play/wwdc2017/703/)
	- [WWDC17 710 Session - Core ML in depth](https://developer.apple.com/videos/play/wwdc2017/710/)
	- [WWDC17 506 Session - Vision Framework: Building on Core ML](https://developer.apple.com/videos/play/wwdc2017/506)
- WWDC18에 Core ML 2 발표
	- [WWDC18 708 Session - What’s New in Core ML, Part 1](https://developer.apple.com/videos/play/wwdc2018/708/)
	- [WWDC18 709 Session - What’s New in Core ML, Part 2](https://developer.apple.com/videos/play/wwdc2018/709/)
	- [WWDC18 717 Session - Vision with Core ML](https://developer.apple.com/videos/play/wwdc2018/717/)
