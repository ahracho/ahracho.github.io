---
layout: post
title:  "[기초 파이썬] 파이썬의 모든 것은 Object이다 (정수편)"
categories: Python
tags: [Python]
comments: true
---

## C에서 변수가 저장되는 방식 : 변수 = 메모리
C에서 특정한 값이 변수에 저장되는 방식은 간단하다. 예를 들어, 아래와 같은 C코드가 작성되어 있다고 하자.  
~~~c
// C 코드
int a = 5;
int b = a;
~~~
코드를 실행하는 세부 과정은 다음과 같다.  
1. int 4바이트 만큼의 메모리를 할당하고 a라는 이름을 붙인다 (컴퓨터는 a를 방금 할당한 메모리의 주소로 기억한다.)  
2. 변수 a 자리에 5를 저장한다. (0x5의 형태로 4바이트만큼 사용할 것이다.)  
3. int 4바이트 만큼의 메모리를 다시 할당하고 b라는 이름을 붙인다.  
4. 변수 a에 있는 값을 꺼내서(당연히 5일 것이다) 변수 b에 저장한다.  

이렇듯 C코드에서의 변수는 메모리를 직접적으로 나타내고, 변수의 값은 할당한 메모리에 저장되어 있는 실제 값을 나타낸다. 그런데 __파이썬에서는 변수를 다른 방식으로 관리한다고 한다!__  

## 파이썬에서 변수가 저장되는 방식 : Everything is Object
> 파이썬에서는 모든 것(부울, 정수, 실수, 문자열, 데이터 구조, 함수, 프로그램)이 객체(Object)로 구현되어 있다. ... 파이썬 변수의 핵심을 살펴보자. 변수는 단지 이름일 뿐이다. **할당한다는 의미는 값을 복사하는 것이 아니다.** 데이터가 담긴 객체에 그냥 이름을 붙이는 것이다. 그 이름은 객체 자신에 포함되는 것이라기보다는 **객체의 참조**다. 이름을 포스트잇처럼 생각하자. (Introducing Python p.42-43)

간단히 말해 5라고 하는 값이 사실은 객체였다는 것이다. 정수는 정수 클래스의 객체로, 문자열은 문자열 클래스의 객체로, 모든 변수와 값들이 사실은 객체로 다루어지고 있다는 것이다. C에서는 변수 a에 5라는 값을 저장하고, 변수 b에 변수 a의 값을 대입하면, 5라는 값이 "복사"되었다. 그런데 파이썬에서는 변수가 자신만을 위한 메모리를 가지는 것이 아니라 5라는 값을 가진 객체를 가리키도록 되어있다는 것이다.

~~~python
# 파이썬 코드
a = 5
b = a
~~~
같은 로직의 위 코드를 실행하면 5라는 값을 가지는 정수 객체가 생기고, 변수 a와 변수 b는 단지 정수 5 객체의 주소를 참조하게 되는 것이다. 이 과정에 대해서 더 자세히 설명하고 있는 블로그의 설명을 들여다봐보자.  

[Why python is Slow:Looking Under the Hood](http://jakevdp.github.io/blog/2014/05/09/why-python-is-slow/)

위 블로그 글에서는 파이썬 코드가 일반적으로 왜 느린지에 대해서 설명하면서 자연스럽게 파이썬에서 변수가 어떤 식으로 관리되고 있는지에 대해서 힌트를 준다.   
  
#### 정수(실수, 문자열 등) 클래스는 어떻게 생겼을까?
파이썬의 변수는 특정 값을 가지는 객체의 참조라고 이야기했다. 그렇다면 그 객체는 어떤 정보들을 담고 있어야 할까?  
- value : 5라는 정수 값, 혹은 5.0 실수값, 'string'이라는 문자열 값 등 이 객체가 나타내는 값을 지니고 있어야 한다.  
- data type : 알다시피 파이썬에서는 변수를 선언하고 초기화할 때 변수의 데이터 타입을 명시하지 않는다. 그렇기 때문에 연산을 할 때마다 해당 변수가 어떤 타입의 데이터인지 확인해야 값은 '+' 연산을 하더라도 덧셈을 할 것인지, 문자열 이어붙이기를 할 것인지 수행하는 작업이 달라질 수 있다.  
- reference count : 몇 개의 변수가 나를 사용하고 있는지 알아야 한다. 아무도 나를 사용하지 않는다면 굳이 메모리를 차지하면서 있을 필요가 없을테니까.

생각나는 속성들은 이 정도인데 실제 파이썬 코드에도 이렇게 구현이 되어 있을까 궁금하다. 위 블로그 글의 __Digging into Python Integers__ 부분을 보면 실제 파이썬 C API 쪽에 구현되어 있는 클래스들을 분해하여 설명하고 있다.  

~~~c++
// Include/longintrepr.h
// 정수 타입을 나타내는 클래스(struct)
struct _longobject {
	PyObject_VAR_HEAD
	digit ob_digit[1];
};

// Include/object.h
typedef struct {
    PyObject ob_base;
    Py_ssize_t ob_size; /* Number of items in variable part */
} PyVarObject;

typedef struct _object {
    _PyObject_HEAD_EXTRA
    Py_ssize_t ob_refcnt;
    struct _typeobject *ob_type;
} PyObject;

// 위 struct와 typedef를 합치고 당장 이해하기 어려운 정보들을 빼면 실제로 아래와 같다.
struct _longobject {
    long ob_refcnt;
    PyTypeObject *ob_type;
    size_t ob_size;
    long ob_digit[1];
};
~~~
위에서 추측했던대로 reference count(ob_refcnt), object type(ob_type), value(ob_digit), 그리고 하나 데이터의 사이즈(ob_size)의 속성을 담고 있다. 

그리고 같은 값(255보다 작은)을 나타내는 변수가 생성되면 새로운 값을 가진 객체를 또 만들어내는 것이 아니라, singleton으로 이미 있는 객체를 리턴하고 reference count를 하나 증가시킨다.  
~~~python
x = 42
y = 42
id(x) == id(y)
~~~
id()는 객체의 주소값을 리턴하는 함수이다. 위의 코드를 실행하면 변수 x, y 모두 42 값을 가지기 때문에 42 객체의 주소 값이 리턴되고 True가 출력될 것이다.