Jenkins
=======

Jenkins pre-prod
----------------

::

    ssh bastion_dev -L8089:192.168.10.24:80


Jenkins marque blanche
----------------------

::

    ssh bastion_dev -L8097:192.168.10.24:8081


Jenkins rancherOS
----------------------

::

    ssh 192.168.20.11 -L9090:192.168.20.11:8080