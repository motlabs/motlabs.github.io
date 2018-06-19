---
title: "Convert to TFRecords dataset"
categories:
  - TensorFlow Basic
tags:
  - tensorflow
  - data input
---


신경망에 학습 데이터를 준비하면서 png 나 jpg와 같은 일반 이미지를 그대로 학습 데이터로 넣는 방법이 있지만, dataset을 tfrecord로 변환하고서 학습 데이터로 넣는 방법이 있다.

TFRecord로 저장하고 학습 데이터로 돌리면 여러가지 장점들이 있는데. Binary로 저장하기 때문에 속도가 더 빨라진다는 장점이 있고, 이미지와 레이블들을 한 파일로 묶을 수 있기 때문에 관리하기가 편한 장점이 있다.

### tfrecord 생성하면서 압축하기

    options = tf.python_io.TFRecordOptions(tf.python_io.TFRecordCompressionType.GZIP)
    writer = tf.python_io.TFRecordWriter(path=tfrecords_name, options=options)

tf.python_io.TFRecordWriter() 안에 파라미터를 tfrecords_name 만 정해줘도 tfrecord는 생성된다. 하지만 option으로 위와 같이 CompressionType을 정해주면 tfrecord 파일이 압축 되면서 생성된다. 압축하지 않으면 이미지 데이터가 완전 raw 하기 때문에 용량이 더 커지는 것을 보고 용량 사이즈에 놀랠 수 있다.

### Image Dataset을 tfrecords로 변환하는 과정

먼저 tfrecord에 넣기 전에 각 데이터 type 에 필요한 함수들을 만들어 준다. 아래 코드는 텐서플로우 깃허브에서 가져온 것이니 그냥 편하게 그대로 쓰면 된다.

    def _int64_feature(value):
        *"""Wrapper for inserting int64 features into Example proto."""
        *if not isinstance(value, list):
            value = [value]
        return tf.train.Feature(int64_list=tf.train.Int64List(value=value))


    def _float_feature(value):
        *"""Wrapper for inserting float features into Example proto."""
        *if not isinstance(value, list):
            value = [value]
        return tf.train.Feature(float_list=tf.train.FloatList(value=value))


    def _bytes_feature(value):
        *"""Wrapper for inserting bytes features into Example proto."""
        *if not isinstance(value, list):
            value = [value]
        return tf.train.Feature(bytes_list=tf.train.BytesList(value=value))

**이미지는 Binary로**
이미지는 tfrecord로 바꿀 때는 binary로 변환하고 넣어줘야 한다.

TFRecords 생성을 하기 전에 위와 같은 코드로 준비하고 각 원하는 파일들을 하나씩 입력 해주면 된다.

    string_set = tf.train.Example(features=tf.train.Features(feature={
            'Image': _bytes_feature(_binary_image),
            'Label': _bytes_feature(_binary_label),
            'mean': _float_feature(image.mean().astype(np.float32)),
            'std': _float_feature(image.std().astype(np.float32))
        }))

    writer.write(string_set.SerializeToString())

전체적인 코드는 아래에서 볼 수 있다.

 <iframe src="https://medium.com/media/6bb410f1e671a6b9df05ecedaddb7f75" frameborder=0></iframe>
