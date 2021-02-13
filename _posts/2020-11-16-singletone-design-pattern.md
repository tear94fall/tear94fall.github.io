---
layout: post
title:  "[Design Pattern] Singleton Pattern (싱글톤 패턴)"
author: Joonsub, Lim
date:   2020-11-16 00:00:00
categories: lecture
comments: true
image: #
---

이번 포스팅에서는 디자인 패턴에 대해서 다뤄 보려고 합니다.    
GoF의 디자인 패턴중 가장 간단한 패턴이며, 가장 많이 사용되는 패턴입니다.     
그만큼 말도 많고 탈도 많은 패턴중 하나입니다.     

---

## 1. Singleton Pattern

### 1.1 싱글톤 패턴
```
인스턴스가 오직 하나만 생성되며, 생성된 인스턴스를 어디서든지 접근 가능하도록 만드는 패턴이다.
```
이름에서 부터 알수 있듯이, 프로그램내 단하나의 인스턴스만을 생성합니다.     
프로그램 전역에서 사용하기 위해 전역변수를 사용하듯, 어디서나 사용이 가능한 객체를 만듭니다.     

## 2. Types of Singleton

### 2.1 Basic Singleton

```cpp
class Singleton{
    private:
        static Singleton instance;

    public:
        static Singleton &GetIstance(){
            return instance;
        }
};

Singleton Singleton::instance; 
```
많은것을 고려하지 않은 구현입니다.   
첫번째로, 생성자를 외부에서 호출 가능해 인스턴스를 어디서든 생성가능합니다.    
두번째 문제점을 찾기에 앞서, 객체의 인스턴스를 `static` 으로 선언 하는 방법을 생각 해볼 수 있습니다.    
하지만, 문제점은 바로 `static` 변수로 선언을 해서 발생합니다.    
c++ 에서 `static` 변수는 초기화 되는 순서가 정해져 있지않습니다.    
만일 static 으로 선언한 인스턴스가 초기화 되지 않았는데, 다른 객체에서 참조한다면, 문제가 발생합니다.    
따라서 객체의 생성 시점을 변경해야 할 필요가 있습니다.    
이를 해결하기 위해 **`Effective C++`** 책에 소개된 **`늦은 초기화`** 라는 개념을 알아야 합니다.   

### 2.2 Dynamic Singleton

```cpp
class Singleton{
    private:
        Singleton(){}
        ~Singleton(){}

        static Singleton *instance;

    public:
        static Singleton *GetIstance(){
            if(instance == NULL){
                instance = new Singleton();
            }

            return instance;
        }
};
```

첫번째 문제점을 해결하기 위해, 생성자를 `private` 으로 선언하여 외부에서 생성 할 수 없도록 합니다.   
인스턴스 생성은 오로지 `GetIstance()`를 통해서만 생성 하고, `NULL`인 경우에는 생성하고 인스턴스를 반환해줍니다.   
인스턴스는 `GetIstance()`를 최초 호출하는 시점에 생성됩니다.    
이를 통해 객체의 생성 시점을 변경할 수 있습니다. 이것이 **`늦은 초기화`** 입니다.   
동적으로 인스턴스를 생성하고 할당 하기 때문에, `다이나믹 싱글톤(Dynamic Singleton)` 이라고 합니다.   

다이나믹 싱글톤의 경우 메모리 동적 할당을 했기때문에, 할당된 메모리를 어떻게 해제할지 궁금 할것입니다.    
첫번째로 `atexit()` 함수를 콜백함수를 만들고 이를 통해 메모리를 해제하는 방법입니다.

```cpp
private:
    static void Destroy(){
        delete instance;
    }
```

인스턴스를 해제 하는 `Destory()` static 함수를 추가해줍니다.

```cpp
instance = new Singleton();
atext(Destory);
```

두번째 방법은 다른 전역 객체에서 소멸자를 호출 하는 방법입니다.   
```cpp
static Singleton *instance;
friend DestroySingleton;

...

static class DestroySingleton{
    public:
        ~DestroySingleton(){
            delete Singleton::GetInstance();
        }
}
```

위의 방법은 friends를 이용해 전역 객체의 소멸자를 이용해 메모리를 해제 하는 방법입니다.

조금 가다듬으니, Basic Singeltone 보다는 사용할만 한것 같습니다. 하지만, 아직 해결해야 할 문제가 있습니다.    
만일 `GetIstance()`의 인스턴스 생성을 화인하는 if(instance == NULL) 이 `동시에` 호출 된다면 어떻게 될까요?    
`동시에` 라는 말에서 눈치 채셨겠지만, 바로 `멀티 쓰레드` 에서 사용할 경우를 고려 해야 합니다.    


### 2.3 Static Local Singleton

```cpp
class Singleton{
    private:
        Singleton(){}
        Singleton(const Singleton*){}
        Singleton& operator = (const Singleton&){}
        ~Singleton(){}

    public:
        static Singleton& GetIstance(){
            static Singleton instance;
            return instance;
        }
}
```
혹은
```cpp
class Singleton{
    private:
        Singleton(){}
        Singleton(const Singleton*){}
        Singleton& operator = (const Singleton&){}
        ~Singleton(){}

    public:
        static Singleton* GetIstance(){
            static Singleton instance;
            return &instance;
        }
};

```

위의 다이나믹 싱글톤 구현 방법은 싱글 쓰레드에서는 아무런 문제 없이 작동합니다.   
그런데 멀티쓰레드에서 사용시에는 문제를 일으킬 수도 있습니다. 중요한건 문제를 일으킬 수도 있다는 겁니다.   
문제을 일으킬수있는 경우가 극소수 라고 하더라도, 우리는 이를 해결해야 합니다.     
이 극소수의 오류가 프로그램이 중지 될수도있는 가능성을 가지고 있기 때문입니다.   

그래서 GetInstance() 함수 내에서 instance 를 초기화 하는 방법입니다.    
static 객체는 여러번 호출해도 객체의 처음 호출된경우에 생성되고 이후에는 생성되지 않습니다.    
따라서 멀티 쓰레드 환경에서도 Thread-safe 하게 사용이 가능합니다.    

그러나 하나의 작은 문제가 남았습니다.   
만일 여러개의 객체에 싱글톤 패턴을 사용해야할 경우 위의 코드를 클래스마다 일일이 입력해줘야 합니다.     
하지만 c++ 에는 자료형 별로 함수를 여러개 선언하지 않도록 해주는 기능이 이미 있습니다.     
네 바로 템플릿 이죠. 코드를 일일이 입력해주지 않고 템플릿 싱글톤 클래스를 만들어 상속만 해주면 됩니다.     

### 2.4 Template Local Singleton

```cpp
template <typename T>
class Singleton{
    public:
        static T* getInstance(){
            if(instance == NULL){
                instance = new T;
            }

            return instance;
        }

    private:
        static T* instance;
};

template <typename T>
T* Singleton<T>::instance = NULL;
```

싱글톤 클래스에 템플릿을 사용하여 준다. 다이나믹 싱글톤의 형태로 구현을 하였다.    
템플릿 T는 상속 받아서 사용할 클래스이다. 그래서 인스턴스를 T의 형태로 선언해준다.     
다이나믹 싱글톤에서 템플릿을 추가하여 준것 외에는 크게 달라진 점은 없다.    

```cpp
static T& getInstance(){
    static T instance;
    return instance;
}
```

마찬가지로 다이나믹 싱글톤의 문제점 해결을 위해 local static 싱글톤과 같이 사용이 가능하다.      
멤버변수 instance를 내부 변수로 바꾸어 준다. 이렇게 하면 좀더 코드가 간결해진다.     
아래에는 사용법을 추가 하였다.     

```cpp
class TestClass : public Singleton<TestClass>{
    public:
        void print(void){
            printf("Test class\n");
        }
};

int main(void){
    // dynamic
    TestClass::getInstance()->print();

    // local static
    TestClass::getInstane().print();

    return 0;
}
```

위와같이 템플릿 싱글톤을 상속하여 준다. T에는 자식 클래스를 넣어준다.    
이렇게 사용하면 싱글톤으로 만들 객체마다 코드를 추가하면서 사용하지 않아도 된다.    
템플릿 싱글톤 클래스를 한개만 선언한뒤 싱글톤으로 사용할 객체에 상속하여 사용 해주면 된다.    

## 3. etc 

포스팅에서는 다루지 않았지만, 피닉스 싱글톤(Phoenix Singleton)과 같은 방법도 존재한다.     
이름에서와 같이 만일 싱글톤 인스턴스가 없으면 다시 생성하는 형태의 구조를 취하고 있다.     
인스턴스의 상태를 나타내는 변수를 사용하는데, 인스턴스 호출시 생성된 인스턴스가 없으면 생성후 리턴 해준다.     
또한 모던 C++ 에서는 `std::call_once()`와 `스마트 포인터`를 이용한 싱글톤 패턴도 존재 한다.    
모던 C++을 이용한 싱글톤은 좀 더 공부한 뒤에 포스팅 하려고 한다.     

---