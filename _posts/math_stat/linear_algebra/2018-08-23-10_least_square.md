---
layout: post
title:  "[선형대수] 11강 : 벡터 투영과 최소제곱법"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---


# 11강 벡터 투영과 최소제곱법
### 이번 장의 목표
1. `m > n` 연립방정식에서 해가 존재하지 않을 때, 최적의 해를 찾는 방법을 알아본다.  
2. 최소제곱법을 활용하여 선형회귀 문제를 푸는 방법을 알아본다.  
  

<iframe src="//www.slideshare.net/slideshow/embed_code/key/hfoZcWBoosa8YA" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/11-111070980" title="선형대수 11강 벡터 투영과 최소제곱법" target="_blank">선형대수 11강 벡터 투영과 최소제곱법</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>    
  
  

한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

## M x N 행렬과 연립방정식
### `M = N` 행렬 
- 방정식의 개수와 미지수의 개수가 동일한 형태  
- 해를 찾기 위해서 가우스 소거법으로 `LDU Decomposition` 수행(참고 : [2강 1차 연립방정식과 가우스 소거법](https://ahracho.github.io/posts/math_stat/linear_algebra/2018-06-26-2_gaussian-elimination/))   
- `Ax=b`에서 A행렬이 Non-singular 일 때 유일한 해가 존재하고, Non-singular 행렬은 가우스 소거법을 완료하였을 때 n개의 0이 아닌 pivot이 존재하는 행렬이다.  
- A가 Singular 하다면 연립방정식의 해는 무수히 많이 존재하거나, 해가 존재하지 않는다.  

### `M < N` 행렬
- 방정식의 개수가 미지수의 개수보다 적은 경우 (예: 미지수 x, y 방정식에 식은 하나)
- 해를 찾기 위해서 가우스 소거법으로 Row Reduced Form 형태로 변형 (참고 : [6강 영벡터공간과 해집합](https://ahracho.github.io/posts/math_stat/linear_algebra/2018-07-25-6_null_space/))  
- 유일한 해가 존재하는 경우는 발생하지 않고, 해가 무수히 많거나 해가 존재하지 않는다.  
- 해집합의 표현은 free variable의 조합으로 나타낸다.  

### `M > N` 행렬
- 방정식의 개수가 미지수의 개수보다 많은 경우 (예: 미지수 x, y 방정식에 식이 3~4개)
- 유일한 해가 존재할 수 있지만, 해가 존재하지 않을 가능성이 높다. (평면 상의 여러 개의 직선이 단 하나의 교차점을 지나는 경우보다 여러 교차점이 생길 가능성이 많다)  
- 이처럼 단 하나의 해가 존재하지 않는 경우 `최적의 해`를 찾아야 한다.   


## 최적의 해 찾기
해가 존재하지 않는다는 것은 `Ax=b`에서 `b ∉ C(A)`라 의미이다. 최적의 해의 의미는 `Projection` 개념을 사용하여, `b와 가장 근접한 C(A)상의 점을 찾는다`는 것이다.  
- error : \\[𝐸^2=‖𝐴𝑥−𝑏‖^2\\]
- error 벡터는 C(A)와 수직이기 때문에(수선의 발을 내려야 최단 거리가 되므로) error 벡터는 left nullspace에 속한다. (참고 : [8강 4가지 부벡터공간](https://ahracho.github.io/posts/math_stat/linear_algebra/2018-07-26-7_linear_independent/))  
\\[A^T(b-A\hat{x})=0\\]  
\\[A^TA\hat{x}=A^Tb\\]  
- $$A^TA$$의 역행렬이 존재한다면,
\\[\hat{x}=(A^TA)^{-1}A^{T}b\\]   
\\[p=A\hat{x}=A(A^TA)^{-1}A^{T}b\\]   


## Least Square Problem
- 일직선에 있지 않은 (같은 벡터 공간에 있지 않은) 점들을 가장 근사한(error가 작은) 직선에 투영하기  
- 직선의 방정식 `y=ax+b`에서 우리가 찾아야 하는 것은 a와 b
- 점들과 직선의 방정식을 재구성하면 `Ax=b` 형태의 연립방정식으로 나타낼 수 있다.
