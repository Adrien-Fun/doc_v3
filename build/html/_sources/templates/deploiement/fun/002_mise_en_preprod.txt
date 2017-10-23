=============================
Mise en pré-production
=============================


Build l'image
-------------

La construction de l'image se fait depuis le jenkins



Methode Live
------------

il faut exporter les variables d'environnement ruby :

::

    cd
    . *env
    export 

Il faut changer les permissions de staticfiles

::

    cd /edx/var/edxapp/
    chown -R edxapp:edxapp staticfiles/

Lancer la reconstruction des assets

::

    cd ~/edx-platform
    paver update_asset lms --settings=fun.lm

Redémmarer les process pythons

::

    EDX_PLATFORM_SETTINGS_OVERRIDE=fun.lms /edx/bin/supervisorctl restart edxapp: