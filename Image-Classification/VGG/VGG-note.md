link: https://arxiv.org/abs/1409.1556

This work investigate the effect of the CNN depth on its accuracy in the large-scale image recognition setting

1. Architecture
  224 × 224 × 3 input shape, preprocessing: substract the mean value of the pixel through out training set
  use 3 kernel size, last CNN model has 7 × 7 out put shape
  A stack of two 3 × 3 layer has an effective receptive field of 5 × 5
    Advantage: a. make the decision function more discriminative
               b. reduce the number of parameters
  1 × 1 conv layer increase the nonlinearity of the decision function without affecting the receptive fields of the conv. layers

2. Training
  a. Initialize parameters:
    training a shallow CNN model by random initialize with fully-connected layers, don't change LR while trianing.

3. Testing
  Test image size is not necessarily equal to the training scale S
  Top-1 error: the propotion of the images' prediction are wrong
  Top-5 error: when the ground truth category is not in the top-5 prediction of the model, then it will be counted as wrong predition
