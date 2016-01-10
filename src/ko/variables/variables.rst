
.. note::

    영어에서, *동의어(synonym)* 를 사용해서 같은 의미를 갖는 다른 단어를 기술한다.
    *변수* 를 해당 객체에 대한 *동의어* 로 간주하는 것이 유용할 수 있다.

동일 객체에 대한 다수 명칭
----------------------------------

이전 예제에서, *단계적 정제* 를 언급했을때,
세상 **Around 4** 에 대한 해법으로 다음을 제시했다::

    from library import turn_right

    # 토큰을 내려놓음으로써 시작점을 표시한다.
    put()

    # 장애물 없는 방향을 찾아 이동을 시작한다.
    while not front_is_clear():
        turn_left()
    move()

    '''  토큰을 내려놓은 지점에 되돌아 왔을 때, 
    세상을 한바퀴 돈 것을 알게 된다. '''

    while not object_here():
        if right_is_clear():  # 우측을 따라서 진행한다.
            turn_right()
            move()
        elif front_is_clear():    # 이동... 우측벽을 따라서...
            move()
        else:
            turn_left()  # 좌회전해서 벽을 따라 진행한다.

그리고 나서, 새로운 함수를 정의해서,
주석을 추가할 필요성을 줄임으로써, 해법에 대한 핵심을 더 잘 기술한다.
현재상태로 간직할 유일한 함수 중 하나는 다음과 같다::

    def follow_right_wall():
        if right_is_clear():
            turn_right()
            move()
        elif front_is_clear():
            move()
        else:
            turn_left()

변수를 사용해서 상기 함수를 나머지 프로그램과 명확한 방식으로 조합하는 
또다른 방식을 사용해보자.
예를 들어, 다음과 같이 작성하는 대신에::

    # 토큰을 내려놓음으로써 시작점을 표시한다.
    put()

다음과 같이 작성한다::

    mark_starting_point = put
    mark_starting_point()

유사한 방식으로, 다음과 같이 작성하는 대신에::

    # 장애물 없는 방향을 찾아 이동을 시작한다.
    while not front_is_clear():
        turn_left()
    move()

다음과 같이 작성한다::

    path_is_blocked = wall_in_front  # "not front_is_clear" 대신에 이것을 사용한다.

    while path_is_blocked:
        turn_left()

    move()

또한, 다음과 같이 작성하는 대신에::

    '''  토큰을 내려놓은 지점에 되돌아 왔을 때, 
    세상을 한바퀴 돈 것을 알게 된다. '''

    while not object_here():
       ...

다음과 같이 작성한다::

    back_to_starting_point = object_here

    while not back_to_starting_point():
        ...

그래서, 상기 변경사항 모두를 함께 넣어서 프로그램을 재작성한다.
먼저 새로운 단어 (변수)를 정의하고 나서, 사용한다::

    from library import turn_right

    mark_starting_point = put
    path_is_blocked = wall_in_front
    back_to_starting_point = object_here

    def follow_right_wall():
        if right_is_clear():
            turn_right()
            move()
        elif front_is_clear():
            move()
        else:
            turn_left()

    # 정의 끝 -- 실제 프로그램 시작

    mark_starting_point()
    while path_is_blocked():
        turn_left()
    move()

    while not back_to_starting_point():
        follow_right_wall()


이전보다 주석이 훨씬 적지만, 프로그램에 대한 의미는 매우 명확하다.
주석 대신에 잘 선택한 변수(명칭)를 사용하는 엄청난 잇점이 
파이썬이 주석이 **아닌** 코드를 실행한다는 것이다;
그래서 만약 코드가 잘못되면, 즉각 볼 수 있다;
만약 주석이 잘못되면, 파이썬이 이를 프로그래머에게 일러줄 수 없다.