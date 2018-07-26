---
layout: post
title:  "[선형대수] 7강 : 선형독립 및 기저벡터"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

[//]: # (Image References)

[Note1]: {{ site.url }}/images/linear-algebra/ch2/7-1.png "Note1"
[Note2]: {{ site.url }}/images/linear-algebra/ch2/7-2.png "Note2"


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다 [한양대 MOOC](http://www.kocw.net/home/search/kemView.do?kemId=977757).  
---


## Linear Independence
### Basis Vectors and Dimension
![Note1]  

- `C1V1 + C2V2 + ... + CnVn = 0` 식에서 `C1 = C2 = ... = Cn = 0`일 때만 식이 만족할 때 `V1, V2, ..., Vn` 벡터들이 선형독립이다.
- `Vk`가 다른 벡터들의 조합으로 표현 불가할 때 선형독립이다.
- 가우스 소거법의 결과로 m개의 pivot이 나왔을 때, 해당 m개의 열벡터는 서로 선형독립이다. 

### Rank of A
- 선형독립인 열벡터의 수
- 선형독립인 행벡터의 수
- 가우스 소거법 pivot의 개수
- C(A)의 Dimension

### Spanning
![Note2]  
- 벡터들이 어떤 공간을 구성할 때 span한다고 한다 (All linear combinations of vectors constract a vector space).
- 특정 공간을 구성하는 벡터의 조합은 유일하지 않다.

### Basis Vector
- Minimum number of vectors to span the vector space : 2차원 공간을 표현하기 위해서는 적어도 2개의 벡터가 필요
- Maximum number of linearly independent vectors
- 특정 공간을 표현하는 기저 벡터는 유일하지 않지만, 특정 기저벡터의 선형 조합은 유일하다. 
