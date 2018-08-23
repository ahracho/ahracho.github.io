---
layout: post
title:  "[선형대수] 2강 : 1차 연립방정식과 가우스소거법"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---


# 2강 1차 연립방정식과 가우스소거법
### 이번 장의 목표
1. 가우스 소거법의 과정을 이해한다.  
2. Singular/Non-singular 행렬의 조건을 알아본다.
3. Ax=b 방정식의 해가 존재하기 위한 조건을 이해한다.
  
  
한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)  
  
  
<iframe src="//www.slideshare.net/slideshow/embed_code/key/LjLUIlWbCIbpsK" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/02-108497093" title="선형대수 02. 가우스 소거법" target="_blank">선형대수 02. 가우스 소거법</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>    
  
  

## Gaussian Elimination
**가우스 소거법**은 행렬로 표현된 연립방정식에서 1행부터 차례로 적절한 값을 곱하고 서로 빼주면서 쉽게 해를 찾을 수 있는 형태로 변형하여 방정식의 해를 찾는 과정이다. 이 과정에서 계수행렬을 Upper Triangular Matrix로 변형하게 되는데, 행렬 U의 대각선 위치에 있는 값들을 Pivot이라고 한다.  
Non-Singular의 경우에는, Pivot이 모두 0이 아닌 값을 가지고, Pivot 중에 0인 값이 있으면 Singular Case로, 이 경우에는 해가 없거나, 무수히 많게 된다.  


## Matrix Notation
Ax=b 형태로 작성된 연립방정식을 다시 풀어보면 상수와 벡터의 Linear Combination으로 표현할 수 있다. 지난 포스팅에서 설명했듯, 연립방정식을 벡터의 조합으로 이해했을 때, 행렬 A의 column vector들을 적절한 배수로 곱하고 더한 값(Linear Combination)이 우항의 벡터가 될 수 있는지를 구하는 것이 연립방정식을 푸는 과정이다.  
b를 행렬 A의 열벡터 조합으로 표현할 수 있다는 것은 b가 행렬 A가 표현하는 어떤 공간 안의 벡터라는 것이고, 연립방정식의 해가 (하나이든 무한개이든) 존재한다는 의미이다.  
