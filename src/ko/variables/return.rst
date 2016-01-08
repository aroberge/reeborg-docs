반환(Return)
==============


.. note::

    북쪽은 화면 상단이 된다; 동쪽은 우측이고, 
    서쪽은 좌측이고, 남쪽은 화면 하단이 된다.

여러분도 아시듯이,
리보그는 정확하게 좋은 모양은 아니다.
리보그는 왼쪽으로만 회전할 수 있고, 기름이 질질 세어나오고,
바로 앞 오른쪽에 있을 때만 벽을 볼 수 있고, 문자 그대로 토큰 위에 서 있을 때만 
토큰을 볼 수 있다. 또한, (일부 망가진) 나침판을 갖고 있어서,
북쪽을 향하고 있는지 ... 아닌지만 알아낼 수 있다.
북쪽을 향하고 있는지 알아내려면, 리보그로 하여금 ``is_facing_north()`` 
테스트를 해야 한다.

.. topic:: 프로그래밍 시간!

    다음 프로그램을 실행해서 단순한 세상을 선택해서, 임의 방향을 향해 리보그가 출발하게 한다.

        World("/src/worlds/face_north.json", "Face north")

    그리고 나서, 시작 방향이 어느 쪽인지에 관계없이, 리보그가 왼쪽으로 회전해서 북쪽을 향할 때까지 
    방향을 확실히 하는 짧은 프로그램을 작성한다.
    

Getting results from functions
------------------------------

Tests like ``is_facing_north()`` are actually Python functions. They
differ from other functions like ``turn_left()`` or ``move()`` in that
they ``return`` a value. Let's start by considering a simple example:

.. topic:: Try this!

    .. code-block:: py3

        def interrupted_two_steps():
            move()
            return
            move()

        interrupted_two_steps()


As you can see, the return statement prevents the second ``move()`` from
being executed.
The ``return`` keyword can actually be accompanied by something else.

.. topic:: Try this!

    For example, try the following::

        def north():
           return is_facing_north()

        while not north():
            turn_left()

As you have tried it, you noticed that ``north()`` was giving the same
result as ``is_facing_north()``; that is the effect of the ``return``
statement. We can use this to have Reeborg be able to identify
orientations other than North. First, note that if Reeborg turns left 4
times, he will be back to its initial orientation; we do want Reeborg to
end the test in the same orientation as that which he had at the start.
Now, suppose we would like to know if Reeborg was facing South. We could
ask Reeborg to turn left twice, note if his orientation is North (which
it should be if he was facing South) or not, turn left twice more, to go
back to its original orientation, and tell us what he remembered using
the ``return`` statement. One thing we need to do: have Reeborg use a
*variable* to remember its orientation after two left turns::

    def is_facing_south():
        turn_left()
        turn_left()
        remember = is_facing_north()
        turn_left()
        turn_left()
        return remember

    # now, ensure that Reeborg is facing South
    while not is_facing_south():
        turn_left()

.. topic:: Try it!

    It will not take you long, and you will be ready for the next exercise!


The above way works ... but, depending on its initial orientation, you might get
dizzy if you keep track of all left turns that Reeborg has to make: when
its orientation is not South, for each left turn that he makes to change
its orientation, he must make 4 more to determine its new orientation!

In a future tutorial, when we talk about Object-Oriented Programming,
we will find a way, by digging in Reeborg's built-in program, to
fix its compass and have it determine its orientation without getting
dizzy.

.. topic:: Mini-quiz!

    Write a program that has Reeborg face West, no matter what his original
    orientation is. Test it with Reeborg in various starting orientations,
    by giving him a few ``turn_left()`` instructions first.

How to think about return
-------------------------

Suppose we have the following::

    def some_function ():
        ...
        return something

    ... = some_function()

In this case, the call to ``some_function()`` on the last line gets
replaced by the value of ``something`` which is what follows the
``return`` keyword. If nothing follows ``return`` the result is
``undefined``.

.. topic:: More returns


    Reeborg can determine if there is a wall in front of him, using
    ``front_is_clear()``, or if there is a wall to his right, using
    ``right_is_clear()``. Write a test that has Reeborg turn left 4 times,
    so that he ends up back in the same orientation that he started with,
    but that returns ``True`` if there is no wall to his left.

.. topic:: Challenges!

    Use the test you have written to have Reeborg get out of worlds **Maze 1** and
    **Maze 2** by following the **left** wall. Do the same for solving
    challenges for worlds **Storm 1** and **Storm 2**, that is, go around the
    one-room houses in the opposite direction compared with your previous
    solutions.


