---
tags:
  - coure
  - virtualisation
  - cloud-computing
date: 14-02-2025
professor: Pr. Hamime
cssclasses:
---




###### 05. domaine d'application

- L'installation de VMware workstation genere des fichier 
	- Fichier de configuration (.vmx) : ce fichier contient les parametere de la VM (RAM, CPU ...)
	- Fichier de disque virtuel (.vmdk) : Represente le disque dur virtuel de la VM 
	- Fichier d'etat de suspendu (.vmss) : fichier est cree lorsque la VM est mise en pause (mode suspendu) il enregistre l'etat exact de la RAM, une repise instantanee.
	- Fichier de journal (.log) : historique des evenements enregistre les actions importants 
	- Fichier journal (.nvram) (BIOS/UEFI) : il font
	- Fichier de verouillage (.KK) : 
	- Fichier snapchot : 
	- Fichier Bridge (Mode pont) : 

	- comment configurer les VMnet :
		- <font color="affc41">Bridge :</font> Ce mode connecte directement la VM, au reseau physique de l'hote. Le VM 
		- <font color="#affc41">NAT :</font> le VM utilisent la connection internet de l'hote mais n'est pas directement visible sur le reseau local.
		- Host only : Le VM peut comminuquer uniquement avec la machine host seulemt.
---

###### TP 1 : 

- Etape 5 : j'ai eu une erreur voila la solution surtout apre la tentative de redemarer l'interface eth0.

```bash 
❌ 📌 Étape 4 : Forcer la Suppression de l'IP
Si le problème persiste, supprime l'IP actuelle avant de redémarrer :

bash
Copy
Edit
sudo ip addr flush dev eth0
sudo systemctl restart networking
Dis-moi si ça fonctionne ou si tu obtiens une autre erreur ! 🚀
```


---

## 02. Gerer des snapshot dans VMware :

- un snapshot permet de capturer l'etat d'uneVM a un instant, afin d'y revenir plus tard dans le temps
- il ne sauvguarde pas toutes le VM, mais plutot les diff entre l'etat actuel et l'etat enregistre 
- snapshot c'est pour les machine vertuel, point de restoration c'est pour les system d'expoloitation.

> [!error]+ Note bien :
> il est important de preciser qu'un snapshot n'est pas la remplacer les sauvguarder 


## 02. L'isolation avec docker : 

- probleme : si un team veulle developper une application web en utilisent ( flask, postgresql, nodejs ) mais le probleme qui ce pose c'est que chaque menbre de team utilisent un systeme d'exploitation different 
	- Dev 1 : utilisent le noyeau Linux.
	- Dev 2 : utilisent windows.
	- Dev 3 : 
	aussi le probleme c'est que chaque dev doit utiliser les memes dependences pour qu'il soit capable de travailer en collaboration sur la meme application.
	
- L'idee ou bien la solution est de cree un envirenement virtuel isole ( fonction de maniere independente par repport a l'os hote ) et identique pour tout les developpeurs, quelle que soit leur platforme
	- L'utilisation des conteneurs : 
		- Envirenement standarise : 
		- Une isolation simplifie :
		- Une compatibilite assure entre developpement, test de production 
		- Un isolation des composants 

##### 01. Qu'est ce qu'un conteneur ? 

- Un conteneur est un concept : un moyen de sparer et isoler des application ou des processus qui s'executent sur un meme hote ( Pricipe d'isolation )
- Les conteneurs partagent le meme noyau OS et 
- Le concept d'isolation a apparus en 2008 par LXC ( Linux Containers )

##### 02. Les composents de docker 

1. <font color="#BAFF29" style="text-decoration: underline">docker image :</font> une image docker est une Template immutable qui contient tout le necessaire pour executer une application dans un conteneur Qui incluent : 
	- Le code de l'application -> app.py
	- Les dependances et bibliotheque requires -> requirements.txt
	- sl

	- Legere 
	- versionnable 
	- immuable 
	- portable

2. <font color="#BAFF29" style="text-decoration: underline">docker container :</font> et une instance d'une image
	- isole
	- emphemere : dure de vie courte 
	- leger 
	- portabilite

3. <font color="#BAFF29" style="text-decoration: underline">docker registry :</font> est un systeme de stockage et de distribution d'image docker, il permet de stocker et partager des images docker
	- Dcoker repo 
	- Docker Hub
	- Private registry

4. <font color="#BAFF29" style="text-decoration: underline">Docker client :</font> c'est l'interface qui permet aux utilisateurs d'interagir avec docker. c'est un outil en ligne de commande qui envoie des commandes docker au client deamon.

5. <font color="#BAFF29" style="text-decoration: underline">Docker deamon :</font> c'est l'unite responsable de gestion et d'orcestration des conteneurs et des images.