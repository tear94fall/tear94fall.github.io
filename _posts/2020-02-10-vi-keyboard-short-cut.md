---
layout: post
title:  "vi 에디터 사용법 (vim 단축키 정리)"
author: Joonsub, Lim
date:   2020-02-10 00:00:00
categories: lecture
comments: true
image: #
---
vi는 emacs와 더불어 가장 많이 사용되는 터미널 텍스트 편집기 중 하나 입니다.   
gui기반의 에디터가 아니라 cli 기반의 에디터 이기 때문에 배우기는 어렵지만, 익숙해지면 정말 편하답니다.   
처음부터 모든 기능을 훑으면서 공부하는것 보다는, 자주 사용하는 것을 위주로 사용하는게 좋습니다.   
저또한 그렇게 vi를 사용하기 시작했습니다. 이 글은 자주 사용하는 것을 중심으로 정리하며 꾸준히 업데이트할 예정 입니다.   

---

## vim 에디터

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Vim_editor/Vim_logo.png ){:width="30%" height="30%"}

우선 vi와 vim에대해서 알아 보도록 하곘습니다. vi는 1976년 빌조이가 만든 편집기 입니다.  
지금은 gui가 당연하게 인식되어있지만, 당시만 하더라도 cli환경이었습니다. vi 이전에는 한줄씩 편집 하는 line editor(줄단위 편집기)를 사용했다고 합니다.   

따라서 vi가 나왔을때는 정말 편리했다고 합니다...   
vi는 visual editor의 약자로 기존의 라인단위에서 화면 단위 편집을 한다는 뜻을 가지고 있습니다.  

그럼 vim은 무엇일까요? vim은 vi improved 라는 뜻을 가지고 있습니다. 즉, 향상된 vi를 의미합니다.
이름에서 부터 알수있듯, vi 보다 더욱 편리한 기능들을 제공합니다.

우선, 단축키 모음표입니다. 처음 사용하신 다면 출력해서 책상에 넣어 두면서 보시는것도 좋은 방법입니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Vim_editor/vi-vim-cheat-sheet-ko.png )

---

### 기본 기능

| 키 | 기능 |
|:-------|:-------|
| h | ⬅️ 커서를 왼쪽으로 움직임 |
| j | ⬇️ 커서를 아래로 움직임 | 
| k | ⬆️ 커서를 위로 움직임 |
| l | ➡️ 커서를 오른쪽으로 움직임|
| - | 커서를 줄의 처음으로 옮기 |
| gg | 문서의 맨위로 커서를 이동 |
| Shift + g | 문서의 맨 마지막으로 커서를 이동 |
| Ctrl + f | 한페이지 아래로 이동 |
| Ctrl + b | 한페이지 이전으로 이동 |
| Ctrl + d | 반페이지 아래로 이동 |
| Ctrl + u | 반페이지 위로 이동 |
| Ctrl + e | 페이지를 한줄씩 아래로 이동 |
| Ctrl + y | 페이지를 한줄씩 위로 이동 |
| Shift + h | 페이지는 이동하지 않고, 화면 내에서 커서를 맨 위로 이동 시킴 |
| Shift + m | 페이지는 이동하지 않고, 화면 내에서 커서를 맨 중간으로 이동 시킴 |
| Shift + l | 페이지는 이동하지 않고, 화면 내에서 커서를 맨 마지막으로 이동 시킴 |
| x | 커서부터 오른쪽으로 삭제 |
| Shift + x | 커서기준으로 커서 왼쪽으로 삭제 |
| v | 글자 단위 블럭 지정 |
| Shift + v | 라인단위 블럭 지정 |
| Ctrl + v | 블럭단위 블럭 지정 (h,j,k,l로 지정이 가능함) |
| dd | 현재 커서가 위치한 라인 삭제 |
| dG | 현재 커서가 위치한 라인부터 마지막 까지 삭제 |
| yy | 현재 커서가 위치한 라인 복사 |
| p | 현재 커서가 위치한 라인 바로 아래 붙여 넣기 |
| Shift + p | 현재 커서가 위치한 라인 바로 위 라인에 붙여 넣기 |
| $ | 커서를 라인의 맨 마지막으로 이동 |
| ^ | 커서를 라인의 맨 처음으로 이동 |
| i | 현재 커서가 위치한 문자의 앞에 insert |
| Shift + i | 현재 커서가 위치한 라인의 맨 앞에 insert |
| a | 현재 커서 위치에서 한칸 다음으로 이동해서 insert |
| Shift + a | 현재 커서가 위치한 라인의 마지막 위치에서 insert |
| o | 현재 커서가 위치한 라인의 아래에 한줄 삽입하고, 커서를 새로운 라인에 위치한 후 insert |
| Shift + o | 현재 커서가 위치한 라인의 위에 한줄을 삽입하고, 커서를 새로운 라인에 위치한 후 insert |
| s | 현재 커서가 위치한 문자를 지우고 insert |
| Shift + s | 현재 커서가 위치한 라인을 지우고 insert |
| u | Undo, 이전으로 되돌리기 |
| Ctrl + r | Redo, 이전으로 되돌리기 취소 |
| > 2번 클릭 | 들여쓰기 |
| >} | 한문단 전체 들여쓰기 |
| 2 > > | 2줄 들여쓰기 |
| < 2번 클릭 | 내어쓰기 |
| ~ | 현재 커서가 위치한 문자가 대문자면 소문자로, 소문자면 대문자로 변경한다 |
| Ctrl + a | 현재 커서가 위치한 문자가 숫자면 숫자를 증가 시킬 수 있다 (자릿수 변경 가능) |
| Ctrl + x | 현재 커서가 위치한 문자가 숫자면 숫자를 감소 시킬 수 있다 (음수 값도 가능) |

### 파일 과련

| 키 | 기능 |
|:-------|:-------|
| :q | 종료 |
| :q! | 강제 종료 |
| :wq | 저장 후 종료 | 
| :w | 현재 파일 명으로 저장 |
| :w {filename} | filename으로 저장 | 
| vi ./{PATH} | 파일 네비게이션 기능이다. 현재 디렉토리의 리스트를 보여준다. <br> 커서가 위치한 디렉토리에 엔터를 누르면 해당 디렉터리의 리시트를 다시 보여준다. <br> 파일에서 엔터를 누르면 해당 파일을 열어서 보여준다. (vim 6.0 부터 사용가능하다) |

### 화면 관련

| 키 | 기능 |
|:-------|:-------|
| :split (:sp) | 화면을 수평으로 나눈다. 두개의 화면에 같은 파일이 표시된다. |
| :split (:sp) {fileanem} | 수평으로 나눠진 화면에 filename을 표시한다. |
| :vsplit (:vs) | 화면을 수직으로 나눈다 |
| :vsplit (:vs) {fileanem} | 수직으로 나눠진 화면에 filename을 표시한다. |
| Crtl + ww | 화면을 이동할때 사용한다. (다음화면으로 이동 한다) |
| Crtl + w {h,j,k,l} | 화면을 이동할때 사용한다. (상하좌우 키를 이용해, 원하는 위치로 이동한다) |
| Ctrl + w= | 분할된 화면 사이즈를 동일하게 |
| :close | 화면을 닫을때 사용한다 |
| :new | 새로운 창을 수직으로 분할된 화면에 열기 |
| :tabnew | 새창을 현재 화면과 같은 위치에 열기 (상단에 탭 추가됨) |
| gt | 오른쪽 탭으로 이동 |
| gT | 왼쪽 탭으로 이동 |

### 기타 기능

| 키 | 기능 |
|:-------|:-------|
| Ctrl + v 로 블럭을 지정, Shift + i 클릭 후 내용 수정, esc 키 두번 클릭 | 여러줄 수정 |
| :set number | 줄번호 보이기 |
| :set nonumber | 줄번호 없애기 |
| :{줄 번호} | 줄번호로 이동1 |
| {줄번호} + Shift + g | 줄번호로 이동2 |
| /{찾을 내용} | 단어 찾기 |
| n 또는 * | 단어 찾기 위로 |
| Shift +n 또는 # | 단어 찾기 아래로 |

### 접기 기능

| 키 | 기능 |
|:-----:|:---|
| zf | 선택 부분 접기 |
| zo | 부분 펴기 (open) |
| zc | 부분 접기 (close) |
| zi | 누를 때마다 접기/펴기 할 수 있음 (zc/zo)를 누르지 않아도 됨 |
| zd | 현재 위치의 폴드 삭제 하기 |
| zM | 모두 접기 |
| zR | 모두 펴기 | 
| zE | 현재 문서의 모든 폴드 삭제 |
| zD | 현재 위치의 겹쳐진 폴드 삭제 |

---
### 업데이트
포스팅에 소개되는 단축키는 사용하고 있거나, 유용하다고 생각되는 것들을 우선적으로 소개 하였습니다.   
단축키를 전부 한번에 포스팅하기는 어려워서 주기적으로 조금씩 업데이트하겠습니다.

---