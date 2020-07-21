---
layout: post
title: Face Landmark Detection
img: "assets/computer_img/18C0483D-175F-4DC5-8257-37731B970030.jpg"
date: July 2020
tags: [Computer Graphics, Computer]
---

![image]({{ page.img | relative_url }})

## Introduction

Opencv와 Dlib을 이용해 사용한 Face Landmark Detection. python을 사용했으며, Light Stage Project를 위해 사용했다.
코드는 [Github 링크](https://github.com/givenone/lightstage/blob/master/facelandmark.py)에서 확인 가능하다.
아래와 같이 실행 가능하며, 코드에 이미지 path 등이 하드코딩 돼있으므로 수정해서 사용해야 한다.

``` 
$ python facelandmark.py
```  

실행을 위해서는 opencv-python 과 dlib이 설치돼있어야 한다. dlib과 opencv-python의 안정적 설치와 실행을 위해 linux 환경에서 실행을 추천한다.
또 face landmark 데이터 (약 1GB)를 다운받아야 한다.

## 사용 기술

딥러닝 라이브러리인 dlib을 사용한 face landmark detection이다. 63개의 face landmark를 찾아낸다. 빠른 시간 ( < 1초) 에 높은 정확도로 찾아낸다.
dlib을 사용하기 전 opencv 내장 함수로 image-processing 단에서 face landmark를 찾으려고 시도해 봤는데 매우 부정확했다. 특히 Lighting Condition에 따라 결과의 편차가 아주 심했다. image processing에서 딥러닝의 강력함을 몸소 느낄 수 있었다. ~~미리 학습 된 모델이 있다면 말이다. 학습을 하는 과정은 끔찍하다.~~

두 사진에서 각각 Face Landmark를 찾은 후 Matching point를 찾는다. Opencv 내장 함수를 이용했다. ORB Detector와 Brute Force Matcher (Norm Distance 사용)을 이용했다. [opencv docs](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_matcher/py_matcher.html) 에서 함수를 확인 가능하다. 

