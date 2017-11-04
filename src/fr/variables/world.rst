Monde
=====

.. index:: Monde()

.. note::

    ``Monde()`` étant une fonction très spéciale, j'ai décidé de ne pas 
    suivre la convention normale de Python et je lui ai mis une masjuscule
    au début.


Choisissez un monde autre que ** But 1**. Exécutez ensuite le programme suivant 
**deux fois**::

    Monde("But 1")
    avance()
    avance()

La première fois que vous l'exécutez, Reeborg vous informera que le monde a 
changé en **But 1**, ce que vous devriez pouvoir confirmer en regardant
tout simplement le monde.

Le deuxième fois que vous l'exécutez, comme **But 1  ** est déjà sélectionné, 
la fonction ``Monde()`` sera ignorée et le reste du programme est exécuté.

Exercice de programmation
-------------------------

Avant de vous en dire plus sur ``Monde()``, je souhaite aborder à nouveau un 
programme que vous avez déjà écrit.

.. topic:: Faites ceci!  C'est important.

    Choisissez le monde **Tempête 1**. Ecrivez un programme qui fait
    ramassez à Reeborg toutes les feuilles et les place dans la pouvelle.
    Votre programme devra sûrement utiliser ``transporte()``.

Charger un monde distant
------------------------

Regardez de plus près le monde **Tempête 1** et notez où se trouvent les feuilles.

Maintenant, tout en haut du programme que vous venez d'écrire où Reeborg
ramasse les feuilles, ajoutez la ligne de code suivante::

    Monde("http://reeborg.ca/worlds/not_storm1.json")

[Notez que c'est le nombre "1" qui est à la fin de not_storm1 et pas la lettre "l".]
Exécutez le programme une fois: Reeborg devrait vous dire que le monde a été chargé
correctement. Son apparence devrait être identique à ce qu'il y avait précédemment.

Notez le nom du monde dans le sélecteur en haut est la long nom qui a été utilisé 
comme argument dans ``Monde()``.

Cliquez sur "Description". Vous trouverez une brève description du monde, 
en particulier que vous ne devez pas utiliser ``transporte()`` Ignorez cela
et exécutez votre programme. Notez ce qui se passe.

Charger un monde distant (bis)
-----------------------------

Votre programme n'a pas fonctionné. Nous verrons comment palier à cela
bientôt. En attendant, essayez autre chose: changez la première
ligne de votre programme ainsi::

    Monde("http://reeborg.ca/worlds/not_storm1.json",
          "Not Storm 1")

J'ai ajouté un second argument à la fonction ``Monde()`` afin d'éviter d'avoir
un long nom dans l'affichage dans l'éditeur.
J'ai placé le second argument sur une deuxième ligne.
Quand Python voit une parenthèse ouvrante pour un argument de fonction, il
continue de lire jusqu'à ce qu'il trouve la parenthèse fermante et 
considère le tout comme une seule ligne.
**Cependant**, notez que je n'ai pas séparé le texte; j'ai inséré une
nouvelle ligne après la virgule.

Exécutez maintenant le programme. Il y a toujours une erreur.
**Cependant"", si vous regardez en haut, le nom qui apparaît maintenant
en haut est ``Not Storm 1`` à la place de la longue adresse qu'il y
avait auparavant.

Sauvegardez votre travail
-------------------------

Vous voudrez peut-être sauvegarder votre travail sur l'ordinateur en
cliquant sur "Autres options", suivi de "Sauvegardez le programme".


Pour le charger à nouveau, cliquez sur "Ouvrir le programme".
