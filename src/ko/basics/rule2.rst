2번째 규칙
=============

.. index:: 규칙 # 2

프로그램하는 방법을 배우는데 첫번째 규칙은 이미 언급했다: 
프로그램을 직접 작성해야 하고 (테스트도 해야하고) 단순히 프로그래밍에 관해서 읽기만 하면 안된다.
이제, 두번째 규칙을 일러줄려고 하는데 좋은 컴퓨터 프로그램을 작성하는 최고 비밀 중의 하나다.

.. important::

    **규칙 # 2**

        **다른 사람** 이 읽고 이해하기 쉽게 컴퓨터 프로그램을 작성한다.

맞는 말이다. 컴퓨터 프로그램을 작성해서 여러분 같은 다른 사람이 그 자체로 읽기 쉽고,
작성한 프로그램이 무엇을 수행하는지 이해하기 쉽게 작성한다.
그렇다, 컴퓨터 언어는 여러분이 컴퓨터와 의사소통하도록 설계되었다.
마치 인간 언어가 사람들이 서로 의사소통할 수 있도록 진화하였듯이 말이다.
하지만, 다른 프로그래머와 작업을 공유하도록 프로그래머가 인간 언어보다 훨씬 단순한 컴퓨터 언어를 흔히 사용한다.

.. index:: #, 주석, " " " (triple), ' ' ' (triple)

주석
--------

다른 사람이 이해하기 훨씬 쉽게 컴퓨터 프로그램을 작성하는데 사용되는 첫번째 도구를 여러분에게 제시합니다: *주석(comments)*.

주석은 컴퓨터에 의해서 무시되어 실행되지 않는 프로그래머가 작성한 메모다; 단지 사람만이 읽고 이해할 수 있다는 의미가 된다.

파이썬을 사용할 때, 두가지 중에 한가지 방식으로 주석을 작성할 수 있다:

-  임의 크기를 갖는 텍스트를 3중 인용부호 사이에 감싸는 것이다. 예를 들어, ``""" ... """`` 혹은 ``''' ... '''``.
-  특정 줄에서 ``#`` 로 시작되는 텍스트를 작성한다.

먼저 어떤 주석도 없는 간단한 프로그램을 작성한다. 그리고 이어서 주석이 가미된 두번째 버전이 있고,
세번째 버젼은 다소 가독성이 떨어진다; 하지만, 저자는 의도적으로 프로그램 3개에 대해서 동일한 오류를 만들었다.
첫번째 혹은 두번째 프로그램에서 좀더 쉽게 오류를 탐지할 수 있나요?

.. code-block:: python

    move()
    move()
    turn_left()
    put()
    move()
    move()
    turn_left()
    put()
    move()
    turn_left()
    put()
    move()
    move()
    turn_left()
    put()

상기 프로그램을, 리보그 관점에서 봤을 때 사람을 위해 주석만 추가된 동일한 프로그램을 비교해 보세요;
주석이 다른 색깔과 폰트 스타일로 나와서 주석을 알아볼 수 있다.

.. code-block:: python

    '''  리보그가 정사각형을 그리고 
    각 정사각형 모서리에 토큰을 놓는 
    간단한 프로그램이다. '''

    move()  # 파이썬 명령어는 개별 줄에 표현된다.
    move()
    turn_left() # 리보그만 왼쪽으로 회전할 줄 안다.
    put()  # 리보그가 충분한 토큰을 보유하고 있다고 가정한다.

    # 정사각형을 완성하는데 상기 명령어를 세번더 수행한다.
    move()
    move()
    turn_left()
    put()

    move()
    turn_left()
    put()

    move()
    move()
    turn_left()
    put()

위에 나온 주석은 특히 좋은 것은 아니다. 
하지만, 적어도 주석중에 하나가 프로그램에 잘못된 것을 찾아내는데 도움이 되어야 한다.
이것이 사기라고 생각할 수도 있다; 하지만, 프로그램 코드라인에 숨겨진 의도를 어떻게 추측할 수 있을까? 주어진 프로그램이 어떤 작업을 수행해야 하는지 설명하는 주석을 추가하면 실수를 찾아내는데 매우 도움이 될 수 있다.

주석에 더해서, 저자는 "논리적(logical)" 코드 덩어리를 구별하는데 빈줄을 사용해서, 패턴을 좀더 잘 볼 수 있게 했다. 주석과 빈줄 삽입을 함께 사용하는 것이 프로그램을 훨씬 더 읽기 쉽게 만든다.



.. admonition:: 선생님께

    만약 이미 함수 인자를 사용하는 방법을 설명했다면, 상기 예제를 변경하도록 제안한다.::

        put()

    에서:

        put('token')
        
    으로.

    위와 같이 하는 이유는 코드를 막 읽기 시작한 사람에게 프로그램 의도를 더 명확하게 만들기 때문이다.

