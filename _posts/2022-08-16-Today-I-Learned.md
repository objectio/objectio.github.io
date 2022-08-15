---
layout: post
date: 2022-08-16 01:14:52
author: Younji Kim
---

2022년 8월 16일 Today I learned

## Table of contents
- [Table of contents](#table-of-contents)
- [함수 포인터](#함수-포인터)
- [switch문](#switch문)

## [함수 포인터](#함수-포인터)
함수 포인터(function pointer)란? <br>
프로그램에서 정의된 함수는 프로그램이 실행될 때 모두 메인 메모리에 적재된다. 이때 함수의 이름은 메모리 내에서 함수의 시작 주소를 가리키는 포인터 상수(constant pointer)가 된다. 이렇게 함수의 시작 주소를 가리키는 포인터 상수를 함수 포인터(function pointer)라고 부른다. <br>
`포인터 상수(constant pointer)란 포인터 변수가 가리키고 있는 주소 값을 변경할 수 없는 포인터를 의미하며, 상수 포인터(pointer to constant)란 상수를 가리키는 포인터를 의미한다.`
이후는 minitalk에 나왔던 포인터 상수의 프로토타입을 참고하여 작성하자..
출처 : http://tcpschool.com/cpp/cpp_function_pointer

## [switch문](#switch문)
if-else문을 연결하여 여러가지 경우의 수를 처리하는 게 보통의 방법이다. 그러나 CPP01의 ex05에서는 if/else-if/else문을 사용하지 말라고 써있어서 switch문으로 우회해보았다.
```c++
if (check == 0)
{}
else if (check == 1)
{
    (this->*ptr[cal])();
}

// if (check)
//   (this->*ptr[cal])();
```
위와 같은 if-else문을 아래와 같이 switch문을 통해 똑같은 일을 수행하는 코드로 만들 수 있다. 
```c++
switch (check)
    {
    case 0:
        break;
    
    case 1:
        (this->*ptr[cal])();
        break;
    
    default:
        break;
    }
```