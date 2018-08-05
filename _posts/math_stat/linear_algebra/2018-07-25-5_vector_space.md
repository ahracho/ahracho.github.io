---
layout: post
title:  "[선형대수] 5강 : 벡터 공간과 열벡터"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

<iframe src="//www.slideshare.net/slideshow/embed_code/key/c2rfeFyOjkf9sk" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/05-108695910" title="선형대수 05. 열벡터공간" target="_blank">선형대수 05. 열벡터공간</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>

---

1단원에서는 `nXn`의 정사각 행렬을 가정하고 연립 방정식을 푸는 방법에 대해 집중하였다면, 2단원에서는 `식의 개수(m)이 미지수의 개수(n)보다 적은 경우(m < n)`를 다룬다. 가로가 긴 직사각 행렬의 경우에는 해가 존재하지 않거나, 해가 존재하는 경우에는 무수히 많이 존재한다.   

## Vector Space and Subspace
### 벡터공간
- 벡터의 덧셈과 스칼라 곱셈에 닫혀있고,
- 원점을 포함하며,
- 항등원과 역원이 존재하는 공간을 벡터공간으로 정의한다.
- 벡터 공간의 조건을 만족하는 부분집합을 subspace라고 정의한다(원점을 반드시 지나야)  

## Column Space of A : C(A)
**행렬 A의 열벡터공간 C(A) : 행렬 A의 column 벡터들의 linear combination으로 이루어진 공간**  

`Ax = b`에서 b가 C(A)에 포함되어야 해가 존재한다 (`Ax=b` is sovable if and only if b can be expressed as a combination of the columns of A. Then b is in the column space).  

A의 역행렬이 존재한다면 `x=A'b`로 해가 존재하고, b는 C(A)에 포함된다. 이 때 b가 무엇이든 C(A)에 속해야 하므고 C(A)는 whole space이다.  
