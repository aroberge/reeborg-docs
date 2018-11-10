If only ...
===========

If only Reeborg could decide on its own, writing programs would be much
simpler ... **WAIT !** Didn't I tell you: Reeborg can make decisions on
its own.


.. index:: ! if


``if`` statement
----------------

The so-called ``if`` **statement** follows a pattern somewhat similar to
that of ``function``\ s :

.. code-block:: python

    def some_name():
        # block of code A

    if some_condition:
        # block of code B


That block of code B will be performed if the condition happens to be true, 
otherwise simply ignored as if it were deleted.

It does not mean that such a deletion would be done permanently: 
if, somehow, our program *looped back* and repeated this part of the code again, 
the ``if`` statement would be reevaluated each time to decide whether or not to execute the lines of
code inside the code block B.


We can represent this description using a flowchart:

.. figure:: ../../flowcharts/if.jpg
   :align: center

There are special functions, used as *conditions*, that Reeborg recognizes
that allow to decide things for himself. The first of these is
``object_here()`` which tells Reeborg that there is at least one object at
the grid position where he is located. For example, if we want to ask
Reeborg to collect tokens, one part of the code could be::

    if object_here():
        take()

Have a look at worlds **Tokens 1** and **Tokens 2**. In both cases, and assuming
that Reeborg moves forward in a straight line, when he finds a token,
all he as to do is:

#. take it
#. move to the next grid
#. put the token down
#. move one more step
#. and he is ``done()``

where I have introduced a new command that Reeborg understands:
``done()``. Actually, you should think of this command as Reeborg saying
it himself and declaring that he has finished.

Let's write the outline of a program that will work in both worlds
**Tokens 1** and **Tokens 2**::

    def move_until_done():
        move()
        if object_here():
            # something
            # something else
            # something else again
            # yet one more
            done()

    repeat 42:
        move_until_done()


Why 42? ... well, I just want to be sure that Reeborg will take enough
steps no matter what world he is in. So far, all the worlds are small
enough that this should be fine. I agree, it does not seem very smart; we'll see how to fix that later.

.. topic:: Try it!

    Copy the above in the Code editor, filling in the missing
    commands, and test your program on both worlds **Tokens 1** and **Tokens 2**.

.. admonition:: For educators

    The function ``object_here()`` returns a list of object types (as strings)
    found at a given location.  For example, if there are stars and tokens
    at the same location, ``object_here()`` could return ``["star", "token"]``
    or ``["token", "star"]``. If no object is present, an empty list is
    returned.  As you likely already know, Python treats an empty list as
    being equivalent to ``False`` in an ``if`` statement, and a non-empty
    list as equivalent to ``True``.

    If many objects could potentially be found in a given world, and we
    are interested in only one object type, we can specify it as a function
    argument::

        if object_here("token"):
            take("token")

    ``object_here("token")`` will either return an empty list or the list
    ``["token"]``.
