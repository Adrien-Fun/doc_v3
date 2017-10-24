=============================
Mise en pré-production
=============================

Build l'image
-------------

La construction de l'image se fait depuis le jenkins

1/ Se connecter en ssh sur le serveur : ssh bastion_dev -L8089:192.168.10.24:80
2/ Aller sur l'adresse : http://127.0.0.1:8089/
3/ Cliquer sur "fun-build-image"
4/ Cliquer sur "lancer un build avec des paramètres" ou "Rebuild Last"
5/ Une fois le build fini, appler dans l'oglet racine "fun-deploy-preprod"
6/ Cliquer sur "lancer un build avec des paramètres" et indiquer le numéro de l'image exemple : 4.9.6_60

Methode Live
------------

.. warning::

    Vérifier sur le bastion quel est l'ip du serveur actuel de pré-prod

il faut exporter les variables d'environnement ruby :

::

    sudo su edxapp -s /bin/bash
    cd
    . *env
    export

Il faut changer les permissions de staticfiles

::

    sudo su
    cd /edx/var/edxapp/
    chown -R edxapp:edxapp staticfiles/

Lancer la reconstruction des assets

::

    sudo -H -u edxapp bash
    source /edx/app/edxapp/edxapp_env
    cd /edx/app/edxapp/edx-platform
    paver update_assets lms --settings=fun.lms
    paver update_assets cms --settings=fun.cms

Redémmarer les process pythons (user: cloud)

::

    EDX_PLATFORM_SETTINGS_OVERRIDE=fun.lms /edx/bin/supervisorctl restart edxapp: