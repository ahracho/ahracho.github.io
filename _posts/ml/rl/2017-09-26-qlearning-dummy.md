---
layout: post
title:  "[Q-Learning] Frozen Lake 사용하기"
categories: 강화학습
tags: [강화학습, OpenAI-Gym, Frozen-Lake]
comments: true
---

## 강화학습이란
심리학개론 수업을 들으면 스키너의 강화이론이라는 것을 배운다. 교육학에서도 언급되는 이론인데, 요지는 이렇다. 대상이 어떤 행동을 하게 하려면 Reward를 주고, 어떤 행동을 하지 않게 하려면 Punishment을 주면 된다. 강화학습은 강화이론을 머신러닝에 적용한 형태라고 이해하면 되는데 알고리즘에 따라서 어떤 판단을 했을 때 돌아오는 Reward에 따라서 이 판단이 옳은 것이었는지를 학습하는 것이다.  

강화학습을 진행할 때는 크게 state, action, reward에 신경을 쓰면 된다. state는 현재의 상태, 테트리스 게임의 예를 들면, 현재 아래에 쌓여있는 블럭과 아래로 내려오고 있는 블럭의 모양 (현재 화면의 상태) 등이 state에 해당될 것이다. 현재 state에 기반하여 다음에 취하게 될 동작을 나타낸다. 테트리스에서 블럭을 아래로 내릴지, 회전시킬지, 옆으로 움직일지 등이 action에 해당된다. reward는 action에 따라 얻게 되는 보상이다. Reward는 각 action마다 특정한 값으로 보상이 되는데, 양수/음수/0의 값이 돌아온다.  

학습을 하는 동안 우리는 **특정 state에서 어떤 action을 취했을 때 돌아오는 reward를 피드백 삼아 앞으로 어떤 action을 취해야 reward를 최대화할 수 있는지 학습**시키는 방법을 공부하게 될 것이다.  

## Playing OpenAI Gym Games
"OpenAI Gym is a toolkit for developing and comparing reinforcement learning algorithms."   

강화학습을 공부하면서 알게된 신세계가 있는데 바로 OpenAI Gym이라는 툴이다. Gym이라는 이름처럼 강화학습 알고리즘을 훈련시키는 체육관 같은 툴킷인데 여러 환경이 구축되어 있다. 앞서 설명했듯이 강화학습은 특정 환경에서 어떤 action을 취할 것인가 하는 모델을 구하는 것인데, OpneAI Gym이 환경을 구성하고 우리는 그 환경 안에서 나의 강화학습 모델이 잘 동작을 하는데 테스트 해보는 것이다. 여러 환경 중에서 김성훈 교수님 강의에서는 강화학습 기초 알고리즘을 배우기 위해서 그 중에서 Frozen Lake라는 환경을 주로 활용한다.  

Frozen Lake는 얼어붙은 호수 위를 가상으로 만들어 놓은 것인데, M by N의 게임판에서 상하좌우로 이동을 하면서 시작점에서 도착점까지 물에 빠지지 않고 이동하는 것을 reward 1로 계산한다. 완벽하게 얼어붙은 호수가 아니기 때문에 중간중간 성긴 얼음판(Hole)이 있고 이 지점으로 이동할 경우 물에 빠져 게임이 종료된다. 발을 내딛기 전(action을 취하기 전)까지는 그 앞이 얼음인지 구멍인지 알 수 없기 때문에 이것저것 시도해보면서 빠지지 않고 도착점에 갈 수 있도록 학습을 해야한다.

OpenAI Gym을 사용하려면 먼저 github에서 gym 라이브러리를 다운받고 필요한 패키지들을 설치해야 한다. 

~~~bash
sudo apt install cmake
apt-get install zlib1g-dev
sudo -H pip install gym
~~~

아래는 Frozen Lake 환경에서 사용자 키입력으로 움직이는 게임을 구현한 것이다.  

~~~python
import gym  # OpenAI Gym을 사용하기 위해 라이브러리 import
from gym.envs.registration import register
import sys, tty, termios # 키 입력을 위한 라이브러리

# 키입력을 받기 위한 클래스
class _Getch:
  # 키값 리턴
  def __call__(self):
      fd = sys.stdin.fileno()
      old_setting = termios.tcgetattr(fd)
      try:
          tty.setraw(sys.stdin.fileno())
          ch = sys.stdin.read(1)
      finally:
          termios.tcsetattr(fd, termios.TCSADRAIN, old_setting)
      print(ch)
      return ch
  
inkey = _Getch()

# OpenAI Gym에서 미리 정의되어 있는 action 매핑
LEFT = 0
DOWN = 1
RIGHT = 2
UP = 3

# 키보드 키와 상하좌우 동작을 매핑
arrow_keys = {
    'w' : UP,
    's' : DOWN,
    'd' : RIGHT,
    'a' : LEFT
}

# Gym 환경설정
# https://gym.openai.com/envs/ 에 들어가면 다양한 환경을 살펴볼 수 있다.
# Frozen-Lake : https://gym.openai.com/envs/FrozenLake-v0/ 
register(
    id = 'FrozenLake-v3', 
    entry_point='gym.envs.toy_text:FrozenLakeEnv', 
    kwargs={
        'map_name' : '4x4', # 4x4 크기의 맵
        'is_slippery' : False # 미끄러질 가능성 없음 (나중에 다룰 것)
    }
)

env = gym.make("FrozenLake-v3")
env.render()

while True:
    # 키 값을 기다린다
    key = inkey()
    # 만약에 우리가 정의한 키 값이 아닌 경우, 게임 종료
    if key not in arrow_keys.keys():
        print("Game aborted!")
        break
    
    # 키값과 액션 매핑을 사용해서 상하좌우 중 어떤 행동을 취할지 리턴
    action = arrow_keys[key]
    # env.step(action) 은 결정한 행동을 실행한다는 의미이고,
    # 행동의 결과로 이동한 자리가 어딘지(state), 행동의 reward는 얼마인지(reward), 
    # 게임이 끝났는지: 구멍에 빠지거나 결승점에 도착하거나 (done), 그 밖의 정보 (info)가 리턴된다.
    state, reward, done, info = env.step(action)

    # 화면에 Frozen Lake 맵과 현재 위치가 어딘지 그림을 그려줌 (Frozen Lake는 콘솔에 출력)
    env.render()
    print("state : {0}, Action : {1}, Reward : {2}, Info : {3}".format(state, action, reward, info))

    # 게임이 끝났으면 Reward를 출력
    # Frozen lake는 결승점에 도착해야만 Reward 1을 받는다.
    if done :
        print("Finished with reward {0}".format(reward))
        break

~~~

위의 예제는 OpenAi Gym 환경에 강화학습을 적용하기 전에 Frozen Lake라는 환경이 대략 어떤 식으로 구성되어 있고 동작하는지 이해하기 위한 것이다. 위의 예제를 어느 정도 이해하였다면 이제 이 환경에 강화학습 이론을 적용해보자.