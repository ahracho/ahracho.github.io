---
layout: post
title:  "[선형대수] 3강 : LU Decomposition"
categories: Linear-Algebra
tags: [Math, Linear-Algebra, KMOOC]
comments: true
---

# 3강 LU Decomposition
### 이번 장의 목표
1. LU Decomposition 과정을 이해한다.  
2. LDU Decomposition 과정을 이해한다.  
  
  
한양대 이상화 교수님의 오픈 강의로 공부한 내용을 정리한 것입니다. 강의 영상과 강의 노트는 다음 링크에서 다운받아 작성하였습니다.  
[http://www.kocw.net/home/search/kemView.do?kemId=977757](http://www.kocw.net/home/search/kemView.do?kemId=977757)  
  
<iframe src="//www.slideshare.net/slideshow/embed_code/key/2wlUBjRmVaPw74" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/ahra-cho/03-lu-decomposition" title="선형대수 03. LU Decomposition" target="_blank">선형대수 03. LU Decomposition</a> </strong> from <strong><a href="https://www.slideshare.net/ahra-cho" target="_blank">AHRA CHO</a></strong> </div>  
  
  

## Elementary Matrix
행끼리 계수를 곱해서 빼기, pivoting을 포함하여 가우스 소거법의 과정을 행렬로 표현할 수 있다. 소거법을 진행하면서 계수를 소거하기 위해서 빼고 곱했던 과정은 Lower Triangular Matrix 행렬 L에 표현되어 최종적으로 `A = LU`의 형태로 표현할 수 있다.  


## Triangular Factorization (Decomposition)
연립방정식의 계수 행렬 A는 가우스 소거법을 통해 `Lower Triangular Matrix L`과 `Upper Triangular Matrix U`로 분할할 수 있다. 거꾸로 L과 U를 알면 A를 구할 수 있게 된다. A라는 비교적 복잡합 시스템을 그대로 이해할 수 없을 때 간단한 L과 U를 안다면, 시스템 A를 추론할 수 있다.  

행렬 U는 다시 pivot들의 대각행렬 D와 U로 분할하여 A = LDU로 표현할 수 있다.  

가우스 소거법 중간에 Pivot 자리에 0이 있으면 다른 행과 교체하여 진행하는데 이를 Pivoting이라고 하고 이 과정도 Permutation 행렬로 표현할 수 있다.  

가우스 소거법의 결과로 생긴 행렬의 Pivot 자리에 0이 생기면 해당 연립방정식은 해를 구할 수 없는 Singular Case이다. 이런 경우에는 행의 위치를 아무리 바꾸어도 Pivot 자리에 적절한 값을 둘 수 없기 때문에 Permutation Matrix를 구할 수 없다. 반대로 Non-singular Case에는 가우스 소거법의 모든 과정을 행렬 연산으로 표현할 수 있고, `PA = LU = LDU`로 표현할 수 있다.  
