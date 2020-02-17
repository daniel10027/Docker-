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
```


- Debian Wheezy

Si oui, vous devez activer les rétroportages (sinon, ignorez cette section):


 1. Connectez - vous dans le système et ouvrir un terminal avec sudoou rootprivilèges (ou exécuter à sudo -ipartir de votre terminal).
 2. Ouvrez /etc/apt/sources.list.d/backports.listavec votre éditeur de texte préféré (si le fichier n'existe pas, créez-le).
 3. Supprimez les entrées existantes.
 4. Ajoutez une entrée pour les rétroportages sur Debian Wheezy:
 
 ```js
 deb http://http.debian.net/debian wheezy-backports main
 ```
 5. Mettez à jour vos packages:
 ```js
 apt-get update -y
 ```
 
- Ubuntu Precise 12.04
Si c'est le cas, vous devez vous assurer que vous disposez de la version 3.13 du noyau. 
Vous devez mettre à jour votre noyau:

1. Ouvrez un terminal sur votre système.
2. Mettre à jour l'aptitude:
```js
 sudo apt-get update -y
 ```
3. Installez les packages supplémentaires:
 ```js
 sudo apt-get install -y linux-image-generic-lts-trusty linux-headers-generic-lts-trusty
 ```
4. Dans un environnement graphique Ubuntu, vous devez en outre exécuter ce qui suit:
 ```js
sudo apt-get install -y xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
```
5. Redémarrez votre système:
```js
sudo reboot
```

Mettre à jour l'aptitude

1. Connectez-vous à votre système avec un utilisateur disposant de sudoprivilèges.
2. Ouvrez une fenêtre de terminal.
3. Purgez les anciens référentiels:
 ```js
 sudo apt-get purge -y lxc-docker* && sudo apt-get -y purge docker.io*
 ```
 
4. Mettez à jour vos packages, en vous assurant qu'ils aptfonctionnent avec httpset que
le serveur dispose de certificats CA:
 ```js
 sudo apt-get update -y && sudo apt-get install -y apt-transport-https ca-certificates
 ```
5. Obtenez la nouvelle clé GPG:
```js
 sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
 ```

6. Ouvrez ou créez le fichier /etc/apt/sources.list.d/docker.list dans votre éditeur de texte préféré
(vous en avez besoin sudo ou rootpour cela).

7. Ajoutez une entrée pour votre système d'exploitation
```js
Version	La source
Ubuntu Precise 12.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-precise main
Ubuntu Trusty 14.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-trusty main
Ubuntu Wily 15.10 LTS	deb https://apt.dockerproject.org/repo ubuntu-wily main
Ubuntu Xenial 16.04 LTS	deb https://apt.dockerproject.org/repo ubuntu-xenial main
Debian Wheezy	deb https://apt.dockerproject.org/repo debian-wheezy main
Debian Jessie	deb https://apt.dockerproject.org/repo debian-jessie main
Debian Stretch / Sid	deb https://apt.dockerproject.org/repo debian-stretch main
```

8. Enregistrez et fermez le fichier.
9. Mettre à jour Aptitude à nouveau:
 ```js
 sudo apt-get update -y
 ```

10. Vérifiez que Aptitude tire du bon référentiel:
```js
sudo apt-cache policy docker-engine
``` 

### Installer Docker
Si vous utilisez Ubuntu Trusty, Wily ou Xenial, installez le linux-image-extrapackage du noyau:
```js
sudo apt-get update -y && sudo apt-get install -y linux-image-extra-$(uname -r)
```

Installez Docker:
```js
sudo apt-get install docker-engine -y
````

Démarrer Docker:
```js
 sudo service docker start
 ````
 
Vérifiez Docker:
```js
 sudo docker run hello-world
 ```
 
• Le groupe Docker

    Si vous préférez,
    vous pouvez configurer un dockergroupe pour exécuter Docker (au lieu de root).
    Cependant , 
    comme dockerdoit y avoir sudoaccès, dockerreçoit le même accès que root.

Exécutez la commande suivante pour créer un groupe Docker sur Ubuntu:
 ```js
 sudo groupadd docker && sudo usermod -aG docker ubuntu
 ```
 
Déconnectez-vous et reconnectez-vous.

Exécutez la commande suivante pour créer un groupe Docker sur Debian:
```js
 sudo groupadd docker && sudo gpasswd -a ${USER} docker && sudo service docker restart
 ```
• Vous pouvez spécifier un utilisateur au lieu de ${USER}si vous préférez.

Vérifiez une installation Docker réussie:
 ```js 
 docker run hello-world
 ```
 
• Red Hat Enterprise Linux (RHEL) et CentOS
• Docker fonctionne sur RHEL 7 et CentOS 7.

- Installer Docker
    - Installer avec Yum
    
        1. Connectez-vous à votre système en tant qu'utilisateur avec des sudoprivilèges.
        Mettez à jour votre système:

        ```js
        sudo yum update -y.
        ```
        2. Ajoutez le repo yum (utilisez le code ci-dessous pour RHEL 7 et CentOS 7):

        ```js
         $ sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
         [dockerrepo]
         name=Docker Repository
         baseurl=https://yum.dockerproject.org/repo/main/centos/7/
         enabled=1
         gpgcheck=1
         gpgkey=https://yum.dockerproject.org/gpg
         EOF
         ````

        3. Installez Docker:
         ```js 
         sudo yum install docker-engine -y
         ```

        4. Démarrer Docker:
         ```js 
         sudo service docker start
         ```
        5. Vérifiez Docker:
         ```js 
         sudo docker run hello-world
         ``` 
    - Installer avec le script d'installation Docker
    
        1. Connectez-vous à votre système en tant qu'utilisateur avec des sudoprivilèges.
        2. Mettez à jour votre système:
         ```js 
         sudo yum update -y
         ```  
     
       3. Exécutez le script d'installation de Docker:
         ```js 
         curl -fsSL https://get.docker.com | sh;
         ```
             . Ce script ajoute le docker.reporéférentiel et installe Docker.

       4.  Démarrer Docker:
         ```js
         sudo service docker start
         ```
      5.  Vérifiez Docker:
        ```js
        sudo docker run hello-world
        ```
- Le groupe Docker
   - Le groupe Docker
 
 ```
    Si vous préférez, vous pouvez configurer un dockergroupe pour exécuter Docker (au lieu de root).
    Cependant , comme dockerdoit y avoir sudoaccès, dockerreçoit le même accès que root.
 ```

      1. Exécutez la commande suivante pour créer un groupe Docker et ajouter votre utilisateur
au groupe (remplacez USERNAME par votre nom d'utilisateur):

     ```js
        sudo groupadd docker && sudo usermod -aG docker USERNAME
      ```
      2. Déconnectez-vous et reconnectez-vous.
    Vérifiez que Docker fonctionne sans sudo:
     ```js
     docker run hello-world
     ```
     
      3. Démarrer Docker au démarrage
         Exécutez l'une des opérations suivantes:

   ````js
    sudo chkconfig docker on
    sudo systemctl enable docker
    ````
    
    ````
Problèmes courants
    Remarque: les membres du groupe Docker ont des privilèges root .
    Hardening Docker est traité dans un futur tutoriel.

Ubuntu

    Ubuntu Utopic 14.10 et 15.05 existe dans le aptréférentiel de Docker sans support officiel. 
    Mettre à niveau vers 15.10 ou [de préférence] 16.04. Si vous utilisez Ubuntu 12.04,
    vous devez mettre à jour votre noyau.

    Debian
    Si vous exécutez Debian Wheezy, vous devez mettre à jour les sources avec des rétroportages.

    «Impossible de se connecter au démon Docker. Le «démon docker» est-il en cours d'exécution sur cet hôte? »
    Si vous obtenez cette erreur, vous devez désactiver DOCKER_HOST; exécuter unset DOCKER_HOSTpour effacer la variable.
```
