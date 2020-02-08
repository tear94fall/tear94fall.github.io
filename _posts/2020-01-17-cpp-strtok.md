---
layout: post
title:  "C/C++ strtok() 함수"
author: Joonsub, Lim
date:   2020-01-17 00:00:00
categories: lecture
comments: true
image: #
---
C/C++을 사용하면서 문자열 처리에 대해 다룰 일이 있었다.  
문자열을 자르거나 붙이고 변경하는 등의 다양한 작업을 했는데, 그중에서 조금 헷갈리는 개념들을 포스팅 해보고자 한다.
포스팅에서 다룰 함수는 strtok()과 strtok_r()이다

---
## 1. strtok() 함수
strtok()함수의 tok은 token을 의미합니다. 
### 1.1 Include
strtok()함수를 사용하기 위해서는 <string.h> 헤더가 필요합니다.
```
#include <string.h>
```

### 1.2 Function
함수의 원형은 다음과 같습니다.
```
char *strtok(char *str, const char *delimiters);
```

### 1.3 Parameters
strtok()함수는 2개의 파라미터를 갖습니다.
- str
    - 자르고자 하는 문자열입니다.   
- delimiters  
    - 자를 기준을 정하는 구분자 입니다.  
    - `_` 처럼 한개의 문자 사용도 가능 하지만, `_:`처럼 문자열 사용도 가능합니다.  
        - 여러개 사용시에는 `_:` 를 하나의 구분자로 다루는것이 아니라 `_`와 `:`로 문자열을 구분한다.

### 1.4 Return
- char *  
    - 잘린 문자열을 반환합니다. 모두 잘랐다면 NULL을 반환합니다.  

### 1.5 Example
```
#include <cstdio> 
#include <string.h>

int main(int argc, char *argv[]) { 
    char str[1024] = "I LOVE YOU"; 
    char *ptr;
    char *delimiter = " ";

    ptr = strtok(str, delimiter); 

    while(ptr) { 
        printf("ptr = [%s]\n", ptr); 
        ptr = strtok(NULL, delimiter); 
    } 
    
    return 0; 
} 
```

### 1.6 Result
실행전   

| 메모리 | I |   | L | O | V | E |    | Y  | O  | U  |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 주소값 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |   

실행후    

| 메모리 | I |NULL| L | O | V | E |NULL| Y  | O  | U  |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 주소값 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |   

결과 값
```
I
LOVE
YOU
```

### 1.7 Warning
- Multi-thread 환경에서 사용을 주의 하자.   
    - 위 코드에서 루프문에서는 `ptr = strtok(NULL, delimiter);`를 사용합니다.
      두번째 인자로 NULL을 사용하는데 이는 내부적으로 static 변수를 공유하여 사용하며 처리한다.  
      Multi-thread 환경에서는 strtok_r 함수를 사용하도록 하자. 
     
- 연속된 구분자의 사용을 주의 하자.
    - 문자열에서 구분자가 연속으로 있는 경우에 연속된 구분자 사이의 `공백` 값은 반환되지 않습니다.  
      또한 구분자로 시작하거나 구분자로 끝나는 문자열의 경우에도 양쪽 끝의 `공백` 값은 반환되지 않습니다.  
      문자열 `A,B,,C,D`를 분리할 경우 `A`, `B`, `공백`, `C`, `D`로 분리되는 것이 아니라 `A`, `B`, `C`, `D`로 분리됩니다.  

- 인자로 전달되는 원본값 훼손을 주의 하자.
    - 파라미터 type에 const 가 없음으로 유추가 가능한 내용이다.
      원본이 변형되면 안되는 경우에는, 함수 수행전에 원본값을 저장해서 사용해야한다.  
      위 코드에서 str문자열은 `I LOVE YOU`으로 되어있다. 함수 수행후 `빈칸`은 모두 `NULL`로 변경된다.

---
## 2. strtok_r() 함수
strtok_r()함수는 Multi-Thread 환경에서 사용이 가능하도록 만들어진 함수입니다.  
전체적인 사용법과 형태가 비슷하므로, 다른 부분만 설명하도록 하겠습니다.   

### 1.1 Function
함수의 원형은 다음과 같습니다.  
strtok() 함수에서 세번째 인자인 `char **ptrptr`가 추가되었습니다.
```
char *strtok_r(char *str, const char *delimiters, char **ptrptr);
```

### 1.2 Parameters
strtok_r()함수는 3개의 파라미터를 갖습니다.
- str, delimiter
    - strtok 함수와 동일
- ptrptr
    - 구분자를 기준으로 자른 문자열을 저장하는 함수이다.
    - `A,B,C,D`를 `,`기준으로 자를 경우 `B,C,D`가 저장된다.
    - strtok() 함수에서는 내부적으로 static 변수를 사용하여 Thread-safe하지 않다.   
      하지만 strtok_r() 함수에서는 Thread-safe하기 위해 외부변수인 **ptrptr을 사용하는 것입니다.

### 1.3 Warning   
- Multi-thread 환경에서 사용이 가능하다.   
- 연속된 구분자의 사용과 원본값이 훼손 됨은 strtok과 동일합니다.

---