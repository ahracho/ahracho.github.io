---
layout: post
title:  "[선형대수] 9강 : 선형변환(Linear Transformation)"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)   

<iframe src="//www.slideshare.net/slideshow/embed_code/key/iiuwZSDB3rWod7" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/08-linear-transformation" title="선형대수 08. 선형 변환 (Linear Transformation)" target="_blank">선형대수 08. 선형 변환 (Linear Transformation)</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>

## Linear Transformation
- `Ax=b`를 이해하는 새로운 관점 : n차원의 Input x를 m차원의 Output b로 변환하는 과정 ▶ **Linear Transformation**
- 선형 변환 과정은 행렬로 표현할 수 있다 : Stretching, Rotation, Reflection, Projection

## Linear Function을 행렬로 표현하기
- 벡터 x가 단순한 미지수 조합이 아니라 다항식도 벡터로 표현할 수 있다.
- 미분/적분 같은 선형 함수 연산도 행렬로 표현할 수 있다.  
- 함수 연산을 하는 행렬 A를 쉽게 알아낼 수 없을까? → Basis 각각에 대해 Ax 값을 알고 있으면 A 없이도 모든 x 값에 대해 함수 결과값을 알 수 있다 (벡터 공간의 x는 Basis의 선형 조합으로 구할 수 있기 때문에).  
- Elementary Basis들의 연산 결과를 알면 A를 쉽게 구할 수 있다.  

