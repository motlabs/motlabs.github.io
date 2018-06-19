---
title: "[input_data] tf.data 으로 batch 만들기"
categories:
  - TensorFlow Basic
tags:
  - tensorflow
  - data input
---

## Generate batch data with tf.data
[**Importing Data | TensorFlow**
*The API supports a variety of file formats so that you can process large datasets that do not fit in memory. For…*www.tensorflow.org](https://www.tensorflow.org/programmers_guide/datasets)

작년에는 데이터를 tfrecord로 변환하고서 그 파일을 학습 데이터로 넣으려고 할 때 enqueue dequeue를 이용하면 코드도 복잡하고, 여러가지 불편함들을 여간 많았던 것이 아니다.

올해 초 반가운 텐서플로우의 새로운 함수가 나왔다. tf.data 라는 것인데. 획기적으로 tfrecord를 열 수 있는 것 뿐만이 아니라 일반 이미지도 역시 손쉽게 배치로 생성하고 넣을 수 있다.

### tf.data 로 데이터 만들기

데이터를 다루게 된다면 제일 먼저 생각하게 되는 순서는 아래와 같을 것이다.

 1. 데이터의 경로를 찾는다.

 2. 데이터의 목록들을 가져오고, 이미지와 레이블을 생각한다.

 3. 목록의 한 열 마다 데이터를 여는 방법을 정의한다.

 4. shuffle 이든 다양한 옵션을 준다.

 5. 배치로 만들어서 model 넣을 준비를 한다.

### 1. 데이터 준비

제일 먼저 원하는 데이터들의 경로를 받아 리스트로 담고서 아래와 같은 함수에 넣어준다.

**tf.data.TFRecordDataset(filenames)**
tfrecord 데이터로 돌릴려고 할 땐 이 함수를 쓰면 된다.

**tf.data.Dataset.from_tensor_slices(filenames)**
제일 먼저 일반 이미지나 array를 넣을 때 list 형식으로 넣어준다. 이미지 경로들이 담긴 리스트 일 수도 있고, raw 데이터의 리스트 일 수도 있다. 이번 글에서는 이 함수로 예제로 보여줄 것이다.

    dataset = tf.data.Dataset.from_tensor_slices((image_list, label_list))

### 2. tfrecords가 아닌 numpy 나 image를 읽어야 한다면 reader 및 preprocess 함수 정의

    def _read_py_function(path, label):
        image = read_image(path)
        label = np.array(label, dtype=np.uint8)
        return image.astype(np.int32), label

    def _resize_function(image_decoded, label):
        image_decoded.set_shape([None, None, None])
        image_resized = tf.image.resize_images(image_decoded, [28, 28])
        return image_resized, label

PIL의 Image로 읽든 openCV로 읽든 어떤 방법으로든 이미지를 읽을 reader 함수를 정의 합니다. 여기에 동시에 preprocess 들을 같이 넣을 수도 있습니다.

    dataset = dataset.map(
        lambda data_list, label_list: tuple(tf.py_func(_read_py_function, [data_list, label_list], [tf.int32, tf.uint8])))

    dataset = dataset.map(_resize_function)

### 3. 읽은 데이터들에게 다른 옵션들 정의

dataset으로 정의 했다면 이를 다양하게 설정 해줄 수 있는데. 설명을 주자면 아래와 같다.

* repeat(step_n) : 원하는 epoch 수를 넣을 수 있다. 아무런 파라미터를 주지 않는다면 iteration이 무제한으로 돌아간다.

* shuffle(1000) : 한번 epoch이 돌고나서 랜덤하게 섞을 것인지 정한다.

    dataset = dataset.repeat()
    dataset = dataset.shuffle(buffer_size=(int(len(data_list) * 0.4) + 3 * batch_size))

### 4. batch size 정의하기

tf.data 를 사용하지 않을 땐 여러 방법들로 batch 를 만들었지만 tf.data는 이렇게 간단히 정의가 가능하다.

[**[input_data] Image 데이터로 Batch 만들어 넣기](https://medium.com/trackin-datalabs/data-input-%EB%A7%8C%EB%93%A4%EA%B8%B0-74bb5c1ce52f) — 참고**

    dataset = dataset.batch(batch_size)

### 5. iterator 정의

마지막으로 iterator 정의 해주고나면 모델에 넣을 image_stacked와 label_stacked까지 만들어 주면 된다.
>  위 코드 중 image_stacked와 label_stacked가 왜 두개로 나눴는지 이해가 안 될 수 있는데. 처음에 데이터 경로를 넣었을 때 image_list와 label_list를 tuple로 넣었기 때문에 이렇게 두 갈래로 나뉘기 전까진 계속 두개가 계속 흘러가는 것이라 생각하면 된다.

    iterator = dataset.make_initializable_iterator()
    image_stacked, label_stacked = iterator.get_next()

### 6. Image 읽기

Session을 열어주고, 아래와 같이 initializer를 한번 run 해준 후 image를 sess.run을 해주면 잘 뽑아지는지 확인 하면 된다.

최종 코드는 아래에서 확인 할 수 있다.

    with tf.Session() as sess:
        sess.run(iterator.initializer)
        image, label = sess.run([image_stacked, label_stacked])

 <iframe src="https://medium.com/media/28681fe117c91078cf496992589ed87e" frameborder=0></iframe>
