---
layout: post
title:  "vim + ctags + cscope + taglist"
author: Joonsub, Lim
date:   2020-03-03 00:00:00
categories: lecture
comments: true
image: #
---
리눅스, 유닉스 환경에서 vi으로 프로그래밍을 할때 vi와 같이 쓰는 유용한 플러그인을 소개합니다.
아무래도 IDE가 아닌 텍스트 편집기이므로, 보다 편하게 사용하기 위해서는 플러그인을 같이 사용해주면 됩니다.

---

## 1. ctags
**소스파일 내에 정의된 전역변수, 함수, 매크로, 구조체 등의 정보를 모아 데이터베이스 파일인 tags 파일을 생성하는 툴**

### 1.1. 설치
```
# 데비안 게열
apt-get install ctags

# 레드햇 계열
yum install ctags
```

### 1.2. 설정
**프로젝트 파일의 최상위 디렉토리로 이동한 뒤 실행해야 한다.**
```
# tags 파일 생성
ctags -R
```

다음은 .vimrc 파일에 tags파일의 경로를 설정해주어야 한다.
```
$ vi ~/.vimrc
set tags=/home/user/workspace/project/tags
```
아래와 같이 여러개를 등록하는것도 가능하다.
```
set tags=./tags, /usr/src/linux/tags
```

### 1.3 사용법
- **Ctrl + ]**
    - 현재 커서가 가리키고 있는 함수나, 구조체 등의 정의로 이동한다.

```
#include "sum.h"

int main(int agrc, char *argv[]){
    ...
    int num1=1, num2=123;
    sum(num1, num2); 
}
```

main함수에서 sum 함수에서 `Ctrl + ]`를 누르면 sum.h의 sum함수의 정의로 이동한다.

- **Ctrl + t**
    - 만일 Ctrl + ] 로 이동했다면, 이전 위치로 할때 사용한다.

```
int sum(int num1, int num2){
    return num1 + num2;
}
```

main 함수에서 `Ctrl + ]` 를 이용해 sum.h로 이동했다면, `Ctrl + t` 를 이용해서 다시 main함수로 돌아온다.

___

## 2. cscope
**ctags로 찾기 힘든 전역 변수의 사용이나, 함수의 호출등을 보기 위해서 사용하는 툴**

### 2.1. 설치
```
# 데비안 게열
apt-get install cscope

# 레드햇 계열
yum install cscope
```

### 2.2. 설정
**ctags와 달리 입력해야 될것이 많아서 스크립트 파일을 만들어서 사용**

```
#!/bin/bash
rm -rf cscope.files cscope.out
find . `pwd` \( -name '*.c' -o -name '*.cpp' -o -name '*.cc' -o -name '*.h' -o -name '*.s' -o -name '*S' \) -print > cscope.files
cscope -i cscope.files
```
mkcscope.sh 파일을 생성하고, 스크립트 파일을 다음과 같이 작성한다. `pwd`를 꼭 입력해주도록 한다.

```
chmod 755 mkcscope.sh
mv mkcscope.sh /usr/local/bin
```
또한 스크립트를 언제나 실행 할수있게 해준다.   

```
$ mkcscope.sh
cscope.files cscope.out
```
이후 최상위 디렉토리에서 mkcscope.sh 파일을 실행해 데이터베이스 파일을 생성해준다.    
스크립트 파일을 실행한 후에는 `Ctrl + d` 를 입력하면 끝이난다.     
실행이 완료된 뒤에는 `cscope.files`와 `cscope.out`파일이 생성된다.    

```
$ vi ~/.vimrc
set csprg=/usr/bin/cscope
set csto=0
set cst
set nocsverb

if filereadable("./cscope.out")
cs add cscope.out
else
cs add /usr/user/workspace/project/cscope.out
endif
set csverb
```
vim에서 사용이 가능하도록 vimrc파일에 다음을 추가헤준다.

### 2.3 사용법
- cs find [0 or s] <name>
    - 해당이름을 가진 함수나 전역변수가 사용된곳을 보여준다.

```
$ vi sum.h
int sum(int num1, int num2){
    return num1 + num2;
}

:cs find 0 sum
```
---

## 3. taglist
**vim사용시 소스파일의 변수와 함수등을 화면 옆면에 리스트로 보여주는 툴**

### 3.1. 설치
`http://vim-taglist.sourceforge.net/download.html` 에서 taglist를 다운받는다.

### 3.2. 설정
**압축 해제 후 파일을 vim의 경로에 복사해준다.**
```
$ unzip taglist.zip
/doc /plugin
```
다운 후 압축을 풀면 `/doc/taglist.txt`와 `/plugin/taglist.vim`의 두개의 디렉토리안에 파일이 있다.
```
/doc/taglist.txt
/usr/share/vim/vim8x/doc/
```
`taglist.txt` 파일은 `/usr/share/vim/vim8x/doc/` 로 복사 해준다.

```
/plugin/taglist.vim
/usr/share/vim/vim8x/plugin/ 에 복사
```
`taglist.vim` 파일은 `/usr/share/vim/vim8x/plugin/` 로 복사 해준다.

### 3.3 사용법
- vi로 파일을 열어준뒤 `:Tlist`를 입력해주면 리스트가 왼쪽에 나타난다. (다시 입력시 사라짐)
    - `Ctrl + ww`를 이용해 소스화면과 리스트 화면사이를 이동할 수 있다.
    - 리스트에서 방향키를 통해 이동하고 싶은 함수로 간뒤, Enter를 누르면 해당 함수로 이동한다.
- 다음과 같은 설정을 통해 더 편리하게 사용할 수 있다.
```
$ vi ~/.vimrc
let Tlist_Auto_Open=1 # 자동으로 taglist표시 (:Tlist 필요없음)
let Tlist_Use_Right_Window = 1 # 리스트를 왼쪽이 아니라 오른쪽에 표시
let Tlist_WinWidth = 35 # 리스트 창의 너비를 35로 조정
```

---

## 4. 마무리
이정도의 설정을 마치면, 왠만한 소스코드를 분석하는데에는 문제 없을 것이다.   

추가로 ctags를 제일 먼저 사용하고 그다음에 안찾아지는 것은 cscope를 사용하는게 좋다.    
cscope가 ctags보다는 느리다. 그리고 taglist는 자동으로 띄워 놓는것보다는 단축키를 설정해서 필요할때만 보이게 하는게 좋다.   왜냐면 vi 편집기 종료할때 창을 두번 종료 해줘야 하기 때문이다.     
ctags를 우선적으로 사용하기 때문에 ctag의 이동하는 경우 두개도 단축키로 등록해놓는것도 좋다. 

다음은 내 사용하는 단축키 설정이다. (cscope는 사용할때마다 그냥 입력해서 쓴다)

| 키 | 기능 |
|:---:|:---:|
| `F5` | taglist |
| `F6` | Ctrl + ] | 
| `F7` | Ctrl + t |

---