---
layout: post
author: Younji Kim
---

2022년 8월 19일 Today I learned

## Table of contents
- [Table of contents](#table-of-contents)
- [타입캐스팅](#타입캐스팅)
- [const와 static에 관하여](#const와-static에-관하여)

## [타입캐스팅](#타입캐스팅)
C++ 권장사항에 따라 명명된 캐스트를 사용하여 데이터 타입을 변경시킬 수 있다. `static_cast`는 값을 확인하지 않고 유형을 변환한다. 그러므로 프로그래머는 정확성을 따져 사용에 유의해야 한다.

## [const와 static에 관하여](#const와-static에-관하여)
1. static 키워드 : 위치에 상관 없이 프로그램의 시작부터 선언되어 있으며 끝날 때 할당이 풀린다. 전역변수든 지역변수든 상관 없다. A 클래스가 static 변수를 가지고 있다면 A 클래스로부터 생성되는 모든 인스턴스들은 이 변수에 접근 가능하고 공유한다.
2. const 키워드 : 해당 변수를 초기화한 이후에는 절대 바꾸지 못하도록 선언. 초기화 후 값 변경을 못한다. 
3. const static 키워드 : const 멤버 변수(상수)의 초기화는 이니셜라이저를 통해서만 가능하지만, const static으로 선언되는 멤버변수는 선언과 동시에 초기화가 가능하다. const static 멤버변수는 클래스가 정의될 때 지정된 값이 유지되는 상수이기 때문에, 선언과 함게 초기화가 가능하도록 C++문법으로 정의되어 있다.
클래스 내에서 함수의 리턴 타입(const static Fixed&)으로 선언했는데, make를 해보니 error : 'static' can only be specified inside the class definition이라고 나온다. 클래스 내에서만 static을 쓸 수 있나보다. 생각해보면 당연하다. static 키워드를 지정해준 해당 변수 또는 함수는 메모리를 프로그램 시작 시에 할당받는다. 이미 클래스 내에서 선언부에게 static 키워드를 줘서 할당을 받았는데 구현부에서 또 할당을 받을 수는 없는 거 아닌가!