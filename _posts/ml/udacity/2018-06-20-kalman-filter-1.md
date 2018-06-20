---
layout: post
title:  "[Udacity SDCND] 칼만필터 Kalman Filter 이해하기 (1)"
categories: Udacity-SDCND
tags: [Machine-Learning, SelfDriving-Car]
comments: true
---

[//]: # (Image References)

[KF Process]: {{ site.url }}/images/ml/udacity/kf-process.png "칼만필터 과정"
[Note1]: {{ site.url }}/images/ml/udacity/kf1_note1.JPG "Prediction 1D"
[Note2]: {{ site.url }}/images/ml/udacity/kf1_note2.JPG "Measurement Update 1D"
[Note3]: {{ site.url }}/images/ml/udacity/kf1_note3.JPG "Kalman Filter in 2D"

Udacity Self-Driving Car Nanodegree Term 2의 첫 과제는 칼만 필터를 구현하는 것이다. 

칼만 필터는 자동차에 부착된 센서(LASER, RIDAR)를 통해 입력된 값을 통해서 차량 주변의 보행자, 자전거, 자동차 등의 물체를 인식하고 움직임을 예측하는 데 사용된다. 수업에서는 칼만 필터를 다루기 전에 Localization의 개념을 먼저 소개하는데 Localization은 다른 포스팅을 통해서 자세히 정리하도록 한다.  

## 칼만 필터란?

현재까지 이해하기로는, (수업에서 다루는 물체 인식을 위한 용도) 칼만 필터는 업데이트된 센서값 + 현재까지 누적된 정보를 사용하여 주변 물체의 단위 시간 후의 위치를 예측한다.  
보행자를 추적한다고 예를 들면, 자동차의 입장에서 보행자가 현재 (x, y) 위치에 있다고 생각하는 것은 참값이 아니라, 사실 확률 분포로 인식하는 것이다 (주어진 정보로 미루어보아 현재로선 보행자가 저기 있을 확률이 가장 크다고 판단하는 것!). 또한, 센서값을 통해 물체의 위치가 연속적으로 주어지기 때문에 현재 위치와 직전 위치를 비교하면 물체의 이동 속도를 예측할 수 있게 된다.  

칼만 필터는 연속적으로 주어지는 센서값을 가지고 물체의 위치와 속도를 예측하면서 동시에 예측에 쓰이는파라미터를 튜닝해가는 일련의 과정이라고 이해하고 있다.  

![KF Process]  

LIDAR와  RADAR 센서값을 받으면 먼저 현재까지의 정보를 바탕으로 물체의 위치(와 속도)를 예측하고, 이번에 받은 센서값을 활용해서 파라미터(행렬)을 업데이트하는 과정을 반복한다. 

## LIDAR 센서
LIDAR 센서는 물체의 위치에 대한 값만 알아낸다 (속도에 대한 정보 없음).  

### 1D - Prediction
현재 우리가 가지고 있는 위치와 속도 정보만 가지고 t+1에서의 위치를 예측한다. Extended Kalman Filter에서는 물체의 이동 속도는 일정하다고 가정한다 (v’ = v).  

![Note1]  

### 1D - Measurement Update

새롭게 얻은 센서값과 우리의 예측값을 비교하여 최종 예측값을 도출한다.  

![Note2]  

### 2D

기본적인 골격은 1차원과 같지만, 2차원에서는 물체의 위치와 속도가 x축과 y축이 각각 있어야 하기 때문에 x 벡터의 모양이 바뀌었다. 이에 따라 행렬 F와 H의 값이 바뀌었다.  

![Note3]  
