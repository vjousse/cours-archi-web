# Initiation à Django

## Vérification de l'environnement

Nous allons travailler sur la machine qui se nomme `mordor`.

Tout d'abord, connectez-vous en ssh dessus pour vérifier que tout est ok.

    ssh spiXXXX@mordor

Nous allons utiliser Python 3.5.1. Exécutez la commande suivante :

    python --version

Quelle est la version de python ? Essayez :

    which python

Où est-il installé ?

Je vous ai installé un python3.5 ici : `/info/projets/archiweb_l3spi/usr/bin/python3`
Ajoutez `/info/projets/archiweb_l3spi/usr/bin/` dans votre `$PATH`.

## Utilisation d'environnements virtuels

Si nous ne changeons rien, nous allons tous utiliser la même installation de python (celle dans `/info/projets/archiweb_l3spi/usr/bin/`) et ça peut vite devenir problématique. 

En effet en python il est possible d'installer des packages (sorte de plugin) de manière automatique. Python dispose d'une sorte d'*App Store* (qui s'appelle `pip`) qui vous permet de télécharger et d'installer automatiquement les packages dont vous avez besoin (dont Django dans notre cas). Le souci étant que ces packages sont installés au niveau global (dans le python que je vous ai installé). Ils ne seront pas installés que pour vous mais bien pour tous les utilisateurs du python concerné.

Heureusement, il existe une solution à ce problème : installer un environ python local pour chacun d'entre vous, basé sur mon installation de python. On appelle ça des **environnements virtuels**.

### Créer son environnement virtuel

Placez-vous à la racine de votre compte en faisant :

    cd

Ensuite, créez votre environnement virtuel (il doit porter votre nom de login spiXXX) :

    virtualenv -p /info/projets/archiweb_l3spi/usr/bin/python3 spiXXXX

Vérifiez que l'environnement a bien été créé :

    ls -al spiXXXX/

Pour pouvoir l'utiliser, vous allez devoir l'activer à chaque fois que vous vous connecterez sur `mordor` comme ceci :

    . ./spiXXX/bin/activate

Votre prompt devrait avoir changé et il devrait être préfixé par `(spiXXXX)` comme ceci :

    (spiXXXX)jousse@mordor:~$

Vérifiez de nouveau votre version de python :

    python --version

Et vérifiez qu'elle est bien située dans votre compte :

    which python

À partir de là, et seulement à partir de là, vous pouvez continuer le TP. À chaque fois que vous voudrez exécuter du python sur mordor pour votre projet, vous devrez avoir au préalable activé votre environnement virtuel :

    . ./spiXXX/bin/activate
    
### Installer django

Maintenant que vous avez activé votre environnement virtuel (votre prompt **DOIT** etre préfixé par (spiXXXX), vous pouvez installer `Django` :

    pip install Django

Ça devrait vous afficher comme dernière ligne :

    Successfully installed Django-1.9.1

Vérifiez que c'est bien le cas avec cette commande :

    python -c "import django; print(django.get_version())"

### Faire le tutorial

Comme je vous l'ai dit en cours, réinventer la roue a souvent assez peu de sens. Nous allons donc nous appuyer sur le tutorial officiel de Django pour réaliser ce tp. 

À un certain moment, on va vous demander d'exécuter cette commande :

    python manage.py runserver

Par défaut, cette commande lance un serveur web sur le port 8000 (et sur l'IP 127.0.0.1 de mordor) qui ira exécuter vos fichiers.

Puisque vous allez chacun exécuter un serveur web de cette manière, le port par défaut (8000) sera surement déjà utilisé. Vous allez donc devoir lancer le serveur sur un autre port. On prendra par défaut, le port correspondant aux nombres de votre login spi**XXXX**. 

Vous voulez en plus pouvoir atteindre votre serveur web de l'extérieur de mordor (à partir du navigateur de votre machine de TP), vous devez donc le faire écouter sur une autre IP que l'IP locale de mordor.

Par exemple, pour **spi1234** ça donnera :

    python manage.py runserver 0.0.0.0:1234

L'IP `0.0.0.0` veut dire que le serveur écoutera sur toutes les IP disponibles de la machine et sur le port `1234`.

Vous y accéderez donc de votre navigateur en tapant dans l'URL `http://mordor:1234/`.

Voilà pour l'introduction, vous pouvez maintenant suivre le tutoriel sereinement, et éventuellement m'appeler quand il s'agit de la base de données.

Le tutoriel est en 7 parties et il se situe [sur le site officiel de Django](https://docs.djangoproject.com/fr/1.9/intro/tutorial01/).

