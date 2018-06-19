---
layout: post
title: "TF Pattern Design (Week3)"
description: "Week3 Study Summary"
author: dygwak
date: 2018-06-19
tags: [TF Pattern study]
comments: true
share: true
---

## 발표1: 관련 tf API 설명

**Speaker : 이준호**

#### tf.layers

레이어를 짤 때 편하게 쓰는<br>
weight를 꺼내서 쓰고 싶을때는 고수준의 `tf.layers`를 사용하지 않고, 펼쳐서 사용.<br>
variable을 생성하지 않고 레이어를 <br>
`get_collection`으로 variable 가져와서 `tf.layers`에 자동으로 만들어준 변수에 접근 가능.<br>
get_collection<br>
☞ 딕셔너리같은것. tf에서 짠 코드를 여기에 모아줌. `tf.operation`이 저장되있는것 같음.<br>

ref: [Using High or Low level of TensorFlow](https://medium.com/trackin-datalabs/using-high-or-low-level-of-tensorflow-329089763f3c)

복잡한 구현은 layers를 쓰고, convolution을 커스텀해서 만들고싶을땐 풀어서 사용

개발자분은 본인이 미리 구현해서 layers같은 것을 이미 쓰고 있음

#### tf.estimator
구글에서 야심차게 준비하고 있는것 같음.<br>
wrapping up 하는 편한 툴.<br>
모델을 만들었고 optimizer를 만들<br>
불필요한 절차(세션열고, 실행하고, ...)를 생략해서 돌려볼 수 있음.<br>
training, inference 둘 다 가능함.<br>
// `tflearn.layers.estimator`와는 다름

estimator로 모델을 열고.

// 아직 짜진 코드가 없음..<br>
estimator를 사용하면 tensorboard를 볼때, 편하게 가능.

estimator하면 필요한 기능<br>
데이터를 넣는 부분 짜줘야함.<br>
모델을 불러옴(옵티마이제이션, 로스 계산)

커스텀 모델을 만들기 매우 어렵더라..<br>
// 아직 estimator를 사용하기엔 이른것 같음...<br>
// estimator를 쓰려다가 더 복잡할수도

// `tf.data`, `np`는 다른 포멧<br>
`tf.data`는 crossvalidation이 안됨.

#### tf.train
ref: [`tf.train` & `tf.test`](https://medium.com/trackin-datalabs/tf-train-tf-test-902c85b103e5)

트레이닝을 할 때 필요한 함수들을 모아놈

* optimizer
* ckpt를 어떻게 할 것 인지?
* exponetial_decay..?
* write_graph : pb파일 프리징할때 씀

사실 준호님도 optimizer, saver 정도만 쓰고 있음
학습 도중 일어나는 필요한 이벤트라던지 

#### tf.test
일반적으로는 쓸 일이 거의 없음. 그리고 잘 안 씀..
* `is_gpu_available(...)` gpu 쓸 수 있는지 
* `is_built_with_cuda(...) `

TFRecord
ref: [Convert to TFRecords dataset](https://medium.com/trackin-datalabs/convert-to-tfrecords-dataset-2087b0ffa4f5)

☞ 이미지를 모아서 한 파일로 저장 가능<br>
바이너리로 저장하기때문에 속도가 빨라짐. -> 이것때매 쓰기도함.<br>
데이터셋 관리하기가 편함, 용량도 작아짐. -> 한 파일로 저장하니.<br>
record로 바꿀땐 시간이 어느정도 걸림.<br>
트레이닝시 시간을 좀 단축시켜보겠다는 의미.<br>
// estimator도 tfrecord로 불러오는걸 지향함<br>
옵션을 써야함(`gz` 파일로 압축시키는 옵션을 쓰면 용량을 조금 줄일 수 있음)<br>
☞ 압축된 `gz`파일 그대로 사용 가능(`tfrecord`가 디코딩해줌)<br>

짜야할게 많을듯. 공식 홈페이지에서 사용법을 

단점이 있음
* 단일 이미지당 어느정도 이상 사이즈가 커지면(128*128*128~) 에러가 나옴!!! 헐.
* 변환시키기가 익숙하기 전까지 복잡
* `hdf5` 포멧을 이렇게 쉽게 접근할 수 있는데 (`hdf_file['folder1']['inner_folder']`), `tfrecord`는 이렇게 편하지 않음.
* `tfrecord` 파일 이름을 디렉토리명처럼 만드는 편법(`data/image`, `info/config`...)
* 직접 들어갈 수 없음.
* 옵션은 한 파일이 있을때 섞냐, 안 섞냐 이것밖에 안됨.
* 전체 데이터가 몇개인지 알려면 `tf.python_io.tf_record_iterator`를 돌려봐야 알 수 있음.

#### tf.data
ref: [data input 만들기](https://medium.com/trackin-datalabs/data-input-%EB%A7%8C%EB%93%A4%EA%B8%B0-74bb5c1ce52f)<br>
ref: [data_manager (mnist).ipynb](https://github.com/motlabs/mot-dev/blob/180506_tfdata_jhlee/lab11_tfdata_example/data_manager%20(mnist).ipynb)

빠르다함. <br>
epoch을 얼마나 줄지 알게되면 repeat()을 사용<br>
epoch 단위 for 루프마다 `tf.data` 불러오면 안 좋음.<br>
// `np` vs `TFRecord` : 서로 다른 데이터 자료형 

#### tf.gfile
ref: [Manage Files with TensorFlow](https://medium.com/trackin-datalabs/manage-files-with-tensorflow-7f31e8fd99d2)

☞ python의 os, copy, glob, exists 같은 모듈을 tf용으로 만든것

#### tf.saved_model
ref: [Save and Load trained Model](https://medium.com/trackin-datalabs/%ED%95%99%EC%8A%B5%ED%95%9C-%EB%AA%A8%EB%8D%B8-save-%EB%B0%8F-load-%ED%95%98%EA%B8%B0-b78ae5de4964)

`tf.saved_model`은 `pb`파일로 변환할때 씀(나아아중에 쓰게될듯)

`.ckpt`

* weight만 저장이 됨.
* 노드의 위치
* 그래프의 구조는 저장 X
* 변수(variable

`.pb`: 구조만 있는것, frozen graph
* freezing 시킨 파일
* `Variable`을 `Constant`로 만든겅

##### 저장시
```python
# Add ops to save and restore all the variables.
saver = tf.train.Saver()
with tf.Session() as sess:
    save_path = saver.save(sess, "/tmp/model.ckpt") # 준비
    ...
    
    for step in iterations:
        saver.save(sess, 'checkpoint.model'), global_step=step) # weight 저장
```
##### 로드시
```python
# Add ops to save and restore all the variables.
saver = tf.train.Saver()
with tf.Session() as sess:
    saver.restore(sess, "/tmp/model.ckpt")
    ...
```
#### Blog



## 발표2: TF 추상화와 간소화, 모델 엑스포트와 서빙

**Speaker : 이규복**

### Chapter 7, 텐서플로 추상화와 간소화

#### TFLearn

- Tensorflow API와 유사함 
- python 기본 array를 사용 
- `ckpt`로 저장 가능(frozen graph로 만들 수 있는것) 

#### Keras

- `TFLearn`과 비슷함 
- 절차형/함수형 원하는 스타일로 코드 짤 수 있음? 
- Numpy를 사용 
- `hdf5` 포멧으로 저장 가능 
- 실제 keras에 api가 `tf.keras`에는 없을 수도 있음 

#### TF.Slim

- `Keras`와 `tf.slim`는 둘 다 내부적으로 Tensorflow를 사용함 
- cnn에 특화된 라이브러리 
- 깊은 layer를 쌓을때 간편하게 가능 
- `tf.nn tf.contrib.framework` 합친.. 
- 미리 `slim`으로 학습된 모델 사용할 수 있음 
- `with` 구문으로 `arg_scope`를 만들 수 있음 

// Tensorflow에서는 `feed_dict`를 써야함. `numpy`를 바로 쓸 순 없음.  

[TFLearn vs Keras: Which One Should You Use?](https://progur.com/2018/04/tflearn-vs-keras-which-better.html)

### Chapter 10 모델 엑스포트와 서빙

저장

- 수동으로 저장 

  ☞ `numpy` 사용, `.npz` 확장자 

  ☞ 불편스. 쓰지말죠. 

- `tf.saver`로 저장 

- - `tf.train.Saver()`로 저장 
  - `saver.restore()`로 불러오기 
  - 변수 이름이 딱 맞아야 저장/불러오기 가능 
  - `tf.reset_default_graph`를 사용? 뭐 충돌 없애주는 것일듯. 

데이터 로딩을 여러가지 api로 간소화 추상화 

#### Slide

<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<!-- this is the embed code provided by Google -->
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSEmHKWnIVz56o6csqbEfzmeDk7OngLeNzgp2RBuOYpDsyOSnHK7pGrTXFKEA_vtqXMBrNiOIhe68kE/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="583" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

## Issues

- 