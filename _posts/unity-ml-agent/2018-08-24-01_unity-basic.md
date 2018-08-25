---
layout: post
title:  "[Unity 기초] Unity 설치 및 화면 구성"
categories: Unity
tags: [Unity, C#, ML-Agent]
comments: true
---

# 유니티 기초

강화학습을 공부하다 보면, 강화학습 이론을 공부하는 것만큼, 공부한 것을 실험해 볼 수 있는 환경 구축하는 것이 어렵다는 것을 느끼게 된다. 나를 포함해서 많은 사람들이 OpenAI Gym으로 강화학습 공부를 시작하는데, 문제는 현장에서 강화학습을 사용하지 않는 사람들의 입장에서 OpenAI Gym을 제외하고 강화학습을 적용해 볼 수 있는 프로젝트 및 환경이 거의 없다는 것이다.  

그러다 최근에 알게 된 것이 바로 **Unity ML Agent**이다. 이전까지 주로 게임 개발에 주력하였던 Unity에서 강화학습/모방학습을 위한 환경 구축에 Unity를 쉽게 사용할 수 있도록 ML Agent를 구축하여 베타버전을 오픈하였다. Unity 특유의 쉬운 사용성으로 많은 사람들이 강화학습 환경 구축에 Unity를 사용할 수 있도록 새로운 시장을 개척한 것이다.  

앞으로 유니티 초심자로서 유니티 기초와 C# 기초, 이를 응용한 ML Agent 사용법 등에 대해서 스터디 진행한 내용을 차근차근히 포스팅할 계획이다.    


[//]: # (Image References)
[image1]: {{ site.url }}/images/unity/download.png "Download"
[image2]: {{ site.url }}/images/unity/install.png "Install"
[image3]: {{ site.url }}/images/unity/new_project.png "New Project"
[image4]: {{ site.url }}/images/unity/basic_layout.png "Basic Layout"
[image5]: {{ site.url }}/images/unity/add_sphere.png "Add Sphere"
[image6]: {{ site.url }}/images/unity/sphere_view.png "View"
[image7]: {{ site.url }}/images/unity/hand_tool.png "Tool"
[image8]: {{ site.url }}/images/unity/parallel.png "Parallel"
[image9]: {{ site.url }}/images/unity/inspector.png "Inspector View"


## 유니티 설치

[유니티 다운로드](https://store.unity.com/kr)  

위 링크를 타고 유니티 홈페이지를 방문하면 유니티를 다운로드 할 수 있다. 영리목적으로 사용하지 않는다면, `Personal` 버전을 다운로드 하면 된다.  

![image1]  

OS에 맞는 설치 exe를 다운받고 설치를 시작한다. 가이드에 따라서 설치를 진행한다. 다만, 주의해야 할 점을, **ML Agent를 사용하기 위해서는, 설치 패키지를 선택할 때 `Linux Build Support`를 반드시 설치해야 한다는 것이다.**   

또한, Microsoft Visual Studio가 설치되어 있지 않다면 함께 설치하는 것이 좋다.   

![image2]  


## 유니티 기본 화면 구성

유니티 설치가 완료되어, 유니티를 실행시키면, 아래와 같은 화면이 뜨고 새로운 프로젝트를 생성하거나 기존에 생성된 프로젝트를 불러올 수 있다. 우리는 유니티를 처음 실행하였기 때문에 새로운 프로젝트를 생성해 보도록 하자.   

![image3]   

새로운 프로젝트 생성에 성공하면, 아래와 같은 기본 화면 구성이 나타난다.  

![image4]  

### 화면 구성

유니티 화면은 크게 4가지로 구분할 수 있다. 

1. Hierarchy View
2. Scene View
3. Inspector View
4. Project View

각 화면의 용도를 파악하기 위해서 빈 화면에 공 모양의 물체를 하나 만들어보자.  

#### 화면에 공 추가하기

1. Hierarchy View에서 오른쪽 마우스를 클릭한다.  
2. 3D Object > Sphere를 선택한다.  
3. Scene View에 흰 색 공이 나타난 것을 확인한다.  

![image5]  
  

#### Hierarchy View
Hierarchy View(하이어락키 뷰)는 화면에 있는 요소들의 리스트를 보여주는 화면이다. 유니티에서 환경을 구축하는 것은 영화를 찍는 과정과 비슷하다. 영화를 찍을 때 반드시 필요한 것이 카메라와 조명이듯이 유니티에서도 `Main Camera`와 `Directional Light` 두 요소는 기본으로 갖추고 있다.  

우리가 해야 할 일은 화면 구성에 필요한 물체를 추가하고, 상황에 따라서 물체들이 어떻게 움직일지 설정을 하고, 카메라가 어느 각도에서 어떻게 촬영을 할지 등을 정하는 것이다.  

![image6]  

프로젝트 생성 직후에는 Hierarchy View에 카메라와 조명 밖에 없었지만, Sphere 물체를 하나 추가하자, `Sphere`가 목록에 추가된 것을 확인할 수 있다.  

다른 유형의 물체를 추가하고자 한다면, 오른쪽 마우스를 클릭하고 추가하려는 물체 유형을 선택하면 된다. 또한, 물체에 대한 속성과 설정을 변경하기 위해서는 먼저 Hierarchy View에서 변경하고자 하는 물체를 선택해야 한다.  

#### Scene View / Game View 
##### Scene View

Scence View(씬 뷰)는 작업실 같은 영역이다. 물체의 위치, 크기, 회전 등을 변경할 수 있고, 카메라 앵글이나 조명 각도도 변경할 수 있다.  

Scene View에서 하는 작업들은 다양한 마우스 툴과 관련이 있는데, 이와 관련해서는 다음 포스팅에서 정리하겠다. 간단히 정리하면, Scene View에서 사용하는 마우스 툴은 크게 5가지가 있다.  
1. Hand Tool : 화면을 움직일 때
2. Move Tool : 물체를 움직일 때
3. Rotate Tool : 물체를 회전시킬 때
4. Scale Tool : 물체 크기를 조절할 때
5. Rect Tool : 물체를 사각형 scale로 조정할 때 

![image7]  

##### Game View

Game View(게임 뷰)는 게임이 실행될 때 사용자에게 보이는 화면이다. Game View는 작업 시에는 사용하지 않고, 나의 작업이 의도한대로 동작하는지 확인할 때 사용한다. Game View를 띄우고 위에 있는 `▶ play` 버튼을 누르면 게임이 실행되는 영상을 확인할 수 있다.  


작업을 하다보면 Scene View와 Game View를 자주 오가게 되는데, 귀찮다면 아래와 같이 두 뷰를 나란히 두고 작업하는 게 훨씬 편하다. `Game` 탭을 클릭한 상태에서 원하는 자리에 드래그하면 Game View를 움직일 수 있다.  

![image8]

#### Inspector View

![image9]

Inspector View(인스펙터 뷰)는 물체의 속성을 변경하거나 추가/삭제하는 곳이다. 속성을 변경하고자 하는 물체를 Hierarchy View에서 선택하면 Inspector View에서 현재 상태를 확인할 수 있다.  

기본적으로 물체의 위치와 회전, 크기를 변경할 수 있는 `Transform`이 생성되어 있다. 유니티에서는 이러한 속성 단위를 `Component(컴포넌트)`라고 하는데 이후 포스팅에서 컴포넌트의 의미와 종류 등에 대해서 하나씩 다룰 것이다.   

위의 화면은 `Sphere`의 위치를 변경한 모습이다. `Transform > Position > Y` 값을 5로 변경하였다. Scene View에서 Move Tool을 선택하고 마우스 움직임으로 이동시킬 수도 있지만, Inspector View에서는 정확한 값을 입력할 수 있다.   


#### Project View

Project View(프로젝트 뷰)는 프로젝트의 폴더/파일 구조를 볼 수 있는 곳이다. 탐색기와 거의 비슷하게 동작하기 때문에 추가 설명은 필요할 때 하겠다.  
