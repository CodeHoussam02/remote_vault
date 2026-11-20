

###### Etape 1 : Creation des tables 

```sql 
-- creation de la table client; 
CREATE TABLE client(
	NCL SMALLINT PRIMARY KEY,
	Nom VARCHAR(15),
	Prenom VARCHAR(15),
	Adresse VARCHAR(15)
);

-- Code creation de la table TypeChambre
CREATE TABLE Typechambre(
	NTC DECIMAL(2, 0) PRIMARY KEY,
	Nom VARCHAR(20), 
	FL  NUMERIC(6,2)
);

-- Creation de la table chambre
CREATE TABLE Chambre( 
	NC DECIMAL(2, 0) PRIMARY KEY, 
	NTC DECIMAL(2, 0), 
	FS  NUMERIC(6, 2), 
	FOREIGN KEY (NTC) REFERENCES typechambre(NTC)
);	

-- Creation de la table Location 
CREATE TABLE Location( 
	NCL SMALLINT, 
	NCH SMALLINT, 
	DL  DATE, 
	PL  SMALLINT CHECK ( PL >= 0 ), 
	PRIMARY KEY (NCL, NCH, DL),
	FOREIGN KEY (NCL) REFERENCES client(NCL), 
	FOREIGN KEY (NCH) REFERENCES chambre(NC)
);
```

List of relations
+-----------+--------------+--------+----------+
|  Schema   |     Name     | Type   |  Owner.  |   
+-----------+--------------+--------+----------+
|  public   |    chambre   | table  | admin.   |
+-----------+--------------+--------+----------+
|  public   |    client    | table  | admin.   |
+-----------+--------------+--------+----------+
|  public   |    location  | table  | admin.   |
+-----------+--------------+--------+----------+
|  public   | typechambre  | table  | admin.   |
+-----------+--------------+--------+----------+
(4 rows)

##### Etape 2 : insertion des donnees :

j’ai utiliser un check sur la colonne Location(PL) pcq le moteur postgresql ne support pas un type <font color="#3FFC6D9">UNSIGNED</font> danc au lieur j’ai fait un check pour verifier que toujour la valeur sera supperieur a 0.
###### 2. Insertion des donnes dans la base de donnes :

[1]. hydratation de la table TypeChambre avec l’ensemble des lignes.

```sql 
INSERT INTO Typechambre VALUES 
	(1, 'Chambre Double',70), 
	(2, 'Chambre Simple',100),
	(3, 'Chambre Double avec TV',150), 
	(4, 'Chambre Simple avec TV',200);
```

l’aure de l’insertion des donnes dans la base de donnes Typechambre ona rencontre un probleme surtt dans la colonne <font color="#F61067">Nom</font> de chambre qui semble tres courte pour certain lnsertion 

apres qu’ona demander au prof nous avons decide de changer la taille de cette colonne pour accepter toutes les insertion donnes dans le TP par la commande suivant.

```sql 
ALTER TABLE Typechambre 
ALTER COLUMN Nom TYPE VARCHAR(50); 
```

+-----------+------------------------+--------+
|    ntc    | nom                    |   fl   |
+-----------+------------------------+--------+
   1        | Chambre Double         |  70.00
   2        | Chambre Simple         | 100.00
   3        | Chambre Double avec TV | 150.00
   4        | Chambre Simple avec TV | 200.00
+-----------+------------------------+--------+
(4 rows)

##### Question 3 : Afficher la valeur maximale et minimale des frais de location des types de chambre.

```sql
SELECT 
		MIN(FL) AS FRAIS_MINIMAL, 
		MAX(FL) AS FRAIS_MAXIMAL
FROM typechambre;
```

Resultat : 

 frais_minimal | frais_maximal
---------------+---------------
         70.00 |        200.00
(1 row)

##### Question 4 : Afficher le nombre de types de chambre existants.

```sql
SELECT COUNT(ntc) AS Nembre_de_chambre
FROM typechambre;
```

Resultat : 

+-------------------+
| nembre_de_chambre | 
+-------------------+
|                 4 |
+-------------------+
(1 row)

##### Question 5 : Modifier le nom du type de chambre N°3, le nouveau nom est ‘Chambre Double Luxe’.

```sql
UPDATE Typechambre
SET nom = 'Chambre Double Luxe' 
WHERE ntc = 3;
```

Avant : 

 ntc |          nom           |   fl
-----+------------------------+--------
   1 | Chambre Double         |  70.00
   2 | Chambre Simple         | 100.00
   3 | Chambre Double avec TV | 150.00
   4 | Chambre Simple avec TV | 200.00
(4 rows)

Apres : 

 ntc |          nom           |   fl
-----+------------------------+--------
   1 | Chambre Double         |  70.00
   2 | Chambre Simple         | 100.00
   4 | Chambre Simple avec TV | 200.00
   3 | Chambre Double Luxe    | 150.00
(4 rows)


##### Question 6 : Ajouter 15% aux frais de location des types de chambre dont les frais de location sont inférieurs à 150.

```sql
UPDATE typechambre 
SET fl = fl + (fl * 0.15)
WHERE fl < 150;
```

Resultat : 

 ntc |          nom           |   fl
-----+------------------------+--------
   4 | Chambre Simple avec TV | 200.00
   3 | Chambre Double Luxe    | 150.00
   1 | Chambre Double         |  80.50
   2 | Chambre Simple         | 115.00
(4 rows)

##### Question 7 : Retrancher 5% des frais de location des types de chambre dont le numéro est entre 2 et 4.

```sql
UPDATE Typechambre
SET fl = fl - (fl*0.05)
WHERE ntc BETWEEN 2 AND 4;
```

Resultat :

 ntc |          nom           |   fl
-----+------------------------+--------
   1 | Chambre Double         |  80.50
   2 | Chambre Simple         | 109.25
   3 | Chambre Double Luxe    | 142.50
   4 | Chambre Simple avec TV | 190.00
(4 rows)

##### Question 8 : Supprimer les types de chambre dont les frais de location sont inférieurs à 100 ou supérieurs à 150.

```sql 
DELETE FROM typechambre
WHERE fl < 100 OR fl > 150;
```

Resultat : 

 ntc |         nom         |   fl
-----+---------------------+--------
   2 | Chambre Simple      | 109.25
   3 | Chambre Double Luxe | 142.50
(2 rows)

##### Question 9 :  Afficher pour chaque type de chambre le numéro du type de chambre ainsi que la somme et la moyenne des frais supplémentaires.

```sql 
ALTER TABLE chambre
ALTER COLUMN nc TYPE NUMERIC(4, 0);
```

changer la taille des de la colonne nc pour qu’il puisse accept des valeur large comme “101” par exemple

```sql
SELECT 
	TC.ntc, 
	SUM(fs) AS SOMME_DES_FRAIS_SUPP, 
	ROUND(AVG(fs), 2) AS MOYENNE_DES_FRAIS_SUPP
FROM Typechambre TC
INNER JOIN Chambre C ON TC.ntc = C.ntc
GROUP BY TC.NTC;
```

Resultat 

 ntc | somme_des_frais_supp | moyenne_des_frais_supp
-----+----------------------+------------------------
   3 |                29.50 |                   9.83
   2 |                30.00 |                  10.00
(2 rows)

##### Question 10 : Afficher pour chaque type de chambre le numéro du type de chambre ainsi que le max et le min des frais supplémentaires.

```sql 
SELECT 
	NTC NUM_TY_CH, 
	MAX(fs) MAX_FRAIS_SUP,
	MIN(fs) MIN_FRAIS_SUP
FROM Chambre C 
GROUP BY NTC; 
```

 num_ty_ch | max_frais_sup | min_frais_sup
-----------+---------------+---------------
         3 |         20.00 |          4.00
         2 |         15.00 |          5.00
(2 rows)
##### Question 11 : Ajouter 20 aux FS des chambres dont le type de chambre a des frais de location  inférieurs à 120

```sql 
UPDATE Chambre 
SET FS = FS + 20 
WHERE NTC IN ( 
     SELECT NTC 
     FROM typechambre 
     WHERE FL < 120
);
```

Resultat : 

 nc | ntc |  fs
----+-----+-------
 21 |   3 |  4.00
 22 |   3 | 20.00
 23 |   3 |  5.50
 11 |   2 | 30.00
 12 |   2 | 25.00
 13 |   2 | 35.00
(6 rows)

##### Question 12 : Retrancher 15 des FS des chambres ‘Double’.

```sql
UPDATE chambre 
SET FS = FS - 15 
WHERE NTC IN (
     SELECT NTC 
     FROM typechambre 
     WHERE Nom LIKE '%Double%'
);
```

 nc | ntc |   fs
----+-----+--------
 11 |   2 |  30.00
 12 |   2 |  25.00
 13 |   2 |  35.00
 21 |   3 | -11.00
 22 |   3 |   5.00
 23 |   3 |  -9.50
(6 rows)

##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.

```sql 
ALTER TABLE typechambre
ALTER COLUMN FL SET DEFAULT 150;
```

##### Question 14 :  Insérer un tuple dans la table TypeChambre sans spécifier de valeur pour le champ FL.

```sql 
INSERT INTO typechambre(NTC, NOM) VALUES 
       (5, 'Chambre King');
```

Resultat : 

 ntc |          nom           |   fl
-----+------------------------+--------
   1 | Chambre Double         |  70.00
   2 | Chambre Simple         | 100.00
   3 | Chambre Double avec TV | 150.00
   4 | Chambre Simple avec TV | 200.00
   5 | Chambre King           | 150.00
(5 rows)

##### Question 15 : Afficher le contenu de la table TypeChambre pour voir la valeur affectée par défault à  FL.

```sql 
DESCRIBE Typechambre;
```

```md
                   Table "public.typechambre"
 Column |         Type          | Collation | Nullable | Default
--------+-----------------------+-----------+----------+---------
 ntc    | numeric(2,0)          |           | not null |
 nom    | character varying(40) |           |          |
 fl     | numeric(6,2)          |           |          | 150
Indexes:
    "typechambre_pkey" PRIMARY KEY, btree (ntc)
Referenced by:
    TABLE "chambre" CONSTRAINT "chambre_ntc_fkey" FOREIGN KEY (ntc) REFERENCES typechambre(ntc)
```
##### Question 16 :  Supprimer la valeur par défaut attribuée au champ FL.

```sql 
ALTER TABLE Typechambre 
ALTER COLUMN FL DROP DEFAULT;
```

```md 
                   Table "public.typechambre"
 Column |         Type          | Collation | Nullable | Default
--------+-----------------------+-----------+----------+---------
 ntc    | numeric(2,0)          |           | not null |
 nom    | character varying(40) |           |          |
 fl     | numeric(6,2)          |           |          |
Indexes:
    "typechambre_pkey" PRIMARY KEY, btree (ntc)
Referenced by:
    TABLE "chambre" CONSTRAINT "chambre_ntc_fkey" FOREIGN KEY (ntc) REFERENCES typechambre(ntc)
```

##### Question 17 :  Ajouter à la Table Chabmre un champ NE (Numéro Etage) de type INT UNSIGNED,  en spécifiant comme valeur par défaut 1. Ce champ doit etre ajouté juste après le champ  NC.



```sql 
-- VERSION MariaDB 
ALTER TABLE chambre 
ADD COLUMN NE INT UNSIGNED;

-- VERSION Postgres
ALTER TABLE chambre 
ADD COLUMN NE INT CHECK (NE >= 0);
```

Resultat : 

```md
                 Table "public.chambre"
 Column |     Type     | Collation | Nullable | Default
--------+--------------+-----------+----------+---------
 nc     | numeric(2,0) |           | not null |
 ntc    | numeric(2,0) |           |          |
 fs     | numeric(6,2) |           |          |
 ne     | integer      |           |          |
Indexes:
    "chambre_pkey" PRIMARY KEY, btree (nc)
Check constraints:
    "chambre_ne_check" CHECK (ne >= 0)
Foreign-key constraints:
    "chambre_ntc_fkey" FOREIGN KEY (ntc) REFERENCES typechambre(ntc)
Referenced by:
    TABLE "location" CONSTRAINT "location_nch_fkey" FOREIGN KEY (nch) REFERENCES chambre(nc)
```

##### Question 18 : Afficher par type de chambre le minimum et le maximum des frais de locations mais  uniquement pour les types de chambre dont le minimum des frais de location est  inférieur à 120.

```sql 
SELECT 
      NTC AS NUM_TP_CH, 
      Nom, 
      MAX(FL) AS MAX_FRAIS_LO,
      MIN(FL) AS MIN_FRAIS_LO 
FROM typechambre 
GROUP BY NTC, NOM
HAVING MIN(FL) < 120;
```

Resultat : 

 num_tp_ch |      nom       | max_frais_lo | min_frais_lo
-----------+----------------+--------------+--------------
         2 | Chambre Simple |       100.00 |       100.00
         1 | Chambre Double |        70.00 |        70.00
(2 rows)

##### Question 19 : Afficher par type de chambre le minimum et le maximum des frais de locations mais  uniquement pour les types de chambre dont le minimum des frais de location est  supérieur à 120 et les frais supplémentaires sont inférieurs à 6.

```sql 
SELECT 
    TC.NTC AS NUM_TYP_CH,
    TC.Nom, 
	MAX(FL) AS MAX_FRAIS_LO,
    MIN(FL) AS MIN_FRAIS_LO  	        
FROM Chambre C
INNER JOIN Typechambre TC ON TC.NTC = C.NTC
WHERE FS < 6
GROUP BY TC.NTC, TC.NOM 
HAVING MIN(FL) > 120; 
```

Resultat : 

 num_typ_ch |          nom           | max_frais_lo | min_frais_lo
------------+------------------------+--------------+--------------
          3 | Chambre Double avec TV |       150.00 |       150.00
(1 row)


##### :LiCircleQuestionMark: Question 20 : Afficher par type de chambre le nombre de chambres existant pour lesquelles la  moyenne des frais de location est entre 100 et 200.

```sql 
SELECT 
    TC.NTC AS NUM_TYP_CH,
    TC.Nom, 
    ROUND(AVG(FL), 2) AS AVG_FRAIS_LOC
FROM Chambre C
INNER JOIN Typechambre TC ON C.NTC = TC.NTC
GROUP BY TC.NTC, TC.Nom
HAVING AVG(FL) BETWEEN 100 AND 200;
```

Resultat : 

 num_typ_ch |          nom           | avg_frais_loc
------------+------------------------+---------------
          3 | Chambre Double avec TV |        150.00
          2 | Chambre Simple         |        100.00
(2 rows)

##### Question 21 : Insérer des clients dans la table Client.

```sql 
INSERT INTO Client (NCL, Nom, Prenom, Adresse) VALUES
    (1, 'Alaoui',  'Ali',    '12 rue de Paris, Créteil'),
    (2, 'Martin',  'Sophie', '5 avenue Foch, Paris'),
    (3, 'Bernard', 'Lucas',  '8 quai du Rhône, Lyon'),
    (4, 'Benali',  'Sara',   '20 rue Victor Hugo, Nice'),
    (5, 'Durand',  'Paul',   '3 place Bellecour, Lyon'),
    (6, 'Petit',   'Emma',   '14 rue Nationale, Lille');
```

Resultat :

 ncl |   nom   | prenom |          adresse
-----+---------+--------+---------------------------
   1 | Alaoui  | Ali    | 12 rue de Paris, Créteil
   2 | Martin  | Sophie | 5 avenue Foch, Paris
   3 | Bernard | Lucas  | 8 quai du Rhône, Lyon
   4 | Benali  | Sara   | 20 rue Victor Hugo, Nice
   5 | Durand  | Paul   | 3 place Bellecour, Lyon
   6 | Petit   | Emma   | 14 rue Nationale, Lille
(6 rows)

##### Question 22 : Insérer pour chaque client des locations.

```sql 
INSERT INTO Location (NCL, NCH, DL, PL) VALUES
    (1, 11, '2026-01-10', 3),
    (1, 21, '2026-02-14', 2),
    (1, 12, '2026-03-05', 1),
    (1, 22, '2026-05-20', 4),
    (1, 13, '2026-07-01', 2),
    (2, 12, '2026-04-12', 2),
    (3, 23, '2026-06-03', 3),
    (3, 11, '2026-09-15', 2),
    (4, 22, '2026-08-01', 15),
    (5, 13, '2026-03-22', 4),
    (5, 21, '2026-10-10', 5),
    (6, 11, '2026-11-02', 1);
```

Resultat : 

 ncl | nch |     dl     | pl
-----+-----+------------+----
   1 |  11 | 2026-01-10 |  3
   1 |  21 | 2026-02-14 |  2
   1 |  12 | 2026-03-05 |  1
   1 |  22 | 2026-05-20 |  4
   1 |  13 | 2026-07-01 |  2
   2 |  12 | 2026-04-12 |  2
   3 |  23 | 2026-06-03 |  3
   3 |  11 | 2026-09-15 |  2
   4 |  22 | 2026-08-01 | 15
   5 |  13 | 2026-03-22 |  4
   5 |  21 | 2026-10-10 |  5
   6 |  11 | 2026-11-02 |  1
(12 rows)

##### Question 23 : Afficher pour chaque client la somme des FL*PL pour toutes les locations faites par ce client.

```sql 
SELECT 
	C.NCL NUM_CLIENT, 
	C.Nom NOM_CLIENT, 
	SUM(TP.FL*L.PL) CHARGE_TOTAL
FROM Location L 
INNER JOIN Client C ON L.NCL = C.NCL 
INNER JOIN Chambre CH ON L.NCH = CH.NC 
INNER JOIN Typechambre TP ON TP.NTC = CH.NTC 
GROUP BY C.NCL, C.NOM;
```

Resultat : 

 num_client | nom_client | charge_total
------------+------------+--------------
          5 | Durand     |      1150.00
          4 | Benali     |      2250.00
          6 | Petit      |       100.00
          2 | Martin     |       200.00
          1 | Alaoui     |      1500.00
          3 | Bernard    |       650.00
(6 rows)

##### Question 24 : Idem que 15 mais uniquement pour les clients dont le numéro est 1, 3 ou 5.

l’énoncé contient une erreur : « Idem que 15 » doit se lire « Idem que 23 ». La question 15 affiche juste la table `TypeChambre`, ça n’a pas de sens ici. Les trois questions reprennent la requête de la question 23 (la somme FL × PL par client) et ajoutent chacune un filtre différent.

La base, c’est la question 23.

```sql
SELECT 
	C.NCL NUM_CLIENT, 
	C.Nom NOM_CLIENT, 
	SUM(TP.FL*L.PL) CHARGE_TOTAL
FROM Location L  
INNER JOIN Client C ON L.NCL = C.NCL 
INNER JOIN Chambre CH ON L.NCH = CH.NC 
INNER JOIN Typechambre TP ON TP.NTC = CH.NTC 
GROUP BY C.NCL, C.NOM
HAVING C.NCL IN (1, 3, 5);
```

##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.
##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.
##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.
##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.
##### Question 13 : Imposer la valeur 150 comme valeur par défaut pour le champ FL de la table  TypeChambre.