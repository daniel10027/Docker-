#### Pourquoi utiliser Docker ?

    Docker répond à une problématique forte dans le monde du développement.
    Prenons un exemple : vous avez développé votre projet de Twitter Lite en local. 
    Tout fonctionne bien, mais au moment de mettre en production, vous vous rendez compte
    que vous ne savez pas comment déployer votre projet. Un autre exemple : vous êtes dans
    une équipe de 10 personnes et chacun utilise un OS différent (Ubuntu, macOS, Windows, 
    CentOS, etc.). Comment faire pour avoir un environnement unifié et fonctionnel chez 
    l'ensemble des développeurs ?
   
    Docker répond à ces problématiques en créant des conteneurs. 
    Grâce à Docker, vous n'aurez plus de problème de différence d'environnement,
    et votre code marchera partout !
    
- [x] Utilisez Docker sur tous vos environnements
```
    Docker est utilisé par de très nombreuses sociétés pour différents usages.
    Ainsi, un des premiers usages de Docker se trouve dans la création d'environnements locaux. 
    Il est plus simple d'utiliser Docker en local quand on travaille avec de nombreuses versions 
    différentes des logiciels, et ainsi ne pas avoir des problèmes de compatibilité entre elles.

    On retrouve aussi Docker dans les domaines de la CI (Continous Integration,
    ou Intégration Continue) et de la CD (Continous Delivery, ou Livraison Continue). 
    Cela permet à la CI/CD de créer rapidement des espaces isolés pour faire tourner vos tests.
    Plus globalement, vous pouvez utiliser Docker sur l'ensemble de vos environnements.
 ```
    
### Installattion

   1. Choisissez votre version de Docker
      - Docker Inc distribue 3 versions de Docker différentes :
        - Docker Community Edition (Linux seulement) ;
        - Docker Desktop (Mac ou Windows) ;
        - Docker Enterprise (Linux seulement).
        
```
Docker Desktop et Docker Community Edition (CE) sont deux versions de Docker gratuites.
Avec les deux solutions, vous aurez un Docker fonctionnel sur votre ordinateur.
Si vous êtes sous Windows ou macOS, utilisez Docker Desktop qui va créer pour
vous l'ensemble des services nécessaires         au bon fonctionnement de Docker.
Si vous êtes sous Linux, prenez la version Community Edition (CE) ;
vous utiliserez aussi cette version pour vos serveurs.
La version Docker Enterprise ne ressemble pas du tout aux versions Desktop et CE.
Celle-ci répond à des besoins plus poussés des entreprises, et propose une interface
de gestion d'infrastructures sous Docker. 
Cette version est soumise à une licence fournie par Docker Inc.
``` 

  2. Docker pour Mac , Linux & Windows 
  
     - Quels sont les différences entre une utilisation de Docker sous Linux et sous Windows ?
     
      ![Image of Yaktocat](https://www.noobunbox.net/wp-content/uploads/2016/04/xlinux_docker_host.png.pagespeed.ic.igpO4IQ1nS.webp)
       ![Image of Yaktocat](https://www.noobunbox.net/wp-content/uploads/2016/04/xwin_docker_host.png.pagespeed.ic.p2mLbveWVR.webp)
       
      •Sous Windows, l’hôte de Docker est une machine virtuelle. 
      Le client Docker tourne sous Windows tandis que le daemon ainsi que les conteneurs tourneront sur cette VM
      
      •Sous Linux, votre ordinateur est l’hôte et l’hôte Docker. Le client Docker, le daemon et tous les conteneurs se               lanceront directement depuis votre machine.
        
     
     - Insttalation de Docker sous windows 
     
         • Assurez vous que votre CPU supporte la virtualisation et que celle-ci soit activée dans le BIOS et                            reconnue par Windows.
         • Si vous ne maitrisez pas trop le bios , ce logiciel pourra vous aider [Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=592) 
         ![Image of Yaktocat](https://www.noobunbox.net/wp-content/uploads/2016/02/xvirtualization.jpg.pagespeed.ic.mMZzUjrmp-.webp)
         
• Installation 

- Commencez par télécharger [Docker Toolbox](https://www.docker.com/toolbox) et installez le programme.
Notez que pendant l’installation Virtualbox ne doit pas être lancé.

• Lancer un conteneur Docker

- Avant de pouvoir lancer un conteneur Docker vous devez créer ou lancer une machine virtuelle existante.
Il y a plusieurs moyens d’utiliser Docker sous Windows, via Docker Quickstart Terminal, l’invite de commandes Windows ou Powershell.


      En utilisant Docker Quickstart Terminal
     
      • Commencez par double cliquer sur l’icone du programme sur votre bureau. L’application va alors
      • Ouvrir un terminal
      • Créer une machine virtuelle default et la démarrer
      • Configurer la VM
      
      Vous devez obtenir le resultat suivant :
```console
Running pre-create checks...
Creating machine...
(default) Copying C:Users\Noobunbox.dockermachine\cache\boot2docker.iso to 
(default) C:\Users\Noobunbox\.dockermachine\machines\defaultboot2docker.iso...
(default) Creating VirtualBox VM...
(default) Creating SSH key...
(default) Starting the VM...
(default) Waiting for an IP...
Waiting for machine to be running, this may take a few minutes...
Machine is running, waiting for SSH to be available...
Detecting operating system of created instance...
Detecting the provisioner...
Provisioning with boot2docker...
Copying certs to the local machine directory...
Copying certs to the remote machine...
Setting Docker configuration on the remote daemon...
Checking connection to Docker...
Docker is up and running!
To see how to connect Docker to this machine, run: docker-machine env default
```
