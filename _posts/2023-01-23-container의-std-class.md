---
layout: post
author: Younji Kim
---

## Table of contents
- [Table of contents](#table-of-contents)
- [binary_function](#binary-function)

<br><br>

## [binary_function](#binary-function)
Binary function object base class. 이 클래스는 C++11 버전에서 사라진 상태이다.

표준 이진 함수 객체들을 위한 base class이다. 일반적으로 함수 객체라 함은 `operator() 멤버 함수를 오버로딩 하고 있는 클래스`의 인스턴스이다. 이 멤버 함수는 객체가 정규 함수 호출과 같은 문법으로 동작할 수 있게끔 만들어준다. 그렇기 때문에 제네릭 함수 타입을 예측할 때 템플릿 파라미터가 타입으로 쓰이는 것이다. 

이진 함수 객체의 예에서, 이 `operator()` 멤버 함수는 두 파라미터를 가진다.

`binary function`은 단지 특정 이진 함수 객체들을 자식으로 가지는 base class이다. 이 클래스는 `operator()`가 정의되어 있지 않다(자식 클래스들이 정의해야 함) - 세 개의 public 데이터 타입 멤버들만 가지고 있다.