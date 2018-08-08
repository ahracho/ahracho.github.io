---
layout: post
title:  "[선형대수] 7강 : 선형독립 및 기저벡터 / 8강 : 4가지 부 벡터 공간"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

<iframe src="//www.slideshare.net/slideshow/embed_code/key/LfU4F58xxkzjle" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/07-4-109037077" title="선형대수 07. 선형독립, 4가지 부벡터공간" target="_blank">선형대수 07. 선형독립, 4가지 부벡터공간</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>


## Linear Independence
### Basis Vectors and Dimension
- `C1V1 + C2V2 + ... + CnVn = 0` 식에서 `C1 = C2 = ... = Cn = 0`일 때만 식이 만족할 때 `V1, V2, ..., Vn` 벡터들이 선형독립이다.
- `Vk`가 다른 벡터들의 조합으로 표현 불가할 때 선형독립이다.
- 가우스 소거법의 결과로 m개의 pivot이 나왔을 때, 해당 m개의 열벡터는 서로 선형독립이다. 

### Rank of A
- 선형독립인 열벡터의 수
- 선형독립인 행벡터의 수
- 가우스 소거법 pivot의 개수
- C(A)의 Dimension

### Spanning
- 벡터들이 어떤 공간을 구성할 때 span한다고 한다 (All linear combinations of vectors constract a vector space).
- 특정 공간을 구성하는 벡터의 조합은 유일하지 않지만, 그 조합의 Linear combination은 유일하다.

### Basis Vector
- Minimum number of vectors to span the vector space : 2차원 공간을 표현하기 위해서는 적어도 2개의 벡터가 필요
- Maximum number of linearly independent vectors
- 특정 공간을 표현하는 기저 벡터는 유일하지 않지만, 특정 기저벡터의 선형 조합은 유일하다. 

## 4 Fundamental Subspaces
`A : m X n 행렬`이고, `Rank = r` 일 때,
- Column Space C(A) : 차원은 r
- Null Space N(A) : 차원은 (n - r)
- Row Space C(AT) : 차원은 r
- Left Null Space N(AT) : 차원은 (m - r)

* C(A) and N(AT) ⊂ Rm, C(AT) and N(A) ⊂ Rn
* Dim(C(A)) + Dim(N(AT)) = m, Dim(C(AT)) + Dim(N(A)) = n
* C(A) ⊥ N(AT), C(AT) ⊥ N(A)


## Existence of Inverse
- An inverse exists only when the rank is as large as possible.
- 정사각행렬이 아닌 경우에, 긴 방향으로만 역행렬이 존재한다.
- For r = m (m <= n), if there is a right inverse, Ax=b always has a solution(infinitely many solutions) (식보다 미지수가 많은 경우)
- For r = n (m >= n), it is hard to have an inverse, but once it exists it guarantees an unique solution. (미지수보다 식이 많은 경우 - 2차원에 여러개 직선)
