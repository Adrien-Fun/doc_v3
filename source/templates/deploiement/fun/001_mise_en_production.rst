==================================
Mise en production
==================================

La mise en prouction se fait via un ticket à Objectif-libre.

Il faut leur fourir le nom de l'image construite en pré-prod à déployer.


Déploiement sur git
-------------------

Pour fun-app Passer sur la branche release-4.9.1

::

    git checkout fun/release-4.9.1

revenir en arrière sur git
--------------------------

::

    git log
    git rebase -i <numéro de commit>
    git push