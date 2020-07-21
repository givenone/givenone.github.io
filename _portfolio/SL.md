---
layout: post
title: "Face Scanner"
img: "assets/computer_img/IMG_5316.JPEG"
tags: [Computer Graphics, Computer]
---

![image]({{ page.img | relative_url }})

### Introduction

Structured Light를 사용한 3D Face Scanner.
Shift Pattern을 적용해 더 정밀한 Depth Estimation이 가능하도록 했다.

Structured Light 3D Scanner에 대한 설명은 [링크](https://en.wikipedia.org/wiki/Structured-light_3D_scanner)에서 확인할 수 있다.

논문 [Capture of hair geometry using white structured light](https://www.researchgate.net/publication/321067082_Capture_of_hair_geometry_using_white_structured_light) 를 구현했다. structured light scanner를 개선해 머리카락의 Geometry까지 Capture가 가능하도록 했다.

### Code

[Github Repo](https://github.com/givenone/SLhaircapture)에서 확인할 수 있다.  
결과로 Depth Map을 얻을 수 있으며, 결과 이미지는 아래 사진과 같다.  
![image]({{ "assets/computer_img/depth_map_final.png" | relative_url }})
Depth Map을 Calibration 정보를 사용해서 pointcloud로 바꾼 후, ply 파일로 저장할 수 있다.
ply 파일은 face와 color 정보는 없으며, meshlab 등에서 vertex rendering으로 볼 수 있다.  

