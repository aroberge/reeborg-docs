Listes
=======

Exécutez le programme suivant, une première fois pour sélectionner
le monde puis une deuxième fois pour exécuter le reste du
programme.

.. code-block:: python3

    Monde("http://reeborg.ca/worlds/old_examples/many.json", "Many")
    avance()
    print(objet_ici())

Le résultat devrait ressembler à ceci::

    ['jeton', 'triangle', 'banane', 'carotte']

.. note::

    Il existe également une fonction qui s'appelle ``list()`` qui permet de
    créer des listes. Vous avez vu que l'on peut utiliser l'instruction ``=``
    pour assigner un nom à un objet, par exemple ``ma_liste=list()``.
    Il ne faut pas utiliser ``list`` comme nom de variable, ceci 
    empêcherait ensuite d'utiliser la fonction ``list()`` que propose Python.


Ceci est un exemple de **liste** en Python.

Une liste Python est représentée par des corchets ``[ ]``,
qui contiennent zéro, un ou plusieurs éléments.

Dans l'exemple ci-dessus, la liste contient 4 éléments, chacun étant 
une chaîne de caractères.

A l'aide de la "notation crochets", on peut créer une liste contenant 
des objets de types différents::

    une_list = [1, "Reeborg", avance]

Accéder aux éléments de la liste
--------------------------------

Lorsque vous avez vu le premier exercice de livraison de journaux, vous avez lu ceci:

    En programmation, on commence généralement à compter à partir de 0 plutôt que 1.
    Comme ces mondes se réfèrent à 3 informaticiens célèbres, j'ai pensé 
    qu'il serait approprié de numéroter ces mondes à partir de 0.

Etant donnée une liste, il est posssible d'obtenir des éléments de cette liste
à l'aide de la notation avec crochets.

.. topic:: Essayez ceci!

	Essayez le programme suivant:

    .. code-block:: python3
    
        nbres_impairs = [1, 3, 5, 7]
        print( nbres_impairs[0] )
        print( nbres_impairs[1] )
        print( nbres_impairs[3] )
        print( "length = ", len(nbres_impairs))

    En Python, la fonction ``len()`` nous donne la longueur d'une liste, c'est-à-dire
    le nombres d'éléments de cette liste.
    
    Le nombre entre crochets qui est utilisé pour obtenir un élément de la liste
    s'appelle **l'index** de cet élément.
    
Il est parfois utile d'obtenir le dernier élément d'une liste, ou l'avant-dernier.
Il serait possible d'utiliser la fonction ``len()`` pour trouver la position 
du dernier élément dans la liste. Mais Python a un racourci pour faire ceci.

.. topic:: Essayez ceci!

    Essayez le programme suivant:

	.. code-block:: python3
		
	    nbres_impairs = [1, 3, 5, 7]
	    print( nbres_impairs[-1] )  # dernier élément
	    print( nbres_impairs[-2] )  # avant-dernier élément

	Notez l'utilisation du signe moins pour récupérer les éléments depuis
	la fin de la liste.
	
Utiliser les listes comme conditions
------------------------------------

Quand elles sont utilisées comme conditions dans une construction ``if`` 
ou ``while``, les listes se comportent différemment selon qu'elles sont
vide ou non.

.. topic:: Que se passe-t-il?

	Exécuter le programme suivant:

	.. code-block:: python3
		
	    # Seule l'un de ces affimations est correcte
	    
	    if []:
	    	print("Une liste vide est considérée comme True.")
	    elif ['Reeborg']:
	    	print("Une liste vide est considérée comme False.")
	    	print("Et une liste non vide comme True.")
	    elif [1, 2, 3, 4, 5]:
	    	print("Une liste est considérée comme True",
	    		"SEULEMENT si elle contient plusieurs éléments.")
	    else:
	    	print("Peut-être que les listes sont toujours considérées comme False ...")

	Comme vous le savez, les branches qui contiennent une condition considérée comme
	``False`` sont ignorées; la première branche qui contient une condition ``True``
	est celle qui sera exécutée.


D'autres défis de récolte
--------------------------

.. topic:: Tout d'abord, un test rapide
	
	Exécutez le programme suivant, qui affiche le premier type d'objet trouvé
	par Reeborg. Changez ensuite le programme pour afficher le deuxième type
	d'objet trouvé.
	
    .. code-block:: python3

        Monde("http://reeborg.ca/worlds/old_examples/many.json", "Many")
        avance()
        print(objet_ici()[0])

La tante de Reeborg est maréchère. Dans ses champs, on trouve
différents types de fruits. Chaque jour, seuls un certain type de fruit
doit être récolté.

Regardez les mondes **Récolte 4a**, **Récolte 4b**, **Récolte 4c** et **Récolte 4d**.
Quand il entre sur le champs, Reeborg voit le type de fruit qu'il doit 
récolter. Sa tante en a mis un exemplaire pour lui. Il le prend et va 
ramasser tous les fruits de ce type.

Reeborg utilise la fonction ``objet_ici()``, qui, comme nous l'avons
vu, retourne une **liste** contenant le nom des objets trouvé à cet endroit.
Pour les mondes **Récolte 4**, les objets possibles sont
``pomme``, ``banane``, ``orange`` ou ``fraise``.

Vous trouverez ci-dessous un programme incomplet qui devrait permettre
à Reeborg d'effcetuer sa récolte dans les 4 mondes mentionnés.
Nous utilisons la variable ``FRUIT`` écrite en majuscules car c'est une
variable utilisée à l'intétieur et à l'extérieur des fonctions: c'est
une variable **globale**.
Cependant, comme nous ne lui associons **pas** de valeur à l'intérieur des 
fonctions avec le signe ``=``, nous n'avons pas besoin de 
l'instruction ``global``.

.. code-block:: py3

    def recolte_une_ligne ():
        while rien_devant():
            if objet_ici():
                if objet_ici()[0] == FRUIT:
                    prend(FRUIT)
            avance()

    def retourne_debut_ligne():
        pass

    def avance_prochaine_ligne():
        pass

    def aller_premiere_ligne():
        pass

    def recolte_une_ligne():
        recolte_une_ligne()
        retourne_debut_ligne()
        avance_prochaine_ligne()

    avance()
    FRUIT = objet_ici()[0]
    prend(FRUIT)
    aller_premiere_ligne()
    repeat 6:
        recolte_une_ligne()


.. topic:: A votre tour!

	Complétez le programme afin qu'il fonctionne dans les
	4 mondes. 
	
Une dernière expérience
-----------------------

Parfois, quand un programme devient trop gros, cela donne
du sens de le séparer en plusieurs fichiers.
Jusqu'à présent, vos programmes ne sont pas dans des fichiers:
ils sont dans l'éditeur et également dans la bibliothèque.

Imaginez que votre programme est si grand qu'il doit être séparé en deux.
Déplacez la définition de la fonction ``recolte_une_ligne()`` dans la bibliothèque.
Imagine that your program above is so big that it has to be broken up
et importez-là dans le programme principal en utilisant

.. code-block:: py3

    from library import recolte_une_ligne

Votre programme fonctionne-t-il toujours? Est-ce que l'utilisation de 
l'instruction ``global`` le fait fonctionner?

Le résultat de cette expérience vous montre qu'il peut y avoir
des problèmes lorsque l'on utilise des variables globales qui sont
utilisées dans une fonction mais qui sont définies ailleurs.

Ressources supplémentaires
--------------------------

Rendez-vous à l'adresse https://cscircles.cemc.uwaterloo.ca/13-fr/ pour 
quelques explications et exercices supplémentaires.

Puis https://cscircles.cemc.uwaterloo.ca/14-fr/

Et puis https://cscircles.cemc.uwaterloo.ca/17-fr/
