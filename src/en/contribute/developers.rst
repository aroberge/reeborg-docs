Information for developers
==========================

Reeborg's World code is on Github
https://github.com/aroberge/reeborg

.. warning::

    **The code is in a state of constant flux.**  My goal is to make Reeborg's
    World as useful as possible to both learners **and** educators: too
    often I find that sites/tools designed to "teach" programming follow
    a prescriptive approach with a constrained "learning path" that leaves
    very little flexibility to students ... and as to be used "as is" by
    educators.   I try to follow almost the opposite approach.  When I am
    contacted by educators who would like to do X, I try to find a way to
    enable them to do so if it does not already exist.  As a result, new
    features get constantly added and pushed to the site almost immediately.

    Before you do any serious work on it,
    you might want to get in touch with me to make sure that the information
    given here is really up to date.




.. topic:: There are no traditional unit tests

   However, there are some quasi-unit tests run from within the browser
   (using QUnit) and a few fairly comprehensive integration tests.
   To see one of these, run thefollowing::

       World("/test/worlds/main_py_en.json")


The main html file is https://github.com/aroberge/reeborg/blob/master/world.html

By commenting/uncommenting some lines, you can change it so that it can work
without any Internet access, using local version of files instead of CDN ones.
If you look at the source, it should be obvious which ones need to be changed.

.. todo::

    In addition to the English world.html, there is a French one (monde.html)
    and a Korean one (world_ko.html).  I am currently planning to create
    a single file with a language selector allowing to switch from one language
    version to another without reloading the page.

    As part of this planned change, I would like to automate the build and
    create a separate version that could run offline.



The main Javascript files are in
https://github.com/aroberge/reeborg/tree/master/src/js
The code is split up in various files,
which are then concanetated into a single
one (https://github.com/aroberge/reeborg/blob/master/src/js/reeborg_dev.js)
which is the one loaded by the html file.  This concatenation is done using
a Windows batch file (combine_js.bat).  I have not found the need
to write a cross-platform solution (using a Python script) to do this.

.. todo::

    I am planning to change this and use browserify, and mostly getting rid
    of the global RUR namespace.


Note that no minification is done.  My original motivation was to make
it easier to explore the code.  For example, in Reeborg's World,
select **Javascript** as a
programming language and run the following program::

    view_source_js(RUR.control.turn_left)

You will see the code of that function extracted from the source and
inserted into a CodeMirror instance with formatting intact.
If you attempt to do the same from Python, you will see some Javascript
code translated by Brython ... which will be less than useful.

.. todo::

    This will likely change when using browserify; however, apparently
    CodeMirror has a plugin that makes it possible to format the code;
    I plan to explore using this plugin when invoking `view_source_js`
    which would allow me to minify the code while making it possible for
    people to still view a readable version of the code.

Human-language specific Javascript files are found in
https://github.com/aroberge/reeborg/tree/master/src/lang

If you work with Python, use the javascript console in the browser
and define::

    RUR.__debug = any_value   # I suggest to use false

As a result, the modified version of the user's program,
including the highlighting information will be printed to the console;
this could be helpful if errors occur when highlighting is turned on,
but not if it is turned off.

If ``RUR.__debug`` is set to any ``true`` value, additional information
is printed to the Javascript console.  I use this occasionnally if I want
to roughly "trace" a program's execution, to help find an error.

The information given above is probably enough to get you started.
Please feel free to contact me if you have any questions.

Conventions used
----------------

Four spaces should normally be used for indentation.
Note that some javascript files may be using two spaces;
when refactoring code, you should change this for
the functions you are working on.


Currently, there is support for programming using Python, Javascript and
using a Blockly interface, in both French and English.
Consider the ``move()`` instruction.  When called in a user program,
it will invoke a function (currently ``RUR.control.move()``) which
is rather complicated (nearly 100 lines of code) as it must check if
a move is allowed (*is there an object blocking the way? etc.*).
Suppose I find that I need to refactor the code (which I have done many
times) with the result that this function would have a different
name (perhaps something like ``RUR.instructions.move()``) or be invoked
with different (hidden) arguments.  Suppose I defined
the end-user Python version of that instruction as follows::

    def move():
        """Move forward, by one grid position."""
        RUR.control.move(RUR.current_world.robots[0])

with similar definitions for the Javascript version, the Blockly versions
(both Python and Javascript), I would have to make a name change in 4
different location for the English version.  Four more similar changes would
have to be made for the French version ... and 4 more each for each new
(human) language version.  To avoid having to do all these changes, I have
created an "interface" (currently in commands.js) as follows::

    RUR._move_ = function () {
        RUR.control.move(RUR.current_world.robots[0]);
    };

and then have::

    def move():
        """Move forward, by one grid position."""
        RUR._move_()

This way, I can change/refactor the "back end" without requiring changing
the various versions used in end-user programs.


.. todo::

    I have been working on a set of tools to facilitate translations into other
    (human) languages.  These tools will also make it easier to compare different
    language versions without requiring to have the functions/methods appearing
    in the same order in different files as it is currently the case if one wants
    to use a diff program to compare versions.
