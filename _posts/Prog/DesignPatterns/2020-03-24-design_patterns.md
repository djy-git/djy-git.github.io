---
title: Design Principles & Design Pattern
tags: DesignPatterns
aside:
  toc: true
---

# Remarks
이 글은 [Head First Design Patterns](http://www.hanbit.co.kr/store/books/look.php?p_code=B9860513241)를 기반으로 작성되었습니다. <br>

<!--more-->

# 디자인 패턴 1
**Strategy Pattern**  
알고리즘군을 정의하고 각각을 캡슐화하여 교환해서 사용할 수 있도록 만드는 방법이다.  
이를 통해, 알고리즘을 사용하는 client와는 독립적으로 알고리즘을 변경할 수 있다.
{:.success}

## 디자인 원칙 1
**애플리케이션에서 달라지는 부분을 찾아내고, 달라지지 않는 부분으로부터 분리시킨다.**  
바뀌는 부분은 따로 뽑아서 **캡슐화**시킨다. 그렇게 하면 나중에 바뀌지 않는 부분에는 영향을 미치지 않은 채로 그 부분만 고치거나 확장할 수 있다.

## 디자인 원칙 2
**구현이 아닌 인터페이스(`interface`)에 맞춰서 프로그래밍한다.**  

## 디자인 원칙 3
**상속보다는 구성(`composition`)을 활용한다.**  
"A는 B이다"(상속) 보다는 "A에는 B가 있다"(구성)가 나을 수 있다.  
**구성(composition)**이란 class가 다른 class의 객체를 멤버 데이터로 포함하는 기능을 뜻한다.
구성을 통해 알고리즘군을 별도의 클래스 집합으로 캡슐화할 수 있도록 만들어주는 것 뿐 아니라, 구성요소로 사용하는 객체에서 올바른 **행동 인터페이스**를 구현하기만 하면 실행시에 행동을 바꿀 수도 있게 해준다.

예제 코드는 [Strategy pattern example](https://djy-git.github.io/2020/03/24/ch01.html)을 참조.


