---
layout: post
date: 2022-08-15 08:08:35
author: Younji Kim
---

2022년 8월 15일 Today I learned

## Table of contents
- [github에서 fork 해제하기](#github에서-fork-해제하기)
- [LF 관련 git 메세지](#LF-관련-git-메세지)
- [The middle](#the-middle)
- [The end](#the-end)

### [github에서 fork 해제하기](#github에서-fork-해제하기)
github에서는 아직 unfork 기능이 추가되지 않았다. 현재 시점에서 repository를 unfork할 수 있는 유일한 방법은 해당 repository를 삭제하는 방법 뿐이다.


### [LF 관련 git 메세지](#LF-관련-git-메세지)
깃에서 add나 커밋을 할 때 종종 `warning: LF will be replaced by CRLF in assets/css/main.scss. The file will have its original line endings in your working directory` 라는 오류가 발생한다. <br>
이 warning의 원인은 윈도우의 줄바꿈 문자와 리눅스의 줄바꿈 문자가 다르기 때문에 발생한다. 리눅스 시스템에서는 개행 또는 End of Line(EOL)을 Line Feed(LF)로 나타내며, 윈도우 시스템에서는 Carriage Return(CR)과 Line Feed(LF)를 합쳐 CRLF로 나타낸다. Git의 명령들은 리눅스를 기반으로 하기 때문에 Line Feed(LF)만을 처리한다. 따라서 해당 메세지는 윈도우에서 작업한 문서들의 데이터 중 CRLF 문자를 LF문자로 변환해서 커밋할 것이라는 의미다. 오류가 아니라서 따로 조치해줄 필요는 없지만 CRLF 문자를 LF문자로 변환하고 싶다면 `git config --global core.autocrlf true` 명령을 수행하는 것을 추천한다.

출처 : https://datadokdok.tistory.com/5