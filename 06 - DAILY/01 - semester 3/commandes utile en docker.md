apres avoir utiliser docker `compose` pour cree des conteneurs associe, et aussi pour simplifier le processus de gestion de plusieurs conteneurs dependents 

on utilisent les commandes suivantes : 

pour demarrer les conteneurs 

```bash 
sudo docker compose up -d
```

pour l'arret des conteneurs 

```bash 
sudo docker compose down # supprime les contenurs 
sudo docker compose stop # juste arreter sans supprimer les conteneurs
```