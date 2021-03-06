Si seulement ...
================

Si seulement Reeborg pouvait prendre des décisions de lui-même, écrire
des programmes serait tellement plus simple ... **OUPS !** J'ai oublié
de vous le mentionner: Reeborg **peut** prendre ses propres décisions!


.. index:: ! if



Énoncé ``if``
----------------

``if`` est un mot anglais, qu'on peut traduire par "si" en français.
L'*énoncé* ``if`` suit un patron semblable à celui de ``def``::

    def un_nom():
        # bloc de code A

    if une_condition:
        # bloc de code B

Ce **bloc de code B** ne sera exécuté que si la condition est vérifiée, autrement
il sera traité comme s'il ne contenait aucune instruction.

Cependant, si l'exécution du programme faisait une *boucle*, 
et que cette partie du code était exécutée à nouveau, la condition
de l'énoncé ``if`` serait réévaluée à chaque fois pour décider
si le bloc de code B doit être exécuté ou non.


On peut représenter un énoncé ``if`` par un organigramme:

.. figure:: ../../flowcharts/if2.jpg
   :align: center


Python regarde si la condition se vérifie : si oui, il attribue le mot-clé ``True`` 
(se traduit par «vrai» en français) à l’instruction ``if`` et exécute le bloc d’instructions; 
sinon il lui attribue le mot-clé ``False`` (se traduit
par «faux» en français) et saute par-dessus le bloc d’instructions comme s’il n’était pas là.

Plus utile que vous ne le pensez...
-----------------------------------

.. index:: objet_ici(), termine()

.. note::

   Le terme général utilisé pour décrire une fonction
   donnant un résultat équivalent à ``True``
   ou ``False``
   dans un énoncé ``if`` est une **condition**::

       if condition:
           ...

Il existe des fonctions, utilisées comme des *conditions*, que
Reeborg reconnaît comme lui indiquant des décisions à prendre. Une de
ces fonctions est ``objet_ici()`` qui indique à Reeborg si un ou
plusieurs objets se trouvent aux coordonnées où Reeborg est situé. Par
exemple, si on demandait à Reeborg de collectionner des jetons, une
partie du code pourrait être::

    if objet_ici():
        prend()

Examinez à tour de rôle les mondes **Jetons 1** et **Jetons 2**. Dans chaque
cas, en supposant que Reeborg se déplace le long d'une ligne, tout ce
qu'il a à faire lorsqu'il trouve un jeton est:

#. prendre ce jeton
#. avancer d'une case
#. déposer ce jeton
#. avancer d'une autre case
#. et il ``termine()``

où j'ai introduit une nouvelle instruction que Reeborg comprend:
``termine()``, qui indique à Reeborg qu'il doit arrêter l'exécution.

Écrivons donc une esquisse d'un programme unique qui pourrait
permettre à Reeborg d'accomplir la tâche dans les deux mondes mentionnés
ci-dessus, soit **Jetons 1** et **Jetons 2**::

    def avance_jusque_tâche_terminée():
        avance()
        if objet_ici():
            # quelque chose
            # quelque chose d'autre
            # autre chose encore
            # une de plus
            termine()

    repeat 42:
        avance_jusque_tâche_terminée()

Pourquoi 42? ... Je n'ai pas de véritables raisons pour ce choix. Tout ce
que je veux est que Reeborg avance suffisamment de fois pour compléter
sa tâche peu importe la dimension du monde. Les deux mondes en question
sont suffisamment petits que de répéter 42 fois est plus que suffisant;
certains diraient même que c'est excessif. 
Si vous pensez la même chose, je suis d'accord avec vous, ceci
ne semble pas être une façon très intelligente de faire les choses ...
On fera mieux plus tard.


.. topic:: À votre tour!

    Copiez le code ci-dessus dans l'éditeur de code, ajoutez
    les instructions manquantes, et vérifiez que votre programme fonctionne
    dans les mondes **Jetons 1** et **Jetons 2**.

.. admonition:: Pour les enseignants

    La fonction ``objet_ici()`` retourne une liste des types d'objets
    trouvés à un endroit donné.  Par exemple, s'il y a des étoiles et
    des jetons, ``objet_ici()`` retournerait soit ``["étoile", "jeton"]``
    ou ``["jeton", "étoile"]``.  Si aucun objet n'est présent, une liste
    vide est retournée.  Comme vous le savez sans doute, Python considère
    une liste vide comme étant l'équivalent de ``False`` dans un énoncé
    ``if``, et une liste non vide comme étant l'équivalent de ``True``.

    Si plusieurs objets pouvaient se trouver dans un monde donné
    et qu'on ne s'intéresse qu'à un seul type d'objet, on peut spécifier
    le type en utilisant un argument::

        if objet_ici("jeton"):
            prend("jeton")

    S'il y a un ou des jetons présents, la fonction retournera la liste
    ``["jeton"]``; sinon, elle retournera une liste vide.
