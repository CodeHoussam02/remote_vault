```sql
-- Création de la base de données
CREATE DATABASE ENTREPRISE;

-- Connexion à la base de données (à exécuter séparément après création)
-- \c ENTREPRISE

-- Création des domaines personnalisés
CREATE DOMAIN type_cp AS VARCHAR(5)
	CHECK (VALUE SIMILAR TO '0[1-9][0-9]{3}|[1-8][0-9]{4}|9[0-5][0-9]{3}');

CREATE DOMAIN type_serie AS VARCHAR(8)
	CHECK (VALUE SIMILAR TO '[A-Z][0-9]{3} [0-9]{2}[A-Z]');

-- Création de la table CATEGORIE (créée en premier pour les références)
CREATE TABLE categorie (
    no_categorie INT PRIMARY KEY,
    designation VARCHAR(20) NOT NULL,
    caracteristique VARCHAR(80)
);

-- Création de la table SOCIETE
CREATE TABLE societe (
    no_societe INT PRIMARY KEY,
    raison_sociale VARCHAR(30) NOT NULL,
    ville VARCHAR(20) NOT NULL,
    code_postal type_cp NOT NULL
);

-- Création de la table CONTRAT
CREATE TABLE contrat (
    no_contrat INT PRIMARY KEY,
    date_souscription DATE NOT NULL CHECK (date_souscription >= '2000-01-01'),
    duree INTERVAL NOT NULL CHECK (duree < INTERVAL '5 years'),
    montant MONEY NOT NULL CHECK (montant > 0.0::MONEY),
    societe INT NOT NULL REFERENCES societe(no_societe)
);

-- Création de la table MATERIEL
CREATE TABLE materiel (
    no_materiel INT PRIMARY KEY,
    no_serie type_serie NOT NULL UNIQUE,
    designation VARCHAR(50) NOT NULL,
    contrat INT NOT NULL REFERENCES contrat(no_contrat),
    categorie INT NOT NULL REFERENCES categorie(no_categorie)
);

-- Ajout de la contrainte LIKE pour le numéro de série (5ème caractère = espace)
ALTER TABLE materiel
ADD CONSTRAINT no_serie_format 
CHECK (no_serie LIKE '____ %');
```


----

```sql
INSERT INTO societe(no_societe, raison_sociale, ville, code_postal)
  VALUES(1, 'AIRBUS', 'BLAGNAC', '31700'); ✅
INSERT INTO societe(no_societe, raison_sociale, ville, code_postal)
  VALUES(2, 'ALSTOM', 'XXX', '93400'); ✅  
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(2, '2018-02-01', '3Y 6M', 22000.00, 1); ✅
INSERT INTO materiel (no_materiel, no_serie, designation, contrat, categorie)
  VALUES (1, 'A123 45B', 'rocking chair', 13, 1); ✅
INSERT INTO categorie(no_categorie, designation, caracteristique)
  VALUES (1, 'Mobilier', 'chaise, bureau, étagère, etc.'); ✅

INSERT INTO societe(no_societe, raison_sociale, code_postal)
  VALUES(3, 'BNP PARIBAS', '75009'); ❌ -- la ville n'est pas mentionner ici
-- solution 
insert into societe(no_societe, raison_sociale, code_postal, ville)
	values (3, 'BNP PARIBAS', '75009', 'Paris');

   
INSERT INTO societe(no_societe, ville, code_postal)
  VALUES(4, 'PARIS', '75017'); ❌ -- ici le raison sociale n'est pas mentioner 
  -- solution 
insert into societe(no_societe, ville, code_postal, raison_sociale)
	values (4, 'PARIS', '75017', 'SG')


INSERT INTO contrat(no_contrat, duree, montant, societe)
  VALUES(1, '5Y', 12000.00, 1); ❌ -- ici la date souscription n'est pas specifier 
  -- solution 
insert into contrat(no_contrat, duree, montant, societe, date_souscription)
	values (1, '5Y', 12000.00, 1, '01-12-2002');
   

INSERT INTO materiel (no_materiel, no_serie, contrat, categorie)
  VALUES (2, 'A123 46B', 11, 1); ❌ -- le probleme c'est que la designation est un champ obligatoire qui est pas specifier ici 
INSERT INTO materiel (no_materiel, no_serie, contrat, categorie, designation)
  VALUES (2, 'A123 46B', 11, 1, 'test text here');
  

INSERT INTO materiel (no_materiel, no_serie, designation, contrat)
  VALUES (3, 'A123 47B', 'rocking chair', 9); ❌ -- ici aussi la colonne categorie n'est pas specifier aussi 
insert into materiel (no_materiel, no_serie, designation, contrat, categorie)
	values (3, 'A123 47B', 'rocking chair', 9, 1);
  
  
INSERT INTO materiel (no_materiel, no_serie, designation, categorie)
  VALUES (4, 'A123 48B', 'rocking chair', 1); ❌ -- ici le champ contrat n'exsite pas 
insert into materiel (no_materiel, no_serie, designation, categorie, contrat)
	values (4, 'A123 48B', 'rocking chair', 1, 10);

insert into materiel( no_materiel, no_serie, designation, contrat, categorie ) values (1, 'A123 45B', 'rocking chair', 12, 1); -- ici si on essaye de stocker cette ligne dans notre base de donnees on aura une erreur qui nous disent que cette ligne deja exist ehh c'est parceque dans ce cas la le no_serie et dupliquer dans la table

-- oolution 
insert into materiel( no_materiel, no_serie, designation, contrat, categorie ) values (1, 'A123 45F', 'rocking chair', 12, 1); 
    

```


### 02. creation des domaines simples 


```sql
-- 01. Correction du domaine durée_contrat
create domain dure_contrat interval 
check ( value >= interval '1 day' and value <= interval '5 years' );

-- 02. Domaine date_souscription (attention au format de date)
create domain date_souscription date 
check ( value >= '2000-01-01' );

-- 03. Domaine montant_exige
create domain montant_exige money 
check ( value > 0::money );
```


```sql 
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(9, '2014-03-01', '1Y', 12000.00, 3); ✅
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(10, '1916-03-01', '1Y', 11000.00, 3); ✅
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(15, '1916-03-01', '100Y', 11000.00, 3); ✅
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(11, '2016-03-01', '12Y 6M', 13000.00, 3); ✅
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(24, '2017-03-01', '12Y 6M', -1400.00, 3); 
INSERT INTO contrat(no_contrat, date_souscription, duree, montant, societe)
  VALUES(24, '2017-03-01', '1Y 6M', -1400.00, 3);
```


Pourquoi cette requete ne marche pas : 

```sql 
create table accidents (
gestion(# noacc int primary key, 
gestion(# date date check ( date like 'YYYY-MM-DD' ), 
gestion(# dpt int );
ERROR:  operator does not exist: date ~~ unknown
LINE 3: date date check ( date like 'YYYY-MM-DD' ), 
                               ^
HINT:  No operator matches the given name and argument types. You might need to add explicit type casts.
gestion=# create table accidents ( 
gestion(# noacc int primary key, 
gestion(# date time check ( time like 'yyyy-mm-dd' ), 
gestion(# dpt int );
ERROR:  column "time" does not exist
LINE 3: date time check ( time like 'yyyy-mm-dd' ), 
                          ^
gestion=# create table accidents ( 
noacc int primary key, 
date time check ( date like 'yyyy-mm-dd' ), 
dpt int );
ERROR:  operator does not exist: time without time zone ~~ unknown
LINE 3: date time check ( date like 'yyyy-mm-dd' ), 
                               ^
HINT:  No operator matches the given name and argument types. You might need to add explicit type casts.
gestion=# 
```
``