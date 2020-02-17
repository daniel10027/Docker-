![Image of Yaktocat](https://www.lebigdata.fr/wp-content/uploads/2018/05/docker-tout-savoir-660x330.png)
### A la decouverte de Docker

- [x] Petite Histoire 

    
    Les machines virtuelles (VM) sont de plus en plus utilisées par les entreprises.
    Une VM est un environnement de système d’exploitation ou d’application installé sur logiciel.
    Elle permet à l’utilisateur de profiter de la même expérience que sur une machine physique,
    avec plusieurs avantages.

    Il est notamment possible de lancer plusieurs environnements d’OS sur la même machine,
    en les isolant les uns des autres. De même, la virtualisation permet de réduire les
    coûts au sein d’une entreprise en diminuant le nombre de machines virtuelles nécessaires.
    Les besoins en énergie s’en trouvent aussi atténués. Les backups et les restaurations
    s’en trouvent aussi simplifiés.

    Cependant, les hyperviseurs de machines virtuelles reposent sur une émulation du hardware,
    et requièrent donc beaucoup de puissance de calcul. Pour remédier à ce problème, 
    de nombreuses firmes se tournent vers les containers, et par extension vers Docker.

    
### 1. Qu'est ce qu'un conteneur ?

   
    Avant d’aborder Docker, il est indispensable de rappeler ce qu’est une image container.
    Il s’agit d’un ensemble de processus logiciels léger et indépendant, regroupant tous les 
    fichiers nécessaires à l’exécution des processus : code, runtime, outils système,
    bibliothèque et paramètres.
    Ils peuvent être utilisés pour exécuter des applications Linux ou Windows.
    
    
    Les containers sont donc proches des machines virtuelles,
    mais présentent un avantage important. Alors que la virtualisation consiste à 
    exécuter de nombreux systèmes d’exploitation sur un seul et même système, 
    les containers se partagent le même noyau de système d’exploitation 
    et isolent les processus de l’application du reste du système.
    
    
    Pour faire simple, plutôt que de virtualiser le hardware comme l’hyperviseur,
    le container virtualise le système d’exploitation.
    Il est donc nettement plus efficient qu’un hyperviseur en termes de consommation 
    des ressources système. Concrètement, il est possible d’exécuter près de 4 à 6 fois 
    plus d’instances d’applications avec un container qu’avec des machines 
    virtuelles comme Xen ou KVM sur le même hardware.
    

### 2. Docker , qu'est ce que c'est ?

    - Définition 
    
    
    Docker est un outil open source, destiné aux développeurs 
    et administrateurs systèmes, 
    dont l’objectif est de faciliter le développement,
    la diffusion et le déploiement d’applications web autonomes.
    Son principal intérêt est d’assembler les briques d’une application en conteneurs 
    pouvant être partagés, sous forme d’images, au travers d’un registre (“docker registry”) 
    et de les exécuter quels que soient la plateforme et l’environnement. Grâce à Docker,
    les applications deviennent   portables et exécutables
    n’importe où : d’ordinateurs portables Mac ou Windows, des machines virtuelles, 
    de serveurs de production etc.
    
    
    
    - Comment ça marche ?
    
    
    A la différence d’un système de virtualisation classique,
    les conteneurs Docker partagent les ressources de la machine hôte et font l’économie 
    de l’installation d’un système  d’exploitation complet.
    Le conteneur ne contient donc que la partie applicative nécessaire ainsi que ses dépendances,
    et fonctionne de la même façon que pour les machines virtuelles de façon isolée et autonome.
    
    
### 3. Docker , quelles sont les fonctionnalités ?

    

    La plateforme de conteneurisation repose sur sept composants principaux. 
    Le Docker Engine est un outil client-serveur sur lequel repose la technologie de 
    container pour
    prendre en charge les tâches de création d’applications basées container.
    Le moteur crée un processus daemon server-side permettant d’héberger les images, 
    les containers, les réseaux et les volumes de stockage. 
    Ce daemon fournit aussi une interface SLI client-side permettant aux utilisateurs 
    d’interagir avec le daemon via l’API de la plateforme.

    Les containers créés sont appelés Dockerfiles.
    Le composant Docker Compose permet de définir la composition des composants au sein d’un 
    container dédié.
    Le Docker Hub est un outil SaaS permettant aux utilisateurs de publier et de partager 
    des applications 
    basées container via une bibliothèque commune.

    Le mode Docker Swarm du Docker Engine prend en charge l’équilibrage des charges des 
    clusters .
    Ainsi, les ressources de plusieurs hôtes peuvent être rassemblées pour agir comme 
    une seul ensemble.
    Ainsi, les utilisateurs peuvent rapidement échelonner le déploiement de containers.

    
### 4 . Les avantages et inconvenients 

![Image of Yaktocat](https://www.lebigdata.fr/wp-content/uploads/2018/05/docker-avantages.jpg)

    ````
    La plateforme Docker présente de nombreux avantages. 
    Elle permet de composer, de créer, de déployer et d’échelonner rapidement des 
    containers sur les hôtes Docker. Elle offre aussi un haut degré de portabilité,
    ce qui permet aux utilisateurs de s’enregistrer et de partager des containers 
    sur une large variété d’hôtes au sein d’environnements publics et privés.

    Par rapport aux machines virtuelles, Docker présente également plusieurs avantages.
    Elle permet de développer des applications de façon plus efficiente,
    en utilisant moins de ressources, et de déployer ces applications plus rapidement.

    Cependant, elle présente aussi plusieurs inconvénients. Il peut être difficile
    de gérer de façon efficiente un grand nombre de containers simultanément.
    De plus, la sécurité être un problème. Les containers sont isolés, mais 
    partagent le même système d’exploitation. De fait, une attaque ou une 
    faille de sécurité sur l’OS peut compromettre tous les containers. 
    Pour minimiser ce risque, certaines entreprises exécutent leurs 
    containers au sein d’une machine virtuelle.

    




### - [x] Suivant =>> : Installation 









