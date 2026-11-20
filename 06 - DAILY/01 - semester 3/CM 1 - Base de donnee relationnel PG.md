
#### 01. Perform any necessary post-installation setup 

```txt 
mysql_secure_installation
set root password 
Remove test DB 
Disable remote root access
```

installation sur <font color="#BAFF29" style="font-weight: bold; text-decoration: underline; font-size: 18px">linux</font>

```bash 
# createe une image mysql 
sudo docker run --rm -it -v $(pwd)/postgres/database ubuntu:latest bash

# installer mysql sur votre machine 
sudo apt install mysql-server -y

# activer le serveur postgres
service mysql start # ou bien 'sysemctl start mysql' si systemd et installe

```

methode 2 : methode simple pour installer postgresql

```bash 
sudo apt install postgresql postgresql-contrib -y # intstaller postgres 
psql --version # verifier la version de postgresql

# demarer le serveur postgres
sudo service postgresql start  
# changer au postgres utilisateur 
sudo su - postgres
# lancer l'interpreteur 
psql
# cree un utilisateur 
create user houssam with password 'P@ssw0rd';
# donner houssam tout les privuleges sur la base de donnee entreprise 
grant all privileges on database entreprise to houssam; 
```

#### <font color="#F61067">Remarque : Probleme de connection dans mon container </font>

apres la creation d'un conteneurs j'ai eu des problemes de connection pour installer des packages necessaire voila la solution : 

1. Etape 1 : vous devez faire un update apres upgrade des packages de votre distro comme ceci 

```bash
sudo apt update && apt full-upgrade
```


---

#### 02. configuration initiale pour votre serveur sql : 

```sql 
-- autoriser les connection a distance du root au serveur mysql 
Alter USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'P@ssword';
```

comment se connecter apres modification d'infos de connection 

```bash 
mysql -u root -pP@ssw0rd # essayer de ne pas faire un espace entre le -p et vptre password
```



#### 03. Les premiers commandes _SQL_ :

```sql
-- Afficher les bases de donnees existants 
show databases; 
```

Afficher le ficher ou les bases de donnes sont stocker 

```sql 
-- on utilisent les variable de system
show variables where variables_name = 'datadir';
```

![[Pasted image 20250908210351.png]]

cree une base de donnees sur mysql 

```sql 
-- pour cree une nouvelle base de donnees
create database testdb;
-- pour changer a cet base de donnee
use testdb;
```

cree une table sur notre table 

```sql 
-- cree une table 
create table tb1 ( id int, name varchar(20) );
-- afficher les tables 
show tables; 
-- ou bien 
show tables from testdb;

-- pour afficher plus d'informations sur votre table 
describe tb1;
```

![[Pasted image 20250908211322.png]]

maintenent si on aller au dossier qui ou se stock nos bases de donnes `/var/lib/mysql/testdb` on va trouver : 

![[Pasted image 20250908211639.png]]

on va trouver que chaque table va etre cree sous le format <font color="#affc41">.ibd</font> 

> [!summary]+ que signifie l'extention .ibd ?
> <font color="#affc41">Les fichers IBD</font> sont des fichiers internes utilisés par le moteur de stockage **InnoDB** de MySQL pour stocker les données des tables, y compris les index et la structure. Ils contiennent des données binaires qui ne peuvent pas être lues avec un simple éditeur de texte.

maintenent on va voire comment restorer une base de donnees deja cree 

```sql 
-- cette commande justement pour cree le chema de notre base de donnee
source /usr/database/sakila-db/sakila-schema.sql;
-- pour inserer des donnees dans notre base de donnees on utilisent la commande 
source /usr/database/sakila-db/sakila-data.sql;
```

<font color="#affc41">Commandes interessantes</font> 

parmis les commandes les plus interessants on trouve la commandes qui permet d'afficher le query qui a ete utiliser pour cree une table 

```sql 
show create table actor\G -- on ajoute \G pour un affichage plus comprihensible
```

![[Pasted image 20250908214748.png]]


--- 

## 01. Partie _Postgres_ : 

tout d'abord on va utiliser docker pour cree des conteneur chaque conteneurs contient une service qu'on va utiliser dans nos tps 

la premier etape c'est d'utiliser cette commandes pour faciliter la resolution des noms, c-a-d pour etre capable de communiquer directement avec les conteneur via leur hostname sont avoir besoin de leur ip etc.

```bash
sudo docker run -d -v /var/run/docker.sock:tmp/docker.sock -v etc/hosts:/tmp/hosts houssam/docker-hoster
```

le fichier compose et celui-ci : 

```yaml
version: "3.8"

services:
  db:
    image: postgres:latest
    container_name: serie_tp
    hostname: serie_tp
    restart: always
    environment: 
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: admin123
      POSTGRES_DB: mydatabase
    ports: 
      - "5432:5432"
    volumes: 
      - ./databases:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4
    container_name: pgadmin_ui 
    hostname: pgadmin_ui
    restart: always
    environment:
      PGADMIN_DEFAULT_EMAIL: Gymhoussam2018@gmail.com
      PGADMIN_DEFAULT_PASSWORD: admin123
    ports:
      - "8080:80"
    depends_on:
      - db
```

### 02. Les commandes postgres 

comment cree une base de donnees. 

```sql
-- cree une base de donnees 
create database entreprise; 
-- afficher les bases de donnees 
\l 
-- ou bien 
\list
```

pour changer de la base de donnees par default a votre base de donnes cree 

```sql 
-- changer a une base de donnees cree 
\c nom_de_base 
```

pour quitter l'interpreteur 

```sql 
\q
```


### 03. TP numero 1 : entreprise 

1. creation de la base de donnees 

```sql
create database entreprise;

-- changer a la base de donnees entreorise 
\c entreprise
```

2. creation des tables

```sql
create table societe ( 
	no_societe int, 
	raison_sociale varchar(30), 
	ville varchar(20), 
	code_postal varchar(5) 
);
```

```sql
create table contrat ( 
	no_contrat int, 
	date_souscription date, 
	duree varchar(30), 
	montant float, 
	societe varchar(30) 
);
```

```sql
create table materiel ( 
	no_materiel int, 
	no_serie varchar(8), 
	designation varchar(50), 
	contract int, 
	categorie int 
);
```

```sql
create table categorie ( 
	no_categorie int, 
	designation varchar(20), 
	caracteristique varchar(80) 
);
```

Ajout des contraintes d'unicite sur l'ensemble des table :

```sql
alter table societe 
	alter column raison_sociale set not null,
	alter column ville set not null, 
	alter column code_postal set not null;
```

```sql
alter table contrat 
	alter column date_souscription set not null, 
	alter column duree set not null,
	alter column montant set not null, 
	alter column societe set not null;
```

```sql
alter table materiel 
	alter column no_serie set not null and unique, 
	alter column designation set not null, 
	alter column contrat set not null,
	alter column categorie set not null;
```

comment definir une column unique sur votre table : 

```sql 
alter table materiel add constraint no_serie_unique unique ( no_serie );ren
```

comment afficher les domaines cree sur votre base de donnees.

```sql
-- Lister tous les domaines
\dD

-- Lister les domaines d'un schéma spécifique
\dD public.*

-- Afficher les détails d'un domaine spécifique
\dD+ nom_du_domaine
```

Remarque : pour decrire un table en postgres on utilisent la commande suivantes 

```sql 
\d nom_table
```

pour changer le nom d'une table on utilisent la commande suivantes :

```sql 
alter table materiel rename column contract to contrat;
```

```sql 
alter table categorie
	alter column designation set not null;
```

--- 

alimentation des bases de donnees 

```sql 
------------------------
---- Table societe -----
------------------------
INSERT INTO societe (no_societe, raison_sociale, ville, code_postal) VALUES
(1, 'TechnoSoft SARL', 'Paris', '75001'),
(2, 'InfoServices SA', 'Lyon', '69002'),
(3, 'DataPro Consulting', 'Marseille', '13008'),
(4, 'NetSolutions', 'Toulouse', '31000'),
(5, 'WebInnov', 'Bordeaux', '33000'),
(6, 'CloudExperts', 'Lille', '59000'),
(7, 'DigitalSoft', 'Nantes', '44000'),
(8, 'TechVision', 'Strasbourg', '67000');

----------------------------
------ table categorie -----
----------------------------
INSERT INTO categorie (no_categorie, designation, caracteristique) VALUES
(1, 'Ordinateurs', 'Matériel informatique de bureau et portable'),
(2, 'Périphériques', 'Souris, claviers, écrans, imprimantes'),
(3, 'Réseau', 'Routeurs, switchs, points d''accès WiFi'),
(4, 'Serveurs', 'Serveurs physiques et baies de stockage'),
(5, 'Téléphonie', 'Téléphones IP et systèmes de communication'),
(6, 'Sécurité', 'Caméras, alarmes, contrôle d''accès');

----------------------------
------ table contrat -------
----------------------------
INSERT INTO contrat (no_contrat, date_souscription, duree, montant, societe) VALUES
(1, '2024-01-15', '12 mois', 12000.00, 'TechnoSoft SARL'),
(2, '2024-02-01', '24 mois', 18500.00, 'InfoServices SA'),
(3, '2024-01-20', '36 mois', 25000.00, 'DataPro Consulting'),
(4, '2024-03-10', '12 mois', 8500.00, 'NetSolutions'),
(5, '2024-02-15', '24 mois', 15000.00, 'WebInnov'),
(6, '2024-03-01', '12 mois', 9500.00, 'CloudExperts'),
(7, '2024-01-30', '36 mois', 32000.00, 'DigitalSoft'),
(8, '2024-02-20', '24 mois', 17500.00, 'TechVision');

-----------------------------
----- table materiel --------
-----------------------------
INSERT INTO materiel (no_materiel, no_serie, designation, contract, categorie) VALUES
(1, 'PC001234', 'Ordinateur portable Dell XPS 15', 1, 1),
(2, 'PC005678', 'Ordinateur bureau HP EliteDesk', 1, 1),
(3, 'ECR00123', 'Écran 24" Samsung', 1, 2),
(4, 'SRV00456', 'Serveur Dell PowerEdge', 2, 4),
(5, 'SW00789', 'Switch Cisco 24 ports', 2, 3),
(6, 'LAP00987', 'Ordinateur portable Lenovo ThinkPad', 3, 1),
(7, 'IPH00111', 'Téléphone IP Yealink', 3, 5),
(8, 'CAM00222', 'Caméra de surveillance Hikvision', 4, 6),
(9, 'IMP00333', 'Imprimante laser HP', 5, 2),
(10, 'RT00444', 'Routeur Cisco', 5, 3),
(11, 'TAB00555', 'Tablette Microsoft Surface', 6, 1),
(12, 'STO00666', 'Unité de stockage NAS Synology', 7, 4),
(13, 'ACC00777', 'Contrôleur d''accès', 8, 6),
(14, 'PH00888', 'Téléphone IP Grandstream', 8, 5),
(15, 'MON00999', 'Écran 27" LG UltraFine', 2, 2);
```

pour vider une table on utilisent la syntaxe suivantes 

```sql 
-- soit on utilisent truncate 
truncate table societe;
-- ou bien on utilisent delete 
delete from societe;
```

pour supprimer des lignes invalid sur postgres on utilisent la commandes suivant :

```sql
-- Bonne commande : utiliser "contrat" au lieu de "contract"
DELETE FROM contrat WHERE date_souscription < '2000-01-01';
```

je doit ajouter les contraintes a ma table contart pour qu'il puisse bloquer les insertion non valide.

```sql 
-- afficher une description de la table
SELECT column_name, data_type, is_nullable, column_default
FROM information_schema.columns
WHERE table_schema = 'public' AND table_name = 'materiel'
ORDER BY ordinal_position;

```

comment on peut associer les domaines a une table deja cree 

```sql 
ALTER TABLE contrat ALTER COLUMN duree TYPE dure_contrat;
ALTER TABLE contrat ALTER COLUMN date_souscription TYPE date_souscription;
ALTER TABLE contrat ALTER COLUMN montant TYPE montant_exige;
```

methode 1 : 

```sql 
-- Création du domaine d'abord
CREATE DOMAIN type_cp AS VARCHAR(5)
CHECK (
    VALUE SIMILAR TO '[0-9]{5}'
    AND VALUE BETWEEN '01000' AND '95999'
);

-- Puis l'utiliser dans la table societe
ALTER TABLE societe 
ALTER COLUMN code_postal TYPE type_cp;
```

methode 2 : en une seule étape avec une contrainte directe

```sql
ALTER TABLE societe 
ADD CONSTRAINT type_cp 
CHECK (
    code_postal SIMILAR TO '[0-9]{5}'
    AND code_postal BETWEEN '01000' AND '95999'
);
```

--- 
connecter a la base de donne `entreprise`

```bash
sudo docker exec -it postgres_db psql -U houssam -d entreprise 
```

### Solution de TP 2 : 

1. A l’aide de PGAdmin, visualisez les données présentes dans les différentes tables afin de mieux comprendre le schéma dela base.

```sql
-- les commande d'affichage des donnees 
select * from clients;
select * from produits;
select * from factures;
select * from remplacements;
select * from interventions;
select * from tauxhoraire;
```

- comment visualiser le shema de la base de donnees

  `on click droit sur notre base de donnee > ERD for database`

![[Pasted image 20250917104657.png]]

apres on va se retrouver avec ce shema global de toutes les table qui exist dans notre base de donnne.

![[Pasted image 20250917104811.png]]

2. determinent les cles primaire et cle etranger pour chaque table

![[Pasted image 20250917105602.png]]

3. deduire l'ordre de la distruction des tables

```sql 
drop table clients;
drop table produits;
drop table facture; 
drop table remplacements;
drop table tauxhoraire;
drop table interventions;
```

lors du processus de distructions des tables l'ordre n'as pas aucun impacte sur l'execution des requete if faut juste toujoure mettre la commande `drop table interventions;` comme derniere drop car cette table depond de plusieur table donc on doit supprimer d'abord ces table la et apres on peut supprimer la totalite.

supprimer toutes les donnes des tables 

```sql 
delete from interventions;
delete from clients;
delete from produits;
delete from remplacements;
delete from factures;
delete from tauxhoraire;
```


## La Modelisation ( Data Modelling ) :

dans cette partie on va explorer les differents type de modelisation 

##### 01. One to One [ un a un ] : 

![[Pasted image 20250920114542.png]]

dans ce type les deux entite doivent referencer a un et un seule record dans la base de donnees 
dans notre exemple la personne doit avoir un et un seule profile et aussi le profile doit etre appartient a un et une seulent personne c'est pour cela la valeur de <font color="#affc41">user_id</font> doit etre unique dans la table profile.

###### Exemple du code : 

```sql 
-- creation de la table personne
create table person (
	id serial primary key, 
	name varchar(40)
);
-- creation de la table profile 
create table profile (
	id serial primary key. 
	person_id int unique, 
	followers int default 0
	-- table constraintes 
	foreign key (person_id) references person(id)
);
```

##### 01. One to Many [ un a plusieurs ]: 

![[Pasted image 20250920121339.png]]

dans ce type de relation l'un des entite peut avoir plusieurs references dans l'autre entite 

###### Exemple du code : 

```sql 
-- create table departement 
create table departememt (
	id serial primary key, 
	name varchar(30) not null
);
-- create table employe 
create table employe ( 
	id serial primary key, 
	departement_id int references departement(id), 
	name varchar(30) not null
);
-- insertion des donnes 
insert into departement(name) values 
('IT'), ('HR'), ('Sales');

-- insertion dans la table employee 
insert into employe(departement_id, name) values 
(1, 'houssam bechar'); 
```


##### 01. Many to Many [ Plusieur a Plusieur ] : 

![[Pasted image 20250920150401.png]]

dans le cas d'une relation plusieur a plusieur chaque entite peut referencer a plusieur entite dans la base de donnee 

###### Exemple du code : 

```sql
-- table student 
create table student (
	id serial primary key,
	name varchar(100) not null 
;
-- table class 
create table class (
	id serial primary key, 
	name varchar(100) not null 
);
-- table student_class 
create table student_class (
	student_id int references student(id), 
	class_id int references class(id),
	primary key (student_id, class_id)
);
```

ona choisie de faire un cle primaire compose pour qu'il soit possible au etudients de s'inscrire a plusieur class au meme temps sans aucun probleme.