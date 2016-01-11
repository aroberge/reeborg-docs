비교 연산자
====================

객체를 비교하는 것이 매우 유용한다. 숫자로 비교 작업을 수행해 보자.

.. topic:: 시도해 보기!

    .. code-block:: py3

        print( 2 == 2 )  # 두 숫자는 같은가?
        print( 2 == 3 )

        print( 2 != 2 )  # 두 숫자는 다른가?
        print( 2 != 3 )

        print( 2 < 3 )  # 첫번재 숫자는 두번째 보다 작은가?
        print( 3 < 2 )
        print( 2 < 2 )

        print( 2 > 3 )  # 첫번째 숫자가 두번째 보다 더 큰가?
        print( 3 > 2 )
        print( 2 > 2 )

        print( 2 <= 3 )  # 첫번째 숫자가 두번째 보다 같거나 더 작은가?
        print( 3 <= 2 )
        print( 2 <= 2 )

        print( 2 >= 3 )  # 첫번째 숫자가 두번째 보다 같거나 더 큰가?
        print( 3 >= 2 )
        print( 2 >= 2 )

낙엽 줍기!
----------------------------------

리보그가 특별한 세상에 떨어진 낙엽을 주울 준비가 되었다. 다음 프로그램을 실행한다::

.. code-block:: py3

    World("http://reeborg.ca/worlds/not_storm1.json",
               "Not Storm 1")

상기 코드는 리보그가 숫자가 알려지지 않은 낙엽을 주워서 쓰레기통에 담는 세상을 볼러운다.


.. topic:: 낙엽 청소하는 프로그램 작성!

    리보그가 낙엽을 세게 한다. 아마도 ``number_of_leaves`` 변수를 사용하고, 초기값은 0으로 둔다.
    리보그가 낙엽을 매번 주울 때마다 변수값을 하나씩 증가시킨다.
    리보그가 쓰레기통에 낙엽을 담을 준비가 되었을 때, 코드는 다음과 같을 것이다::

    .. code-block:: py3

        while number_of_leaves > 0:
            # 낙엽을 쓰레기통에 넣는다.
            # 변수를 감소시킨다.

.. hint::
    .. code-block:: py3

        from library import *

        think(10)

        World("http://reeborg.ca/worlds/not_storm1.json",
              "Not Storm 1")

        number_of_leaves = 0

        while not wall_in_front():
            move()
            if object_here():
                while object_here():
                    take()
                    number_of_leaves += 1
        turn_around()

        while not wall_in_front():
            move()

        turn_right()
        move()

        while number_of_leaves > 0:
            put()
