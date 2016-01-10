리스트(List)
================

다음 프로그램을 실행한다.
먼저 올바른 세상을 선택하고 두번째에는 프로그램 나머지 부분을 실행한다.

.. code-block:: python3

    World("/worlds/many.json", "Many")
    move()
    print(object_here())

결과는 아마도 다음과 같을 것이다::

    ['token', 'triangle', 'banana', 'carrot']

.. note::

    파이썬 함수로 ``list`` 가 있는데, 리스트를 생성하는데 사용된다!
    할당 대입 ``=`` 기로를 사용해서 객체에 명칭을 할당하는 것을 이미 살펴봤다;
    ``list`` 를 변수명칭으로 사용하는 것을 회피해야 되는데, 이유는 파이썬에 있는 ``list()``
    함수를 사용하지 못하게 되기 때문이다.

상기 프로그램이 파이썬 **리스트(list)** 예제다.
파이썬 리스튼 꺾쇠 괄호( ``[ ]`` )로 표현되고,
아무 것도 없거나, 하나 혹은 많은 항목을 담을 수 있다.
상기 예제에서, 리스트에는 4개 항목이 담겨 있는데, 각각은 파이썬 문자열이다.
"꺾쇠 표기법"을 사용해서, 다른 유형의 객체를 담을 수 있는 리스트를 생성할 수 있다::

    a_list = [1, "Reeborg", move]

리스트 요소 접근하기
--------------------------

첫번째 신문배달 작업을 봤을 때, 다음을 읽어봤을 것이다::

    컴퓨터 프로그래밍에서, 일반적으로 1 대신에 0에서부터 세기 시작한다. 여기 나온 세상은 컴퓨터 과학에서 유명한 세명을 지칭하기 때문에, 세상을 0 으로부터 번호를 붙이는 것이 적절하다고 본다.

리스트가 주어지면, 꺾쇠 표기법을 사용해서 단일 요소를 불러올 수 있다.

.. topic:: 시도해 보기!

    다음 프로그램을 시도해 본다::

        odd_numbers = [1, 3, 5, 7]
        print( odd_numbers[0] )
        print( odd_numbers[1] )
        print( odd_numbers[3] )
        print( "length = ", len(odd_numbers))

    파이썬 함수 ``len()`` 은 리스트 길이 정보를 제공한다.
    리스트 길이는 해당 리스트가 갖고 있는 총 항목 갯수와 같다.

    리스트에서 항목 하나를 뽑아내는데 사용되는 꺾쇠괄호 내 숫자를 해당 항목에 대한 **인덱스(index)** 라고 부른다.

종종, 리스트 마지막 요소를 뽑아내거나, 그 이전 것을 뽑아내는 것이 유용할 수 있다.
``len()`` 함수를 사용해서 마지막 항목 위치를 알아낼 수 있지만,
파이썬에는 더 편리한 지름길(shortcut, 단축)이 있다.


.. topic:: 시도해 보기!

    다음 프로그램을 실행해 본다::

        odd_numbers = [1, 3, 5, 7]
        print( odd_numbers[-1] )  # 마지막 항목
        print( odd_numbers[-2] )  # 끝에서 두번째 항목

    리스트 마지막에서 시작되는 항목을 뽑아내는데 음수 부호를 포함하여 편리하게 사용하는 법에 주목한다.

리스트를 조건으로 사용하기
---------------------------------------

리스트가 ``if`` 혹은 ``while`` 문장에서 조건으로 사용될 때, 리스트에 항목이 있느냐 없느냐에 따라 다르게 동작한다.

.. topic:: 여러분 스스로 파악해 본다!

    다음 프로그램을 실행한다::

        # 다음 중 하나만 맞다.

        if []:
            print("An empty list is considered to be equivalent to True,")
        elif ['Reeborg']:
            print("An empty list is considered to be equivalent to False.")
            print("But a non-empty list is considered to be equivalent to True.")
        elif [1, 2, 3, 4, 5]:
            print("A list is considered to be equivalent to True",
                  "ONLY if it contains many items")
        else:
            print("Perhaps lists are always considered to be False ...")

    아시다시피, ``거짓(False)`` 로 간주되는 조건을 담고 있는 분기는 건너뛴다;
    ``참(True)`` 조건을 포함하는 첫째 분기만 실행된다.


더 많은 추수 도전과제
-----------------------------

.. topic:: 먼저, 신속한 테스트

    다음 프로그램을 실행한다.
    리보그가 발견한 첫번째 유형의 객체를 출력한다.
    그리고 나면, 프로그램을 변경해서 두번째 발견한 유형의 객체를 출력한다.

    .. code-block:: python3

        World("/worlds/many.json", "Many")
        move()
        print(object_here()[0])

리보그 이모는 과일농부다.
이모 농장에는, 다양한 유형의 과일이 심어져 있다.
특정한 달에는, 특정한 유형의 과일만 수확이 가능하다.
**Harvest 4a**, **Harvest 4b**, **Harvest 4c**, **Harvest 4d** 세상을 살펴본다.
이모가 농장에 들어설 때, 리보그 이모가 표식을 해서,
수확할 준비가 된 과일 유형을 식별할 수 있다.
리보그는 과일을 골라 유사한 유형의 모든 과일을 수확한다.

리보그는 ``object_here()`` 함수를 사용한다.
앞에서 봤듯이, ``object_here()`` 함수는 해당 지점에서 발견된 객체 명칭을 담고 있는 **리스트** 를 반환한다;
**Harvest 4** 세상에는 ``"apple", "banana", "orange", "strawberry"`` 네가지 과일이 가능한 객체로 있다.

앞에서 언급된 네가지 세상에서 작업을 수행하는데 필요한 프로그램이 완성되지 않은 채로 나와 있다.
``FRUIT`` 변수를 사용하는데, 함수 내부와 외부에서 동일 변수명칭이 사용되기 때문에 대문자로 표기했다;
본질적으로 **전역** 변수다. 하지만, ``=`` 기호를 사용해서 함수 내부에서 값을 할당하지 **않았기** 때문에, ``global`` 키워드를 사용할 필요는 없다.

.. code-block:: py3

    def harvest_one_row ():
        while front_is_clear():
            if object_here()[0] == FRUIT:
                take(FRUIT)
            move()

    def go_back_to_beginning_of_row():
        pass

    def move_to_next_row():
        pass

    def go_to_first_row():
        pass

    def complete_one_row():
        harvest_one_row()
        go_back_to_beginning_of_row()
        move_to_next_row()

    move()
    FRUIT = object_here()[0]
    take(FRUIT)
    go_to_first_row()
    repeat 6:
        complete_one_row()


.. topic:: 여러분 차례!

    상기 프로그램을 완성해서, 네가지 세상 모두에서 동작하도록 한다:
    **Harvest 4a**, **Harvest 4b**, **Harvest 4c**, **Harvest 4d**.

마지막 한가지 더  실험
---------------------------

종종, 프로그래밍 너무 커다랄 때, 프로그램을 여러 파일에 담는 것이 의미있게 된다.
여기서, 작성한 프로그램은 파일에 담겨있지 않다:
프로그램이 코드 편집기에 있지만, 프로그램 일부가 라이브러리에 있을 수도 있다.
위에서 작성한 프로그램이 너무 커서, 두 조각으로 쪼갤 필요가 있다고 가정하자.
라이브러리에서 ``harvest_one_row()`` 함수를 정의하고,
다음 명령어를 사용해서 메인 프로그램으로 가져온다.

.. code-block:: py3

    from library import harvest_one_row

프로그램이 여전히 잘 동작하는가? ``global`` 키워드를 사용하면 동작이 되는가?
실험 결과 전역 변수를 사용할 때 문제점을 지적할 수도 있다. 전역 변수는 함수 내부에 사용되지만
다른 곳에서 정의된 것이다.
