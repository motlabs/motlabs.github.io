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
작년 WWDC를 보신 분은 아실지도 모르겠지만 WWDC17에서 [Core ML](https://developer.apple.com/kr/machine-learning/)과 [AR Kit](https://developer.apple.com/kr/arkit/)을 비롯한 재밌는 프레임워크들이 많이 나왔습니다. 그리고 올해 WWDC18에서는 Core ML 2와 AR Kit 2, Create ML등 ML과 AR쪽 프레임워크를 업그레이드 시켜 발표했는데요. 이 프레임워크를 사용해서 재밌는 예제들도 많이 나오고 있습니다.

[Magic Sudoku for iOS](https://magicsudoku.com/)<br>[![Magic Sudoku](/assets/images/ios-ml-posting-01/magicsudoku.gif)](https://itunes.apple.com/us/app/magic-sudoku/id1286979959?ls=1&mt=8)



[Inceptionv3를 사용한 CoreML+ARKit 예제](https://github.com/hanleyweng/CoreML-in-ARKit)<br>
![Core ML in AR Kit](/assets/images/ios-ml-posting-01/giphy.gif)


이번 글에서는 모바일에서 Core ML을 사용할 때 전체적인 흐름에대해 이야기하려고 하는데, 다음에 기회가되면 AR Kit도 다뤄보도록 하겠습니다.

## Core ML이란?
모바일에서 머신러닝을 실행시키려면 제일 먼저 Core ML에대해 알아야 합니다. 예상하듯 Core ML이란 머신러닝 프레임워크입니다. 보통 머신러닝 프레임워크라함은 TensorFlow, Caffe, PyTorch 이런게 있는데요. Core ML은 다른 툴과 비교했을때 몇가지 특징을 가집니다.
- 모바일용 머신러닝 프레임워크
- 애플 플랫폼 위에서만 동작<br>
☞ 애플의 모바일 기기에 최적화된 성능
- 추론만 가능<br>
☞ 보통의 머신러닝 툴은 **학습**과 **추론**, 두 단계로 나뉩니다.
- 편리한 사용성<br>
☞ 프로젝트에 모델을 넣는 방법
☞ 미리 제공된 전/후처리(특히 Vision 프레임워크의 이미지 변환)

### Core ML 기능 
Core ML은 크게는 두가지 종류의 기능을 제공합니다.
1. 내장된 모델 사용(Vision, NLP)
2. 커스텀 모델 사용

##### 내장된 모델 - Vision
- Face Detection: 얼굴 인식
- Face Landmarks: 얼굴 랜드마크 인식
- Image Registration: 이미지 변환
- Rectangle Detection: 사각형 인식
- Barcode Detection: 바코드 인식
- Text Detection: 글자 인식
- Object Tracking: 물체 추적


##### 내장된 모델 - NLP(Natural Language Framework)

- Language Identification: 언어 식별
- Tokenization(Word, Sentence, Paragraph): 토큰화
- Part of Speech
- Lemmatization
- Named Entity Recognition: 개체명 인식

#### 커스텀 모델
내장된 모델을 사용하면 따로 모델을 준비할 필요가 없고, 제공된 API로 편리하게 사용할 수 있습니다. 하지만 커스텀 모델을 사용해야한다면 이야기는 조금 달라집니다. **1)모델을 준비**하는 과정부터 **2)모델을 소스코드에 넣고**, **3)전처리**를 한 뒤에 **4)추론을 실행**시키면 결과를 받아서 **5)후처리**를 해야하는 일련의 과정들이 있습니다. 

### Core ML 구조
아래 그림은 머신러닝 툴로 모델을 만든 후에 모바일 프로젝트(Xcode)까지 불러오는 과정입니다. Xcode  프로젝트에 필요한 파일은 Core ML 모델(`.mlmodel` 포맷의 파일)이며, 이 모델은 Core ML 프레임워크가 해석하고 실행해 줍니다.
![Alt text](/assets/images/ios-ml-posting-01/1529830936112.png)
##### 1. TRAINING
준비된 데이터셋으로 학습을 시켜 모델을 만듭니다. 보통 모바일 개발자의 영역은 아니며 TensorFlow나 Caffe, turi 혹은 이번에 나온 Create ML 머신러닝 툴로 만들 수 있습니다. 사용한 툴에 따라서 각자 다른 포맷의 모델이 나오게 됩니다.
##### 2. CONVERSION
만들어진 모델을 Core ML 모델로 변환합니다. TensorFlow를 사용했다면 `.pb`나 `.ckpt`포맷의 모델이 나옵니다. 이 모델을 Core ML 모델(`.mlmodel`) 포맷의 모델로 변환시킵니다. 다양한 모델 변환기가 있는데, 아래 링크를 참고해서 필요한 변환기를 사용하면 되겠습니다. <br>
[![Alt text](/assets/images/ios-ml-posting-01/Screen Shot 2018-06-25 at 12.46.26 PM.png)](https://github.com/ysh329/deep-learning-model-convertor)<br>
[https://github.com/ysh329/deep-learning-model-convertor](https://github.com/ysh329/deep-learning-model-convertor)

저는 개인적으로 이 영역도 모델 개발자분께서 해주셔야한다고 생각하지만, 모바일 개발자가 맡게된다면 여러 이슈(특히 머신러닝 도메인 지식이 부족해 생기는 이슈..)에 부딪힐 수 있습니다.
##### 3. INFERENCING
이 부분은 모바일 개발자가 해야하는 영역입니다. Core ML 모델이 준비되었다는 가정에서 시작합니다. 주로 하는 작업은 전처리/후처리이며, 다음글에서 자세히 설명하도록 하겠습니다.

### 마치며
Core ML이 무엇인지와 전체적인 흐름에대해 살펴보았습니다. 다음 글에서는 커스텀 모델과 Core ML을 실제로 사용해본 예제 코드를 하나하나 설명해보겠습니다.

## 참고
- WWDC17에 Core ML 발표
	- [WWDC17 703 Session - Introducing Core ML](https://developer.apple.com/videos/play/wwdc2017/703/)
	- [WWDC17 710 Session - Core ML in depth](https://developer.apple.com/videos/play/wwdc2017/710/)
	- [WWDC17 506 Session - Vision Framework: Building on Core ML](https://developer.apple.com/videos/play/wwdc2017/506)
- WWDC18에 Core ML 2 발표
	- [WWDC18 708 Session - What’s New in Core ML, Part 1](https://developer.apple.com/videos/play/wwdc2018/708/)
	- [WWDC18 709 Session - What’s New in Core ML, Part 2](https://developer.apple.com/videos/play/wwdc2018/709/)
	- [WWDC18 717 Session - Vision with Core ML](https://developer.apple.com/videos/play/wwdc2018/717/)