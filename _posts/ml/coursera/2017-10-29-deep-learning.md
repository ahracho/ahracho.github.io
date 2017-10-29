---
layout: article
title:  "[Deep Learning] Introduction to deep learning"
categories: coursera
tags: [deeplearning, coursera, andrewng]
comments: true
---

## What is Neural Network?
딥러닝은 머신러닝 기법의 하나로, 신경망 학습을 여러 층으로 설계하는 기법을 나타낸다. 신경망 학습은 입력값을 설계된 네트워크에 적용하여 결과를 예측하는 방식인데, 여기서 네트워크란 학습된 가중치들의 집합이라고 정의할 수 있겠다. 즉, 입력값(X, input layer)에 가중치(hidden layer)를 적용해서 미리 정의된 식에 대입하면 예측값(Y, output layer)를 얻게 되는 것이다.  

우리는 각각의 가중치를 적당히 조절해가면서 우리가 예측한 값이 실제의 결과와 최대한 비슷할 수 있도록 해야하고, 이것을 '학습'시킨다고 한다.  

(네트워크 관련 이미지 삽입)  

## Supervised Learning with Neural Network
지도학습(Supervised Learning)은 정답이 주어진 학습 과정이라고 이해할 수 있다. 실제 (X, Y)값의 데이터들이 준비되어 있고, 우리는 이 실제 데이터를 가지고 새로운 X들이 주어졌을 때 실제와 가까운 Y값을 예측할 수 있도록 식을 설계해야 한다. X와 Y 값의 관계식 혹은 학습시키는 방식은 문제에 따라서 달라질 수 있는데, 딥러닝을 적용할 때도 마찬가지이다.  

### Neural Network 종류
Standard NN : Regression이 필요한 경우  
CNN : 이미지 분류  
RNN : 음성 인식, 번역 (데이터의 순서(Sequencial Data)가 의미있는 분석의 경우)  

### 데이터의 종류
Structured Data : 각 featrue들이 정의되어 있고, 정리되어 있는 데이터
Unstructured Data : 오디오, 이미지, 자연어 등 feature들이 정의되어 있지 않은 데이터  
