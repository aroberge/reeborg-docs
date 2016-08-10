객체, 배경 이미지, 등
================================

리보그 경로를 막는 벽 외에도, 다양한 객체를 표현하는데 사용되는 이미지가 많다.


기본 객체
-------------

리보그는 다양한 객체와 상호작용 할 수 있다.
리보그는 ``take()`` 와 ``put()`` 함수를 사용해서 다음에 나오는 객체를 집거나 놓을 수 있다.
특히, 리보그가 가장 좋아하는 객체는 |token| **토큰** 이다.
사람 대부분이 가치가 없다는 것을 제외하면, 토큰은 웃는 얼굴을 갖는 동전 같다; 리보그는 가치가 없다는 점에 대해서 다르게 생각한다.

만약 객체가 하나 이상 있고, 어떤 객체를 ``take()`` 해서 집거나, ``put()`` 해서 내려놓을지 명시해야 되면, 문자열로 객체 명칭을 사용한다. 예를 들어, ``put("token")``  혹은 ``take('token')``. [짝만 맞기만 하면, 이중 인용부호든 단일 인용부호든 사용가능하다.]

토큰외에도, 리보그는 다양한 과일, 꽃, 도형 등과 상호작용 할 수 있다.
[많은 이미지는 http://openclipart.com 사이트에서 가져왔다]


:사과-apple: |apple|
:바나나-banana: |banana|
:당근-carrot: |carrot|
:데이지꽃-daisy: |daisy|
:민들레-dandelion: |dandelion|  민들래는 예쁘지만, 여기서는 잡초로 간주된다 - 세상에서 제거될 필요가 있다.
:낙엽-leaf: |leaf|  리보그는 특히 낙엽을 좋아하지 않는다. 리보그 세상에서 낙엽의 존재는 가을의 도착을 알린다. 낙엽이 나무에서 떨어지고, 리보그는 낙엽을 가지고 놀기 보다 모아야 된다. 틈만 나면, 리보그는 항상 놀고 싶어 한다.
:오렌지-orange: |orange|
:딸기-strawberry: |strawberry|
:튤립-tulip: |tulip|
:정사각형-square: |square|
:별-star: |star|
:삼각형-triangle: |triangle|  이런 유형의 삼각형은 리보그 세상 내부에만 존재한다. 삼각형을 확대해 보면 다음과 같다.

|impossible-triangle|

장식 객체
----------------

상기 객체가 순전히 장식 객체로 그려질 수 있다. 장식으로 그려진 경우, 리보그는 장식객체와 상호 작용할 수 없고, 작업이 완수되었는지 아닌지를 판단할 때 고려되지 않는다.

해당 지점에서 발견한 "정상" 객체 갯수는 표식되는 반면에, 장식 객체에는 숫자가 없다.


배경 타일
----------------

:잔디-grass: |grass| |pale_grass|  리보그가 걸어가는데 문제가 되지 않음
:자갈-gravel: |gravel|  리보그가 걸어가는데 문제가 되지 않음
:물-water: |water|  리보그가 익사할 수 있음. 다행스럽게도, 리보그는 ``front_is_clear()`` 함수를 사용해서 물을 탐지할 수 있음.
:진흙-mud: |mud| 리보그를 수렁에 빠지게 만들 수 있다. 리보그가 진흙에 빠지기 전까지, 탐지할 수 없다.
:벽돌벽-brick wall: |bricks|  리보그는 벽돌벽과 충돌할 수 있다; 다행스럽게도, ``front_is_clear()`` 함수를 사용해서 벽돌벽을 탐지할 수 있다.
:얼음-ice: |ice|  리보그가 미끌어져서 다음 격자로 이동하게 한다. 만약 다음 격자에 장애물이 있다면, 문제가 될 소지가 있다. 얼음위에 서서 미끌어지기 전까지 얼음을 탐지할 수 없다.

|slip|

특수 객체
---------------

정규 객체처럼, 특수 객체는 배경 타일 위에 그려진다.
하지만, 리보그가 특수 객체를 집을 수는 없고, 타일에 대한 예상 행동을 변경할 수 있다.


:다리-bridge: |bridge|  다리를 통해, 리보그는 안전하게 물을 건널 수 있다. 물에 빠지는 대신에 다리를 건널 수 있음에 리보그는 항시 기쁨을 표시한다.
:담장-fences:  |fence_right| - |fence_left| - |fence_double| - |fence_vertical|
  리보그는 담장을 탐지할 수 있다.
  만약 리보그에게 담장을 옮겨 배치하게 명령하면, 리보그는 뛰어 넘으려고 해서 슬프게도 실패하게 된다.
  둘러싼 영역을 만들려면, 마지막 이미지와 다른 이미지 세개가 겹치게 만들어야 된다.
:상자-box: |box|  리보그는 상자를 밀어서 치울 수 있다... 하지만, 벽 혹은 다른 상자처럼 다른 것이 있다면,
  박스를 옮길 수 없게 된다. 리보그가 물에 박스를 밀어 넣으면, 박스가 뜨게 되어 다리가 되어서 안전하게 물을 건널 수 있게 한다. 박스를 밀어 다리로 만들어 물을 건너는 것이 아래 예제에 나와 있다.

|box-blocked|

목적지
----------

리보그는 최종 지점에 도착하거나 특정 지점에 특정 객체를 놓는 것처럼, 특정 목적을 완수할 수 있다.
객체 하나(혹은 그 이상)를 특정 지점에 놓아야 됨을 표기하기 하는데, 다음과 같은 회색 이미지가 사용된다.

|apple_goal| |banana_goal| |carrot_goal|
|daisy_goal| |dandelion_goal| |leaf_goal| |orange_goal|
|strawberry_goal| |tulip_goal| |square_goal| |star_goal|
|triangle_goal| |token_goal|

리보그가 정해진 최종 지점에서 작업을 끝마쳐야 됨을 표기하는데,
다음 이미지 중 하나가 사용된다.

|green_home_tile| |house| |racing_flag|


.. |green_home_tile| image:: ../../../src/images/green_home_tile.png
.. |house| image:: ../../../src/images/house.png
.. |racing_flag| image:: ../../../src/images/racing_flag.png

.. |apple| image:: ../../../src/images/apple.png
.. |banana| image:: ../../../src/images/banana.png
.. |carrot| image:: ../../../src/images/carrot.png
.. |daisy| image:: ../../../src/images/daisy.png
.. |dandelion| image:: ../../../src/images/dandelion.png
.. |leaf| image:: ../../../src/images/leaf.png
.. |orange| image:: ../../../src/images/orange.png
.. |strawberry| image:: ../../../src/images/strawberry.png
.. |tulip| image:: ../../../src/images/tulip.png
.. |square| image:: ../../../src/images/square.png
.. |star| image:: ../../../src/images/star.png
.. |triangle| image:: ../../../src/images/triangle.png
.. |impossible-triangle| image:: ../../images/impossible-triangle.png
.. |token| image:: ../../../src/images/token.png

.. |grass| image:: ../../../src/images/grass.png
.. |pale_grass| image:: ../../../src/images/pale_grass.png
.. |gravel| image:: ../../../src/images/gravel.png
.. |ice| image:: ../../../src/images/ice.png
.. |water| image:: ../../../src/images/water.png
.. |mud| image:: ../../../src/images/mud.png
.. |bricks| image:: ../../../src/images/bricks.png
.. |slip| image:: ../../images/ice_slip.gif

.. |bridge| image:: ../../../src/images/bridge.png
.. |box| image:: ../../../src/images/box.png
.. |fence_right| image:: ../../../src/images/fence_right.png
.. |fence_left| image:: ../../../src/images/fence_left.png
.. |fence_double| image:: ../../../src/images/fence_double.png
.. |fence_vertical| image:: ../../../src/images/fence_vertical.png
.. |box-blocked| image:: ../../images/box_blocked.gif

.. |apple_goal| image:: ../../../src/images/apple_goal.png
.. |banana_goal| image:: ../../../src/images/banana_goal.png
.. |carrot_goal| image:: ../../../src/images/carrot_goal.png
.. |daisy_goal| image:: ../../../src/images/daisy_goal.png
.. |dandelion_goal| image:: ../../../src/images/dandelion_goal.png
.. |leaf_goal| image:: ../../../src/images/leaf_goal.png
.. |orange_goal| image:: ../../../src/images/orange_goal.png
.. |strawberry_goal| image:: ../../../src/images/strawberry_goal.png
.. |tulip_goal| image:: ../../../src/images/tulip_goal.png
.. |square_goal| image:: ../../../src/images/square_goal.png
.. |star_goal| image:: ../../../src/images/star_goal.png
.. |triangle_goal| image:: ../../../src/images/triangle_goal.png
.. |token_goal| image:: ../../../src/images/token_goal.png
