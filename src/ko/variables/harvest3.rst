추가된 추수 도전과제 
==========================

리보그 이모는 과일농부다. 
이모 농장에는, 다양한 유형의 과일이 심어져 있다.
특정한 달에는, 특정한 유형의 과일만 수확이 가능하다.
**Harvest 4a**, **Harvest 4b**, **Harvest 4c**, **Harvest 4d** 세상을 살펴본다.
이모가 농장에 들어설 때, 리보그 이모가 표식을 해서,
수확할 준비가 된 과일 유형을 식별할 수 있다.
리보그는 과일을 골라 유사한 유형의 모든 과일을 수확한다.

.. todo::

    이번 학습을 충분히 이해하기 위해서, 
    파이썬 리스트에 관해 알고 있어야 된다.
    특히, 아직 저자가 다루지 않은 리스트 인텍싱(list indexing)도 알고 있어야 된다.
    아래 예제에서, 다음과 같이 구분할 필요도 있다.

        objects = object_here()
        selection = objects[0]

        # 이어서...

        selection = object_here()[0]

리보그는 해당 지점에서 발견한 객체 명칭이 담겨진 
**리스트** 를 반환하는 ``object_here()`` 함수를 사용한다;
**Harvest 4** 세상에는, 네가지 객체 ``"apple, "banana", "orange", "strawberry"`` 
중에서 하나가 발견될 수 있다.

.. warning::

    처음에 코드를 읽게 되면, 이해가 되지 않는 새로운 점이 두개 다음 코드에 나와 있다.
    먼저, **인자** 를 받는 함수를 처음으로 정의하는데, 이 경우에 ``fruit`` 가 된다.
    두번째로, 연속된 등호 기호, ``==``, 를 사용해서 둘이 같은지 확인하려고 시험한다.


.. code-block:: py3

    think(0)  # 선택옵션; 너무 오래 걸리지 않게 한다...

    def harvest_one_row(fruit):
        while front_is_clear():
            if object_here() == fruit:
                take(fruit)
            move()

    def go_back_to_beginning_of_row():
        ...

    def move_to_next_row():
        ...

    def go_to_first_row():
        ...

    def complete_one_row():
        harvest_one_row(selection)
        go_back_to_beginning_of_row()
        move_to_next_row()

    move()
    selection = object_here()[0]   # 리스트에 나온 객체 명을 선택한다
    take(selection)
    go_to_first_row()
    for i in range(6):
        complete_one_row()

.. hint::
    .. code-block:: py3

        from library import *
        
        think(0)
        
        def harvest_one_row(fruit):
           while front_is_clear():
               if object_here() == fruit:
                   take(fruit)
               move()
        
        def go_back_to_beginning_of_row():
            turn_around()
            while front_is_clear():
                move()
        
        def move_to_next_row():
            turn_right()
            move()
            turn_right()
        
        def go_to_first_row():
            turn_right()
            while not wall_in_front():
                move()
            turn_left()        
        
        def complete_one_row():
            harvest_one_row(selection)
            go_back_to_beginning_of_row()
            move_to_next_row()
        
        move()
        selection = object_here()
        take(selection)
        for i in range(9):
            complete_one_row()
        go_to_first_row()  

.. topic:: 시도해 보기!

    상기 프로그램을 완성해서, 네가지 세상 모두에서 동작하도록 한다:
    **Harvest 4a**, **Harvest 4b**, **Harvest 4c**, **Harvest 4d**.

