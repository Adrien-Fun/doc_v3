Open EDX
========

`Documentation Open EDX <http://edx.readthedocs.io/projects/edx-guide-for-students/en/latest/>`_

Open EDX est une solution open source développé par Edx.

Elle permet de créer une plateforme de MOOC / COOC et d'implémenter ses propres fonctionnalités grâce aux XBlock.

Edx met régulièrement à jour sa solution. Il est donc indispensable de faire des monté de version pour chaque nouvelle mise à jour.

La version actuelle d'Open EDX est la gingko.1.

XBlock 
******
`Documentation Xblock <http://edx.readthedocs.io/projects/xblock-tutorial/en/latest/index.html>`_

Xblock est le composant d'architecture pricipal d'EDX pour personaliser la plateforme. 

il s'agit un template. 

Architecture exemple de fun_glowbl :

.. image:: ../../_static/images/xblock_example.png

Dans le fichier python pilote :

- lti : sert à l'autentification au sein des xblocks

- Cette classe permet de changer les champs éditable du cour.

::

    @XBlock.needs('i18n')    
    class FUNGlowblXBlock(LtiConsumerXBlock, StudioEditableXBlockMixin, XBlock):

        editable_fields = ['title', 'description', 'rendezvous', 'custom_course_type', 'max_user']

        title = String(scope=Scope.settings, default="",
            display_name=_("Glowbl Live Event title"),
            help=_("Enter the title of the event."))
            
Le champ editable_fields indique les valeurs éditable.

title est un exemple de champ.