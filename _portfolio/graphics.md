---
layout: post
title: Computer Graphics
img: "assets/img/graphics.png"
feature-img: "assets/img/pexels/computer.jpeg"
date: July 2020
tags: [Computer Graphics, Computer]
---

# Computer Graphics 공부, 개발

------------------

## [world2tangent](https://github.com/givenone/world2tangent)

convert world space normal to tangent space normal in obj file

reference :: 
- http://www.opengl-tutorial.org/intermediate-tutorials/tutorial-13-normal-mapping/#preparing-our-vbo
- https://www.cs.utexas.edu/~fussell/courses/cs384g-spring2016/lectures/normal_mapping_tangent.pdf

##### Specification

- "n" vector는 face에 수직인 벡터로, p1-p0와 p2-p0의 cross (외적)임.
- tangent, bitangent vector를 계산한 후, Gram-Schmidt Orthogonalization, normalization 해서 orthonormal하도록 해줌.
- t,b,n의 방향 (오른손 좌표계)를 유지하기 위해, 오른손 좌표계의 방향이 아닐 경우 t의  방향을 reverse해줌.

-------------------

## [normal_position_combination](https://github.com/givenone/normal_position_combination)
Efficiently Combining Positions and Normals for Precise 3D Geometry 구현체 사용 프로젝트.  
Normal map을 사용해 Geometry를 변경시키는 작업.  
Normal map에 포함된 Face의 High Frequency Detail (모공, 주름)을 Position에 포함시키기 위한 시도.  
렌더링 자체에서는 필요성이 크게 없으며, 용량이 큰 데이터에서 시간이 꽤 걸린다 (약 1분 이상).

Copyright :: [source](http://w3.impa.br/~diego/software/NehEtAl05/)

Combining positions and normals following the article below
 Efficiently Combining Positions and Normals for Precise 3D Geometry

```Nehab, D.; Rusinkiewicz, S.; Davis, J.; Ramamoorthi, R.
ACM Transactions on Graphics - SIGGRAPH 2005
Los Angeles, California, July 2005, Volume 24, Issue 3, pp. 536-543
```


-------------------------

## [Displacement map from normal map](https://github.com/givenone/displacement-from-normal)

reconstruct a displacement map from a fine normal map

[Generating Displacement from Normal Map for use in 3D Games](http://developer.download.nvidia.com/assets/gamedev/docs/nmap2displacement.pdf) by Kirill Dmitriev - NVIDIA, 구현.