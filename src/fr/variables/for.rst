Boucles ``for``
===============

.. todo::

   Changer ceci pour introduire les boucles ``for`` d'abord en
   utilisant des listes, puis des chaînes (par exemple: épeler un nom),
   pour finalement terminer avec le fameux idiome ``for _ in range(n)``.
   Alternativement, référez les étudiants au site https://cscircles.cemc.uwaterloo.ca/7c-fr/


Comme nous l'avons vu, les boucles ``while`` peuvent être utilisées avec
des nombres suivant le patron::

    n = 0                      # initialisation
    while n < valeur_maximale : # condition pour terminer
        ...
        n += 1  # incrément

Une autre façon d'écrire un bout de programme ayant **exactement le
même sens** est d'utilisé une boucle ``for``::

    for n in range(valeur_maximale):
       ...

La boucle ``for`` peut être utilisée pour plus de choses que simplement
compter des objets. 


.. topic:: À votre tour!

   Essayez le programme ci-dessous avec le monde **Autour 1**::

      for case in range(6):
          avance()
      tourne_a_gauche()

      for côté in range(3):
          for case in range(9):
              avance()
          tourne_a_gauche()

      for case in range(3):
          avance()


Ressources supplémentaires
-------------------

Rendez-vous à l'adresse https://cscircles.cemc.uwaterloo.ca/7c-fr/ pour 
quelques explications et exercices supplémentaires.
