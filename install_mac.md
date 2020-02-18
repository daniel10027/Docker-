Installer Docker Desktop sur Mac
Temps de lecture estimé: 6 minutes
Pour télécharger Docker Desktop, accédez à Docker Hub et connectez-vous avec votre ID Docker.

Télécharger depuis Docker Hub

En téléchargeant Docker Desktop, vous acceptez les termes de l' accord de licence utilisateur final du logiciel Docker et de l' accord de traitement des données Docker .

À savoir avant d'installer 
LISEZ EN PREMIER pour les utilisateurs de Docker Toolbox et Docker Machine

Si vous exécutez déjà Docker sur votre ordinateur , lisez d'abord Docker Desktop pour Mac vs Docker Toolbox pour comprendre l'impact de cette installation sur votre configuration existante, comment configurer votre environnement pour Docker Desktop sur Mac et comment les deux produits peuvent coexister .

Relation avec Docker Machine : l'installation de Docker Desktop sur Mac n'affecte pas les machines que vous avez créées avec Docker Machine. Vous avez la possibilité de copier des conteneurs et des images de votre defaultmachine locale (le cas échéant) vers la machine virtuelle Docker Desktop HyperKit . Lorsque vous exécutez Docker Desktop, vous n'avez pas besoin que les nœuds Docker Machine s'exécutent localement (ou ailleurs). Avec Docker Desktop, vous disposez d'un nouveau système de virtualisation natif en cours d'exécution (HyperKit) qui remplace le système VirtualBox. Pour en savoir plus, consultez Docker Desktop pour Mac vs Docker Toolbox .

Configuration requise 
Votre Mac doit répondre aux exigences suivantes pour réussir l'installation de Docker Desktop:

Le matériel Mac doit être un modèle 2010 ou plus récent, avec la prise en charge matérielle d'Intel pour la virtualisation des unités de gestion de la mémoire (MMU), y compris les tables de pages étendues (EPT) et le mode illimité. Vous pouvez vérifier si votre machine dispose de cette prise en charge en exécutant la commande suivante dans un terminal:sysctl kern.hv_support

Si votre Mac prend en charge le framework Hypervisor, la commande s'imprime kern.hv_support: 1.

macOS doit être la version 10.13 ou plus récente. Nous vous recommandons de mettre à niveau vers la dernière version de macOS.

Si vous rencontrez des problèmes après la mise à niveau de votre macOS vers la version 10.15, vous devez installer la dernière version de Docker Desktop pour être compatible avec cette version de macOS.

Remarque: Docker prend en charge Docker Desktop sur les versions les plus récentes de macOS. Autrement dit, la version actuelle de macOS et les deux versions précédentes. Au fur et à mesure que de nouvelles versions majeures de macOS sont rendues disponibles, Docker cessera de prendre en charge la version la plus ancienne et prendra en charge la dernière version de macOS (en plus des deux versions précédentes).

Au moins 4 Go de RAM.

VirtualBox avant la version 4.3.30 ne doit pas être installé car il n'est pas compatible avec Docker Desktop.

Remarque : Si votre système ne satisfait pas à ces exigences, vous pouvez installer Docker Toolbox , qui utilise Oracle VirtualBox au lieu de HyperKit.

Ce qui est inclus dans le programme d'installation 
L'installation Docker Desktop comprend Docker Engine , le client CLI Docker, Docker Compose , Notary , Kubernetes et Credential Helper .


Installez et exécutez Docker Desktop sur Mac 

1. Double-cliquez Docker.dmgpour ouvrir le programme d'installation, puis faites glisser l'icône Docker vers le dossier Applications.
![images](https://docs.docker.com/docker-for-mac/images/docker-app-drag.png)

2. Double-cliquez Docker.appdans le dossier Applications pour démarrer Docker. (Dans l'exemple ci-dessous, le dossier Applications est en mode d'affichage «grille».)
![images](https://docs.docker.com/docker-for-mac/images/docker-app-in-apps.png)


Vous êtes invité à autoriser Docker.appavec votre mot de passe système après l'avoir lancé. Un accès privilégié est nécessaire pour installer les composants réseau et les liens vers les applications Docker.

Le menu Docker dans la barre d'état supérieure indique que Docker Desktop est en cours d'exécution et accessible à partir d'un terminal.

![images](https://docs.docker.com/docker-for-mac/images/whale-in-menu-bar.png)

Si vous venez d'installer l'application, vous obtenez également un message avec les étapes suivantes suggérées et un lien vers la documentation. Cliquez sur le menu Docker ![images](https://docs.docker.com/docker-for-mac/images/whale-x.png) dans la barre d'état pour fermer cette notification contextuelle.

![images](https://docs.docker.com/docker-for-mac/images/mac-install-success.png)

3. Cliquez sur le menu Docker ( menu baleine) pour voir les préférences et autres options.

4. Sélectionnez À propos de Docker pour vérifier que vous disposez de la dernière version.

Toutes nos félicitations! Vous exécutez maintenant avec succès Docker Desktop.


