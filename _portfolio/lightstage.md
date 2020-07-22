---
layout: post
title: "Light Stage"
img: "assets/computer_img/ls.jpg"
feature-img: "assets/img/pexels/computer.jpeg"
tags: [Computer Graphics, Computer]
---

![image]({{ page.img | relative_url }})


### Introduction

[Morpheus 3D](https://morpheus3d.co.kr/wp/en/)에서 1학기 동안 인턴으로 생활하며 진행한 프로젝트.
모르페우스와는 서울대학교 창의적통합설계에서 처음 인연을 맺게 됐다. 한 학기 프로젝트를 같이 진행한 후, 회사에서 나를 좋게 평가해서 인턴십을 제안했고 인턴을 하게돼었다. 원래는 겨울방학에 짧게 인턴생활을 하려 했지만 코로나19로 인한 비대면 수업으로 한학기동안 인턴생활을 했다. Light Stage 프로젝트에 참여했다.

[Light Stage](https://en.wikipedia.org/wiki/Light_stage)는 [Paul Devebec 교수 등이 만든 장비](https://www.youtube.com/watch?v=c6QJT5CXl3o)로 사람 얼굴을 아주 높은 Quality로 스캔해내는 장비다. 주로 영화나 애니메이션을 만들 때, 사람의 흉상을 제작할 때에 사용된다. 기술적으로는 물체의 BRDF를 알아내는 데에 사용된다. 물체의 표면이 빛을 어떻게 반사하는 지를 알아내는 것으로, 매우 정밀한 색깔과 normal vector 등을 계산하는 데에 사용된다.

Light Stage는 적개는 수십개에서 많게는 수백개의 Light를 달아야 하므로 매우 큰 장비를 필요로 한다. 회사는 이 장비를 직접 제작했고, 장비를 사용하는 소프트웨어 개발을 진행했다. LED Light를 조절하고 알맞은 타이밍에 여러 대의 카메라에서 촬영을 해 얻어진 영상으로부터 물체의 표면을 분석한다.

### Code

[Github](https://github.com/givenone/lightstage) Repository다.
[ICL에서 나온 논문](https://wp.doc.ic.ac.uk/rgi/project/diffuse-specular-separation-using-binary-spherical-gradient-illumination/)인 
```Diffuse-Specular Separation using Binary Spherical Gradient Illumination``` 를 구현한 내용이다. 편광기를 사용하지 않은 하드웨어에서 Reconstruction을 해내는 논문이다. 옥의 티가 있다면 저자가 내 심금을 울리는 메일에 답변을 해주지 않았다는 것이다.

핵심 코드는 [Binary Reconstruction](https://github.com/givenone/lightstage/blob/master/binary_reconstruction.py)에서 확인 가능하다. 인풋으로 5장의 사진이 필요하다. 

### Result

![image]({{ "assets/computer_img/IMG_7585.JPG" | relative_url }})  
<p style="text-align: center"> Light Stage를 사용하지 않고 3D Scanner만 사용한 경우 </p>

![image]({{ "assets/computer_img/IMG_7586.png" | relative_url }})
<p style="text-align: center">Light Stage를 사용해서 얻어낸 Normal Map을 사용한 경우 </p>


