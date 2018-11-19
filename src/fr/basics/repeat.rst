Répète
======

.. index:: repeat

Comme nous l'avons vu, il arrive souvent que l'on doive répéter une
instruction donnée un certain nombre de fois. Il y a une façon standard
de faire cela en Python ... mais cela requiert de comprendre trop de
nouveaux concepts à la fois. Je vais juste vous montrer le code requis
pour ceci puis présenter un mot clé plus simple à comprendre,
``repeat``, unique au monde de Reeborg.

La façon standard s'appelle une *boucle* ``for``
et est écrite de la façon suivante::

    for _ in range(n):
        # diverses
        # instructions
        # ici


.. note::

   Si vous écrivez des programmes Python ailleurs que dans le Monde
   de Reeborg, ``repeat`` ne sera pas reconnu comme étant un nom valide.
   ``repeat`` est un mot anglais qu'on pourrait traduire en français
   par **répète**.  Le mot "boucle" désigne un bloc d'instructions
   qui sera peut-être répété plusieurs fois.

Dans le monde de Reeborg, on peut écrire une *boucle* ``repeat``
de la façon suivante::

    repeat n:    # "n" est un nombre entier
        # diverses
        # instructions
        # ici


Par exemple, le code suivant ferait en sorte que Reeborg dessine
un carré::

    repeat 4:
        avance()
        tourne_a_gauche()


En utilisant ``repeat`` on peut récrire certains fonctions
sans avoir à répéter des instructions, comme par exemple::

    def tourne_a_droite():
        repeat 3:
            tourne_a_gauche()


.. topic:: À votre tour!

    Si vous avez toujours dans l'éditeur de code une copie
    du programme permettant à Reeborg de livrer le journal à Monsieur Pattis,
    modifiez-le de façon à utiliser une boucle ``repeat``
    à toutes les fois que ceci permet de raccourcir le code.


.. admonition:: Pour les enseignants

    Comme ce tutoriel reporte à plus tard l'introduction du concept
    de variables ainsi que de l'utilisation d'arguments de fonctions,
    j'ai jugé préférable de modifier la syntaxe traditionnelle de Python
    en ajoutant le mot-clé ``repeat`` pour éviter d'introduire quatre
    concepts différents en même temps (soit en plus des boucles,
    les variables comme la variable ``_`` dans ``for _ in range(n)``,
    les fonctions "builtin" comme ``range``,
    ainsi que le concept d'arguments de fonction).

    J'ai choisi de façon intentionnelle d'obliger que ``n`` dans
    l'expression ``repeat n`` soit absolument un entier sous forme
    de chiffre et non sous forme de variable.  Lorsque les étudiants
    apprennent ce qu'est une variable, et qu'ils veulent l'utiliser
    dans les boucles, ils devraient apprendre la véritable syntaxe
    Python et oublier la notation ``repeat`` qui ne sera pas
    reconnue par Python.
