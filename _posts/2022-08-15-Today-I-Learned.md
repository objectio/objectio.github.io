---
layout: post
date: 2022-08-15 08:08:35
author: Younji Kim
---

2022년 8월 15일 Today I learned

## Table of contents
- [Table of contents](#table-of-contents)
- [github에서 fork 해제하기](#github에서-fork-해제하기)
- [LF 관련 git 메세지](#LF-관련-git-메세지)
- [CPP01-string](#CPP01-string)
- [CPP01-입출력 스트림](#CPP01-입출력-스트림)

## [github에서 fork 해제하기](#github에서-fork-해제하기)
github에서는 아직 unfork 기능이 추가되지 않았다. 현재 시점에서 repository를 unfork할 수 있는 유일한 방법은 해당 repository를 삭제하는 방법 뿐이다.

## [LF 관련 git 메세지](#LF-관련-git-메세지)
깃에서 add나 커밋을 할 때 종종 `warning: LF will be replaced by CRLF in assets/css/main.scss. The file will have its original line endings in your working directory` 라는 오류가 발생한다. <br>
이 warning의 원인은 윈도우의 줄바꿈 문자와 리눅스의 줄바꿈 문자가 다르기 때문에 발생한다. 리눅스 시스템에서는 개행 또는 End of Line(EOL)을 Line Feed(LF)로 나타내며, 윈도우 시스템에서는 Carriage Return(CR)과 Line Feed(LF)를 합쳐 CRLF로 나타낸다. Git의 명령들은 리눅스를 기반으로 하기 때문에 Line Feed(LF)만을 처리한다. 따라서 해당 메세지는 윈도우에서 작업한 문서들의 데이터 중 CRLF 문자를 LF문자로 변환해서 커밋할 것이라는 의미다. 오류가 아니라서 따로 조치해줄 필요는 없지만 CRLF 문자를 LF문자로 변환하고 싶다면 `git config --global core.autocrlf true` 명령을 수행하는 것을 추천한다.

출처 : https://datadokdok.tistory.com/5

## [CPP01-string](#CPP01-string)
C++에서는 문자열을 표시하기 위해 char* 형태보다 string이라고 하는 데이터 유형을 사용한다. string은 char나 int 처럼 원시 유형(primitive type)은 아니고 객체 유형(object type)이다. 기본적으로 string은 *비어 있는 문자열*, 즉 아무 문자도 포함되지 않는 문자열로 초기화된다. 빈 문자열 리터럴은 ""로 쓸 수 있다. 다음 두 문장은 같은 문장이다.
```c++
string s;
string s = "";
```


## [CPP01-입출력 스트림](#CPP01-입출력-스트림)
C++에서는 파일을 처리하고 다루기 위해 ifstream, ofstream, fstream 클래스가 제공된다. 이 클래스들은 모두 <fstream> 헤더 파일에 정의되어 있으며, 주로 파일로부터 데이터를 읽기 위해서는 ifstream 클래스, 파일에 데이터를 쓰기 위해서는 ofstream 클래스를 사용한다. stream이란 데이터의 흐름이며, 만일 데이터가 프로그램 쪽으로 흐르면 입력 스트림(input stream)이라 하고, 데이터가 프로그램으로부터흘러나오면 출력 스트림(output stream)이라고 한다. <br>
이와 비슷하게 이미 우리는 입력 스트림과 출력 스트림을 사용했었다. 거쳐가는 게 파일일 뿐이다. cin(console input)은 미보드로부터 입력을 읽기 위해 미리 정의된 객체이고, cout(console output)은 콘솔에 문자를 출력하기 위해 미리 정의된 객체이다. 이들 두 객체는 <iostream> 헤더 파일 내에 정의되어 있다.

```c++
```