You only look once: Uified, real-time object Detection

link: https://arxiv.org/pdf/1506.02640.pdf

# Introduction

* reframe object detection as a single regression problem, straight from image pixels to bounding box coordinates and class probabilities.

* benifits: 
  * fast. frame detection as a regression problem we don't need a complex pipeline.
  * see the entire image during training and test time.
  * Yolo learns generalizable representations of objects.

# Unified Detection

* system divides the input image into an $S*S$, if the centrer of an object falls into a grid cell, that grid cell is responsible for detecting that project.
* for each cell, it would output $B*5 + C$, where B is the number of bounding box, C represent the number of classes in dataset.
* C -- confidence scores for those boxes. reflect how confident the model is that the box contains an object and also how accurate it thinks the box is that it predicts. C = Pr(Object|Object) (Only one set of class probabilities per grid cell, regardless of the number of boxes B.
* At test time C = Pr(Class|Object) * Pr(Object) * IOU = Pr(Class) * IOU
* Bounding box: x, y, w, h. (x, y) coordinates represent the center of the box relative to the bounds of the grid cell, while (w, h) is the size of bounding box relative to the whole image.

# Network Design

* inspired by the GoogLeNet Model. 24 Conv layers followed by 2 fully connected layers. Instead of the inception moduels used by googlenet, simply use 1*1 reduction ayers followed by 3*3 Conv layers.

* The final output of the network is the 7*7*30 tensor of prediction.

# Training

* Pretrain the Conv layers on the ImageNet 1000-class competition dataset. Use <mark>Darknet</mark> framwork for all training and inference.
