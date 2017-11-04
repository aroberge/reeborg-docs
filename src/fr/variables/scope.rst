Portée: local vs global
=======================

Voici un petit rappel.

.. important::

    Régle # 1
        Apprendre la programmation informatique est comme apprendre à jouer 
        d’un instrument de musique: il faut le faire et non pas se contenter 
        de lire à ce sujet.

Maintenant que j'ai votre attention, il est important que vous essayez 
ces programmes sans lire plus loin.

.. topic:: Excécutez ces programmes

    Comencez par celui-ci::

        # Premier programme
        a = 2

        def test():
            a = 3
            print("intérieur de test: ", a)

        test()

    Ensuite celui-ci::

        # Deuxième programme
        a = 2

        def test():
            print("intérieur de test", a)

        test()
        print("après test", a)

    Et encore::

        # Troisième programme
        a = 2

        def test():
            a = 3
            print("intérieur de test", a)

        test()
        print("Après test", a)

    Et pour finir::

        # Quatrième programme
        a = 2

        def test():
            global a
            a = 3
            print("intérieur de test", a)

        test()
        print("après test", a)


Que se passe-t-il? ...

Besoin de la portée
-------------------

.. index:: portée
.. index:: ! global


Au moment où j'écris ceci, le fichier du programme principal écrit en Javascript
qui implémente le monde de Reeborg, https://github.com/aroberge/reeborg/blob/master/src/js/reeborg_dev.js, 
contient environ 16000 lignes de code: C'est un peu plus que ce que vous avez écrit jusqu'à présent !
Quand les gens travaillent en collaboration, ils écrivent des programmes
qui contiennet des centaines de milliers de lignes de code. Comme vous pouvez vous l'imaginer, 
il est impossible il est impossible de trouver des noms de variables qui gardent 
le même sens durant tout le programme.

Imaginez que vous collaborez pour écrire un très, très long programme. Si je 
définis une variable ``longueur`` égale à ``32`` et vous définissez la même variable
avec le même nom ailleurs avec la valeur ``45``, nous risquons d'avoir un problème
en utilisant ces variables.

Python et la pluparts des langages de programmation ont une solution pour ce genre
de problème: les variables qui sont définies à l'intérieur d'une fonction
ne sont connues qu'à l'intérieur de cette fonction. Donc si **vous** définissez une
variable ``longueur`` et que **je** définis dans une autre fonction une variable
``longueur``, celles-ci seront traitées comme deux variables différentes par Python.

On dira que ces variables sont **locales** à la fonction ou qu'elles ont 
une portée locale.

Regardons le premier programme ci-dessus. On définie une variable nommée 
``a`` à l'intérieur de la fonction ``test()``. Cette variable est considérée 
comme **locale** pour cette fonction. Lui donner une valeur n'affecte
pas la valeur de la variable ``a`` **en dehors** de la fonction. Les
deux variables sont considérées comme différentes.

Dans le second programme, on ne définie pas de variable ``a`` à l'intérieur 
de la fonction ``test()``, c'est-à-dire que nous avons pas quelque chose
du type::

   a = qqc

à l'intérieur de la fonction. Lorsque l'on affiche (``print``)
la valeur de la variable, Python reconnait que c'est une variable
qui a sûrement été définie en dehors de la fonction (une variable dite
**globale** ou de **portée globale**) et il regarde dans son environnement
global s'il trouve une variable avec ce nom et l'utilise.

.. note::

    Croyez-le ou non, la description ici est une simplication de la
    réalité. Il y a une autre instruction Python ``nonlocal`` qui 
    se réfère à une portée entre **local** et **global** !
    Mais en écrivant ce tutoriel, je n'ai pas trouvé d'exemple pertinent
    pour illustrer cette notion dans le monde de Reeborg.

Dans le troisième programme, Python trouve une variable ``a`` localeà la fonction
(donc définie à l'întérieur de la fonction) car il y a une ligne::

    a = qqc   # avec qqc égal à 3 ici...

Alors Python détermine qu'à l'intérieur de la fonction ``a`` se 
réfère toujours à la variable **locale**. Comme on essaye d'afficher (``print``)
sa valeur avant que celle-ci ne soit assignée (définie), Python nous
informe, à sa manière, qu'il ne peut pas le faire.

Enfin, dans le quatrième programme, on a ajouté la ligne::

    global a

``global`` est une instruction Python qui l'informe que la variable
``a`` qui est utilisée **à l'intérieur** de la fonction est la 
même que celle qui est définie **à l'extérieur** de la fonction 
(dans l'environnement **global**).

Donc la variable ``a`` a une valeur connue quand la ligne ::

    print("intérieur de test", a)

est exécutée. La ligne suivante, ``a = 3``, change la valeur de
``a`` si bien qu'après l'exécution de ``test()``, ``a`` a 
partout une nouvelle valeur.

.. important::

	Quand un programmeur expérimenté voit une fonction dans
	laquelle une ou plusieurs variables sont précédées du l'instruction
	``global``, celui-ci commence à s'inquiéter.
	Au lieu d'essayer de comprendre la fonction, le programmeur cherche
	où des valeurs sont assignées à ces variables et comment cela
	va affecter comment la fonction va fonctionner.

    Pour cette raison, un programmeur expérimenté essaye toujours
    d'utiliser d'autres outils (que vous ne connaissez pas encore) afin 
    d'éviter de devoir utiliser des variables globales.
    Il est cependant important de savoir comment utiliser des variables globales
    et surtout de savoir **quand** elles sont indispensables.

Perturbé?
---------

Beaucoup de gens trouve le concept de **portée** perturbant au premier abord.
Prenez du temps à excéter les quatre programmes pour bien comprendre
ce qui se passe.

Ressources supplémentaires
--------------------------

Rendez-vous à l'adresse https://cscircles.cemc.uwaterloo.ca/1-fr/ pour 
quelques explications et exercices supplémentaires.

