### Installation de Docker sur Windows 

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

    Une fois ce processus terminé vous pouvez utiliser les [commandes docker](),
    commencez par lancer le conteneur [hello-world]().
    
```console 
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
511136ea3c5a: Pull complete
31cbccb51277: Pull complete
e45a5af57b00: Pull complete
hello-world:latest: The image you are pulling has been verified.
Important: image verification is a tech preview feature and should not be
relied on to provide security.
Status: Downloaded newer image for hello-world:latest
Hello from Docker.
This message shows that your installation appears to be working correctly.


To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
   (Assuming it was not already locally available.)
3. The Docker daemon created a new container from that image which runs the
   executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
   to your terminal.


To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash


For more examples and ideas, visit:
http://docs.docker.com/userguide/

````
    
        En utilisant l’invite de commandes Windows (cmd.exe)

        •  Ouvrez une invite de commandes Windows et créez une nouvelle machine virtuelle Docke     
```console 
docker-machine create --driver virtualbox default
```   
        • Si tout se passe bien voila ce que votre terminal devrait afficher
     

```console
     Microsoft Windows [version 10.0.10240]
(c) 2015 Microsoft Corporation. Tous droits réservés.

C:Users\Noobunbox>docker-machine create --driver virtualbox default
Running pre-create checks...
Creating machine...
(default) Copying C:Users\Noobunbox.dockermachine\cache\boot2docker.iso to C:\Users\Noobunbox\.dockermachine\machines\defaultboot2docker.iso...
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
      • Vous pouvez lister vos machines virtuelles créer pour fonctionner avec Docker

```console 
docker-machine ls
````
 #### Ce qui vous donne :

```console 
C:Users\Noobunbox> docker-machine ls
NAME                ACTIVE   DRIVER       STATE     URL                         SWARM
default        *        virtualbox   Running   tcp://192.168.99.101:2376
````

       • Maintenant « lions » les commandes du shell à notre nouvelle VM

```
C:Users\Noobunbox> docker-machine env --shell cmd my-default
```
       • Puis copier et coller la commande affichée afin de connecter l’invite de commandes à notre VM default
```console 
FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO %i
````


       • Lancez la commande hello-world afin de vérifier que tout fonctionne
```console 
C:Users\Noobunbox> docker run hello-world
```


       En utilisant Powershell
       • Lançons la même commande utilisée que pour l’invite de commandes afin de lier Powershell a notre VM
         en modifiant la variable shell
```console
C:UsersNoobubnbox> docker-machine env --shell powershell default
```

       • Powershell retourne une commande à rentrer afin qu’il puisse se connecter à la VM default. Lancez la commande

```console
PS C:Users\Noobunbox> docker-machine env --shell powershell default
$Env:DOCKER_TLS_VERIFY = "1"
$Env:DOCKER_HOST = "tcp://192.168.99.104:2376"
$Env:DOCKER_CERT_PATH = "C:\Users\Noobunbox\.dockermachine\machines\default"
$Env:DOCKER_MACHINE_NAME = "default"
# Run this command to configure your shell:
# & "C:\Program Files\Docker\ Toolboxdocker-machine.exe" env --shell powershell default | Invoke-Expression

PS C:Users\Noobunbox> & "C:\Program Files\Docker\ Toolboxdocker-machine.exe" env --shell powershell default | Invoke-Expression
```



    
