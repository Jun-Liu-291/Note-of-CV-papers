# Activation function overview

## Sigmoind Function
<div align=center><img width="400" height="100" src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/sigmoid.PNG"/></div>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logistic-curve.svg/1024px-Logistic-curve.svg.png"></div>
  It is a logistic function. No matter what is the input data, the output is in interval (0, 1). <br> It's derivative equation is:<br>
<div align=center><img width="400" height="100" src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/derevitive%20sigmoid.PNG"/></div>
  So during backpropogation procedure, if x has a very large absolute value, we can get a value closing to 0. Therefore, when we update weights w and bias b, there won't decrease the loss in a proper speed. This is Gradient Vanishing problem.
## 
