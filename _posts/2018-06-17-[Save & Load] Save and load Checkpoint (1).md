---
title: "[Save & Load] Save and load Checkpoint (1)"
categories:
  - TensorFlow Basic
tags:
  - tensorflow
  - data input
---

오랜 시간을 들여서 모델을 학습하고 그것을 저장하고 싶을 땐 tensorflow는 weight과 model을 저장 하도록 하였다.

weight를 저장하면서 checkpoint를 저장하게 하는데. 저장하는 방법은 아래와 같다.

    # Add ops to save and restore all the variables.
    saver = tf.train.Saver()

    with tf.Session() as sess:
        save_path = saver.save(sess, "/tmp/model.ckpt")

        ...

        for step in iterations:
            saver.save(sess, 'checkpoint.model'), global_step=step)

그럼 다시 load를 할 때는

    # Add ops to save and restore all the variables.
    saver = tf.train.Saver()

    with tf.Session() as sess:
        saver.restore(sess, "/tmp/model.ckpt")

        ...
