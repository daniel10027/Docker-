### Installer Docker sur Linux

```
Quelle que soit la distribution de votre choix,
vous aurez besoin d'une installation 64 bits et d'un noyau à 3.10 ou plus récent.
Les noyaux antérieurs à 3.10 ne disposent pas des fonctionnalités nécessaires dont
Docker a besoin pour exécuter des conteneurs;
la perte de données et les paniques du noyau se produisent fréquemment dans certaines conditions.
````

```
Vérifiez votre version actuelle de Linux avec uname -r. Vous devriez voir quelque chose comme
3.10.[alphanumeric string].x86_64.
````

```js
Debian et Ubuntu
Docker fonctionne sur:

Ubuntu Xenial 16.04 LTS
Ubuntu Wily 15.10
Ubuntu Trusty 14.04 LTS
Ubuntu Precise 12.04 LTS
Debian testing stretch
Debian 8.0 Jessie
Debian 7.0 Wheezy (vous devez activer les rétroportages)
Debian Wheezy
```


Si oui, vous devez activer les rétroportages (sinon, ignorez cette section):

Connectez - vous dans le système et ouvrir un terminal avec sudoou rootprivilèges (ou exécuter à sudo -ipartir de votre terminal).
Ouvrez /etc/apt/sources.list.d/backports.listavec votre éditeur de texte préféré (si le fichier n'existe pas, créez-le).
Supprimez les entrées existantes.
Ajoutez une entrée pour les rétroportages sur Debian Wheezy:
 deb http://http.debian.net/debian wheezy-backports main
Mettez à jour vos packages:
 apt-get update -y
Ubuntu Precise 12.04
Si c'est le cas, vous devez vous assurer que vous disposez de la version 3.13 du noyau. Vous devez mettre à jour votre noyau:

Ouvrez un terminal sur votre système.
Mettre à jour l'aptitude:
 sudo apt-get update -y
Installez les packages supplémentaires:
 sudo apt-get install -y linux-image-generic-lts-trusty linux-headers-generic-lts-trusty
Dans un environnement graphique Ubuntu, vous devez en outre exécuter ce qui suit:
 sudo apt-get install -y xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
Redémarrez votre système:
 sudo reboot
Mettre à jour l'aptitude
Connectez-vous à votre système avec un utilisateur disposant de sudoprivilèges.
Ouvrez une fenêtre de terminal.
Purgez les anciens référentiels:
 sudo apt-get purge -y lxc-docker* && sudo apt-get -y purge docker.io*
Mettez à jour vos packages, en vous assurant qu'ils aptfonctionnent avec httpset que le serveur dispose de certificats CA:
 sudo apt-get update -y && sudo apt-get install -y apt-transport-https ca-certificates
Obtenez la nouvelle clé GPG:
 sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
Ouvrez ou créez le fichier /etc/apt/sources.list.d/docker.listdans votre éditeur de texte préféré (vous en avez besoin sudoou rootpour cela).
Ajoutez une entrée pour votre système d'exploitation

Version	La source
Ubuntu Precise 12.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-precise main
Ubuntu Trusty 14.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-trusty main
Ubuntu Wily 15.10 LTS	deb https://apt.dockerproject.org/repo ubuntu-wily main
Ubuntu Xenial 16.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-xenial main
Debian Wheezy	deb https://apt.dockerproject.org/repo debian-wheezy main
Debian Jessie	deb https://apt.dockerproject.org/repo debian-jessie main
Debian Stretch / Sid	deb https://apt.dockerproject.org/repo debian-stretch main
Enregistrez et fermez le fichier.
Mettre à jour Aptitude à nouveau:
 sudo apt-get update -y
Vérifiez que Aptitude tire du bon référentiel:
sudo apt-cache policy docker-engine
Installer Docker
Si vous utilisez Ubuntu Trusty, Wily ou Xenial, installez le linux-image-extrapackage du noyau:

sudo apt-get update -y && sudo apt-get install -y linux-image-extra-$(uname -r)
Installez Docker:
sudo apt-get install docker-engine -y
Démarrer Docker:
 sudo service docker start
Vérifiez Docker:
 sudo docker run hello-world
Le groupe Docker
Si vous préférez, vous pouvez configurer un dockergroupe pour exécuter Docker (au lieu de root). Cependant , comme dockerdoit y avoir sudoaccès, dockerreçoit le même accès que root.

Exécutez la commande suivante pour créer un groupe Docker sur Ubuntu:
 sudo groupadd docker && sudo usermod -aG docker ubuntu
Déconnectez-vous et reconnectez-vous.

Exécutez la commande suivante pour créer un groupe Docker sur Debian:
 sudo groupadd docker && sudo gpasswd -a ${USER} docker && sudo service docker restart
Vous pouvez spécifier un utilisateur au lieu de ${USER}si vous préférez.

Vérifiez une installation Docker réussie:
 docker run hello-world
Red Hat Enterprise Linux (RHEL) et CentOS
Docker fonctionne sur RHEL 7 et CentOS 7.

Installer Docker
Installer avec Yum
Connectez-vous à votre système en tant qu'utilisateur avec des sudoprivilèges.
Mettez à jour votre système: sudo yum update -y.
Ajoutez le repo yum (utilisez le code ci-dessous pour RHEL 7 et CentOS 7):
 $ sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
 [dockerrepo]
 name=Docker Repository
 baseurl=https://yum.dockerproject.org/repo/main/centos/7/
 enabled=1
 gpgcheck=1
 gpgkey=https://yum.dockerproject.org/gpg
 EOF
Installez Docker:
 sudo yum install docker-engine -y
Démarrer Docker:
 sudo service docker start
Vérifiez Docker:
 sudo docker run hello-world
Installer avec le script d'installation Docker
Connectez-vous à votre système en tant qu'utilisateur avec des sudoprivilèges.
Mettez à jour votre système:
 sudo yum update -y
Exécutez le script d'installation de Docker:
 curl -fsSL https://get.docker.com | sh;
Ce script ajoute le docker.reporéférentiel et installe Docker.

Démarrer Docker:
 sudo service docker start
Vérifiez Docker:
 sudo docker run hello-world
Le groupe Docker
Si vous préférez, vous pouvez configurer un dockergroupe pour exécuter Docker (au lieu de root). Cependant , comme dockerdoit y avoir sudoaccès, dockerreçoit le même accès que root.

Exécutez la commande suivante pour créer un groupe Docker et ajouter votre utilisateur au groupe (remplacez USERNAME par votre nom d'utilisateur):
 sudo groupadd docker && sudo usermod -aG docker USERNAME
Déconnectez-vous et reconnectez-vous.
Vérifiez que Docker fonctionne sans sudo:
 docker run hello-world
Démarrer Docker au démarrage
Exécutez l'une des opérations suivantes:

sudo chkconfig docker on
sudo systemctl enable docker
Problèmes courants
Remarque: les membres du groupe Docker ont des privilèges root . Hardening Docker est traité dans un futur tutoriel.

Ubuntu
Ubuntu Utopic 14.10 et 15.05 existe dans le aptréférentiel de Docker sans support officiel. Mettre à niveau vers 15.10 ou [de préférence] 16.04. Si vous utilisez Ubuntu 12.04, vous devez mettre à jour votre noyau.

Debian
Si vous exécutez Debian Wheezy, vous devez mettre à jour les sources avec des rétroportages.

«Impossible de se connecter au démon Docker. Le «démon docker» est-il en cours d'exécution sur cet hôte? »
Si vous obtenez cette erreur, vous devez désactiver DOCKER_HOST; exécuter unset DOCKER_HOSTpour effacer la variable.

