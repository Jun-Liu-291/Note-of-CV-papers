# Activation function overview

## Sigmoind Function
<div align=center><img width="400" height="100" src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/sigmoid.PNG"/></div>
<div align=center><img width="600" height="400" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logistic-curve.svg/1024px-Logistic-curve.svg.png"></div>
  It is a logistic function. No matter what is the input data, the output is in interval (0, 1). <br> It's derivative equation is:<br>
<div align=center><img width="600" height="100" src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/derevitive%20sigmoid.PNG"/></div>
  So during backpropogation procedure, if x has a very large absolute value, we can get a value closing to 0. Therefore, when we update weights w and bias b, there won't decrease the loss in a proper speed. This is Gradient Vanishing problem.
  
## Gradient Vanishing
  Just as mensioned, if the value of the partial derivative is small, the parameters will get very small update. This will prevent the nereul network from learning, which will let the model far away from the best model we desire.<br>
<div align=center><img width="400" height="100" src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/parameter%20update.PNG"/></div>

## Gradient Explosion
  Gradient explosion is the opposite problem of gradient vanishing.<br>
  Basicly, when 0<w<1, we might have gradient vanishing problem. Since when model get deeper, if all w are in (0,1), the update of parameters will get smaller and smaller. when w>0, we have a bigger chance to have gradient explosion problems. Because the function of caculate derivative of weights has the component of weights in last layers. When one specific layer has one kind of problems, there will absolutely be more weights have the same problem.<br> 

  ### how to solve this problem
    Set a threshold: if the gradient is bigger then this threhold then apply Gradient clipping or gradient specification
    But this method will not solve gradient vanishing problem.
    
 ## Relu Function
  Full name: rectified linear unit
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/ReLu.PNG"/></div>
  <div align=center><img src="https://miro.medium.com/max/357/1*oePAhrm74RNnNEolprmTaQ.png"/></div>
  Derivative Function:
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/ReLu%20Derivative.PNG"/></div>
  
  In this condition, when we use ReLu as our activation function, we will get either 1 or 0 during backpropogation. If we get too much value are equal to 0, what will happen? Then we will not get any update in backporopogation, which is also called death ReLu
  
  1. advantage:
    a. Introduce Sparcity: decrease the time and space complexity; Does not involve exponential calculations. 
    <font color=red>What is sparcity in Deep Learning?</font>
