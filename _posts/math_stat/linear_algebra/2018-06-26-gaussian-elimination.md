---
layout: post
title:  "[선형대수] 2강 : 1차 연립방정식과 가우스소거법"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

[//]: # (Image References)

[Note1]: {{ site.url }}/images/linear-algebra/2-1.png "Note1"
[Note2]: {{ site.url }}/images/linear-algebra/2-2.png "Note2"
[Note3]: {{ site.url }}/images/linear-algebra/2-3.png "Note3"
[Note4]: {{ site.url }}/images/linear-algebra/2-4.png "Note4"


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다 [한양대 MOOC](http://www.kocw.net/home/search/kemView.do?kemId=977757).  

## Singular Case
행렬(벡터)의 관점에서 연립방정식 푸는 방법을 지난 포스팅에서 설명하였는데, 연립방정식을 풀 때, 해가 없거나 해가 무수히 많은 경우가 발생할 수 있다는 것은 중학교 수학 시간에 배워서 알 것이다. 그렇다면 이런 경우는 벡터로 어떻게 설명할 수 있을까?  

![Note1]  

## Gaussian Elimination
가우스 소거법은 행렬로 표현된 연립방정식에서 1행부터 차례로 적절한 값을 곱하고 서로 빼주면서 쉽게 해를 찾을 수 있는 형태로 변형하여 방정식의 해를 찾는 과정이다.  
![Note2]  

이 과정에서 계수행렬을 Upper Triangular Matrix로 변형하게 되는데, 행렬 U의 대각선 위치에 있는 값들을 Pivot이라고 한다. Non-Singular의 경우에는, Pivot이 모두 0이 아닌 값을 가지고, Pivot 중에 0인 값이 있으면 Singular Case로, 이 경우에는 해가 없거나, 무수히 많게 된다.  
![Note3]  

## Matrix Notation and Multiplication
![Note4]  
