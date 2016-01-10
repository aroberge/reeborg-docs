창고지기 (Sokoban)
===================

.. figure:: ../../images/sokoban_ani.gif
   :figwidth: 55%
   :align: left

   "Sokoban ani" by Carloseow at English Wikipedia.
   Licensed under CC BY 3.0 via Wikimedia Commons -
   http://en.wikipedia.org/wiki/Sokoban#/media/File:Sokoban_ani.gif

From http://en.wikipedia.org/wiki/Sokoban

*정사각형 보드에서 게임을 즐기는데, 각 정사각형은 바닥이거나 벽이다.
일부 정사각형은 상자가 있고, 일부 정사각형은 상자 저장소 지점으로 표시되어 있다.
플레이어는 보드에 한정되어 있고, 수평 혹은 수직방향으로 빈 정사각형에만 이동할 수 있다
(벽을 혹은 상자를 뚫고 지나갈 수는 없다).
플레이어는 상자를 옮길 수도 있는데 상자를 정사각형 넘어 밀어 넣는다.
상자를 다른 상자나 벽에 밀어 넣을 수 없고 빼낼 수도 없다.
모든 상자가 상자 저장소 위치에 놓여질 때, 퍼즐이 풀린다.*


창고지기와 리보그 세상
----------------------------

리보그 세상으로 창고지기(Sokoban) 유형의 퍼즐을 풀 수도 있다.
하지만, 리보그를 제어하는데 화살표를 사용하는 대신에,
리보그가 어떤 작업을 수행해야 하는지 일러주도록 코드를 작성한다.
하지만, 원작 창고지기와 마찬가지로, 상자를 다른 상자 혹은 벽에 밀어 넣을 수 없다.
원작 창고지기와 다른 점은, 이와 같은 방식으로 상자를 밀어 넣으려고 하면 리보그가
불평하고 프로그램이 멈춘다.

|sokoban_wiki|

창고지기 퍼즐을 ``move()`` 와 ``turn_left()`` 명령어만으로 해결할 수 있지만...
극도로 지겨울 것이다. 더욱이, 리보그 기름이 누유되어 난잡스러워진다.
창고지기 라이브러리(sokodan library)에서 ``up()``, ``down()``, ``left()``, ``right()`` 함수를 가져와서 사용하는 것이 훨씬 더 낫다: 화살표를 사용하여 동작시키는 것과 같은 방식으로 동작한다.
더욱이, 창고지기 라이브러리에서 가져온 함수는 정수를 선택옵션 인자로 받아서,
해당 함수가 얼마나 반복되어야 되는지 지정할 수 있다: 이를 통해서 훨씬 더 짧게 프로그램을 작성할 수 있게 된다.

마지막으로 창고지기 라이브러리를 가져우면, 리보그 기름 누유는 자동으로 멈춘다.

추가 도전과제
------------------

상자를 리보그가 물에 밀어 넣으면 다리로 변하게 되기 때문에,
다른 유형의 도전과제를 만들 수 있는데, 이는 원작 창고지기로는 불가능한 것이다.

|sokoban2|

.. |sokoban_wiki| image:: ../../images/sokoban_wiki.gif
.. |sokoban2| image:: ../../images/sokoban2.gif

마지막으로 **얼음** 타일을 추가하는 것을 생각해 볼 수 있는데, 도전과제를 좀더 미끄럽고 어렵게 만들 수 있다.

왜 창고지기인가?
---------------------------

창고지기 유형 문제는 기본적으로 로직 문제로, 해법을 찾는 것 자체가 도전과제다.
저자의 실험에 따르면, 문자를 제어하는데 사용되는 화살표키가 사용되는 전통적인 환경보다 코드를 사용하는 환경이 문제를 푸는데 더 어려워 보인다.

완전 초보자에게는 창고지기 유형 문제가 흥미로울 수 있다. 완전 초보자는 아직 제어 흐름 구조(``if/elif/else/while/...``)를 학습하지 않았지만, 로봇이 어려운 작업을 수행하는 프로그램을 작성하길 원한다.

특수 창고지기 ``up(), down(), left(), right()`` 함수를 사용해서 창고지기 문제가 해결되면,
학생들에게 ``move()`` 와 ``turn_left()`` 만 사용해서 해법을 바꿔보게 한다.

우수 학생을 위한 창고지기
-----------------------------

.. Topic:: 전문가만

   **여러분이 고급 프로그래머가 아니라면, 다음 코드는 의미가 없다.**

    창고지기 퍼즐을 우수 학생들에게만 가르쳐 준 검색 기법을 사용해서 풀 수 있다.
    그러한 기법을 사용하려면, 직접적으로 프로그램이 세상에 관한 정보를 입수해야만 된다.
    세상은 실제로 자바스크립트 객체(속성만, 메쏘드는 아님)로 인코딩되어 json 문자열이 파이썬 딕셔너리로 전환된다. 다음 프로그램을 실행하면, 적재된 세상이 어떤 방식으로 표현되고, 
    파이썬 딕셔너리로 변환되는지 볼 수 있다.

    .. code-block:: python

        import json  # very incomplete Brython module
        from browser import window

        # First, use the builtin JSON Javascript function as it can
        # show a nicely formatted representation of the world;
        # this should have been implemented in the Brython json module
        # but is currently missing.
        world_str = window.JSON.stringify(RUR.current_world, None, 2);
        print(world_str)

        # Convert the json world representation into a Python dict
        # using Brython's json module.
        world_dict = json.loads(world_str)

        # We can now use Python's standard notation for dicts and lists
        # to extract the required information.
        print(world_dict["robots"][0]["orientation"] == RUR.EAST)


