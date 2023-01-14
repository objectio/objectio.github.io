---
layout: post
author: Younji Kim
---

## Table of contents
- [Table of contents](#table-of-contents)
- [인라인 함수(inline function)](#인라인-함수inline-function)
- [매달린 else문 (dangling else)](#매달린-else문-dangling-else)
- [중첩 구조체 템플릿(중첩-구조체-템플릿)](#중첩-구조체-템플릿중첩-구조체-템플릿)

<br><br>

## [인라인 함수(inline function)](#인라인-함수inline-function)
일반 함수는 코드 재사용 등 여러가지 이점이 있다. 그러나 함수가 호출될 때마다 발생하는 일정량의 성능 오버헤드가 생긴다는 게 단점이다.

CPU는 나중에 함수를 부른 위치 즉 반환할 위치를 알기 위해, 다른 레지스터와 함께 실행 중인 현재 명령어의 주소를 저장해야 한다. 그래서 **모든 함수의 매개 변수를 생성해야 한다.**

크거나 복잡한 함수의 경우에는 함수 실행 시간 >>>> 함수 호출의 오버헤드 이기 떄문에 호출될 때 발생하는 오버헤드는 무시해도 된다. 그러나 함수 내부에 선언된 코드가 짧은 함수인 경우(일반적인 경우) 함수 호출에 필요한 시간이 실제로 함수 코드를 실행하는 데 필요한 시간보다 훨씬 많은 경우가 있다. 이럴 경우에는 호출 오버헤드로 인해 성능 저하가 발생한다. 

이를 해결하기 위해 C++은 인라인 함수를 제공한다. `inline` 키워드는 컴파일러에서 함수를 인플레이스(in-place) 확장시킨다. 즉, 함수를 호출할 때 함수가 위치에 있는 부분을 함수 내부의 코드로 대체한다. 

예를 들면 아래와 같다.
```c++
int min(int x, int y) {
    return (x > y ? y : x);
}

int main() {
    std::cout << min(5, 6) << std::endl;
    std::cout << min(3, 2) << std::endl;
    return (0);
}
```
위 코드는 함수 min()을 두 번 호출하기 때문에 함수 호출 오버헤드 패널티를 두 번 발생시킨다. min()같은 짧은 함수 같은 경우는 함수 선언부의 가장 앞에 `inline` 키워드를 주어 인라인화를 시키자.
```c++
inline int min(int x, int y) {
    return (x > y ? y : x);
}
```
이 경우, 프로그램이 main()을 컴파일하면 다음 프로세스처럼 수행하는 기계 코드를 생성한다.
```c++
int main() {
    std::cout << (5 > 6 ? 6 : 5) << std::endl;
    std::cout << (3 > 2 ? 2 : 3) << std::endl;
    return (0);
}
```
첫번째 main()문과 비교해보면 인라인화 시킨 버전의 경우가 더 빠르게 실행된다. 

주의할 점은, 코드를 그대로 복사해 대체하는 것이기 때문에 내부 루프가 없는 짧은 함수인 경우가 inline화 시키기에 가장 적합하다. 컴파일러는 인라인에 대한 요청을 자유롭게 무시할 수 있다. 긴 함수를 인라인화 하려고 하면 무시할 가능성이 있다.

추가로 현대 컴파일러는 자동으로 함수를 인라인화하기 때문에 함수를 인라인으로 표기하지 않더라도 성능이 향상될 가능성이 보이는 함수에 대해서는 컴파일러가 자동으로 인라인화를 시켜서 컴파일링을 한다. 즉, 실제로 inline 키워드를 붙일 필요가 없으니 개념만 알아두자.

<br><br>

## [매달린 else문 (dangling else)](#매달린-else문-dangling-else)
if tree에서 다음과 같은 경우를 보자.
```c++
if (cond1)
    if (cond2)
        stmt1;
else
    stmt2;
```
들여쓰기를 보면 else문은 cond1을 조건으로 가지고 있는 첫번째 if문과 연결된 것 같지만, 실제로 컴파일러는 두번째 if에 연결되어 있는 것으로 해석한다. else는 가장 가까운 if문에 귀속되어 파싱됨에 유의하자.

모든 if문이 else를 가질 때에는 저렇게 괄호 없이 써도 `dangling else` 문제가 일어나지 않는다.

파이썬과 다르게, C 계열의 언어는 코드 들여쓰기로 범위를 구분할 수 없다. 따라서 dangling else를 쓰지 않기 위해서는 brace{} 로 범위를 정확히 표시해야 한다. 

<br><br>


## [중첩 구조체 템플릿(중첩-구조체-템플릿)](#중첩-구조체-템플릿중첩-구조체-템플릿)
RB tree 클래스에 있었던 `typedef typename Alloc::template rebind<Rb_tree_node<Val> >::other Node_allocator;` 가 대체 뭘 의미하는 걸까?

그냥 Alloc, 즉 std::allocator를 사용한다면 얘한테 넘긴 템플릿 매개변수는 Val이기 때문에 할당할 때 계속 Val 크기만큼의 바이트만 할당이 될 것이다. 우리는 노드가 필요한 건데!

따라서 각 노드들을 할당해주기 위해 `Rb_tree_node<Val>` 타입에 대한 allocate가 필요해진다.
따라서 STL allocator는 반드시 rebind 중첩 구조체 템플릿을 가져야 한다. (중첩 타입이므로 typename 필요)


<br><br>

#### 출처
[inline함수](https://boycoding.tistory.com/220)

[dangling else](http://blog.woong.org/v/551d17b906c2ab0c569cebd0)

[중첩 구조체 템플릿](http://egloos.zum.com/sweeper/v/2966785)