---
layout: post
author: Younji Kim
---

## Git에서의 서브모듈(Submodule)

<br>

서브모듈(submodule)이란 하나의 git 저장소 속에 연결된 또 다른 git 저장소를 말한다. <br>
깃허브에서는 아래와 같이 폴더 이름이 파란 글씨로 보이는 화살표 폴더로 보인다. <br>
![](https://github.com/objectio/objectio.github.io/blob/main/_posts/images/Git_Submodule/Screen%20Shot%202022-09-27%20at%204.41.22%20PM.png?raw=true) <br>
원래 화살표 폴더는 내부에 .git 파일이 있어서 깃허브에서 제대로 트래킹이 안되는 폴더였는데 서브모듈을 이용하면 이런 식으로 링크 파일로 쓸 수 있다. 
<br> <br> <br>

### 서브모듈 만들기
먼저 bash에서 서브모듈을 추가하고 싶은 레포지토리로 들어간다. <br>
`cd <나의 repository>` <br><br>

다음 코드로 레포지토리 내에 submodule을 추가한다. <br>
`git submodule add <연결하고 싶은 repository 주소>` <br><br>

그러면 레포지토리에 .gitmodules라는 파일이 생성되는데, 이 파일 내부를 들여다보면 다음과 같다. <br>
```
[submodule "Cub3d"]  # 따옴표 안에 submodule(즉 폴더) 이름
	path = Cub3d     # 파일의 위치 (여기에선 상대경로)
	url = https://github.com/S0YKIM/Cub3d.git
```

이후 추가된 폴더와 .gitmodules 파일을 add 후 commit해서 push해주면 첫 단락에서의 사진과 같이 잘 연결된다! <br>
<br><br>

### 서브모듈 내려받기
```bash
git submodule init    # git local config에 submodule을 인지시킴
git submodule update  # submodule로 기록되어 있는 git 저장소에서 clone 해오기
```

<br><br>

#### 출처
https://sgc109.github.io/2020/07/16/git-submodule/