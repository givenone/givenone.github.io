---
layout: post
title: HairNet, Data Generation 코드 분석
tags: [HairNet, Computer, Computer Graphics]
author: givenone
excerpt_separator: <!--more-->
---

딥러닝을 사용해 이미지로부터 3d 머리카락 데이터를 생성하는 HairNet 논문 분석, 그리고 저자 구현 코드 분석.
<!--more-->

# HairNet 논문 분석

[ppt 파일]({{ "assets/files/HairNet 분석 - 서준원.pptx" | relative_url}}) 참고

# HairNet Data Generation 코드 분석

HairNet 저자가 구현해 놓은 학습용 데이터 생성 코드. 두 가지 파트로 구분되어 있음. 논문의 내용을 그대로 구현해 놓음.
Github에 공개되어 있는 [저자 구현 코드](https://github.com/papagina/HairNet_DataSetGeneration)를 분석한 내용이다. HairNet은 한 장의 Input 이미지로부터 input image와 가장 비슷한 3D Hair Data를 생성해내는 Deep Learning 네트워크다. AutoEncoder 네트워크로 구성되어 있다. 자세한 내용은 [논문](https://arxiv.org/abs/1806.07467)을 참고.


## 1. HairMix

- 코드가 없음. executable file만 존재함
- 343개의 usc hair salon데이터로부터 데이터를 생성해내는 것.
- 10개의 클래스로 스타일을 나눈 후, Pairwise Mix를 함
- 각 헤어 스타일에서는 clustering으로 strand를 5개 클래스로 나눈 후 mix -> 2^5개 데이터가 생성
- 논문 내용에 따르면 모든 pair에 대해 mix를 하지 않고 랜덤하게 해서 40k 이상의 데이터만 생성한다고 함.
- 구현체는 모든 pair에 대해 생성하는 것으로 보임. 그래서 몇백기가 이상의 데이터가 생성됨. 적당한 범위에서 끊어주거나, 데이터를 랜덤하게 제거한 후 프로그램을 실행하는 것이 방법이 될 수 있을 듯... **(모든 페어의 데이터에 대해서 32개를 만들 경우 약 1000만개의 데이터가 생성될 것으로 예상됨....)**
- `rootPosition_new.txt` (strand가 시작하는 root position)을 기준으로 모든 데이터가 같은 위치로 부터 시작한다고 되어있음. (1000개의 strand) 각 root 에 대해 position과 normal이 저장되어 있음. 그런데 이 좌표가 무언가 이상함... (뭔가 translation이 되어있음. y 좌표가 굉장히 큼). 그래서 생성된 데이터를 살펴 보니, 원본 데이터(Usc)와 마찬가지로 원점 기준으로 기껏해야 2를 초과하지 않은 포지션에 있음. 이 txt 데이터가 모든 데이터가 생성된 후에 작성되는 것인지, 원래 있는 건진 모르겠으나 일단 무시해도 좋을 것 같음. (3D head데이터와 hair data로부터 알아낼 수 있음)

## 2. Hair_generate_convdata_and_imgs  

- 컴파일 해야 함. 다음과 같은 dependency가 존재하며, CMake로 컴파일. 컴파일 되는 것까지 확인함.
```
#OpenGL
#GLEW
#glfw3
#GLUT
#OPENCV
#OPENMP
#OpenMesh-6.3
```
- 마찬가지로 논문 내용을 착실히 구현해 놓음
- Train data를 포맷에 맞게 생성해 놓은 것임. (input : orientation map (256 * 256 * 3(rgb)); output : strand data(32 * 32개, position & curvature) )
- orientation map은 헤어 데이터로부터 tangent를 계산한 후, opengl LINE으로 그렸음... 256 * 256이어서 그런지 아래 사진처럼 꽤 자연스럽게 보이는 걸 확인할 수 있음...  
![strands00086]( {{ "assets/computer_img/strands00086.png" | relative_url}})
- body는 obj 파일을 로드해서 헤어와 같이 렌더링 한 것.
* 여기서 생기는 의문이, 코드에는 헤어 데이터와 body(head를 포함한 것)을 align해주는 부분이 없음. 원래 부터 position이 정확히 일치하는 데이터인 것 같음. 아마 rootposition.txt가 이 데이터와 관련이 있는 듯. 우리는 실행 시에 usc hair salon에 있는 obj 파일을 넣어주면 됨.

- 코드를 분석해서 주석을 추가해 놓음. 추후 수정해서 사용할 수 있음.
- 전에 제작한 HairNet 분석 PPTX를 참고.


**TODO**
- Hair_generate_convdata_and_imgs 가 잘 실행되는 지 확인해 볼 필요가 있음
- Hair Data를 보기 위한 툴(렌더링)을 만들어야 함. 일단 gl로 작업 중. 
- Hair를 렌더링하기 위한 방법을 고안해야 함. 이것이 정해지면 Unity로 작업하면 됨.
- 현재 컬러는 생성되지 않기 때문에, 원본 이미지로부터 Texture Mapping 을 할 수 있는 방법을 찾아야 함.