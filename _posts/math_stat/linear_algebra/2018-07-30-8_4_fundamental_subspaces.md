---
layout: post
title:  "[선형대수] 8강 : 4가지 부 벡터 공간"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

[//]: # (Image References)

[Note1]: {{ site.url }}/images/linear-algebra/ch2/8-1.png "Note1"
[Note2]: {{ site.url }}/images/linear-algebra/ch2/8-2.png "Note2"
[Note2]: {{ site.url }}/images/linear-algebra/ch2/8-3.png "Note3"
[Note2]: {{ site.url }}/images/linear-algebra/ch2/8-4.png "Note4"


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다 [한양대 MOOC](http://www.kocw.net/home/search/kemView.do?kemId=977757).  
---


## 4 Fundamental Subspaces
![Note1]  ![Note2]

A : m X n 행렬이고, Rank r 일 때,
- Column Space C(A) : 차원은 r
- Null Space N(A) : 차원은 (n - r)
- Row Space C(AT) : 차원은 r
- Left Null Space N(AT) : 차원은 (m - r)

* C(A) and N(AT) ⊂ Rm, C(AT) and N(A) ⊂ Rn
* Dim(C(A)) + Dim(N(AT)) = m, Dim(C(AT)) + Dim(N(A)) = n
* C(A) ⊥ N(AT), C(AT) ⊥ N(A)


## Existence of Inverse
![Note3] ![Note4]
- An inverse exists only when the rank is as large as possible.
- 정사각행렬이 아닌 경우에, 긴 방향으로만 역행렬이 존재한다.
- For r = m (m < n), if there is a right inverse, Ax=b always has a solution(infinitely many solutions) (식보다 미지수가 많은 경우)
- For r = n (m > n), it is hard to have an inverse, but once it exists it guarantees an unique solution. (미지수보다 식이 많은 경우 - 2차원에 여러개 직선)
