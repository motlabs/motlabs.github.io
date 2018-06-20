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

> Reviewed and edited by Jaewook Kang


## 발표1: 잘쓰는 tf API 설명

**Speaker : 이준호**

#### tf.layers
---------------------------------------

레이어를 구성할때 사용하는 high-level api set

```bash
- 레이어 구성에 있어서 `1)variable의 생성`과 `2)연결`을 한 줄의 api로 구현가능
- variable에 직접 접근이 필요한 경우 `get_collection()`을 사용
- 여기서 `get_collection()`이란 
- 복잡한 구현은 `tf.layers`를 쓰고, convolution을 커스텀해서 만들고 싶을땐 `tf.nn` 사용
    - 사실 거의 `tf.layers`로 해결됨 
```
- ref: [정겨울님 블로그: Using High or Low level of TensorFlow](https://medium.com/trackin-datalabs/using-high-or-low-level-of-tensorflow-329089763f3c)


#### tf.estimator
---------------------------------------

구글에서 야심차게 준비하고 있는 scikest learn와 같은 정말 high-level api
- 주의!: `tflearn.layers.estimator`와는 다름

```bash
- 1) 모델을 만드는 것에서 부터 
- 2) loss + optimizer를 설정
- 3) training + inference 하는 것 까지 통합api로 지원함
```
단점은 항상 있음!
```bash
- 굉장히 정형화 된 모델에 대해서만 지원 (현재까지는!)
- 커스터 마이제이션이 번거로움 (구글에서 원하는 포맷에 맞게 코딩해야함)
- tensorboard과 호환성이 매우 좋음
``` 
- TF 공식문서: [https://www.tensorflow.org/api_docs/python/tf/estimator](https://www.tensorflow.org/api_docs/python/tf/estimator)


#### tf.train & tf.test
---------------------------------------

training & testing 할때 필요한 api를 모아놓음
- TF 공식문서:
    - `tf.train`: [https://www.tensorflow.org/api_docs/python/tf/train](https://www.tensorflow.org/api_docs/python/tf/train) 
    - `tf.test`: [https://www.tensorflow.org/api_docs/python/tf/test](https://www.tensorflow.org/api_docs/python/tf/test)
- ref: [정겨울님 블로그:`tf.train` & `tf.test`](https://medium.com/trackin-datalabs/tf-train-tf-test-902c85b103e5)


#### TFRecord
---------------------------------------

데이터 TF에서 빠르게 로드 할 수 있는 binary 포맷. 
데이터의 io시간을 단축해서 트레이닝시 시간을 좀 단축시켜보겠다는 의미

```bash
- 바이너리로 저장하기때문에 속도가 빨라짐
- 데이터셋 관리하기가 편함, 용량도 작아짐
- TFrecord로 변환할 때 시간이 어느정도 걸림
- tf.Session()안에서 tf.data api에 의해서 로드
- 옵션을 써야함(`gz` 파일로 압축시키는 옵션을 쓰면 용량을 조금 줄일 수 있음)
    ☞ 압축된 `gz`파일 그대로 사용 가능(`tfrecord`가 디코딩해줌)
```

단점이 있음

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


#### tf.data
---------------------------------------

**준호님 여기 내용 추가 필요**
- ref: [정겨울님 블로그: data input 만들기](https://medium.com/trackin-datalabs/data-input-%EB%A7%8C%EB%93%A4%EA%B8%B0-74bb5c1ce52f)<br>
- ref: [data_manager (mnist).ipynb](https://github.com/motlabs/mot-dev/blob/180506_tfdata_jhlee/lab11_tfdata_example/data_manager%20(mnist).ipynb)

#### tf.gfile
---------------------------------------

python의 os, copy, glob, exists 같은 모듈을 tf용으로 만든것
- ref: [정겨울님 블로그: Manage Files with TensorFlow](https://medium.com/trackin-datalabs/manage-files-with-tensorflow-7f31e8fd99d2)



## 발표2: TF 추상화와 간소화, 모델 엑스포트와 서빙

**Speaker : 이규복**
### Slide

<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<!-- this is the embed code provided by Google -->
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSEmHKWnIVz56o6csqbEfzmeDk7OngLeNzgp2RBuOYpDsyOSnHK7pGrTXFKEA_vtqXMBrNiOIhe68kE/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="380" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

### 요약
---------------------------------------

**TFLearn**
```bash
- Tensorflow API와 유사함 
- python 기본 array를 사용 
- `ckpt`로 저장 가능(frozen graph로 만들 수 있는것) 
```

**tf.keras**
```bash
- `TFLearn`과 비슷함 
- 절차형/함수형 원하는 스타일로 코드 짤 수 있음? 
- Numpy를 사용 
- `hdf5` 포멧으로 저장 가능 
- 실제 Keras에 api가 `tf.keras`에는 없을 수도 있음 

```
- 읽을 거리: [TFLearn vs Keras: Which One Should You Use?](https://progur.com/2018/04/tflearn-vs-keras-which-better.html)

**TF.Slim**
```bash
- `tf.keras`와 `tf.slim`는 둘 다 내부적으로 Tensorflow를 사용함 
- cnn에 특화된 라이브러리 
- 깊은 layer를 쌓을때 간편하게 가능 
- `tf.nn tf.contrib.framework` 합친.. 
- 미리 `slim`으로 학습된 모델 사용할 수 있음 
- `with` 구문으로 `arg_scope`를 만들 수 있음 
```

## Issues
- 이슈 없음