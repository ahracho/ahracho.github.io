---
layout: post
title:  "[Udacity SDCND] 칼만필터 Kalman Filter 이해하기 (2)"
categories: Udacity-SDCND
tags: [Machine-Learning, SelfDriving-Car]
comments: true
---

[//]: # (Image References)

[KF Process]: {{ site.url }}/images/ml/udacity/kf-process.png "칼만필터 과정"
[Note1]: {{ site.url }}/images/ml/udacity/ekf-note1.png "h(x) function"
[Note2]: {{ site.url }}/images/ml/udacity/ekf-note2.png "Jacobian"


## Extended Kalman Filter

칼만 필터는 센서 하나의 값만으로 사용하는 것이 아니라 여러 개의 센서 값을 동시에 사용할 수 있기 때문에 유용성이 크다. 자율주행차에서도 마찬가지인데, LADAR와 RIDAR 센서를 통해 얻어진 값을 조합하여 물체 인식과 움직임 예측에 사용한다. 센서를 여러 개 사용하더라도 앞선 포스팅에서 설명했던 기본적인 칼만 필터의 동작 방식은 동일하다. 센서값이 들어오면 예측을 하고, 예측 알고리즘을 업데이트를 하여 최종 예측값을 계산한다. 다만, 달라지는 것은 여러 개의 센서들이 번갈아가면서 값을 입력한다는 것이다.  

LADAR와 RIDAR 센서는 특성도 다르고, 센서 계측값의 형태도 다르다. 물체의 (x,y) 좌표를 결과값으로 주는 LADAR 센서와 달리, RIDAR 센서는 다른 형태의 측정값을 출력한다 (거리, 각도, 속도 등). Prediction 단계에서는 LADAR / RIDAR 센서의 차이가 없지만, Measurement Update 단계에서는 센서에 따라 다른 식을 사용해야 한다. 특히, 예측값과 센서값을 비교하기 위한 식에서 x를 z(센서 출력값)와 같은 형태로 바꾸기 위한 행렬 H가 바뀌어야 한다. 여기서는 행렬 H 대신 함수 h(x)를 사용한다.  

![Note1]  

Error 계산 뿐만 아니라, 행렬 S, K, P를 계산할 때에도 행렬 H가 사용되기 때문에, 이들도 변화가 필요하다. 이때 위에서처럼 함수 h(x)를 그냥 쓰면 간단하겠지만, h(x)는 비선형 함수이기 때문에 이를 사용하면 결과값이 더이상 Gaussian 분포를 따르지 않게 된다는 문제가 있다. 칼만 필터는 Gaussian 분포를 바탕으로 동작하기 때문이다. 기존의 행렬 H도 사용할 수 없고, 함수 h(x)도 사용할 수 없다면 어떡해야 하지?  

비선형 함수인 h(x)와 가장 비슷한 분포를 가진 선형 함수를 행렬(Jacobian 행렬)을 찾아 기존의 행렬 H를 대체한다. h(x)의 Jacobian 행렬을 찾는 과정은 아마 미적분 공부를 해야 정확히 이해할 수 있을 것 같다.  

![Note2]  


## 종합
![KF Process]

칼만필터는 센서값을 가지고 물체의 다음 움직임을 예측하고, 예측값을 튜닝하는 과정을 반복하는 것으로 이루어져 있다. 자율주행차에서는 LADAR와 RIDAR 센서를 사용하여 주변 환경을 인식하는데, 특히 RIDAR 센서를 사용할 때는 센서값이 LADAR와 다른 형태이기 때문에 이를 변형하는 과정이 추가된다. Delta t는 이전 센서값과 현재 센서값 사이의 시간 차이를 나타내고, 두 종류의 센서값이 번갈아가면서 입력되기 때문에, 값을 다룰 때 어떤 센서의 값인지 구분하여야 한다.  
