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
  
  1. advantage:<br>
    a. Introduce Sparcity: decrease the time and space complexity; Does not involve exponential calculations. <br>
    <font color=#008000>What is sparcity in Deep Learning?</font><br>
    b. Avoid gradient vanishing problem
   
  2. disadvantage:<br>
    a. Involve death ReLu problem, most part of the model will not be updated, but some time, this will be an assist.<br>
    b. Can not avoid Gradient Explosion problem
    
## ELU(Exponential linear unit)
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/ELU.PNG"/></div>
  <div align=center><img src="https://support.dl.sony.com/wp-content/uploads/2017/08/13143208/layer_6_6_elu.png"/></div>
  Derivative Function:
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/ELU%20derivatie.PNG"/></div>
  1. advantage:<br>
    a. avoid death relu problem<br>
    b. When input values are negative, we still can get non-zero outputs, then we can update weights and bias
  2. disadvantage:<br>
    a. contains exponetial caculation, make the caculation time longer<br>
    b. can't avoid gradient explosion problems<br>
    c. we need to pre-set the a value (not a trainable value)
 
 ## Leaky ReLu
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/Leaky%20ReLu.PNG"/></div>
  <div align=center><img src="https://www.i2tutorials.com/wp-content/uploads/2019/09/Deep-learning-25-i2tutorials.png"/></div>
  Derivative Function:
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/Leaky%20ReLu%20derivative.PNG"/></div>
  1. advantage:<br>
    a. avoid death relu problem<br>
    b. When input values are negative, we still can get non-zero outputs, then we can update weights and bias<br>
    c. Doesn't contain exponential caculation, faster then ELU
  2. disadvantage:<br>
    a. both positve part and negative part are linear, but we prefer non-linear activation
    b. can't avoid gradient explosion problems<br>
    c. we need to pre-set the a value (not a trainable value)<br>
    
## SELU(Scaled Exponential Linear Unit)
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/SELU.PNG"/></div>
  where in the paper:<br>
  <div align=center><img src="https://pic3.zhimg.com/80/v2-88211966c09f79ed8d5b6ce3eda7733c_720w.jpg"/></div>
  <div align=center><img src="https://pytorch.org/docs/master/_images/SELU.png"/></div>
  
  Derivative Function:
  <div align=center><img src="https://github.com/Jun-Liu-291/Note-of-DL/blob/master/Deep-Learning-Basis/Activation-Function/img/SELU%20derivative.PNG"/></div><nr>
  When actually applying this activation function, we should use lecun normal to initialize the model, when applying dropout, we should use Alphadropout.<br>
  When we using lecun normal to initialize the model, all the model will be normal distribution, and after apply input to SELU actication function, we will also get the outputs with 0 mean and 1 varience. Since if input is smaller than 0, it will decrease the varience, and if the input is larger than 0, it will increase the varience; and we got both positive and negative, then we can get 0 mean.<br>
  1. advantage:<br>
    a. internel nomalization: which can let the model converge more quick.<br>
    b. There will not be gradient vanishing or gradient explosion problem<br>
  2. disadvantage:<br>
    a. we still need more research in applying SELU in CNN model.
  
