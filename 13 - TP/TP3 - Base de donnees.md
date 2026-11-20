### Exercice 1 : 

> Dans le premier exercice on travail sur la base de donnes d'une FPJ 


##### Question 1 : crestion de la base de donnes :

```sql 
CREATE DATABASE FPJ;
```

##### Question 2 : crestion des tables :

```sql
CREATE TABLE Fournisseur ( 
    Codfrs   VARCHAR(4) PRIMARY KEY, 
    Nomfrs   VARCHAR(30), 
    Villefrs VARCHAR(30), 
    Telfrs   VARCHAR(10) DEFAULT '+33700000000'
)

CREATE TABLE Piece ( 
    Codepiece VARCHAR(4) PRIMARY KEY, 
    Nompiece  VARCHAR(30), 
    Couleurpiece VARCHAR(20) DEFAULT 'SANS COULEUR', 
    Poidspiec NUMERIC(5, 2) DEFAULT 0.0, 
    Villepiece VARCHAR(30)
)

CREATE TABLE Directeur (
    Coddirecteur VARCHAR(4) PRIMARY KEY, 
    Nomdirecteur VARCHAR(30)
)

CREATE TABLE Projet ( 
    Codeproj     VARCHAR(4), 
    Nomproj      VARCHAR(50), 
    Villeproj    VARCHAR(30), 
    Budjetproj   NUMERIC(10, 4) DEFAULT 0.0, 
    Coddirecteur INT, 
    FOREIGN KEY ( coddirecteur ) REFERENCES Directeur(coddirecteur)
)

CREATE TABLE Fpj (
    Codfrs     VARCHAR(4), 
    Codpiece   VARCHAR(4), 
    Codproj    VARCHAR(4), 
    qtelivree  INT, 
    dateliv    DATE DEFAULT NOW()
)
```
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :

##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :
##### Question 1 : crestion de la base de donnes :##### Question 1 : crestion de la base de donnes :