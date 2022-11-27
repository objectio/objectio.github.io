---
layout: post
author: Younji Kim
--- 

## Table of contents
- [Table of contents](#table-of-contents)
- [dup과 dup2](#dup과-dup2)
- [심볼릭 링크 거는 법](#심볼릭-링크-거는-법)
- [이건 뭐지](#이건-뭐지)

## [dup과 dup2](#dup과-dup2)
- `int dup(int fd);` : 파일 식별자를 복제한다. 새로운 파일 서술자를 반환하지만 숫자만 다를 뿐 **원래의 서술자, 복제된 서술자 모두 완벽하게 같은 파일을 가리킨다. ** `int fd2 = dup(fd1)` 을 하게 되면, fd1과 fd2는 똑같은 파일을 가리키는 서로 다른 파일 디스크립터인 것!

- `int dup2(int old_fd1, int new_fd2);` : 파일 식별자를 복제한다기보단, new_fd2를 old_fd1로 바꾼다고 설명하는 게 좀 더 정확할 듯! 예로, `dup2(fd, stdout)`을 사용한다면, 표준 출력이 fd로 바뀌어버려서 쉘에 `echo abc` 등을 실행할 경우 아무것도 출력되지 않게 된다. <br>

<br>

## [심볼릭 링크 거는 법](#심볼릭-링크-거는-법)
`/usr/bin/grep : No such file or directory` 이런 에러가 발생한다면, <br>
`ln -s /bin/grep /usr/bin/grep`으로 심볼릭 링크를 걸어주자. <br>
Usage: `ln -s [원본 파일] [바로 가기]` original <- copy라 생각하자! <br>

<br>

## [이건 뭐지](#이건-뭐지)
```
$> ./a.out /bin/ls "|" /usr/bin/grep microshell ";" /bin/echo i love my microshell
error: cannot execute /usr/bin/grep
i love my microshell
GREP (standard input): input/output error
```
파이프 잘못 연결해서 그런 거 같은데... 확실하진 않음.

명령어 실행하기 전에 `ulimit -u 30` 먼저 실행해보기. 파이프 누수 따져보자.