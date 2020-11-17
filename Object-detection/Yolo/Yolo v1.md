You only look once: Uified, real-time object Detection

link: https://arxiv.org/pdf/1506.02640.pdf

# Introduction

* reframe object detection as a single regression problem, straight from image pixels to bounding box coordinates and class probabilities.

* benifits: 
  * fast. frame detection as a regression problem we don't need a complex pipeline.
  * see the entire image during training and test time.
  * Yolo learns generalizable representations of objects.

# Unified Detection

* system divides the input image into an $S * S$, if the centrer of an object falls into a grid cell, that grid cell is responsible for detecting that project.
* for each cell, it would output $B * 5 + C$, where B is the number of bounding box, C represent the number of classes in dataset.
* C -- confidence scores for those boxes. reflect how confident the model is that the box contains an object and also how accurate it thinks the box is that it predicts. C = Pr(Object|Object) (Only one set of class probabilities per grid cell, regardless of the number of boxes B.
* At test time C = Pr(Class|Object) * Pr(Object) * IOU = Pr(Class) * IOU
* Bounding box: x, y, w, h. (x, y) coordinates represent the center of the box relative to the bounds of the grid cell, while (w, h) is the size of bounding box relative to the whole image.

# Network Design

* inspired by the GoogLeNet Model. 24 Conv layers followed by 2 fully connected layers. Instead of the inception moduels used by googlenet, simply use 1 * 1 reduction ayers followed by 3 * 3 Conv layers.

* The final output of the network is the 7 * 7 * 30 tensor of prediction.

# Training

* Pretrain the Conv layers on the ImageNet 1000-class competition dataset. Use <span style="background-color: #FFFF00">Darknet</span> framwork for all training and inference.
* Convert the model to perform detection. Add four COnv layers and two fully connected layers with rondomly initialized weights. and increase the input resolution of the network from 224 * 224 to 448 * 448.
* final layer predicts both class probabilities and bounding box coorinates. Normalize the bounding box width and height by the image width and height. Parametrize the bounding box *x* and *y* coordinates to be offsets of a particular grid cell location.
* apply activation function for the final layer and all the other layers use the leaky Relu activatoin: a = 0.1
* loss: sum-squared error. 
  * disadvantage: </br>
    1. does not perfectly align with the goal of maximizing average precision. </br>
    2. in every image many grid cells do not contain any object, which push the confidence scores of those cells towards 0, oftheb overpowering the gradient from cells that do contain objects.
  * Remdy:
