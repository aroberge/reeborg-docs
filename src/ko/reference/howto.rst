고급 기능
==================

리보그 세상은 프로그래밍 작업 환경을 설정하기 쉽게 설계되어서 학생에게 자동화된 피드백을 제공할 수 있다.
하지만, 때때로, 부가적인 사용자 설정을 원할 수도 있다.
다양한 가능성을 이번 페이지에서 문서화하는데, 일부는 이미 어딘가에서 언급된 것이다.

단순한 작업
-----------------

먼저, 단순한 작업을 생각해 보자. 다음 세상을 적재한다::

    World("Demo 1")

완수해야 되는 초기 작업 시작은 다음과 같다:

|simple_demo1|

.. |simple_demo1| image:: ../../images/simple_demo1.png

그리고 최종 결과는 다음과 같다:

|simple_demo1f|

.. |simple_demo1f| image:: ../../images/simple_demo1f.png

상기 실행결과를 편집기에 코드 **그리고** 라이브러리에 코드를 포함하는 permalink로 저장한다.


다른 궤적: 스타일
------------------------

기본 디폴트 설정으로, 리보그는 약간 "중심에서 벗어난" 궤적을 남긴다.
따라서, 좌회전과 우회전(좌회전 3회 수행) 사이에 분명한 차이가 보인다.
아마도 우회전에 좌회전 3번 한 것이라는 것에는 관심이 없고, 
리보그가 지나간 궤적만 보고 싶을 수도 있다;
이 작업은 다음 코드를 사용해서 수행된다::

    set_trace_style("thick")

결과는 다음과 같아 보일 것이다:

|simple_demo2|

.. |simple_demo2| image:: ../../images/simple_demo2.png


대안으로, 궤적을 뒤에 남기 않고, 로봇이 작업을 수행하는 것만 보고자 한다고 가정한다.
이 작업에는 "think" 대신에 "none"을 사용한다. (정상적인 경우는 "default"가 되고, 자동으로 원복된다.)

.. important::

    ``"thick"`` 혹은 ``"default"`` 값을 갖는 ``set_trace_style`` 함수는 전역 함수로
    모든 로봇 궤적에 영향을 미친다. 프로그램 내부에서 여러번 함수를 호출하면, 
    가장 마지막 호출된 것만 영향을 미친다.

    ``"none"`` 값이 선택되면, 퀘적은 덮어쓸 수 있는 완전히 투명한 색으로 칠해진다.
    아래에서 보듯이, 로봇은 다른 색 궤적을 가질 수 있다.

다른 궤적: 색깔
------------------------

다른 로봇은 다른 궤적 색깔을 갖게 하거나, 프로그램 내에서 어느 시점이든지 뒤에 남긴 궤적
색깔을 변경할 수도 있다. 다음 세상을 적재해서 해당 예제를 살펴본다::

    World("Demo 2")

``set_trace_color()`` 인자로 사용되는 
적법한 색깔 명칭에는 html 색깔, RGB 값, RGBA 값이 포함된다 - 나중에 나온 값이
궤적을 임시로 보이지 않게 만드는데 유용하다.

|simple_demo2b|

.. |simple_demo2b| image:: ../../images/simple_demo2b.png


다양한 로봇 모형
----------------------

기본 설계로, 로봇 모형 선택은 사용자에게 맡겨졌다.
사용자는 세상 상단에 이미지 버튼을 클릭해서 로봇 모형을 고를 수 있다.

|models|

.. |models| image:: ../../images/models.png

모든 로봇은 동일한 모형이 된다.
하지만, 로봇을 생성할 때, 특정 모형을 다음 명령어를 사용해서 지정할 수 있다::

    reeborg = UsedRobot()
    reeborg.set_model(0)

다음 예제에서 앞에서 언급된 점을 시연하고 있다::

    World("Demo 2")


무작위 세상
--------------

세상을 설계하는 것도 가능한데, 
로봇 초기 위치가 명세된 선택지에서 무작위로 선택된다;
이번 예제에서, 다소 투명한 이미지가 가능한 모든 지점에 처음에 나타난다.

유사하게, 특정 지점에서 발견할 수 있는 객체 숫자에 대해 범위 내에서 가능한 값을 지정하는 것도 가능하다.
만약 이런 작업이 수행되면,
특정 유형의 모든 객체를 해당 지점에 놓도록 지시하는 것도 가능하게 된다.
이런 경우에, 세상이 그려질 때, 물음표가 처음에 객체 숫자 옆에 나타난다.
프로그램 첫번째 단계가 실행된 후에, 각각에 특정한 값이 나타나게 된다.

마지막으로, 로봇의 최종 지점을 주어진 집합에서 고르는 것도 가능하다.

이 모든 것이 다음 예제에 시연되어 있다::

    World("Demo 3")

|simple_demo3|

.. |simple_demo3| image:: ../../images/simple_demo3.png


Adding code to be run in addition to user's program
----------------------------------------------------

When editing the world, you can add a extra code that will be run
either before the user's program is run, or after it is run, or both.


.. warning::

   A word of caution: if you include *post* code and the user
   include the instruction ``done()`` in their program, the
   post code will never be reached when ``done()`` is executed.
   In this case, a good strategy is to redefine ``done()``
   in the **pre** code part, perhaps replacing it with
   something like this::

        def done():
            raise ReeborgError("You are not allowed to use 'done()'.")

|pre_post_code|

.. |pre_post_code| image:: ../../images/pre_post_code.png

You can see a very simple example of this by selecting the world
**Pre & Post code demo**
and then run the resulting program, which simply
insert a print statement before and another one after the
program in the editor.  A **much** longer example,
illustrating the usage of ``narration()`` is the world **Story**.
This program adds a "twist" to the story, simply
included for effect: make sure to let the program
run to the end.


Replacing the default robot
---------------------------

Suppose you want to use a robot that can has enhanced capabilities in
one of your examples while using an existing world.
For instance, suppose I want to show a solution to jumping over the
hurdle with a robot that can turn right directly, without doing three left turns.
One "obvious" way might be as follows:

1. Create a copy of the desired world.
2. Remove the robot
3. Save the world under a different name
   (if using the same browser to show the example) or a usb key
   (and load it in a different browser, if planning the work at home
   and using it in the classroom)
4. Write a program that first creates a robot with the desired attributes.

This approach would work ... except that the world initially shown will
not have any robot visible and would thus be different than what the
students would see when they would attempt to work on it with their robot.

There is a better way!

.. note::

   By using this code in the "pre" code, or in the library, we ensure that
   the line executed is not "highlighted" and have a frame with no robot
   present.

Either in the "pre" code, or in the library you can use the instruction::

   RUR.world.remove_robots()

as the very first instruction in your program, and
then create an instance of your robot with the desired enhanced capabilities.
Since there will be only one robot in the world,
basic instruction like ``move()` or ``turn_left()``
will work on your robot as-is: by design,
they work with the first robot created without requiring the instance name.

Have a look at the world **Robot replacement**
to see an example where a new robot, capable of turning right directly,
is defined in the library and replaces the default robot.

Easy collaboration with TogetherJS
----------------------------------

From **Additional menu** at the top, you can find the button
"Collaboration": this activates Mozilla's TogetherJS which allows two, or
more, users to effectively interact on the same webpage.

Stepping back and forth through program execution
--------------------------------------------------

Programs are executed in two steps: first, the program is run
and a series of "frames", representing the complete state of
the world at that time, are recorded.  Second, these frames
are played back one at a time.

From the **Additional menu**, one has access to a "step back"
button which steps backwards, one frame at a time, instead of
forward.

An example of such use might be to run a program quickly,
by setting ``think(0)`` up to a "crucial" point at which
the program is paused using ``pause()``.  From that point on,
the program could be run either forward or backward, one frame at a time,
allowing to focus on one particular aspect being demonstrated.

Easy support for multiple human languages
-----------------------------------------

As mentioned elsewhere, it is fairly straightforward to
port Reeborg's World so that languages other than English
can be used.  Currently, only French is completely supported.
Thus, one can write::

    from reeborg_fr import *

    avance()           # equivalent to move()
    tourne_a_gauche()  # equivalent to turn_left()

However, French users should use http://reeborg.ca/monde.html
which has a French User Interface.

Using Python's standard library
-------------------------------------------------

Brython comes with a significant portion of Python's standard
library; however only pure Python modules are supported.


Possibility to write programs using different languages
-------------------------------------------------------

Support for Python, Javascript and CoffeeScript.  Other languages
could be supported as well if they have a javascript transpiler.

Embedding in an iframe
----------------------

.. todo::

    It is possible to embed Reeborg's World in a different website
    using an html ``iframe``.  I need to explain how to do this.

Possibility to integrate within a Learning Management System
------------------------------------------------------------

One teacher in Lithuania has made Reeborg's World accessible within Moodle
for students tasks that are then marked automatically.  Ideally, such use
should be made with local copies of Reeborg's World.

.. _changing-the-user-interface:

Changing the User Interface
---------------------------

If you know Javascript, html and css, and possibly how to use the jQuery library,
you can customize the look of Reeborg's World by running code
with a specially crafted permalink; the changes made will
remain until the site is reloaded.

If you want to make your own changes, you might want to
open Reeborg's World into a separate tab and enable the javascript console.
Then, use Javascript/jQuery commands in the console to change the UI as desired.
Copy **all** of your required code (not forgetting semi-colons...) into the textarea below.

For example, suppose you wanted to hide the choice of programming
language selection; you could do so using the following jQuery code:

.. code-block:: javascript

    $("#header-child form").hide();

You can use the above as an example and copy it into the textarea below
and then click the "Create permalink code" button; the result will
appear below the button.  Note that you need to create all the UI
changes into a single conversion.  Once you have the result, copy it
and *append it* to a "normal" permalink created within Reeborg's
World; your new permalink, when used to update Reeborg's world,
will make the required changes to the UI.


.. raw:: html
   :file: css_mod.html

If you need help with making changes to the User Interface, please do not hesitate to contact me.
