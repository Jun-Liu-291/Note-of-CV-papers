# Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network

2020-12-11</br>
https://arxiv.org/pdf/1609.04802.pdf</br>

## Abstract:

  * One central problem remain: how do we recover the finer texture details when we super-resolve at large upscaling factors?
  * The behavior of optimization-based super-resolution methods is principally driven by the choice of the objective function (mean squared reconstruction error).
  * To achieve 4 times upscaling photo-realistic natural images, they propose a perceptual loss function which consists of an adversarial loss and a content loss.
    * the adversarial loss: push solution to the natural image manifold using a discriminator network that is trained to differentiate between the super-resolved images and original photo-realistic images.
    * Content loss: motivated by perceptual similaarity insteaad of similarity in pixel space
 * Mean-option-score (*MOS*)

## 1. Introduction
 * The optimization target of supervised SR algorithms is commonly the minimization of the MSE between recovered HR image and the ground truth, which also maximizes the peak signal-to-noise ratio (a common measure used to evaluate and compare SR algorithms.
 * while MSE and PSNR to capture perceptually relevant differences, such as high texture detail, is very limited as they are defined based on pixel-wise image differences.
 * Propose a super-resolution generative adversarial network (SRGAN) for which they employ a deep residual network (ResNet) with skip-connection and diverge from MSE as the sole optimization target.
 * Define a novel perceptual loss using high-level feature maps of the VGG network combined with a discriminator that encourages solutions perceptually hard to distinguish from the HR reference images.

### 1.1 Related work
#### 1.1.1 Image super-resolution
