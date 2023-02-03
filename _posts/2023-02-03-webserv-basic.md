---
layout: post
author: Younji Kim
---

## CRLF
캐리지 리턴(Carriage Return)과 라인 피드(Line Feed)의 약자들이다. 이들은 C, C++에서 문자열의 줄바꿈 문자를 담당하는 아이들이다. 

이 단어들은 타자기에서 따온 것으로, 타자기는 줄을 하나 입력하고 나면 마치를 제일 앞으로 이동시켜주는 작업(캐리지 리턴)을 한 후, 종이를 위로 올려서 커서가 다음 라인으로 내려가도록 하는 작업(라인 피드)이 필요하다.

그럼 이번에는 두 개행 문자의 사용에 대해 비교를 해보자.
* 캐리지 리턴(CR-Carriage Return) : 커서의 위치를 앞으로 이동, 코드에선 `\r`
* 라인 피드(LF-Line Feed) : 현재 위치에서 바로 아래로 이동,코드에선 `\n`

<br><br><br>

```c
int main() {
    printf("test\r");
    printf("1004");

    printf("test\n");
    printf("1004");
}
```

위 코드를 실행시켰을 때 실행 결과는 다음과 같다.
```bash
1004
test
1004
```

<br><br><br>

## 각 운영체제에서의 줄바꿈 정의
운영체제마다 줄바꿈의 정의가 다르다.

윈도우/DOS에서는 CRLF 조합으로 줄바꿈을 정의하고, Unix/Linux/C 계열에서는 LF만으로 줄바꿈을 정의한다. 그렇기 때문에 윈도우에서 작성된 것을 Unix/Linux 계열로 올리면 vi로 편집했을 때 ^M이 붙는 것이다.

<br><br><br>

#### 출처
[[C]줄바꿈 종류](https://jink1982.tistory.com/122)

[캐리지 리턴이란?](https://kwangcheolchae.wordpress.com/2012/12/04/캐리지-리턴이란/)