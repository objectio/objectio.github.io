---
layout: post
author: Younji Kim
---

string의 find_first_of 와 find_first_not_of 함수란?
find_first_of는 주어진 문자열에서 함수의 인자로 전달된 문자열의 문자들 중 첫 번째로 나타나는 문자의 위치를 찾는다. `find_first_of("chewing", "def")`를 실행하면 함수는 d, e, f 중 가장 처음에 나타나는 게 e이므로 문자열에서의 e의 위치인 2를 반환한다.<br>
string.find_first_not_of 함수는 인자로 넘겨주는 문자가 해당 문자열의 제일 앞에 있는 경우 해당 위치(길이)를 반환한다. 해당 문자로 시작하지 않는 경우 0을 반환한다. 넘겨주는 문자가 문자열의 끝까지 다 포함되어 있으면 문자열의 길이만큼을 반환한다.

`"1509".find_first_not_of('0')`은 맨 처음이 0이 아니므로 0을 반환한다.
`"01509".find_first_not_of('0')`은 맨 처음이 0이므로 그 길이인 1을 반환한다.<br>
```
 string lower_case = "abcdefghijklmnopqrstuvwxyz ,-";
  string str = "this is the lower-case part, AND THIS IS THE UPPER-CASE PART";
  cout << "first non-lower-case letter in str at: " << str.find_first_not_of(lower_case) << endl;
```
이 코드는 find_first_not_of를 써서 소문자나 공백, 콤마와 하이픈이 들어가지 않은 부분의 위치를 반환하는 예시이다. 실행 결과는 `first non-lower-case letter in str at: 29`로 AND의 A로 시작하는 부분의 위치 29를 반환한다.
