# Tensorflow-Tips

These are just some points for reference in the future.

The [CenterNet MobileNetV2 FPN 512x512](http://download.tensorflow.org/models/object_detection/tf2/20210210/centernet_mobilenetv2fpn_512x512_coco17_od.tar.gz) in the [TensorFlow 2 Detection Model Zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md) requires modification in the pipeline.config file to allow to be re-trained.

Changes to be made:
```
data_augmentation_options { // delete
    random_horizontal_flip {
      keypoint_flip_permutation: 0
      ...
    }
  }
  // in train_input_reader & eval_input_reader
  num_keypoints: 17 // delete
```
