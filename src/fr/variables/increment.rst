Increment
=========

Choisissez le monde **Autour 1**.

Supposons que vous vouliez compter le nombre de pas que Reeborg
a fait pour arriver au mur de droite depuis sa position de départ. 
Une manière de faire cela est d'utiliser une variable que j'appele 
``nombre_de_pas`` et de lui donner une valeur initiale de 0.
Ensuite, à chaque fois que Reeborg fait un pas, j'ajoute 1 à la 
valeur précédente de ``nombre_de_pas``.

Facile?

Avant d'écrire un programme Python qui fait cela, faisons une expérience.

.. topic:: Essayez ceci!

    Exécutez le programme::

        n = 1
        n = n + 3
        print(n)

    Que voyez-vous?    Ensuite, exécutez ceci::

        a = a + 3
        print(a)

    Les résultats sont très différents, n'est-ce pas?



Comprendre les incréments
-------------------------

En programmation, l'action de changer la valeur d'une variable
telle que celle-ci augmente se nomme **incrémenter**.
Quand une variables diminue, on utilise le verbe **decrémenter**.

Souvenez-vous quand nous avons vu les variables et l'opérateur ``=``.
Une variable est un nom donné à un objet pour que l'on puisse
s'y référer en utilisant ce nom.
La syntaxe de base est::

    variable = objet

Un exemple que nous avons vu est::

    longueur = 4
    largeur = 6
    aire = longueur * largeur
    print(aire)  # imprimera 24

Pour savoir à quoi ``aire`` se réfère, Python doit 
remplacer les variables ``longueur`` et ``largeur`` par les objets
auxquelles elles se réfèrent::

    aire = 4 * 6

Cependant, ``4 * 6`` n'est toujours pas un objet: c'est le produit de deux objets.
Donc Python doit continuer son travail pour obtenir::

    aire = 24

Dans ce cas, nous avons vraiment une équation avec un nom (variable) 
à gauche de l'opérateur ``=`` et un objet (``24``) à droite.

Reprenons l'exemple précédent::

    n = 1
    n = n + 3

Quand la variable ``n`` apparaît des deux côtés de l'opérateur ``=``,
la logique ne change pas:

On cherche tout d'abord quel objet **seul** devrait être à droite et ensuite
on lui assigne un nom.

Donc la ligne de code::

    n = 1

informe Python qu'à chaque fois que l'on écrit ``n``, on veut dire ``1``.  
La prochaine ligne de code est::

    n = n + 3

Cela n'est très clairement pas une opération mathématique standard!
Souvenez-vous que nous venons juste de voir que l'opérateur ``=``
indique à Python qu'il doit assigner un nouveau nom à un objet.
Ici, l'objet est obtenu via::

    n + 3

Nous avons déjà informé Python que ``n`` se réfère à ``1``.
Donc  ``n + 3`` est en fait  ``1 + 3``. Python sait additionner deux
entiers et remplace la somme de deux entiers par un seul:  ``4``.

Donc ``n + 3`` se réfère à l'obje ``4``, et la ligne de code::

    n = n + 3

signifie::

    n = 4

Et cela peut être interprété comme par Python comme: quelque soit le
sens de ``n`` auparavant, oublie-le et à partir de maintenant cela signifie 
``4``.

Que dire de ``a = a + 3``? Python regarde d'abord à droite ``a + 3``,
trouve une variable ``a`` à laquelle aucun objet n'a été assignée 
donc il ne sait pas quoi faire avec et nous informe à l'aide
d'un messsage d'erreur.

.. topic:: Compter les pas

    Il est maintenant temps de faire compter à Reeborg le nombre 
    de pas pour arriver jusqu'au mur en face de lui dans le monde
    **Autour 1**.
    Essayez en premier le programme suivant::

        nombre_de_pas = 0

        while rien_devant():
            nombre_de_pas = nombre_de_pas + 1
            avancer()

        print(nombre_de_pas)

.. topic:: A vous

    Programmez Reeborg pour qu'il fasse le tour du monde **Autour 1**.
    Pendant son parcourt, Reeborg doit compter ses pas et le nombre de fois
    qu'il tourne à gauche.
    A la fin, celui-ci doit afficher ces informations.
    **Important**: faites ceci sans définir vos propres fonctions.

Opérateurs d'affectation augmentés
----------------------------------

.. index:: opérateurs affectation augmentés

.. index:: +=, -=, /=, *=, //=, **=

Dans les programmes Python, on doit souvent faire des opérations telles
que celle-ci::

    nombre_de_pas = nombre_de_pas + 1

ou::

    nombre_de_parts_de_pizza = nombre_de_parts_de_pizza - 2

Ceci est non seulement long à écrire mais cela ne respecte pas 
la troisième règle: **Ne vous répétez pas** car la même variable
est écrite **deux fois** sur la même ligne.
Il existe un moyen plus court d'écrire de telles lignes de code 
pour éviter les répétitions en utilisant ce que l'on appelle les 
**opérateurs d'affectation augmentés**.

Il est possible de réécrire les deux lignes précédentes ainsi::

    nombre_de_pas += 1
    nombre_de_parts_de_pizza -= 2

Pour chaque opérateur mathématique, ``+, -, /, //, *, **``, il existe
un opérateur d'affectation augmenté ``+=, -=, /=, //=, *=, **=``.

.. important::
   
   Quand on utilise les opérateurs d'affectations augmentés, il ne faut
   pas mettre d'espaces entre les différents symboles. Ecrivez  ``+=`` et non
   pas ``+  =``.

.. topic:: A votre tour

    Programmez Reeborg pour qu'il fasse le tour du monde **Autour 1**.
    Pendant son parcourt, Reeborg doit compter ses pas et le nombre de fois
    qu'il tourne à gauche.
    A la fin, celui-ci doit afficher ces informations.
    Cette fois-ci faites-le à l'aide des **opérateurs d'affectation augmentés**.


De retour à la tâche de rammasage de feuilles?
----------------------------------------------

A la fin de la leçon précédente, vous aviez une tâche que vous ne pouviez
pas réaliser car vous ne pouviez pas utiliser la fonction ``transporte()``.
Maintenant que vous savez compter le nombre de feuilles ramassées par
Reeborg, il vous manque encore deux concepts de programmation afin d'accomplir
cette tâche. Nous allons les aborder dans les deux prochains chapitres.


