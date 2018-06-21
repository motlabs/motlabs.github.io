---
layout: post
title: "TF Pattern Design (Week2)"
description: "Week2 Study Summary"
author: jwkang
date: 2018-06-11
tags: [TF Pattern study]
comments: true
share: true
---

## About
## 발표1: tf.data, tf.gflie, tf.python_io.TFrecord
**Speaker: SeoYeon YANG**

```
- Hello Tensorflow
- Interactive Session
- 입력 파이프라인
- TFRecord
- Queue
- Multi Thread / Coordinator / QueueRunner
```
#### Slide
<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<!-- this is the embed code provided by Google -->
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vS1XZSl4WFEELAf9V1TLehuT0oCufbY-dIC9TxKg5MVMGhn9p1vZ4Z_QX2EZZt-1Q5P7msOGmMAzuqB/embed?start=true&loop=false&delayms=10000" frameborder="0" width="720" height="380" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

## 발표2: TF fundamental, Code structure overview, TF Pattern design philosophy, and Lack Lenet5 Tf model
**Speaker : Jaewook Kang**

1) Tensorflow: The first Step

```
- Tensorflow 개요
- Why Tensorflow
- Tensorflow 설치
- 계산그래프와 텐서
- tf.Variable() Vs. tf.constant()
- tf.Variable() Vs. tf.get_variable()
- tf.variable_scope()와 tf.name_scope()
- tf.placeholder()
```

2) TF code Structure Overview

```
- Dataset의 종류
- 머신러닝 훈련 단계
- Tensorflow에서 머신러닝 훈련 
```

3) TF Code Pattern Design 철학

```
- 데이터셋 준비하는 코드 -> `data_loader.py`, `preprocess_data.py`
- 러닝 파라미터 설정하기  -> `train_config.py`
- 계산 그래프 정의하는 코드 ->  `model.py` , `model_config.py`
- 성능 측정 모델 + 모델 훈련시키기 -> `trainer.py`
- 모델 평가하기 -> `eval.py`
```

#### Slide
<style>
.responsive-wrap iframe{ max-width: 100%;}
</style>
<div class="responsive-wrap">
<!-- this is the embed code provided by Google -->
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vT1zTUU36nekwbv7kKwPYTMn-CGbX-7B3Yfz_dzBmb0nOrkM1kqXBtDZRnFIXH_UNmhj2dbuY8gE8Ze/embed?start=false&loop=false&delayms=10000" frameborder="0" width="720" height="584" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

#### Github Repo
- @jwkanggist, [EveryBodyTensorFlow](https://github.com/jwkanggist/EveryBodyTensorFlow)
- @jwkanggist, [부족한 LetNet5 TF model](https://github.com/jwkanggist/tensorflowlite)


## Issues
- Q) tf.Variable()을 가지고는 tf.get_variable()과 같이 코드 재사용이 불가능한가? (by 이규복)

    