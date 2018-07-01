---
layout: post
title:  "[선형대수] 4강 : 역행렬과 전치행렬"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

[//]: # (Image References)

[Note1]: {{ site.url }}/images/linear-algebra/4-1.png "Note1"
[Note2]: {{ site.url }}/images/linear-algebra/4-2.png "Note2"
[Note3]: {{ site.url }}/images/linear-algebra/4-3.png "Note3"
[Note4]: {{ site.url }}/images/linear-algebra/4-4.png "Note4"


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다 [한양대 MOOC](http://www.kocw.net/home/search/kemView.do?kemId=977757).  

## 역행렬의 조건
- 역행렬은 Det(A) != 0 일 때에만 존재한다. 즉, 가우스 소거를 수행하고 Pivot 자리의 수가 모두 0이 아닌 값일 때만 역행렬이 존재한다. 
- 행렬 A에 대하여, 역행렬이 존재한다면, 행렬 A의 역행렬은 유일하다(Unique). 이는 반대로, Ax = b에서 A의 역행렬이 존재한다면 x도 유일하다는 것을 의미한다. 

![Note1]  

## 역행렬 구하는 법
가우스 소거법과 역행렬의 성질을 사용하면 행렬 A의 역행렬을 구할 수 있다. A' = U'L' (편의상 행렬 A의 역행렬을 A'라고 표기하였다)이고, Det(A) = 행렬 U의 대각선 값의 곱이다. 
![Note2]  
![Note3]  

## 전치행렬과 대칭행렬의 성질
![Note4]  
