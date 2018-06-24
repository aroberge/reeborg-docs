
Newspaper delivery
==================

Reeborg has a new job: he delivers the *Northern Star* newspaper. Many
of Reeborg's customers do not live on the ground floor of their
building. For each of these customers, Reeborg has to do the following

#. Pick up a single copy of the newspaper (it would be too heavy to
   carry them all up the stairs).
#. Climb up the required number of floors to reach the customer's door.
#. For some customiers, get the money (tokens) left by the customer.
#. Leave a copy of the newspaper (simply nicknamed the *star*) behind.
#. Climb down to the ground level

.. note::

    In computer programming, we generally start counting at zero instead of 1.
    Since these worlds refer to two famous
    people in computer science, I thought it would be appropriate to number these worlds starting at zero.

While Reeborg has many clients, I only included two with their
corresponding worlds:

-  Dr. Richard Pattis, creator of Karel (an ancestor of Reeborg);
   Reeborg always leaves a free copy of the newspaper at Pattis's home,
   so that Dr. Pattis has learned not to leave any money.
   This world is **Newspaper 0**.
-  The nice `Ada Lovelace <https://en.wikipedia.org/wiki/Ada_Lovelace>`__, who often leaves some extra tokens as a gift to
   Reeborg; hers is world **Newspaper 1**.


Writing programs for worlds containing two
types of objects (like a star **and** some
tokens) that can be found at the same place
is more complicated than what we have seen so far;
we will see how to do this later.  For now, let's
focus on world **Newspaper 0** which has only
one object.  Later we will learn how to teach
Reeborg to do deliveries in both worlds **Newspaper 0** and **Newspaper 1**.

.. topic:: Try it!

    Make Reeborg deliver a newspaper to Dr. Pattis.

.. important::

   Save your program; you will come back and use it again soon.
