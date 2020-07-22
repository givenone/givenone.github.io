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

참고로 머리카락은 3D 스캔이 매우 어렵다. 머리카락은 얇고, 빛을 반사하지 않고 대부분 흡수한다. 또한 머리카락 간의 광학적 상호작용이 복잡하기 때문에 빛을 이용해 스캔하는 것은 쉽지 않다. 따라서 일반적인 패턴을 사용할 경우 노이즈로 인식되는 경우가 많으며 정확한 Geometry 정보를 획득할 수 없다.  

한 픽셀씩 이동하는 Shift Pattern을 structure light 패턴에 적용한 후, Sine Fitting 등의 후처리작업을 거쳐 머리카락의 위치를 최대한 정밀하게 측정해볼 수 있었다. 패턴 뿐만 아니라 하드웨어 컨트롤, 캘리브레이션, 프로젝터 해상도 등 다양한 요소가 성능에 영향을 미치는 것도 확인했다.

### Code

[Github Repo](https://github.com/givenone/SLhaircapture)에서 확인할 수 있다.  
결과로 Depth Map을 얻을 수 있으며, 결과 이미지는 아래 사진과 같다.  
![image]({{ "assets/computer_img/depth_map_final.png" | relative_url }})
Depth Map을 Calibration 정보를 사용해서 pointcloud로 바꾼 후, ply 파일로 저장할 수 있다.
ply 파일은 face와 color 정보는 없으며, meshlab 등에서 vertex rendering으로 볼 수 있다.  

Input 이미지로 프로젝터로 Structure Light 패턴을 주사한 이미지가 필요하다. 아래 사진과 같은 이미지가 필요하며, 카메라와 프로젝터 간의 Calibration 정보와 Camera Calibration 정보가 필요하다. 샘플 사진들은 [다음 링크](https://github.com/givenone/SLhaircapture/tree/master/SLhaircapture/hair_800/inverse_pattern)에서 확인 가능하다.
![image]({{ "assets/computer_img/18.bmp" | relative_url }})