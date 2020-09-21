---
layout: post
title:  "[Algorithm] N-Queen 문제"
author: Joonsub, Lim
date:   2020-09-16 00:00:00
categories: lecture
comments: true
image: #
---

얼핏 보면 매우 간단해 보이는 문제이지만, 생각보다 꽤 많은 시간을 고민 했던 문제이다.   
처음에 구상한 대각선을 체크하는 코드가 맞다고 생각하고 원인을 게속 찾다보니, 결국 대각선에 위치했는지 확인하는 코드가 문제였다.
개인적으로 재밌게 푼 문제이기도 하고, 정리할겸 포스팅을 해보려고 한다.

---

## 1. N-Queen 문제
### 1.1 문제 소개

체스를 해본적이 있는가? 체스는 `8 x 8` 크기의 판에서 말을 움직여 승부를 겨루는 게임이다.   

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/chess-board.jpg ){: width="49%" height="49%"}

체스를 잘 안다면 이미 알고 있겠지만, 체스를 잘 모르는 사람도 있을수 있으니 설명하자면,   
문제에서 사용되는 퀸(Queen)은 왼쪽하단의 그림과 같이 상하좌우, 대각선으로 칸수에 관계없이 움직일 수 있다.   

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/queen-attack-range.jpg ){: width="49%" height="49%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/nqueen-solve.jpg ){: width="49%" height="49%"}

N-Queen 문제는 딱 한 문장으로 설명이 가능하다.

```
크기가 N x N 인 체스판 위에 퀸 N 개가 서로를 공격 할 수 없게 놓는 경우의 수를 구하는 문제이다.  
```

N개의 서로 다른 퀸이 서로를 공격할 수 없도록 N개의 퀸을 놓으려면, 오른쪽상단의 그림과 같이 놓아야 한다.   
이렇게 서로의 공격할 수 없는 N개의 퀸을 놓을 수있는 경우의 수가 문제의 정답이다.   

## 2. 문제 해결 과정
### 2.1. 첫번째 퀸의 위치

어떻게 접근 해야할까 생각하다가 직접 퀸을 놓아 보았다. 가장 먼저 왼쪽 맨위 모서리인 `A8`에 퀸을 놓았다.   

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/first-queen-position.jpg ){: width="49%" height="49%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/first-queen-range.jpg ){: width="49%" height="49%"}

머리속으로 상상하기 어려우면 종이에 직접 체스판을 그려보면서 이해하는 것을 추천한다.  
퀸을 놓고, 다음 퀸을 놓을 수 없는 위치는 칠해가는 방식으로 말이다.   
`A8`의 위치에 퀸을 놓았을때 다음 퀸을 놓을 수 없는 위치는 `X`자로 표시해둔다.

### 2.2 두번째 퀸의 위치

첫번째 퀸을 놓으면서 칠해 놓은 자리에는 퀸을 놓을 수없으므로, 두번째 퀸은 가능한 자리에 놓아준다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/second-queen-position.jpg ){: width="49%" height="49%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/second-queen-range.jpg ){: width="49%" height="49%"}

역시, 두번째 퀸을 놓은뒤에 다음 퀸을 놓을 수 없는 자리는 X자로 표시해둔다.   
이렇게 N개의 퀸을 놓을때 까지, 첫번째~두번째 퀸을 놓으면서 했던 작업을 반복 한다.   
N개의 퀸이 모두 놓여졌을 때마다 +1을 해준다면, 정답을 얻을 수 있다.   

### 2.3 문제 해결

체스판에 퀸(Queen)을 새롭게 놓을 때마다 확인해야 하는것은 다음과 같다.
```
1. 상하좌우 같은 줄에 이미 위치한 퀸(Queen)이 있는가?
2. 대각선의 같은 줄에 이미 위치한 퀸(Queen)이 있는가?
3. 현재 놓는 퀸이 N번째(마지막) 퀸(Queen)인가?
```

* 1번과 2번
    - 1번과 2번에 해당하는 경우 다음퀸을 놓지 않아도 된다.
    - 이전 상태로 돌아가 다시 퀸을 놓는다. `백트래킹 알고리즘`
    - 1번과 2번에 해당하지 않는 경우에는 다음 퀸을 놓는다.
* 3번에
    - 현재 놓는 퀸이 N번째 퀸인 경우는 정답이므로 퀴을 놓는 경우의 수를 1 추가 해준다.
    - 현재 놓는 퀸이 N번째 퀸이 아닌경우에는 다음 퀸을 놓는다.

### 2.4 백트래킹 (Back-tracking)

N-Queen 문제를 푸는 가장 쉽고도 간단한 방법은 모든 경우의 수를 조사하는 방법이다.   
하지만 다음 퀸을 놓을 수 없을 경우에 그이후 과정을 생략한다면 좀 더 빠르게 정답을 구할 수 있을것이다.   
퀸을 놓을 수 없는 경우를 확인 하기 위해서는, 위의 3가지 조건을 모두 따져본다.   

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/first-queen-position.jpg ){: width="24%" height="24%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/wrong-position.jpg ){: width="24%" height="24%"}    

`A8`에 퀸을 놓았을 경우 다음 퀸을 놓으려고 할때, `B8`에 놓을 수 없다.   
이때 다음 퀸을 놓을지 생각하지 말고 다시 `A8`에 퀸이 놓여있는 상황으로 다시 돌아간다.    

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/first-queen-position.jpg ){: width="24%" height="24%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/wrong-position2.jpg ){: width="24%" height="24%"}    

방금전 상황에서 `B8`에 퀸을 놓을 수 없다는것을 알았으므로, 다음 위치인 `B7`에 퀸을 놓는 것을 생각해 볼 수 있다.   
하지만, `A8`의 퀸의 대각선에 위치하므로 놓을 수 없다. 다시 `A8`만 놓여져 있는 상황으로 다시 돌아간다.    
역시 다음 퀸을 놓는 것은 생각하지 않는다.    

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/first-queen-position.jpg ){: width="24%" height="24%"}
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/NQueen/second-queen-position.jpg ){: width="24%" height="24%"}

방금전 두 상황에서 `B8`, `B7`에는 퀸을 놓을 수 없다는 것을 깨달았다.   
이제 다음 위치인 `B6`에 퀸을 놓으려고 한다. 위에서 퀸을 놓을때마다 체크해야 하는 3가지 상황을 체크 한다.   
모두 해당되지 않는다. 즉, `B6`에는 퀸을 놓을 수 있다. (상하좌우 대각선에 퀸이 없고, 마지막 퀸이 아니다)    
따라서 다음 퀸을 놓는 방법을 생각한다.   

위의 과정에서 알 수 있듯이 백트래킹 알고리즘은 가능한 경우만 수행하는 알고리즘이다.  
수행 가능하지 않다면 수행하지 않고, 이전으로 돌아가 수행 가능한 방법을 찾는 알고리즘이다.

## 3. 구현
### 3.1 핵심 코드
처음 문제를 풀때 2차원 배열을 생각했다. 퀸의 위치를 x, y 좌표로 표시하면 매우 편리 할것이라고 생각했다.     
체스 판으로 사용할 2차원 배열 1개와 방문을 확인 하는 2차원 배열 1개를 사용했으나, 시간이 꽤나 오래 걸렸다.    
특히나 숫자가 커질수록 엄청난 시간이 소모되었다. 따라서 1차원 배열을 통해서 문제를 풀어야 했다.   
```cpp
board[15]={0, }; // chess 판
board[1]=1; // 1번째 column에 위치한 퀸의 좌표
board[2]=3; // 2번쨰 column에 위치한 퀸의 좌표
```
**쉬운 설명을 위해서 퀸의 위치를 x, y 좌표로 표현, 실제 좌표값은 i (x), board[i] (y)가 된다.**   
이전에 놓여진 퀸의 좌표 값을 x1, y1 이라고 하고, 새로 놓을 퀸의 좌표를 x2, y2라고 할때
새로 놓으려고 하는 퀸이 이전 퀸의 대각선에 있는지 확인하는 코드는 다음과 같다.
```cpp
if((x1-x2)==(y1-y2)||(x1-x2)==(y2-y1)){
    // 대각선에 위치하고 있음
}
```
다음의 로직을 첫번째 퀸이 놓여진 column 부터 놓으려고 하기 직전 column까지 확인 해야한다.
```cpp
for(int i=0;i<column;i++){
    if((x1-x2)==(y1-y2)||(x1-x2)==(y2-y1)){
        // 대각선에 위치하고 있음
    }
}
```
또한 놓으려고 하는 퀸의 위치가 같은 줄에 위치해 있는지 확인해야 하는 로직이 필요하다.   
column의 위치는 for 문을 통해 1씩 증가시킬 것이므로 확인할 필요가 없다. y 좌표값만 비교해준다.   
`y1, y2`가 일치하는 로직 역시 for을 통해 이전에 위치한 퀸은 row 위치를 계속 비교해준다.    
```cpp
for(int i=0;i<column;i++){
    if(y1==y2){
        // 같은 줄에 위치하고 있음
    }
}
```

이제 퀸을 놓을 때마다 대각선에 위치한 퀸인지 확인하고, 같은 라인에 위치하는지 확인해준다.   
만일 퀸을 놓을 수 있는 경우라면 퀸을 놓을 자리를 계속해서 찾아는 방법으로 코드를 작성해 나간다.   
위의 코드를 토대로 하여 최종적으로 완성된 코드를 작성한다.   

### 3.2 전체 코드
```cpp
#include <cstdio>

int n, cnt=0;
int temp[16]={0, };

void nqueen(int col);

int main(void){
    scanf("%d", &n);
	
    for(int i=0;i<n;i++){
        temp[0]=i;
        nqueen(1);
    }

    printf("%d\n", cnt);

    return 0;
}

void nqueen(int col){
    if(col==n){
        cnt+=1;
        return;
    }
	
    for(int i=0;i<n;i++){
        int check = true;
        for(int j=0;j<col;j++){
            temp[col]=i;
            if(temp[j]==temp[col]||((j-col)==(temp[j]-temp[col]))||((j-col)==(temp[col]-temp[j]))){
                check = false;
                break;
            }
        }
		
        if(check){
            nqueen(col+1);
        }
    }
}
```

---