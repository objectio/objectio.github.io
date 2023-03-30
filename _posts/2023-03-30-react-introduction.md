---
layout: post
author: Younji Kim
---

# React.js Introduction

<!-- ## Table of contents
- [Table of contents](#table-of-contents)
- [binary_function](#binary-function) -->

- 리액트로 만들어진 웹사이트를 개발자 도구로 소스코드를 살펴보면, 'index.html'의 코드가 보여지고, 그 안에 `<script defer src="/static/js/bundle.js">~`가 보인다. 우리가 작업할 src 폴더의 파일들이 bundle.js에 계속 들어가게 되는 것이다. 
- 이때 가장 먼저 실행되는 게 index.js이다. 내부적으로는 index.js에 정의되어 있는 코드들이 실행이 되는 것이다.
- SPA의 경우, root div 안의 내용이 바뀌는 방식이다. 어떤 걸 클릭할 때마다 (url이 바뀔 때마다), 우리가 원하는 컴포넌트를 매핑시킨 후 디스플레이하는 것을 라우팅이라고 한다.
- 라우팅을 하려면, 모듈 하나를 더 설치해야 한다. 작업하는 루트 폴더에서 `npm install react-router-dom@6`을 실행한다.
- react-router-dom을 반영하려면, index.js에 `import { BrowserRouter } from 'react-router-dom';`로 browserRouter를 임포트 한 뒤 root.render 안에 `<BrowserRouter>`태그를 추가하고 그 안에 `<App>` 태그를 추가한다.
- 