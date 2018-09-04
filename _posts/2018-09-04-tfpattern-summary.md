---
layout: post
title: "TF Pattern Study Summary"
description: "An example"
author: howtowhy
date: 2018-09-04
tags: [TF Pattern study]
comments: true
subdir: postformat
thumbnail: mot_logo.png
share: true
---

## TF pattern study contents summary (MoT Lab)

MoT Lab Github : [https://github.com/motlabs]

TF Pattern Study Github : [https://github.com/howtowhy/mot-tf-codepattern-study]

 

![Alt text](https://user-images.githubusercontent.com/10994112/45034300-0f1be400-b092-11e8-9204-db282648d466.jpg "MoT LAB")



**Date**: 2018. 06

**Study Director :** 양서연

**Advisors :** 강재욱, 이준호, 김보섭

**Members :** 백윤범, 오시영, 류지은, 이규복, 김형섭, 이승재

**Supported by :** MoT Lab, 모두의 연구소



## About

- Tensorflow 의 기본 문법을 익히고 심화된 코드 패턴을 익힌다.
- input 전처리와 파이프라인 처리를 위한 공부
- model 재사용과 성능을 높여주는 코드 공부
- 학습과정 visualization 을 위한 tensorboard 사용법
- 모델 학습 결과 저장을 위한 코드 공부
- 분산 처리를 위한 multi GPU
- CNN / RNN / LSTM model study



 MoT Tensorflow Pattern study 는 다음 교재를 이용하여 진행 되었습니다. 

**< 기본 교재 : 러닝 텐서플로 - 톰호프, 예헤즈켈 레셰프, 이타이 리더 지음 / 한빛 미디어 >**

<iframe src="https://book.naver.com/bookdb/book_detail.nhn?bid=13465439" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>


매 스터디 내용은 *해당 교재 Chapter 요약과 어드바이서들의 강의 slide*  두가지로

발표하며 진행되었고, 총 4회에 걸쳐 진행되었습니다. 



 본 블로그를 참고하여 공부하시려는 분들께는 러닝텐서플로 책의 해당 챕터를 공부하신 후, 

요약 발표자료를 확인하시고 추가적으로 제시된 발표자료로 공부해나가시길 추천합니다.



-----------------------------------



## < TF Study day1 "안녕 텐서플로 / 입맞에 맞는 input 처리" >

* 러닝 텐서플로 해당 단원 : Chapter 1, 2, 3

* 스터디 목표 : 
  * 텐서플로의 개괄

  * 텐서플로 설치에서 실행 까지

  * 텐서플로의 그래프 이해하기

  * 텐서플로 기본 문법 뽀개기

  * 관련 API : 

    ```
    - tf.train
    - tf.test
    - tf.estimator
    - tf.saved_model 
    - tf.layers
    - (tf.get_variable)
    - (tf.variable_scope)
    ```

* 스터디 참석자 : 양서연, 강재욱, 이준호, 백윤범, 이규복, 이승재, 김형섭

* 발표자 : 양서연, 강재욱

* 발표내용 : 

  ### 1) 양서연 (러닝 텐서 플로 Chapter 1, 2, 3)

  ### : 텐서플로 기초 / 입력파이프라인 (TFRecord, Queue)

  ```
  - Hello Tensorflow
  - Interactive Session
  - 입력 파이프라인
  - TFRecord
  - Queue
  - Multi Thread / Coordinator / QueueRunner
  ```

  <style>
  .responsive-wrap iframe{ max-width: 100%;}
  </style>
  <div class="responsive-wrap">
  <!-- this is the embed code provided by Google -->
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vS1XZSl4WFEELAf9V1TLehuT0oCufbY-dIC9TxKg5MVMGhn9p1vZ4Z_QX2EZZt-1Q5P7msOGmMAzuqB/embed?start=true&loop=false&delayms=10000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
  </div>
  
  ### 2) 강재욱 : Tensorflow 기초 문법 / 코드 Structure / 코드 Pattern 철학
    ```
    1) Tensorflow: The first Step
    - Tensorflow 개요
    - Why Tensorflow
    - Tensorflow 설치
    - 계산그래프와 텐서
    - tf.Variable() Vs. tf.constant()
    - tf.Variable() Vs. tf.get_variable()
    - tf.variable_scope()와 tf.name_scope()
    - tf.placeholder()
  
    2) TF code Structure Overview
    - Dataset의 종류
    - 머신러닝 훈련 단계
    - Tensorflow에서 머신러닝 훈련 
  
    3) TF Code Pattern Design 철학
    - 데이터셋 준비하는 코드 -> `data_loader.py`, `preprocess_data.py`
    - 러닝 파라미터 설정하기  -> `train_config.py`
    - 계산 그래프 정의하는 코드 ->  `model.py` , `model_config.py`
    - 성능 측정 모델 + 모델 훈련시키기 -> `trainer.py`
    - 모델 평가하기 -> `eval.py`
    ```
    <div class="responsive-wrap">
    <!-- this is the embed code provided by Google -->
    <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vT1zTUU36nekwbv7kKwPYTMn-CGbX-7B3Yfz_dzBmb0nOrkM1kqXBtDZRnFIXH_UNmhj2dbuY8gE8Ze/embed?start=false&loop=false&delayms=60000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
    </div>



### < TF Study day1 과제>

* 러닝 텐서플로 Chapter 1,2,3 공부하기

* Tensorflow 설치 및 기본 코드 익혀오기

* 데이터 input 전처리 코드 만들어 보기

  * 참고 코드 : 

    **1) 강재욱 github :**   [data loader (tf.gfile)](https://github.com/jwkanggist/tf-cnn-model/blob/master/mnist_data_loader.py)

    **2) 이준호 github :**   [data_manager (tf.data)](https://github.com/motlabs/mot-dev/blob/180506_tfdata_jhlee/lab11_tfdata_example/data_manager%20(mnist).ipynb) 

    **3) Learning Tensorflow github :**  [queue, multithread, tf.python_io.Tfrecord](https://github.com/Hezi-Resheff/Oreilly-LearningTensorFlow/tree/master/08__queues_threads)


  * 참고코드를 이용하여 자신만의 CNN을 위한 MNIST 입력처리 코드를 자신의 

    깃헙에 업로드 하기 아래의 코드를 작성해 본다.

    ```
    - data_loader.py : 데이터를 빠르게 불러와 메모리에 로드하는 코드
    - input_ops.py : 사용 모델 인풋 형식에 맞게 변환하는 코드 
      (여러 데이터를 쉽게 바꿔끼고 섞을 수 있어야한다.)
    - preprocess_data.py : 사용 모델에 필요한 인풋 전처리 
    ```

----------------------------------------------------


## < TF Study day2  "model 만들기, 라이브러리 사용해보기">

- 러닝 텐서플로 해당 단원 : Chapter 7, 10 

- 스터디 목표 : 
  - Model training loop 및 pipeline을 구현한다 

    텐서플로 추상화/간소화와 라이브러리를 사용해본다.

    - Optimizer

    - stepwise validation

    - full validation

    - pre-trained model loading

    - check-point saving

    - Logging

    - 관련 API :

      ```
      - tf.train
      - tf.test
      - tf.estimator
      - tf.saved_model
      - tf.layers
      - (tf.get_variable)
      - (tf.variable_scope)
      ```

- 참석자 : 양서연, 이준호, 백윤범, 곽도영, 강재욱, 이규복, 김보섭, 류지은, 오시영, 이승재

- 발표자 : 이준호, 이규복

- 발표내용 : 

  ### 1) 이준호 TF API : Model train / test 에서 사용하는 API 들 정리 

  아래 요약 내용 보다 자세한 내용은 링크의 **준호님 블로그** 에서 확인하실 수 있습니다.

   tf.layers
  ---
  레이어를 구성할때 사용하는 high-level api set

  ```bash
  - 레이어 구성에 있어서 `1)variable의 생성`과 `2)연결`을 한 줄의 api로 구현가능
  - variable에 직접 접근이 필요한 경우 `get_collection()`을 사용
  - 여기서 `get_collection()`이란 
  - 복잡한 구현은 `tf.layers`를 쓰고, convolution을 커스텀해서 만들고 싶을땐 `tf.nn` 사용
      - 사실 거의 `tf.layers`로 해결됨 
  ```

  - ref: [정겨울님 블로그: Using High or Low level of TensorFlow](https://medium.com/trackin-datalabs/using-high-or-low-level-of-tensorflow-329089763f3c)

  tf.estimator
  ------

  구글에서 야심차게 준비하고 있는 scikest learn와 같은 정말 high-level api

  - 주의!: `tflearn.layers.estimator`와는 다름

  ```bash
  - 1) 모델을 만드는 것에서 부터 
  - 2) loss + optimizer를 설정
  - 3) training + inference 하는 것 까지 통합api로 지원함
  ```

  단점 : 

  ```bash
  - 굉장히 정형화 된 모델에 대해서만 지원 (현재까지는!)
  - 커스터 마이제이션이 번거로움 (구글에서 원하는 포맷에 맞게 코딩해야함)
  - tensorboard과 호환성이 매우 좋음
  ```

  - TF 공식문서: [https://www.tensorflow.org/api_docs/python/tf/estimator](https://www.tensorflow.org/api_docs/python/tf/estimator)

  tf.train & tf.test
  ------

  training & testing 할때 필요한 api를 모아놓음

  - TF 공식문서:
    - `tf.train`: [https://www.tensorflow.org/api_docs/python/tf/train](https://www.tensorflow.org/api_docs/python/tf/train) 
    - `tf.test`: [https://www.tensorflow.org/api_docs/python/tf/test](https://www.tensorflow.org/api_docs/python/tf/test)
  - ref: [정겨울님 블로그:`tf.train` & `tf.test`](https://medium.com/trackin-datalabs/tf-train-tf-test-902c85b103e5)

  TFRecord
  ------

  데이터 TF에서 빠르게 로드 할 수 있는 binary 포맷. 
  데이터의 io시간을 단축해서 트레이닝시 시간을 좀 단축시켜보겠다는 의미

  장점 : 

  ```bash
  - 바이너리로 저장하기때문에 속도가 빨라짐
  - 데이터셋 관리하기가 편함, 용량도 작아짐
  - TFrecord로 변환할 때 시간이 어느정도 걸림
  - tf.Session()안에서 tf.data api에 의해서 로드
  - 옵션을 써야함(`gz` 파일로 압축시키는 옵션을 쓰면 용량을 조금 줄일 수 있음)
      ☞ 압축된 `gz`파일 그대로 사용 가능(`tfrecord`가 디코딩해줌)
  ```

  단점 : 

  ```bash
  - 단일 이미지당 어느정도 이상 사이즈가 커지면(128*128*128~) 에러가 나옴!!! 헐.
  - 변환시키기가 익숙하기 전까지 복잡
  - `hdf5` 포멧을 이렇게 쉽게 접근할 수 있는데 (`hdf_file['folder1']['inner_folder']`), `tfrecord`는 이렇게 편하지 않음.
  - `tfrecord` 파일 이름을 디렉토리명처럼 만드는 편법(`data/image`, `info/config`...)
  - 직접 들어갈 수 없음.
  - 옵션은 한 파일이 있을때 섞냐, 안 섞냐 이것밖에 안됨.
  - 전체 데이터가 몇개인지 알려면 `tf.python_io.tf_record_iterator`를 돌려봐야 알 수 있음.
  ```

  - ref: [정겨울님 블로그: Convert to TFRecords dataset](https://medium.com/trackin-datalabs/convert-to-tfrecords-dataset-2087b0ffa4f5)

  tf.data
  ------

  장점 : 

  ```
  - 배치별로 일일이 따로 뽑아서 내보내지 않아도 된다.
  - 메모리 상으로 더 가볍고 빠르게 해준다.
  - tf.records format 으로도 더 쉽게 로드하게 해준다. 
  ```

  - ref: [정겨울님 블로그: data input 만들기](https://medium.com/trackin-datalabs/data-input-%EB%A7%8C%EB%93%A4%EA%B8%B0-74bb5c1ce52f)<br>
  - ref: [data_manager (mnist).ipynb](https://github.com/motlabs/mot-dev/blob/180506_tfdata_jhlee/lab11_tfdata_example/data_manager%20(mnist).ipynb)

  tf.gfile
  ------

  python의 os, copy, glob, exists 같은 모듈을 tf용으로 만든것
   - ref: [정겨울님 블로그: Manage Files with TensorFlow](https://medium.com/trackin-datalabs/manage-files-with-tensorflow-7f31e8fd99d2)

  ### 2) 이규복 (러닝 텐서 플로 Chapter 7, 10 요약) : TF 에서 사용 가능한 라이브러리들을 알아보자!

  TF Learn
  ------

  ``` 
  - Tensorflow API와 유사함 
  - python 기본 array를 사용 
  - `ckpt`로 저장 가능(frozen graph로 만들 수 있는것) 
  ```

  tf.keras
  -------

  ```
  - TFLearn`과 비슷함 
  - 절차형/함수형 원하는 스타일로 코드 짤 수 있음? 
  - Numpy를 사용 
  - `hdf5` 포멧으로 저장 가능 
  - 실제 Keras에 api가 `tf.keras`에는 없을 수도 있음 
  ```

  - 읽을 거리: [TFLearn vs Keras: Which One Should You Use?](https://progur.com/2018/04/tflearn-vs-keras-which-better.html)

  tf.slim
  ------------------------------------------------

  ```
  - tf.keras`와 `tf.slim`는 둘 다 내부적으로 Tensorflow를 사용함 
  - cnn에 특화된 라이브러리 
  - 깊은 layer를 쌓을때 간편하게 가능 
  - `tf.nn tf.contrib.framework` 합친.. 
  - 미리 `slim`으로 학습된 모델 사용할 수 있음 
  - `with` 구문으로 `arg_scope`를 만들 수 있음 
  ```

  <style>
  .responsive-wrap iframe{ max-width: 100%;}
  </style>
  <div class="responsive-wrap">
  <!-- this is the embed code provided by Google -->
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSEmHKWnIVz56o6csqbEfzmeDk7OngLeNzgp2RBuOYpDsyOSnHK7pGrTXFKEA_vtqXMBrNiOIhe68kE/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
  </div>



## <TF Study day2 과제> 

* 러닝 텐서플로 Chapter 7, 10 공부

* 자신만의 CNN 모델 만들어보기 

* 자신만의 추상화, 라이브러리를 통해 간소화 된 CNN 코드를 깃헙에 업로드하기

  * 참고코드

      **1) 강재욱님 github :** [CNN (`run_lenet5_save_pb_ckpt_with_tfboard.py`로 실행)](https://github.com/jwkanggist/tensorflowlite)
      
      **2) Learning Tensorflow github :** [Oreilly convolutional neural networks](https://github.com/Hezi-Resheff/Oreilly-Learning-TensorFlow/tree/master/04__convolutional_neural_networks)
      
      **3) Learning Tensorflow github :** [Oreilly abrtraction]( https://github.com/Hezi-Resheff/Oreilly-Learning-TensorFlow/tree/master/07__abstractions)
      
      **4) 정찬희님 keras 코드**

  * 작성해야 할 코드

    ```
    - train.py : training 코드
    - eval.py : evaluation 코드
    ```



--------------------------------------------------------



##  <TF Study day3 "시계열 데이터 다뤄보기 / Tensorboard ">

* 러닝 텐서플로 해당 단원 : Chapter 5, 6

* 스터디 목표 : 

  * 텐서 보드 시각화와 시계열 데이터를 다뤄보자

  * 관련 tf API:

    ```
    - tf.nn
    - Tensorboard summary
    ```

* 참석자 : 양서연, 이준호, 백윤범, 곽도영, 강재욱, 김보섭, 류지은, 오시영, 이승재, 김형섭

* 발표자 : 양서연, 류지은, 이준호, 김보섭

* 발표내용 : 

  ### 1) 양서연 : RNN , LSTM , ATTENTION 이론 파헤치기

  ```
  - RNN
  - Bi-directional RNN
  - Sequence to Sequence
  - LSTM
  - Attention
  ```

  <style>
  .responsive-wrap iframe{ max-width: 100%;}
  </style>
  <div class="responsive-wrap">
  <!-- this is the embed code provided by Google -->
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTlHpaHyVWuglvdwrxSEqNm8luAem6LEl6SliY2ZcE7dV_XZeRAk1vtP913ogWqAhNvnV-sWC6uB2Te/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
  </div>

  ### 2) 류지은 (러닝 텐서플로 Chapter 5, 7 요약) 

  ### : TF RNN / LSTM API 살펴보기

   ```
  - tf.scan
  - tf.nn.dynamic
  - tf.contrib.rnn.BasicRNNCell
  - tf.contrib.rnn.MultiRNNCell
  - tf.contrib.rnn.BasicLSTMCell
   ```
  <style>
  .responsive-wrap iframe{ max-width: 100%;}
  </style>
  <div class="responsive-wrap">
  <!-- this is the embed code provided by Google -->
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vS6iUPjZoze-pfS6oU7581bBF4QqNtdrElhfPiNfp0PL74wCfF2QuSjEqhXtN3Y4-rrj1yRESHpq07b/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
  </div>

  ### 3)  이준호 : Tensorboard 로 시각화 해보기

  ```
  무엇을 보고 싶은가
  tf.summary.scalar(name, scalar)
  tf.summary.image(name, image)
  tf.summary.histogram(name, histogram)
  
  어디에 기록하고 싶은가
  tf.summary.merge_all()
  tf.summary.merge(summaries)
  tf.summary.FileWriter(log_dir, graph)
  
  언제 마다 기록하고 싶은가
  summary = sess.sun(merge)
  writer.add_summary(summary, global_step)
  ```

  * [텐서보드 왜 사용할까 ? ](https://medium.com/trackin-datalabs/tensorboard-tensorboard-%EA%B8%B0%EC%B4%88-6163e1642bb0)
  * [텐서보드의 Histogram의 이해 ](https://medium.com/trackin-datalabs/tensorboard-tensorboard-%EA%B8%B0%EC%B4%88-6163e1642bb0)
  * [텐서보드 간단히 시작하기](https://medium.com/trackin-datalabs/tensorboard-%EA%B0%84%EB%8B%A8%ED%9E%88-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-18a4fda2efb1)

  ### 4)  (김보섭) : RNN, LSTM 코딩 제대로 알아보기 (백수콘)

  ```
  - RNN
  - LSTM
  - GRU
  - Bi-directional
  - Stacked 
  - Stacked Bi-directional
  ```

  - [발표자료링크](https://drive.google.com/drive/folders/1ZDMJwMRID6KqEFzTPcALC1W0y0wfg-B1)
  - [nbvierwer jupyter material](https://nbviewer.jupyter.org/github/aisolab/CS20/blob/master/Lec11_Recurrent%20Neural%20Networks/To%20quickly%20implementing%20RNN.ipynb)
  - [aisolab-c20 github repo](https://github.com/aisolab/CS20)



## <TF Study day3 과제> 

* L.T. Chapter 5, 6 공부

  * 참고코드

     **1) 김보섭님 github** :  [RNN, LSTM API]( https://github.com/aisolab/CS20)

     **2) Learning Tensorflow github** : [Text and visualization](https://github.com/Hezi-Resheff/Oreilly-Learning-TensorFlow/tree/master/05__text_and_visualizations)

     **3) Learning Tensorflow github** : [word embedding and rnns](https://github.com/Hezi-Resheff/Oreilly-Learning-TensorFlow/tree/master/06__word_embeddings_and_rnns)

* 참고코드를 이용하여 시계열 데이터를 처리하는 rnn / lstm 구현해보기
* 텐서보드로 시각화 해보기

 

--------------------------------------------------



## <TF Study day4 "모델 구조화, 분산처리, Hyper parameter">

* 러닝 텐서플로 해당단원 : Chapter A.1, 9

* 스터디 목표 : 
  - 모듈화 / 클래스 / 캡슐화
  - 명령줄 파라미터 받는 매커니즘
  - 데이터 병렬처리
  - 테스크 분산처리(gpu 나누기)
  - Hyper parameter 의 정의 및 종류

* 발표자 : 곽도영, 백윤범 

* 참석자 : 양서연, 백윤범, 곽도영, 이성진, 강재욱, 김보섭, 류지은, 오시영

* 발표내용 : 
  ### 1) 백윤범 : Hyper parameter 의 정의 및 종류
        
     ```
        - Hyperparameter 란
        - Hyperparameter Optimization
        - Bayesian Optimization
        - Model 평가, 성능추정
        - Model selection
        - K fold cross validation
     ```
  
   <style>
   .responsive-wrap iframe{ max-width: 100%;}
   </style>
   <div class="responsive-wrap">
   <!-- this is the embed code provided by Google -->
   <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRkH2uDd8fKQke6eLY0N_mDxgrpatqWLLpCFDxoYIR7g4hCXQGyMUK4IhZj3WTEFFXaLrwnuXiCSyAx/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
   </div>

  ### 2) 곽도영 :  (러닝 텐서플로 Chapter A.1, 9  요약)
  ```
   - Flags 메커니즘 소개 (Command Line 파라미터 받는 법)
   - 분산 텐서플로
   - 모델 구조화 (모듈화 / 클래스 / 캡슐화)
  ```

  <style>
  .responsive-wrap iframe{ max-width: 100%;}
  </style>
  <div class="responsive-wrap">
  <!-- this is the embed code provided by Google -->
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTW7DQiGj-57t5TAnmzINIDZhtqkqsT88s3GBRhDp9j1vnK69xgKJa_j553eo3z3Wm4egdxQxCYspPb/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
  </div>



## <TF Study day4 과제> 

*  러닝 텐서플로 Chapter A.1, 9 
*  참고 자료 및 코드

    **1) Code Pattern 최종욱/신범준 [Referenece slide](https://wookayin.github.io/TensorFlowKR-2017-talk-bestpractice/ko/#1)**
  
    **2) Learning Tensorflow github : [distributed tensorflow](https://github.com/Hezi-Resheff/Oreilly-Learning-TensorFlow/tree/master/09__distributed_tensorflow)**

* 참고코드를 이용하여 model부분을 모듈화 해보고 readability를 높이는 아래 코드를 작성해보자.
  * model.py
  * models/xxxnet.py
  * meta-parameter / model configuration 을 해보자
  * model.py
  * models/xxxnet.py 

--------------------------------------------------



## Picture of Study
![Alt text](https://user-images.githubusercontent.com/10994112/45034369-4d190800-b092-11e8-859b-e4d8d96b806b.jpg "Picture")

####                                       Thank you for TF Pattern Study Member :)

