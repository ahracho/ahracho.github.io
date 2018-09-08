---
layout: post
title:  "[선형대수] 12강 : Gram-Schmidt Orthogonalization"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---


# 12강 Gram-Schmidt Orthogonalization
### 이번 장의 목표
1. Gram-Schmidt Orthogonalization 과정을 이해한다.   
2. Orthonormal 벡터들을 사용하였을 때의 이점을 이해한다.
3. QR 분할을 이해한다.   

    
<iframe src="//www.slideshare.net/slideshow/embed_code/key/sq0PtVOvHW53Lt" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/12-gramschmidt-orthogonalization" title="선형대수 12강 Gram-Schmidt Orthogonalization" target="_blank">선형대수 12강 Gram-Schmidt Orthogonalization</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>  
    


한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

## Gram-Schmidt Orthogonalization
- Orthogonal 벡터들로 벡터 공간을 구성하면 연산이 간편해진다.  
- Linearly Independent 벡터들이 주어졌을 때, 이들을 변형하여 Orthogonal Basis로 바꾸면 이후 연산을 편하게 할 수 있을 것!  
- 이 과정이 바로 `Gram-Schmidt Orthogonalization`!  

### 과정
Linearly Independent 벡터 n개가 있을 때, 1차원에서 N차원까지 하나씩 차원을 늘여가면 된다.  
1. `벡터 a` 방향으로 길이 1인 `q1`을 구한다.  
2. `q1`과 수직인 방향으로 `벡터 b`를 Projection 한 길이 1의 `q2`를 구한다.  
  - `q1`과 `q2`로 벡터 a와 b를 표현할 수 있다.  
3. `q1, q2`와 수직 방향으로 `벡터 c`를 Projection한 길이 1의 `q3`를 구한다.
4. N차원까지 이를 반복한다.  

## Orthogonal Basis
### 정사각 행렬
`Ax=b`에서 행렬 A가 NxN 정사각 행렬이고, N개의 Linearly Independent 벡터로 구성되어 있을 때, 유일한 해를 구할 수 있다. N개의 Linearly Independent 벡터가 있다는 것은, 이 벡터들로 N차원 공간을 모두 표현할 수 있다는 의미이다. 행렬 A를 그대로 사용할 수 있지만, 이를 Orthogonal한 벡터 N개로 변형을 하면 연산이 간편해진다.  

- **Orthonormal (Orthogonal + 길이 1)인 벡터 N개로 구성된 행렬 Q가 있을 때, Q Transpose와 Q Left-Inverse는 동일하다.**   
  - Q가 정사각 행렬이면 역행렬은 좌우 모두 존재한다.  
  - Q 행렬의 대표적인 예는 `Rotation Matrix`  
  - `Qx=b` 형태라면 역행렬을 가우스 소거법으로 따로 구할 필요없이 Q Transpose만 하면 해를 계산할 수 있다.  


### 직사각 행렬
M x N 행렬 A에서 직사각 행려은 M > N 혹은 M < N 두가지 경우인데, Orthogonal 벡터들로 Q를 구성하기 위해서는 공간의 차원보다 열벡터가 적어야 한다. 3차원 공간에서 Orthogonal한 벡터가 3개까지 밖에 나올 수 없다는 사실을 떠올려보자. 따라서, M > N 경우만 생각하면 된다.  

M > N의 경우, `Ax=b`는 단 하나의 해가 존재하거나, 해가 존재하지 않는다. (미지수보다 식이 많은 경우!) 해가 존재하지 않을 때, 우리는 Projection 개념을 활용하여 최적의 해를 찾아내었다.  
- `Qx=b`로 변형하게 되면, Q Transpose와 Q Left-Inverse가 동일하다는 성질을 이용하여 최적의 솔루션 x를 (Q Transpose x b)로 쉽게 구할 수 있다.  
- 마찬가지로 Projection 포인트 p = (Q x Q Transpose x b)로 구할 수 있다.  


## QR Factorization
- Gram-Schmidt 기법을 사용하여 행렬 A를 Orthonormal Vector들로 이루어진 행렬 Q와 Upper Triangular R로 분할한다.  
- 가우스 소거법을 활용하여 LU 분할을 하였을 때, 역행렬 계산이나 행렬곱 등이 편하게 이루어졌던 것처럼, QR로 분할하였을 때도 연산량이 훨씬 줄어든다.  
