---
layout: post
title:  "[선형대수] 4강 : 역행렬과 전치행렬"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

<iframe src="//www.slideshare.net/slideshow/embed_code/key/luEwMB6aAPAxf9" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/04-inverse-and-transpose" title="선형대수 04. Inverse and Transpose" target="_blank">선형대수 04. Inverse and Transpose</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>

---

## 역행렬의 조건
- 역행렬은 `Det(A) != 0` 일 때에만 존재한다. 즉, 가우스 소거를 수행하고 Pivot 자리의 수가 모두 0이 아닌 값일 때만 역행렬이 존재한다. 
- 행렬 A에 대하여, 역행렬이 존재한다면, 행렬 A의 역행렬은 유일하다(Unique). 이는 반대로, Ax = b에서 A의 역행렬이 존재한다면 x도 유일하다는 것을 의미한다. 


## 역행렬 구하는 법(Gauss-Jordan Method)
- 가우스 소거법과 LU Decomposition을 활용하면 행렬 A의 역행렬을 구할 수 있다. (PPT 4-5 페이지)


## 전치행렬과 대칭행렬의 성질
- 전치행렬과 대칭행렬의 성질을 적절히 이용하면 Decomposition 등 계산이 훨씬 쉬워진다.
