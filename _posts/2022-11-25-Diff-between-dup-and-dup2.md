---
layout: post
author: Younji Kim
--- 

## Table of contents
- [Table of contents](#table-of-contents)
- [dup과 dup2](#dup과-dup2)
- [심볼릭 링크 거는 법](#심볼릭-링크-거는-법)
- [템플릿을 헤더에 정의해야 하는 이유?](#템플릿을-헤더에-정의해야-하는-이유?)

## [dup과 dup2](#dup과-dup2)

## [심볼릭 링크 거는 법](#심볼릭-링크-거는-법)
`/usr/bin/grep : No such file or directory` 이런 에러가 발생한다면, <br>
`ln -s /bin/grep /usr/bin/grep`으로 심볼릭 링크를 걸어주자. <br>
Usage: `ln -s [원본 파일] [바로 가기]` original <- copy라 생각하자! <br>


## [이건 뭐지](#이건-뭐지)
```
$> ./a.out /bin/ls "|" /usr/bin/grep microshell ";" /bin/echo i love my microshell
error: cannot execute /usr/bin/grep
i love my microshell
GREP (standard input): input/output error
```
파이프 잘못 연결해서 그런 거 같은데... 확실하진 않음.

명령어 실행하기 전에 `ulimit -u 30` 먼저 실행해보기. 파이프 누수를 잡을 수 있음.