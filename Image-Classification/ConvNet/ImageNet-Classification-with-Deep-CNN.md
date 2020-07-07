link: https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf

1. ReLu activation:
  Before 2012, tanh is the most used activation function. They compare the ReLu and tanh on CIFAR-10 dataset. the result shows that to  get 25% training error rate, ReLu is six time faster than an equivalent network with tanh neurons.
  
2. Training on multiple GPU
  They train the model on two pieces of GTX 580. basicly, they build two same model and train them seperately on two GPU, but in layer 4, the input is not only from the output of layer 3 from the same GPU, but from both, which makes two model not independent.

3. Overlapping Pooling
  for Pooling layer in CNN, traditionally we apply the stride = the size of the pooling layer. If we set the size of the layer > stride, then we can get overlapping pooling, which can imporve the accuracy of the prediction.
  
4. Over all architecture
  CNN-layer-1 11×11×3 with stride = 4, depth = 48×2. 
  CNN-layer-2 5×5×48 with stride = 1, depth = 128×2. + MaxPooling
  CNN-layer-3 3×3×256 with stride = 1, depth = 192×2. + MaxPooling
  CNN-layer-4 3×3×192 with stride = 1, depth = 192×2.
  CNN-layer-5 3×3×102 with stride = 1, depth = 128×2.
  fully-connected layers have 4096 neurons each, 2 fully-connected layers.
  output layer 1000 neurons.
  
5. Reduce Overfitting
  5.1 data augmentation: artificially enlarge the dataset using label-preserving transformations
                         Generate transformed image by Python code on CPU, while the GPU is training on previous batch
                         First Image translation and horizontal reflection
                         Second altering the intensities of the RGB channels in training images
  5.2 dropout:           0.5

6. Training
  6.1 batch size = 128, momentum = 0.9, weight decay = 0.0005 ? 
