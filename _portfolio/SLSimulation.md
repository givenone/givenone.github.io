---
layout: post
title: "Light Stage Simulation"
img: "assets/computer_img/IMG_6455.JPG"
feature-img: "assets/img/pexels/computer.jpeg"
tags: [Computer Graphics, Computer]
---

![image]({{ page.img | relative_url }})

### Blender를 사용한 Light Stage 시뮬레이션

### Introduction

LightStage는 최소 수십개의 Light와 지름 약 2m 이상의 기구가 필요하기 때문에 실제 장비로 촬영하기 쉽지 않다.
Light Stage를 Blender로 시뮬레이션 해서 촬영 결과를 렌더링할 수 있는 프로그램을 개발했다.
Blender의 Cycles 렌더링 엔진을 이용했으며, PBRT를 적용했다. 카메라의 위치, 광원의 세기, Multi-view, 대상 물체 등의 옵션을 설정할 수 있다.

Blender의 Python 패키지인 bpy를 사용했으며 ubuntu 18.0.4에서 작동한다. Blender는 2. 버전을 사용해야 한다.

Default로 사용된 물체는 **Digital Emily**다. [Digital Emily](https://vgl.ict.usc.edu/Data/DigitalEmily2/) Wiki Human Project로 USC에서 만든 데이터이다. Emily O'Brien을 스캔해서 배포했다. Diffuse, Specular, Subsurface Scattering을 위한 HDR Texture를 사용했으며, Base Mesh와 2 종류의 Displacement Map을 Shader Input으로 사용해서 최대한 실제와 같은 렌더링을 할 수 있도록 했다.

### Result

렌더링 결과로 아래와 같은 이미지가 얻어진다. 패턴은 Binary Spherical Gradient와 Spherical Gradient를 구현해놓았다. x, y, z, w(all on)과 그 반대를 켠 사진, 총 6-7장을 렌더링한다.
<p align="center">  
    <img src="{{"assets/computer_img/x.png" | relative_url}}" alt="junwon" width="60%" align="center"/>
</p>

작업할 때가 넷플릭스 킹덤 시즌 2가 나올 때였다. 유쾌한 작업을 위해 홍채의 텍스쳐를 입히지 않아 킹덤의 좀비같은 연출을 했다. 눈 자체는 Light Stage 렌더링에 메인 대상이 아니었기 때문에 눈을 좀비처럼 남겨두었다.

[Github Repo](https://github.com/givenone/morpheus/tree/master/Simulation)에서 코드와 다양한 샘플 이미지 등을 확인할 수 있다.