---
layout: post
title:  "[선형대수] 3강 : LU Decomposition"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

[//]: # (Image References)

[Note1]: {{ site.url }}/images/linear-algebra/3-1.png "Note1"
[Note2]: {{ site.url }}/images/linear-algebra/3-2.png "Note2"
[Note3]: {{ site.url }}/images/linear-algebra/3-3.png "Note3"
[Note4]: {{ site.url }}/images/linear-algebra/3-4.png "Note4"
[Note5]: {{ site.url }}/images/linear-algebra/3-5.png "Note5"


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다 [한양대 MOOC](http://www.kocw.net/home/search/kemView.do?kemId=977757).  

## Elementary Matrix
행끼리 계수 곱해서 빼기, pivoting을 포함하여 가우스 소거법의 과정을 행렬로 표현할 수 있다. 소거법을 진행하면서 계수를 소거하기 위해서 빼고 곱했던 과정은 Lower Triangular Matrix 행렬 L에 표현되어 최종적으로 A = LU의 형태로 표현할 수 있다.  

![Note1]  
![Note2]  

## Triangular Factorization (Decomposition)
연립방정식의 계수 행렬 A는 가우스 소거법을 통해 Lower Triangular Matrix L과 Upper Triangular Matrix U로 분할할 수 있다. 거꾸로 L과 U를 알면 A를 구할 수 있게 된다.  
![Note3]  

행렬 U는 다시 pivot들의 대각행렬 D와 U로 분할하여 A = LDU로 표현할 수 있다.  
![Note4]  

가우스 소거법 중간에 Pivot 자리에 0이 있으면 다른 행과 교체하여 진행하는데 이를 Pivoting이라고 하고 이 과정도 Permutation 행렬로 표현할 수 있다.  
![Note5]  
