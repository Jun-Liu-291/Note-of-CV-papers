You only look once: Uified, real-time object Detection

link: https://arxiv.org/pdf/1506.02640.pdf

# Introduction

* reframe object detection as a single regression problem, straight from image pixels to bounding box coordinates and class probabilities.

* benifits: 
  * fast. frame detection as a regression problem we don't need a complex pipeline.
  * see the entire image during training and test time.
  * Yolo learns generalizable representations of objects.

# Unified Detection

* system divides the input image into an ${S}{S}$

