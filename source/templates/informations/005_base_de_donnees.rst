Base de données
===============

Pour se connecter à la base de données en préprod, il faut :

::
    
    $> ssh -vvv 192.168.20.34 -L3306:192.168.10.254:3306


puis sur un autre shell :

::
    
    $> mysql


Mais avant dans .my.cnf

::
    
    [client]
    host=127.0.0.1
    user=root
    password=edx_password
    
    [clientpek]
    host=192.168.10.254
    user=pekin_edxapp
    password="71-uk0jsuM69j7Dr"
