Opérateurs de comparaison
=========================

Il est parfois utile de pouvoir comparer de objets. Voyons ceci avec des nombres.

.. topic:: Essayez ceci!

    .. code-block:: py3

        print("2 == 2 is", 2 == 2)  # est-ce que les deux nombres sont égaux?
        print("2 == 3 is", 2 == 3)

        print("2 != 2 is", 2 != 2)  # est-ce que les deux nombres sont différents?
        print("2 != 3 is", 2 != 3)

        print("2 < 3 is", 2 < 3)  # est-ce que le premier nombre est plus petit que le deuxième?
        print("3 < 2 is", 3 < 2)
        print("2 < 2 is", 2 < 2)

        print("2 > 3 is", 2 > 3)  # est-ce que le premier nombre est plus grand que le deuxième?
        print("3 > 2 is", 3 > 2)
        print("2 > 2 is", 2 > 2)

        print("2 <= 3 is", 2 <= 3)  # est-ce que le premier nombre est plus petit ou égal au deuxième?
        print("3 <= 2 is", 3 <= 2)
        print("2 <= 2 is", 2 <= 2)

        print("2 >= 3 is", 2 >= 3)  # est-ce que le premier nombre est plus grand ou égal au deuxième?
        print("3 >= 2 is", 3 >= 2)
        print("2 >= 2 is", 2 >= 2)

Ramasser les feuilles!
----------------------

Reeborg est enfin capable de ramasser les feuilles dans le monde spécial.

Exécutez le programme suivant::

    Monde("http://reeborg.ca/worlds/not_storm1.json",
          "Not Storm 1")

Comme vous le savez, ceci sélectionne un monde dans lequel Reeborg doit ramasser
un nombre inconnu de feuilles et les mettre à la poubelle tout cela 
sans utilser l'instruction ``transporte()``.

.. topic:: Ecrivez un programme pour faire cela!

	Faites compter à Reeborg le nombre de feuilles en utilisant par exemple
	une variable ``nombre_de_feuilles`` avec comme valeur de départ 0.
	
	Incrémentez cette valeur à chaque fois que Reeborg ramasse une feuille.
	
	Quand il est prêt à les mettre à la poubelle, vous pourriez utliser 
	quelque chose comme cela:

        .. code-block:: py3
	
            while nombre_de_feuilles > 0:
                # mettre une feuille à la poubelle
                
                # décrémenter la variable

