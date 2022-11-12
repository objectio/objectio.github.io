---
layout: post
author: Younji Kim
---

11월 10일에 진행한 김민창 멘토님과의 멘토링을 정리한 내용이다. 

## Table of contents
- [Table of contents](#table-of-contents)
- [아핀 변환, 아핀 좌표계](#아핀-변환,-아핀-좌표계)
- [로드리그 공식](#로드리그-공식)
- [해밀턴의 사원수](#해밀턴의-사원수)
- [쿼터니언 보간법](#쿼터니언-보간법)
- [Phong Shading](#phong-shading)
- [ETC...](#etc)

## [아핀 변환, 아핀 좌표계](#아핀-변환,-아핀-좌표계)
나중에 알게 되면 정리해놓자..

## [로드리그 공식](#로드리그-공식)
[Rodrigues의 공식(Legendre 다항식)](https://m.blog.naver.com/roty22/220743263453)

## [해밀턴의 사원수](#해밀턴의-사원수)

실수평면 -> 복소평면

복소평면이랑 4원수

해밀턴의 4원수 알아보기! <br>
[사원수에 관한 블로그 해설](https://ghebook.blogspot.com/2010/07/quaternion.html) <br>
[사원수(Quaternion) 위키피디아](https://en.wikipedia.org/wiki/Quaternion)

## [쿼터니언 보간법](#쿼터니언-보간법)
쿼터니언 보간법 : 숫자 4개를 사차원 공간 상에서 보간
물병을 던지는 애니메이션 하나를 만든다고 했을 때, 시점 세 개를 찍어서 그 사이에 움직이는 물병의 회전을 자연스럽게 구현하기 위해서 쿼터니언 보간법을 쓴다.

## [Phong Shading](#phong-shading)
- Phong shading : Phong interpolation이라고도 불리며, 표면의 점들을 보간하는 방식을 말한다. 표면 위의 정점들의 `normal vector`값으로 모든 polygon에 대한 normal vector, 즉 표면 벡터를 구한다. 그 후 표면 벡터를 이용하여 각 픽셀의 노말 벡터를 구하고 이 값을 이용하여 빛을 계산한다. <br>
즉 **보간 작업을 통해 픽셀 단위로 노말 벡터값을 구하는 테크닉**을 Phong Shading이라고 부른다.
- Phong reflection : Phong illumination 또는 Phong Lighting이라고 불린다. Phong shading을 사용하여 Phong reflection model을 만들어 낼 수 있는 것. 기본적으로 빛의 양을 계산하는 작업이다. <br>
https://puppystep.tistory.com/10

## [ETC...](#etc)
openGL에서 모델들의 확장자(file format)는 다음과 같이 여러가지가 있다. 

stl obj fbx assimp

[assimp에 관하여 Learn openGL 번역본](https://heinleinsgame.tistory.com/21)

texturing

#### 멘토님이 추천하는 openGL 도서 리스트
1. openGL Super Bible
2. openGL ES를 이용한 3차원 컴퓨터 그래픽스 입문