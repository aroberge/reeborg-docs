변수
==============

사용설명서 시작부에, 다음과 같이 적을 것을 기억할 것이다:

.. epigraph::

    ``move()`` 는 파이썬 **함수** 의 한 사례다.
    함수는 명칭이 있다; 이 경우에 명칭은 ``move`` 가 된다.
    유효한 명칭은 문자 혹은 밑줄 문자 "_" 로 시작되고, 문자, 숫자, 밑줄 문자 "_" 를 
    포함할 수 있다. 함수명 다음에 ``()`` 가 따라온다.
    이것을 통해서 리보그(파이썬)에게 함수는 
    실행되거나 혹은 호출(실행과 호출은 동의어)되도록 일러준다.

함수는 **객체(object)** 라고 부르는 것의 한 사례다.
해당 객체에 하나 혹은 다수 명칭을 부여할 수 있다.
**변수(variable)** 는 객체에 부여하는 명칭이다.
파이썬에서 ``=`` 등호를 사용해서 명칭(변수)과 객체를 다음과 같은 방식으로 연결한다::

    variable = object

예를 들어, ``turn_left()`` 함수를 타이핑하는 것이 너무 길다면,
다음과 같이 또다른 명칭(변수)을 정의할 수 있다::


    left = turn_left    # 괄호 없음!
    left()              # 활용 예

.. topic:: 여러분 차례!

    적어도 기존 함수 하나에 대해 새로운 명칭(변수)을 사용해 본다.
    **단일 프로그램에서 같은 객체를 참조하는데 두가지 다른 명칭을 사용할 수 있는가?**

.. toctree::
   :maxdepth: 2
   :numbered:

   variables
   diary
   think
   newspaper3
   world
   increment
   scope
   comparison
   return
   listes
   string_index
   for
   arguments1a
   arguments1b
   slice
   harvest3

