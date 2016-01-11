미로
=====

이번 절에서, 미로 생성을 자동으로 하고 미로 탈출을 하는 간단한 해법을 살펴본다. 미로를 생성하는데 사용하는 접근법은 
https://en.wikipedia.org/wiki/Maze_generation_algorithm 위키에서 언급된 깊이 우선 알고리즘(depth-first algorithm)이고, 파이썬 구현은 http://rosettacode.org/wiki/Maze_generation#Python 사이트에서 참조했다.

.. note::

    표기법에 대한 축약어. ``RUR`` 은 리보그 세상에서 사용되는 일반적인 네임스페이스다; Reeborg the UsedRobot에서 RUR이 왔다.

    ``RUR.we`` 는 world_editor.js에 나오는 함수를 표기한다; 
    ``RUR.vis_world`` 는 visible_world.js에 나오는 함수를 표기한다.

    world_editor.js 파일에는 그래픽 세상 편집기에 사용되는 함수 대부분이 담겨 있다.

먼저 벽 네개로 둘러싸인 격자를 모든 셀에 생성한다.
리보그 세상에서, 해당 셀위치마다 두 벽만 기록한다: 하나는 해당셀 우측("동쪽")에 위치하고, 다른 하나는 해당셀 윗쪽("북쪽")에 위치한다. 전체 *세상* 그자체는 벽 경계로 둘러싸여져서, 마지막 칼럼의 우측벽과 위쪽 행 벽을 생성할 필요는 없다.

.. code-block:: python

    def make_filled_maze(w, h):
        '''Creates a maze of size w by h with
           all grid cells surrounded by walls
        '''
        RUR.we.remove_all()
        RUR.vis_world.compute_world_geometry(w, h)
        for i in range(1, w):
            for j in range(1, h):
                RUR.we.toggle_wall(i, j, "east")
                RUR.we.toggle_wall(i, j, "north")
        for i in range(1, w):
            RUR.we.toggle_wall(i, h, "east")
        for j in range(1, h):
            RUR.we.toggle_wall(w, j, "north")




|maze_gen1|

.. |maze_gen1| image:: ../../images/maze_gen1.gif

.. important::

   파이썬과 자바스크립트에서, 미로생성 예제를 세상 메뉴에서 찾을 수 있다. 일반적으로, 파이썬 Brython 코드를 자바스크립트로 전환하면 순수 자바스크립트 코드 속도와 비교될만큼 빠르게 실행된다. 하지만, 미로 생성 사례의 경우, 자바스크립트 코드가 **훨씬** 더빨리 실행된다.

   누구나 자바스크립트 코드를 사용해서 미로(세상, 즉 JSON 파일)를 생성할 수 있는데, 어느 프로그래밍 언어로도 나중에 사용할 수 있다.

벽으로 가득찬 격자를 갖추게 되면, 이를 다음과 같이 미로로 변환시킨다:


1. 랜덤하게 셀을 고른다
2. 랜덤하게 인접한 셀을 선택한다 ...
3. ... 해당 셀은 방문한 적이 없다.
4. 두 셀사이 벽을 제거하고 인접한 셀을 방문한 셀 목록(list)에 추가한다.
5. 만약 방문한 적이 없는 인근 셀이 없다면, 적어도 한번도 방문한 적이 없는 인근셀로 되돌아 간다; 최초 시작한 셀로 되돌아갈 때까지 과정을 반복한다.

재귀를 사용해서 알고리즘을 구현하면 다음과 같다::

    from random import shuffle, randrange

    def make_maze(w = 16, h = 8):
        visited = [[False] * w + [True] for _ in range(h)] + [[True] * (w + 1)]
        def walk(x, y):
            visited[y][x] = True
            d = [(x - 1, y), (x, y + 1), (x + 1, y), (x, y - 1)]
            shuffle(d)              # 2 randomize neighbours
            for (xx, yy) in d:
                if visited[yy][xx]: # 3 (ignore visited)
                    continue
                if xx == x:
                    RUR.we.toggle_wall(x+1, min(y, yy)+1, "north")  # 4
                elif yy == y:
                    RUR.we.toggle_wall(min(x, xx)+1, y+1, "east")   # 4
                RUR.rec.record_frame()
                walk(xx, yy)     # recursive call; push ahead
                                 # 5; after recursion, effectively backtrack

        walk(randrange(w), randrange(h))  # 1


|maze_gen2|

.. |maze_gen2| image:: ../../images/maze_gen2.gif

상기 알고리즘은 http://rosettacode.org/wiki/Maze_generation#Python 사이트에서 참조했다. 
알고리즘에 흥미로운 면이 하나 있다. 리스트 크기보다 큰 인텍스 값에 도달하면, ``IndexError`` 인덱스오류가 발행하는데, 이를 회피하려고 추가로 거짓으로 방문된 리스트 항목을 추가한다. 똑똑하게 ``[-1]`` 이 리스트에 나온 최종 항목이라는 사실을 이용했다. (저자 스스로 생각하지 못했던 것이다.)

전체 코드가 다음에 나와 있다::

    from random import shuffle, randrange, randint

    # Maze parameters
    max_x = 5
    max_y = 5
    RUR.current_world.small_tiles = False

    # display related options
    RUR.MAX_STEPS = 2000  # bigger for large mazes
    think(30)


    def make_filled_maze(w, h):
        '''Creates a maze of size w by h with
           all grid cells surrounded by walls
        '''
        RUR.we.remove_all()
        RUR.vis_world.compute_world_geometry(w, h)
        for i in range(1, w):
            for j in range(1, h):
                RUR.we.toggle_wall(i, j, "east")
                RUR.we.toggle_wall(i, j, "north")
        for i in range(1, w):
            RUR.we.toggle_wall(i, h, "east")
        for j in range(1, h):
            RUR.we.toggle_wall(w, j, "north")
        RUR.rec.record_frame()


    def make_maze(w = 16, h = 8, name="maze"):
        '''Adapted from
           http://rosettacode.org/wiki/Maze_generation#Python

           "name" is the value used to save the maze in the
           browser's local storage so that it is available
           if the page is reloaded.
        '''
        make_filled_maze(w, h)
        pause(500)
        vis = [[False] * w + [True] for _ in range(h)] + [[True] * (w + 1)]
        def walk(x, y):
            vis[y][x] = True
            d = [(x - 1, y), (x, y + 1), (x + 1, y), (x, y - 1)]
            shuffle(d)
            for (xx, yy) in d:
                if vis[yy][xx]:
                    continue
                if xx == x:
                    RUR.we.toggle_wall(x+1, min(y, yy)+1, "north")
                elif yy == y:
                    RUR.we.toggle_wall(min(x, xx)+1, y+1, "east")
                RUR.rec.record_frame()
                walk(xx, yy)

        walk(randrange(w), randrange(h))

        reeborg = UsedRobot(randint(1, max_x), randint(1, max_y))
        RUR.we.add_object("star", randint(1, max_x), randint(1, max_y), 1)
        RUR.rec.record_frame()
        RUR.storage.save_world(name)


    def turn_right():
        turn_left()
        turn_left()
        turn_left()

    make_maze(max_x, max_y)
    pause(500)

    while not object_here():
        if right_is_clear():
            turn_right()
            move()
        elif front_is_clear():
            move()
        else:
            turn_left()

코드에는 로봇, 별이 포함되어 있고, 로봇이 별을 찾는 빠른 방법도 포함되어 있다. 


|maze_gen2b|

.. |maze_gen2b| image:: ../../images/maze_gen2b.gif

``RUR.rec.record_frame()`` 행은 해당 시점에 세상 상태를 "사진 찍는"(프레임을 기록) 명령이다. 문서 나머지 부분을 읽지 않은 분을 위해 짧게 설명하면 다음과 같다: 리보그 세상에서, 프로그램은 먼저 뒷무대에서 전체가 실행되고 프레임으로 기록된다; 그리고 나서, 연속된 프레임으로 한번에 하나씩 재생된다. ``think(ms)`` 함수를 사용해서 지연 시간을 조정할 수 있는데, 각 동작 사이에 리보그가 생각하는데 소요되는 시간을 나타낸다. ``RUR.storage.save_world(name)`` 명령어가 브라우저 로컬 저장소에 미로를 저장한다. 그래서, 나중에 리보그 세상에 접근할 때(물론 동일한 브라우저를 사용), 미로를 불러올 수 있다. 로봇과 찾을 객체를 추가했다. 로봇이 객체를 찾는데 사용된 전략은 "우측 벽을 따라 진행함"으로, 바로 우측에 있는 벽 방향으로 이동한다.

``pause()`` 에 다양한 호출을 포함할 수 있는데, 진행단계를 좀더 면밀히 살펴보는데 유용하다.


**주목: 프레임이 기록될 때, 화면은 사실상 정지된다.** [앞에서 언급했듯이, 순수 자바스크립트 코드가 **훨씬** 더 빨라 긴 지연문제를 야기하지 않는다.] 예를 들어, 다음 화면이 출력될 때까지 40초 걸렸다:

|maze_gen3|

.. |maze_gen3| image:: ../../images/maze_gen3.gif


.. topic:: 학생을 위한 사용법

    누군가 임의 생성된 미로 세상을 갖고자 한다면,
    선호하는 접근법은 세상 "pre-code" 부분에 미로 생성 코드를 포함시키는 것이다. 그렇게 함으로써, 편집기에는 학생 코드만 담겨지게 된다.
