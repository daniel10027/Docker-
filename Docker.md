### A LA DECOUVERTE DE DOCKER 
![Image of Yaktocat](https://github.com/daniel10027/Docker-/blob/master/te%CC%81le%CC%81chargement.png)


### Docker , Qu'est ce que c'est ?

```

Docker est un outil open source, destiné aux développeurs et administrateurs systèmes, 
dont l’objectif est de faciliter le développement, la diffusion et le déploiement d’applications web autonomes.
Son principal intérêt est d’assembler les briques d’une application en conteneurs pouvant être partagés, 
sous forme d’images, au travers d’un registre (“docker registry”) et de les exécuter quels que soient
la plateforme et l’environnement. Grâce à Docker, les applications deviennent portables et exécutables
n’importe où : d’ordinateurs portables Mac ou Windows, des machines virtuelles, de serveurs de production etc.

```
 

### Comment ça marche ?

```
A la différence d’un système de virtualisation classique,
les conteneurs Docker partagent les ressources de la machine hôte et font l’économie de l’installation d’un système d’exploitation complet.
Le conteneur ne contient donc que la partie applicative nécessaire ainsi que ses dépendances,
et fonctionne de la même façon que pour les machines virtuelles de façon isolée et autonome.
```
 

#### Images et conteneurs

```
Ces deux notions sont fondamentales à la compréhension de Docker.
Une image Docker peut être comparée à une image de machine virtuelle.
Elle contient tout ce dont Docker a besoin pour faire tourner les conteneurs.
Un conteneur est la version exécutée d’une image Docker.
Le “Docker registry” contient un très grand nombre d’images permettant d’utiliser sous forme de conteneur
la plupart des outils utilisées aujourd’hui : nginx, apache, mariadb, php-fpm etc.
```

# Création d’un conteneur


Voici un exemple simple :
```
$ docker run -i -t debian:wheezy /bin/bash
$ root@5e44d246ccea:/#
```

Dans cet exemple, le moteur Docker va récupérer l’image “debian:wheezy” dans le “docker repository” 
et créer un conteneur avec. Dans un deuxième temps, 
il exécutera la commande voulue, c’est-à-dire “/bin/bash” qui nous ouvrira un accès bash au conteneur créé.
Il est possible à ce moment de faire tout ce qu’on peut faire dans un système Debian.
On peut installer des packages, créer des fichiers etc :

```
$ root@5e44d246ccea:/# apt-get update
$ root@5e44d246ccea:/# apt-get install nginx
```

Une fois ces modifications effectuées il est possible de les sauvegarder, de “commit” ces changements :

```
$ docker commit 5e44d246ccea mynginx
b39ca21fe2e8173ac3dceea30406b074a87c
```

Une nouvelle image “mynginx” a été créée. Il est désormais possible de l’utiliser directement :

```
$ docker run mynginx /usr/sbin/nginx -g “daemon off;”
```
L’utilisation de l’option -g “daemon off;” 
est nécessaire pour éviter que le conteneur ne se stoppe juste après avoir exécuté la commande,
ce qui est le comportement normal d’un conteneur. Une fois la commande exécutée, le conteneur s’arrête.

Il existe cependant une autre façon, plus propre et plus riche de créer des images en utilisant un fichier “Dockerfile”.



## # Les “Dockerfile”


Ces fichiers permettent de décrire les étapes nécessaires à la fabrication d’une image.
L’utilisation d’un fichier apporte clairement une meilleure visibilité de ces modifications et permettent ainsi d’être maintenues et évolutives.
Pour cela, il est possible d’utiliser un certain nombre de commandes décrites sur le site officiel :

```
FROM : image utilisée pour fabriquer la nouvelle image. Ex : debian:wheezy.
```

```
RUN : permet d’exécuter directement des commandes permettant la création de l’image.
Ex : RUN apt-get update && apt-get install -y nginx
```

```
CMD : cette commande permet d’exécuter les applications installées. Ex : CMD [“nginx”, “-g”, “daemon off;”]
```

```
EXPOSE : permet d’exposer un port en particulier. Ex : EXPOSE 80
```

```
COPY / ADD : ces commandes permettent de copier des fichiers locaux à l’intérieur du conteneur.
A la différence de COPY, ADD permet d’extraire des archives.
Ex :
COPY ./monscript.sh /monscript.sh
ADD ./messcripts.tgz /
```

```
ENTRYPOINT : permet d’exécuter la commande principale du conteneur.
On peut également lui passer un script:
Ex :
COPY ./entrypoint.sh /entrypoint.sh
ENTRYPOINT [“/entrypoint.sh”]
```

• Pour revenir à notre exemple précédent, en mettant en place un serveur NGINX,
on obtiendrait par exemple le Dockerfile suivant :

```
# Dockerfile:

FROM debian:wheezy

# Installation de nginx
RUN apt-get update && apt-get install -y nginx
# Option daemon off pour éviter que le conteneur ne s’arrête
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 80

ENTRYPOINT [“nginx”]

```

# Construction de l’image :

```
$ docker build -t mysupernginx ./
$ docker images
REPOSITORY TAG IMAGE ID
mysupernginx latest 24c607dad5e9
debian wheezy c9fa20ecce88
```
• On voit que notre image “mysupernginx” est désormais utilisable, partageable et taggable. 
En effet, regardons la commande suivante :

```
$ docker build -t mysupernginx:0.1 ./
$ docker images
REPOSITORY TAG IMAGE ID
mysupernginx latest 24c607dad5e9
mysupernginx 0.1 24c607dad5e9
debian wheezy c9fa20ecce88
```

•Notre image possède désormais deux références : latest et 0.1 faisant référence à la même image (IMAGE ID).

•Pour exécuter notre commande et lancer un serveur nginx, il ne nous reste plus qu’à l’instancier :

```
$ docker run -d -p 80:80 mysupernginx:0.1
```
•L’option “-p” permet ici de rediriger le port du conteneur vers le port de l’hôte :
“ip:hostPort:containerPort”

•Pour voir si votre conteneur a bien été créé, vous pouvez faire un :

```$ docker ps```
•Et pour tester si NGINX s’est installé correctement :

```$ curl -I 127.0.0.1```
•Attention ! Sur Mac, il faut obtenir avant tout l’ip de boot2docker

```$ boot2docker ip
192.168.59.103
$ curl -I 192.168.59.103
```

• Avoir les images, c’est un bon premier pas. Mais qu’en est-il de l’orchestration de ces
différentes images pour une utilisation concrète dans le cadre d’une application ?
Pour ce faire, Docker nous propose un outil fort pratique, voire indispensable : 
“docker-compose”.

• Docker compose

“Docker Compose” s’installe très simplement :

```
$ curl -L https://github.com/docker/compose/releases/download/1.1.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
$ chmod u+x /usr/local/bin/docker-compose
```

L’objectif de “docker-compose” est de permettre d’éxécuter et de mettre en relation
les différentes images dont notre application a besoin.
Il se présente sous la forme d’un fichier “docker-compose.yml”

Si on reprend notre image précédente :
docker-compose.yml:

```
nginx:
image: mysupernginx:0.1
volumes:
- ./var/www:/usr/share/nginx/www
ports:
- 80:80
```

Il faut tout d’abord initialiser le/les conteneurs :

```$ docker-compose up -d```

• Un simple “docker ps” nous indiquera si tout s’est bien passé.
Vous pouvez également taper la commande “docker-compose logs” pour voir les logs.

• L’intérêt est bien entendu ici de créer des liens entre les différents conteneurs nécessaires.
Dans le cas d’un serveur LAMP, on peut imaginer le cas suivant :

Nous avons sur notre machine hôte le répertoire suivant :
/home/user/docker-compose.yml
/home/user/var/lib/mysql
/home/user/var/www
/home/user/etc/nginx/sites-enabled

```
#docker-compose.yml:

nginx:
image: disko/nginx
volumes:
- home/user/etc/nginx/sites-enabled:/etc/nginx/sites-enabled
- home/user//var/www:/usr/share/nginx/www
ports:
- 80:80
links:
- phpfpm
- mariadb
phpfpm:
image: disko/phpfpm
volumes:
- /home/user/var/www:/usr/share/nginx/www
mariadb:
image: disko/mariadb
volumes:
- /home/user/var/lib/mysql:/var/lib/mysql
command:
- /run.sh
```

```
Décrivons brièvement les différents éléments.
nginx :
– nous partageons les dossiers/fichiers locaux dont nous avons besoin dans le conteneur,
– nous redirigeons le port 80 vers la machine hôte,
– nous lions nginx aux conteneurs “mariadb” et “phpfpm”.
Ceci permettra de donner accès à ces conteneurs uniquement à l’intérieur du conteneur nginx.

phpfpm :
– nous partageons le dossier contenant les sources php (le même que pour Nginx)
mariadb :
– nous lions un dossier local contenant les fichiers MySQL
– nous exécutons des instructions destinées par exemple à créer la structure de la BDD si besoin.

 
```


### Conclusion

```
Les possibilités sont vastes et parfois complexes.
Les exemples pris ici sont extrêmement simples.
Par ailleurs “docker-compose” est à ce jour encore en “bêta” de même qu’une série d’autres outils :
“docker-machine”, “docker-swarm” destinés à améliorer et fluidifier le déploiement et la scalabilité des applications.
Il n’en reste pas moins que l’utilisation de docker sur des machines de production est tout à fait pertinent.
Pour le développement il pourrait s’imposer comme un outil de normalisation particulièrement efficace :
– mise en place d’images communes entre les développeurs,
– maintenance de ces images,
– ensemble applicatifs pré-configurés grâce à “docker-compose”
– des environnements de dev/test indépendants des systèmes d’exploitation.
```

```
En conclusion, plongez sans plus tarder dans l’univers de Docker et de sa multitude 
d’images disponibles qui permettent en quelques clics d’installer un serveur solr, Apache, Mysql,
MongoDB et tout cela indépendemment du système d’exploitation utilisé : MacOSX, Linux,
Windows … etc.

