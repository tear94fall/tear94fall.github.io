---
layout: post
title:  "리눅스와 유닉스 그리고 터미널"
author: Joonsub, Lim
date:   2020-02-25 00:00:00
categories: Essay
comments: true
image: #
---
미리보기 글이 없습니다.

---

요즘 리눅스와 유닉스를 많이 사용 ~~해야~~ 한다. 리눅스는 학교에 다닐때부터 지금까지도 사용하고 있다.
단, 유닉스는 솔라리스를 깔아본것이 사용해본것의 전부였다. cli 환경이 낯설지 않다. 오히려 디자인적인 요소를 다뤄야 하는 gui 작업보다는 로직 자체를 다루는 작업을 더 선호하는 편이다. 미적감각이 없다고 생각하는 이유도 있다.

그런데, gui도 있고 cli도 있는게 아니라, cli만 있다면 어떨까? 우선 우분투의 경우 서버 버전과 데스크탑 버전을 베포하고 있다. 데스크탑 버전은 gui환경이고 서버 버 전은 cli 환경이다. 물론 서버 버전을 설치했다고 하더라도 x-window를 설치해 gui를 사용할수도 있겠지만, 무조건 cli 환경만 사용해야 된다면...?

처음에는 왜 이렇게 사용해야 하는가? 했고 다른 방법이 없나 고민도 했지만, 어쩔수없다. 그냥 그렇게 쓰는 수밖에... 인간은 적응의 동물이라는걸 직접 느끼고 있다. 어디까지나 리눅스를 쓰면서 터미널을 항상 켜 놓고 사용하긴 헀지만, gui를 이용한 작업을 아예 하지 않았던것은 아니었다. 어디까지나 gui는 보조적인 느낌이었다. 하지만 이젠 그런 보조적인 도구가 없으니 cli로만 해결해야한다.

나는 리눅스를 사용하기 시작한 이유가, 프로그래밍을 위해서 사용했었다. 리눅스의 비동기 io를 이용한 소켓프로그래밍을 위해 gcc, g++ 컴파일러를 이용해서 c/c++ 프로그래밍을 했다. 이때는 vi를 이용해서 코딩을 했다. 프로그래밍만 하다보니 딱히 많은 것을 알아야 하지는 않았고, 자주쓰는 명령어 몇개와 vi를 이용해서 프로그래밍을 헀어야 했어서, vi 단축키등을 조금 외워서 사용했다. 그러다가 vscode의 remote ssh를 사용하면서 신세계를 경험하였다.

프로그래밍을 하기 위해서 사용하는 리눅스는 그렇게 사용했다. 적어도 간단한 작업을 위해서는 사용할 수 있었다. 하지만, 운영체제로써, 정말 제대로 사용하기 위한 리눅스는... 단순 파일을 복사하려고 해도, 명령어로... 삭제도 명령어도... 모든것을 명령어를 이용해야 한다. 그렇다 보니 반대로 생각하게 되었다. 그럼 반대로 명령어만 잘 알아 두면 끝 아닌가? 라고 말이다. 터미널을 사용해 모든것을 할 수 있으니, 명령어 사용법을 익히고 터미널과 친해지자 라고 말이다. 자주 사용하고 꼭 필요한 명령어는 계속 사용하다보니 쉽게 외울수 있었다.

적응하고 보니 생각보다 터미널을 이용한 리눅스 사용은 어렵지 않았다. 처음에는 단순 명령어 한개만을 가지고 사용하다가, 명령어를 섞어쓰고 쉘 스크립트까지 배우면서 직접 명령어를 치는 시간보다 스크립트 파일을 이용해서 단순 반복 작업은 효율적으로 진행했다. 처음에는 배울게 정말 많아서 애를 먹었지만, 역시나 익숙해지고난 지금은 아주 잘 사용하고 있다. 현재 나는 `80x24` 크기의 세상에서 나는 살고있다.

무튼, 리눅스와 유닉스는 단순히 사용하려고 해도 정말 배울게 많고, 숙련자가 되기는 더욱 어려운것 같다. 무엇보다 알아야 할게 정말 너무나도 많다. 또한 간혹가다 베포판 마다 명령어가 달라지는 경우도 있고, 옵션값의 변화도 있어서 여러 버전을 사용한다면 모두 알고 하고 있어야 할것이다. 이러한 리눅스를 누군가가 어떻게 빨리 배울수있냐고 묻는다면, 책을 사서 명령어 부터 외우는것보다는 리눅스 설치부터 바로 해보기를 추천한다. 물론 설치가 완료되면 바로 터미널을 사용한것을 추천한다.