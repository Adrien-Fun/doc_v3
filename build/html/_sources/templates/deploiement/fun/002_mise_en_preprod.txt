=============================
Mise en pré-production
=============================

Build l'image
-------------

La construction de l'image se fait depuis le jenkins

- Se connecter en ssh sur le serveur : ssh bastion_dev -L8089:192.168.10.24:80
- Aller sur l'adresse : http://127.0.0.1:8089/
- Cliquer sur "fun-build-image"
- Cliquer sur "lancer un build avec des paramètres" ou "Rebuild Last"
- Une fois le build fini, aller dans l'oglet racine "fun-deploy-preprod"
- Cliquer sur "lancer un build avec des paramètres" et indiquer le numéro de l'image exemple : 4.9.6_60

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