Exercice de lecture
-------------------

Vous souvenez-vous de ce qui suit?

.. important::

    **Règle numéro 2**

        Écrivez vos programmes pour qu'ils soient faciles à lire et à comprendre
        par des **humains**.

Pouvez-vous déterminez ce que fait le programme suivant, simplement
en le lisant et sans l'exécuter?

.. code-block:: py3

    def a():
        tourne_a_gauche()
        tourne_a_gauche()

    def b():
        tourne_a_gauche()
        a()

    def c():
        avance()
        avance()

    def d():
        c()
        b()

    def e():
        d()
        d()
        d()
        d()

    tourne_a_gauche()
    e()
    b()

Pas vraiment facile, n'est-ce pas?

.. topic:: Vérifiez!

    Lorsque vous serez convaincu de savoir ce que fait le programme ci-dessus,
    vérifiez votre compréhension en l'exécutant.


Cet exercice devrait vous aider à mieux comprendre pourquoi il est utile
d'écrire des programmes en utilisant des fonctions avec des noms
bien choisis.
