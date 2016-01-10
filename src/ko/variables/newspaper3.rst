신문 배달 재방문
==================================

신문 배달 예제로 되돌아 가자.
하지만, 이번에는 신문대금을 지불된 신문배달 사례만 살펴볼 것이다.

러브레이스 누님 **Newspaper 1** 세상과, 
배비지 아저씨 **Newspaper 2** 세상에서 모두 동작하는 해법이 다음에 나와 있다:

.. code-block:: py3
    :emphasize-lines: 28

    from library import turn_right, turn_around

    def climb_up_one_floor():
        turn_left()
        move()
        turn_right()
        move()
        move()

    def climb_down_one_floor():
        move()
        move()
        turn_left()
        move()
        turn_right()

    def get_money():
        while object_here() :
            take()

    # === 정의 끝 ===

    take()
    while not object_here():
        climb_up_one_floor()

    get_money()
    put()   # 별신문을 내려놓는다.
    turn_around()
    while not at_goal() :
        climb_down_one_floor()


.. topic:: 중요한 테스트!

    상기 프로그램을 다시 생성하고, 실행하고, 결과를 살펴본다.

위에서 보듯이, 리보그는 노란색으로 강조된 행에 ``put()`` 명령어를 실행하려고 할 때, 멈춰서 다음과 같이 소리친다; 
``I carry too many different objects. I don't know which one to put down!``.

그래서, 문제는 리보그가 돈(토큰)과 신문(별)을 함께 지니고 다니는데 있다.

.. topic:: 해결책?

    프로그램을 변경해서 리보그가 돈을 집기 **전에** 신문을 
    내려놓도록 한다. 그러면 잘 동작하는가?

함수 인자
------------------

위에서 언급된 세상에 별과 토큰처럼, 해당 지점에 두개 혹은 그이상 다른 유형의 객체가 있는 경우,
리보그로 하여금 ``take()`` 해서 객체를 집어들게 하지만, 집어 올리는 것이 어떤 유형인지 알 수가 없다.
마찬가지로, 리보그가 많은 유형의 객체를 지니고 다니다가 객체를 놓게 ``put()`` 명령을 하면, 어느 객체를 놓아야하는지 알지 못한다.

해법은 간단하다: 좀더 구체적이면 된다.

함수 인자를 살펴봤다.
행복한 우연(!)이랄까, 함수 ``take()`` 와 ``put()`` 모두 인자를 받을 수 있다. 이경우 흥미로운 것은... 별 신문이 별로 표현되서, 사용할 인자는 다음과 같이 ``"star"`` 이 된다.

.. index:: take(arg), put(arg), object_here(arg)

.. code-block:: py3

    take("star")
    put("star")

돈에 대해서는 ``"token"`` 을 사용한다.


.. topic:: 여러분 차례!

    상기 프로그램을 변경해서, 리보그가 어떤 유형의 객체를 놓거나 집을지 지정할 수 있다. 작성한 프로그램이 **Newspaper 1** 와 **Newspaper 2** 세상 모두에서 올바르게 동작하는지 확실히 한다. ``think()`` 함수를 사용해서 경우에 따라서 리보그 행동을 높이거나 늦추도록 한다.


.. topic:: 또다른 선택옵션

    ``object_here()`` 를 ``object_here("token")`` 로 인자를 바꿔넣도록 프로그램을 변경해서도, 잘 동작하는지 확실히 한다.
