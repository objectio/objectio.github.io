---
layout: post
author: Younji Kim
--- 

Linux 기반 운영체제나 Mac OS에서 파일을 16진수나 2진수 형태로 볼 수 있게 해주는 명령어인 `xxd`와 그 옵션에 대해 알아보자.

`xxd` : 주어진 파일이나 standart input으로 들어온 문자들에 대해서 hex dump(컴퓨터 데이터의 16진법적인 보임새)를 만들어 준다. Endian에 관계 없이 파일에 존재하는 순서대로 나온다. <br>
`xxd <filename>`이런 식으로 쓴다.

`xxd -b` : 