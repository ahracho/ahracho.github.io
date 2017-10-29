---
layout: article
title:  "[Deep Learning] Logistic Regression (Part 1)"
categories: coursera
tags: [deeplearning, coursera, andrewng]
comments: true
---
<script type="text/javascript"  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## Logistic Regression에 신경망 적용하기
### Binary Classification
Logistic Regression은 보통 Yes or No 문제를 정의할 때 사용한다. 어떤 사진을 주고 고양이 사진인지 아닌지를 판단한다든지, 스팸 메일인지 아닌지 판단하는 등의 문제를 떠올리면 된다.  

고양이 사진을 추려내는 문제가 있다고 가정해보자. 우리에게 64X64 크기의 사진이 주어질 것이고, 각 픽셀은 RGB 값으로 나타낸다. 우리의 학습 모델에서 Input Layer는 64X64X3의 픽셀 색상 정보가 될 것이고, Output Layer는 0 / 1이 될 것이다.  

M개의 데이터가 있고, 각 X가 N개의 요소로 구성되어 있다고 하면, {(X1, Y1), (X2, Y2), ... (Xm, Ym)}으로 나타낼 수 있고, 이것을 한 행렬로 나타내면 X = '[X1;X2; ... ;Xm'] '(N X M 행렬'), Y = '[Y1; Y2; ... ;Ym']이 된다.  

### Logistic Regression
X가 주어졌을 때 Yes or No로 결과를 얻기 위해서는 어떤 식으로 식을 설계해야할까? 일단 결과값 Y를 P(y=1 | X), 즉, X가 주어졌을 때 결과가 1일 확률이라고 정의해보자. 그럼 이 확률이 우리가 가진 기준보다 높을 때 고양이일 것이라고 판단하는 것이 합리적이다.  

저 확률은 어떻게 구할까? X와 Y의 관계식을 가장 간단하게 1차식으로 정의하면 Y(0 <= Y <= 1) = wX + b이 되고, X는 N X M 행렬이기 때문에 W는 N차 행렬로 정의할 수 있다.  

wX + b의 값이 항상 0 <= Y <= 1 이도록 하기 위해서 Sigmoid 함수를 사용하는데, 식과 그래프는 다음과 같다.   
\\(sig(t)=\frac{1}{1+e^(-t)}\\)  
(Sigmoid 함수 그래프 삽입)  

위의 식에서 t에 해당하는 것이 wX + b가 된다.

### Cost Function
우리가 참에 가까운 관계식을 찾아가기 위해서 w와 b를 계속해서 바꿔나가면서 학습을 할텐데, 지금의 관계식이 다른 것들보다 효과적인 모델인지 아닌지 판단할 수 있는 기준이 필요하다. 머신러닝에서는 Cost Function을 판단 기준으로 삼는다. 즉, 이 식으로 학습을 시킬 때의 Cost, 비용이 얼마나 드는지를 계산하는 것인데, 여기서 Cost란 참값과 예측값 사이의 차이의 합(Training Set이 여러개이기 때문에)이다. 쉽게 말해, 우리가 식을 가지고 도출해낸 예측값과 실제의 y값들의 차이가 적으면 적을수록 효과적인 모델을 찾아낸 것이라고 생각할 수 있다는 것이다. 각 Training Set에서의 비용을 계산하는 식을 Loss(Error) Function이라고 하는데,   

Linear Regression에서는 아래와 같은 식으로, 
\\( L(X, Y) = ((wX+b)-Y)^2)\\)

Logistic Regression에서는 아래의 식을 사용한다.  
\\(L(y, Y) = -(Ylogy + (1-Y)log(1-y))\\) (y는 예측값, Y는 참값이라고 하자) 

선형회귀와 달리 Logistic 회귀에서 이런 괴상한 식이 나오게 된 이유를 찬찬히 생각해보자. Loss Function의 기능은 예측값과 참값의 차이를 계산하는 것이기 때문에, 예측값과 참값이 다르면 값이 커지고, 같으면 값이 작아져야 한다. 그런데 Logistic Regression은 선형회귀분석과 달리 y값의 범위가 0과 1 사이로 한정되어 있기 때문에 기존의 것을 그대로 사용할 경우 함수의 결과값이 차이를 드러내는 데에 효과적이지 않다. 그래서 좀 더 극적으로 예측값과 참값의 차이를 드러내기 위해서 위와 같은 Loss Function을 고안하게 된 것이다.  

생각해보자. Y = 1이라고 하면 L = -logy가 될 것이고, L의 값이 작아지기 위해서는 y 값이 커야하고, y가 1일 때 가장 크다. 반대로 Y = 0이라고 하면 L = -log(1-y)이고, L의 값이 작아지기 위해서는 마찬가지로 1-y의 값이 커야하고, y가 0일 때 가장 크다.  위의 Loss Function은 예측값과 참값이 같을 때 가장 작은 값을, 다를 때 가장 큰 값을 리턴하는 아주 효과적인 함수인 것이다.  

각각의 Training Set에 대해 Loss를 구하면 그것을 다 더한 값이 Cost Function의 결과가 된다(내가 지금 가지고 있는 모델의 Cost).  
\\( Cost(w, b) = \frac{1}{M}sum(L(y, Y))\\)