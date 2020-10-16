---
layout: post
title: "내 손안의 헤어샵"
img: "assets/elastin/1.GIF"
tags: [Computer Graphics, Computer]
---

![hook]({{"assets/elastin/2.GIF" | relative_url}})

### Introduction

소프트웨어 마에스트로 [링크](https://swmaestro.org/user/main.do) 에서 진행한 프로젝트 "내 손 안의 헤어샵"

한 장의 사진으로부터 3d face와 Hair 생성, 헤어 스타일 시뮬레이션을 할 수 있는 서비스.

Deep Learning, Vision, 3D 등의 기술이 사용됐다. 인터페이스는 Unity를 사용해 개발했다.

![hook]({{"assets/elastin/1.GIF" | relative_url}})

### 기획 의도

![hook]({{"assets/elastin/hook.PNG" | relative_url}})

![hook2]({{"assets/elastin/hook2.PNG" | relative_url}})

![hook2]({{"assets/elastin/intro.PNG" | relative_url}})

### Segmentation

![hook2]({{"assets/elastin/Segmentation.PNG" | relative_url}})

### Orientation Map

![hook2]({{"assets/elastin/Orientation.PNG" | relative_url}})

### 헤어 데이터 생성

- HairNet

Single Shot Image로부터 3d hair 데이터 생성하는 네트워크

[논문](https://arxiv.org/abs/1806.07467)  
[깃헙](https://github.com/givenone/HairNet)   
[논문 분석]({{ "assets/files/HairNet 분석 - 서준원.pptx" | relative_url}})  
[포스트](http://givenone.me/2020/07/22/HairNet-Data-Generation-%EC%BD%94%EB%93%9C%EB%B6%84%EC%84%9D.html)  

- Unsupervised Learning을 이용한 비슷한 스타일 추천 네트워크 (ResNet50)
simclr 참고  
[깃헙](https://github.com/givenone/hair_feature)  

### 얼굴 데이터 생성

**[링크 참고](http://givenone.me/works/singleshot)**


한 장의 사진으로부터 3d face를 생성한다. EOS (face fitting) 라이브러리를 사용했다.  
Segmentation 결과와 Dlib의 Landmark Detection을 사용하여 머리카락 부분을 지우는 후작업을 했다.  
또한 한 장의 사진으로부터 만들다보니 생긴 에러 영역(가려진 부분 등)에 대해서 자연스럽게 채워주는 인페인팅 작업을 진행했다.  
![hook2]({{"assets/elastin/face.jpg" | relative_url}})

### 헤어 렌더링

가벼운 헤어 렌더러를 개발했다. (Opengl 사용)
[링크 참고](http://givenone.me/works/hair)

![hook2]({{"assets/elastin/ex.PNG" | relative_url}})

### 헤어 스타일 시뮬레이션

유니티를 이용해 개발했다. 헤어 디자이너와의 인터뷰를 통해 스타일 상담 시 사용할 수 있는 인터페이스를 구성했다. 또한 실제 스타일링 과정에 고려되는 요소들을 포함시켰다. 아래와 같은 기능들이 있다. 개발 진행 중이다.

- 머리카락 선택
- 염색
- 펌
- 커트

![hook2]({{"assets/elastin/curl.jpg" | relative_url}})
![hook2]({{"assets/elastin/ccurl.jpg" | relative_url}})