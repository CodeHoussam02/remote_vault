#### Introduction 

Ce TP a pour but de familiariser avec un système de gestion de bases de données relationnelles, MariaDB, qui est installé sur Debian. On mettra en pratique le langage SQL à travers trois situations concrètes : la gestion des vols d'une compagnie aérienne, la gestion des fournisseurs et des articles, ainsi que la gestion des notes d'une promotion d’étudiants.

Pour chaque exercice, on suit les étapes de la conception d'une base de données :

- modéliser les données à l’aide d’un modèle conceptuel (MCD) et repérer les entités, les associations et les cardinalités ;

- passer au modèle relationnel et créer les tables en utilisant SQL (CREATE TABLE), avec les clés primaires, les clés étrangères et les contraintes d’intégrité (NOT NULL, CHECK, DEFAULT) ;

- insérer des données de test (INSERT) ;

- interroger et gérer la base : faire des sélections, trier, filtrer, mettre à jour, supprimer, utiliser des fonctions d’agrégation (MIN, MAX, AVG, COUNT), des sous-requêtes, des jointures et des vues.

Ce travail permet aussi de comprendre l’importance des contraintes. Par exemple, tenter d’insérer une clé primaire en double ou de référencer un avion qui n’existe pas entraîne l’échec de la requête : c’est le SGBD qui assure la cohérence des données.

###### 1. MCD : Model de conception de donnes 

Le premier exercice traite la modelisation d'une comapgnie aerienne 
et les differents entite qu'on peut retrouve dans une base de donnes 
de ce type ou ona : 
Le modèle comprend trois entités : PILOTE identifié par NP ou *"Numero de Pilote"* , AVION identifié par NA ou "Numero d'avion" et VOL identifié par NV ou "Numero d'avion". Ces trois entités sont connectées par deux associations :

Piloter relie un pilote à un vol. Un vol est géré par un seul pilote (1,1). Un pilote peut gérer zéro ou plusieurs vols (0,n).

Utiliser relie un avion à un vol. Un vol utilise un seul avion (1,1). Un avion peut être utilisé pour zéro ou plusieurs vols (0,n).

Lors de la conversion en modèle relationnel, NP et NA deviennent des clés étrangères dans la table VOL.

![[Pasted image 20261103153121.png]]
###### Code de creation des tables : 
tout d'abord on va cree la base de donnee supposent la bd : <font color="#BAFF29" style="font-size: 18px; font-weight: semi-bold;">Compagnie</font>

```sql 
create database Compagnie;
use Compagnie;
```

On peut aussi exécuter la commande `drop database if exists Compagnie;` avant d'exécuter cette requête pour s'assurer qu'il n'y aura pas de conflit entre les bases de données et éviter une erreur de type <font color="#FF4646" style="font-size: 18px; font-weight: semi-bold;">"ER_DB_CREATE_EXISTS"</font>. Cette approche garantit qu'il ne restera aucun résidu de la base de données précédente.

Après on passe au code de la creation des tables 

|. Code de creation de la table Avion

```sql 
CREATE TABLE Avion (
	NA INT PRIMARY KEY,
	Nom VARCHAR(12),
	Capacite INT,
	Localite VARCHAR(10)

);
```

||. Code de creation de la Pilote : 

```sql 
CREATE TABLE Avion (
    NA        INT PRIMARY KEY,
    Nom       VARCHAR(12),
    Capacite  INT,
    Localite  VARCHAR(10)
);
```

|||. Code de creation de la table Vol : 

```sql 
CREATE TABLE Vol (
    NV  VARCHAR(6) PRIMARY KEY,
    NP  INT,
    NA  INT,
    VD  VARCHAR(10),
    VA  VARCHAR(10),
    HD  INT,
    HA  INT,
    FOREIGN KEY (NP) REFERENCES Pilote(NP),
    FOREIGN KEY (NA) REFERENCES Avion(NA)
);
```


Ajouter les insertion des autres requetes 


###### Question 1 : Insérer les avions suivants dans la table Avion

Ici, on voit que le NA “101” est dupliqué deux fois, ce qui va provoquer une erreur lors de l'exécution de la requête d'insertion des données dans la base de données. Après avoir interrogé M. Jalel, il nous a indiqué que c'est simplement une erreur de frappe. Nous avons donc corrigé en remplaçant la valeur. (101, B737,220,PARIS) par (102, B737,220,PARIS)

```sql 
INSERT INTO Avion VALUES 
	(100, 'AIRBUS', 300, 'PARIS'),
	(101, 'B737', 250, 'NICE'),
	(102, 'B737', 220,'PARIS');
```

###### Question 2 : Afficher tous les avions

Pour afficher l'ensemble des avions dans la table Avion on execute la commande suivantes : 

```sql 
SELECT * FROM Avion;
```

Resultat : 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
| 101 | B737   |      250 | NICE     |
| 102 | B737   |      220 | PARIS    |
+-----+--------+----------+----------+
3 rows in set (0.001 sec)

###### Question 3 : Afficher tous les avions par ordre croissant sur le nom

```sql 
SELECT * FROM Avion 
ORDER BY Avion.nom;
```

Resultat : 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
| 101 | B737   |      250 | NICE     |
| 102 | B737   |      220 | PARIS    |
+-----+--------+----------+----------+
3 rows in set (0.004 sec)

###### Question 4 : Afficher les noms et les capacités des avions

```sql 
SELECT Nom, Capacite 
FROM Avion;  
```

Resultat : 

+--------+----------+
| Nom    | Capacite |
+--------+----------+
| AIRBUS |      300 |
| B737   |      250 |
| B737   |      220 |
+--------+----------+
3 rows in set (0.001 sec)

###### Question 5 : Afficher les localités des avions sans redondance

```sql 
SELECT DISTINCT Localite
FROM Avion;
```

Resultat : 

+----------+
| Localite |
+----------+
| PARIS    |
| NICE     |
+----------+
2 rows in set (0.002 sec)

###### Question 6 : Afficher les avions dans la localité et PARIS ou NICE

```sql
SELECT * 
FROM Avion 
WHERE Avion.Localite in ("PARIS", "NICE");

-- Ou en peut aussi utiliser cette commande : 

SELECT * FROM Avion
WHERE Localite = 'PARIS' OR Localite = 'NICE';

```

Resultat 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
| 101 | B737   |      250 | NICE     |
| 102 | B737   |      220 | PARIS    |
+-----+--------+----------+----------+
3 rows in set (0.002 sec)

###### Question 7 : Modifier la capacité de l’avion numéro 101, la nouvelle capacité et 220

```sql 
UPDATE Avion 
SET capacite = 220
WHERE Avion.NA = 101;
```

Resultat : 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
| 101 | B737   |      250 | NICE     |
| 102 | B737   |      220 | PARIS    |
+-----+--------+----------+----------+
3 rows in set (0.001 sec)

###### Question 8 : Supprimer les avions dans la capacité et inférieure à 200

```sql 
DELETE FROM Avion 
WHERE Avion.Capacite < 200;
```


Resultat : 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
| 101 | B737   |      250 | NICE     |
| 102 | B737   |      220 | PARIS    |
+-----+--------+----------+----------+
3 rows in set (0.001 sec)

###### Question 9 : Afficher la capacité maximale, minimale, moyenne des avions

```sql 
SELECT MAX(Capacite), Min(Capacite), AVG(Capacite)
FROM Avion;
```

Resultat : 

+---------------+---------------+---------------+
| MAX(Capacite) | Min(Capacite) | AVG(Capacite) |
+---------------+---------------+---------------+
|           300 |           220 |      256.6667 |
+---------------+---------------+---------------+
1 row in set (0.002 sec)

###### Question 10 : Afficher les données des avions dont la capacité et la plus basse

```sql 
SELECT * 
FROM Avion 
WHERE Capacite < ( SELECT AVG(Capacite) FROM Avion );
```

Resultat : 

+-----+------+----------+----------+
| NA  | Nom  | Capacite | Localite |
+-----+------+----------+----------+
| 101 | B737 |      250 | NICE     |
| 102 | B737 |      220 | PARIS    |
+-----+------+----------+----------+
2 rows in set (0.002 sec)

###### Question 11 : Afficher les données des avions dont la capacité et supérieure à la capacité moyenne

```sql 
SELECT * 
FROM Avion 
WHERE Capacite > ( SELECT AVG(Capacite) from Avion );
```

Resultat : 

+-----+--------+----------+----------+
| NA  | Nom    | Capacite | Localite |
+-----+--------+----------+----------+
| 100 | AIRBUS |      300 | PARIS    |
+-----+--------+----------+----------+
1 row in set (0.002 sec)

###### Question 12 : Afficher le nom et l’adresse des pilotes assurant les vols IT100 et IT104

```sql 
SELECT P.Nom as NOM_PILOTE, P.Adresse as ADRESSE_PILOTE
FROM Vol as V INNER JOIN Pilote as P
ON V.NP = P.NP 
WHERE V.NV in ('IT100', 'IT104');
```

Resultat : 

+------------+---------------------------+
| NOM_PILOTE | ADRESSE_PILOTE            |
+------------+---------------------------+
| Dupont     | 12 rue de Paris, Paris    |
| Petit      | 20 rue Victor Hugo, Paris |
+------------+---------------------------+
2 rows in set (0.002 sec)
###### Question 13 : Afficher les numéros des pilotes qui sont en service

```sql 
SELECT NOM
FROM Pilote 
WHERE Pilote.NP in ( SELECT np FROM Vol ); 
```

Resultat : 

+---------+
| NOM     |
+---------+
| Dupont  |
| Martin  |
| Bernard |
| Petit   |
+---------+
4 rows in set (0.002 sec)

###### Question 14 : Afficher les numéros des pilotes qui ne sont pas en service

```sql 
SELECT NOM
FROM Pilote 
WHERE Pilote.NP NOT IN ( SELECT np FROM Vol ); 
```

Resultat : 

+--------+
| NOM    |
+--------+
| Durand |
+--------+
1 row in set (0.002 sec)

###### Question 15 : Afficher les noms des pilotes qui conduisent un AIRBUS

```sql 
SELECT P.Nom 
FROM Vol as V
INNER JOIN Pilote as P on V.NP = P.NP 
INNER JOIN Avion as A on V.NA = A.NA
WHERE A.Nom = "AIRBUS";
```

+---------+
| Nom     |
+---------+
| Dupont  |
| Bernard |
| Petit   |
+---------+
3 rows in set (0.002 sec)







### Exercice 2 :

###### 1. MCD : Model de conception de donnes pour l'exercice 2 

### Exercice 3 : 

![[Pasted image 20261104112012.png]]

La question 3 demande « la moyenne de chaque étudiant dans chaque matière ». On ne peut calculer une moyenne que si plusieurs valeurs sont présentes. Ali peut donc avoir, par exemple, deux notes dans la meme matier :

+----------------+-----------+-------------------------+-------------+
|   NEtudiant    |  CodeMat  | Date                    | Note        |
+----------------+-----------+-------------------------+-------------+
|      1 (Ali)   |    MATH   |  2026-10-05             |   12        |
+----------------+-----------+-------------------------+-------------+
|      1 (Ali)   |    MATH   |  2026-12-10             |   16        |
+----------------+-----------+-------------------------+-------------+
|      1 (Ali)   |    BD     |  2026-10-20             |   14        |
+----------------+-----------+-------------------------+-------------+

Choix de l’identifiant de l’association Evaluer

Un étudiant peut être évalué plusieurs fois dans une même matière. C’est ce que montre la question 3, qui demande la moyenne de chaque étudiant dans chaque matière. Par exemple, l’étudiant n°1 peut avoir deux notes en mathématiques : 12 le 05/10 et 16 le 10/12.

Le couple (NEtudiant, CodeMat) ne peut donc pas être utilisé comme clé primaire. Une clé primaire doit être unique pour chaque ligne, or ces deux évaluations ont la même valeur pour ce couple, (1, MATH). Le SGBD refuserait la deuxième insertion avec une erreur de clé dupliquée. Ce qui distingue ces deux évaluations, c’est la date : les triplets (1, MATH, 05/10) et (1, MATH, 10/12) sont différents. La clé primaire de EVALUER est donc le triplet (NEtudiant, CodeMat, Date).

Dans le MCD, une association est identifiée par les identifiants des entités qu’elle relie. Pour que la date fasse partie de l’identifiant de Evaluer, elle doit être elle-même l’identifiant d’une entité. On crée donc une entité DATE, et Evaluer devient une association ternaire qui relie ETUDIANT, MATIERE et DATE.

Enfin, la propriété Note est portée par l’association Evaluer. Une note n’appartient ni à l’étudiant seul, ni à la matière seule, ni à la date seule : elle dépend des trois à la fois, puisqu’elle correspond à un étudiant donné, dans une matière donnée, à une date donnée.


###### Etape 1 : Creation des tables : 

```sql
-- Table Etudient 
CREATE TABLE Etudient (
    NEtudient int primary key, 
    Nom varchar(30) not null, 
    Prenom varchar(30) not null
)
-- Table Matiere 
CREATE TABLE Matiere (
    CodeMat varchar(30) primary key,
    LibelleMat varchar(30) not null, 
    CoeffMat int not null
)
-- Table Evaluer
CREATE TABLE Evaluer (
    NEtudient int, 
    CodeMat varchar(30), 
    DateEval date, 
    Note NUMERIC(2, 4) CHECK (Note BETWEEN 0 AND 20),
    PRIMARY KEY (NEtudient, CodeMat, DateEval),
    FOREIGN KEY (NEtudient) REFERENCES Etudient(NEtudient), 
    FOREIGN KEY (CodeMat)   REFERENCES Matiere(CodeMat) 
);
```

explication : 

###### Etape 2 : Insertion des donnes 

```sql 
-- Table Etudient 
INSERT INTO ETUDIANT VALUES
    (1, 'Alaoui',  'Ali'),
    (2, 'Martin',  'Sophie'),
    (3, 'Bernard', 'Lucas'),
    (4, 'Benali',  'Sara');
    
-- Table Matiere
INSERT INTO Matiere VALUES
    ('MATH', 'Mathématiques',     3),
    ('BD',   'Bases de données',  2),
    ('ANG',  'Anglais',           1);
    
-- Table Evaluations 2 notes par étudiant et par matière
INSERT INTO Evaluer VALUES
    (1, 'MATH', '2026-10-05', 12),
    (1, 'MATH', '2026-12-10', 16),
    (1, 'BD',   '2026-10-20', 14),
    (1, 'BD',   '2026-12-15', 15),
    (1, 'ANG',  '2026-11-03', 10),
    (1, 'ANG',  '2026-12-18', 13);
 INSERT INTO Evaluer VALUES
    (2, 'MATH', '2026-10-05', 17),
    (2, 'MATH', '2026-12-10', 18),
    (2, 'BD',   '2026-10-20', 15.5),
    (2, 'BD',   '2026-12-15', 16),
    (2, 'ANG',  '2026-11-03', 14),
    (2, 'ANG',  '2026-12-18', 15);
 INSERT INTO Evaluer VALUES
    (3, 'MATH', '2026-10-05', 8),
    (3, 'MATH', '2026-12-10', 10),
    (3, 'BD',   '2026-10-20', 9),
    (3, 'BD',   '2026-12-15', 11.5),
    (3, 'ANG',  '2026-11-03', 12),
    (3, 'ANG',  '2026-12-18', 11);
 INSERT INTO Evaluer VALUES
    (4, 'MATH', '2026-10-05', 13),
    (4, 'MATH', '2026-12-10', 11),
    (4, 'BD',   '2026-10-20', 19),
    (4, 'BD',   '2026-12-15', 17),
    (4, 'ANG',  '2026-11-03', 6),
    (4, 'ANG',  '2026-12-18', 9);

```


###### Question 1 : Calculer le nombre total d’étudiants .

```sql 
SELECT COUNT(NEtudient) as Nembre_Etudient
FROM Etudient; 
```

explication : 

Resultat

+-------------------+
| nembre_etudient   |
+-------------------+
|              4    |
+-------------------+
(1 row)

###### Question 2 : Quelles sont, parmi l’ensemble des notes, la note la plus haute et la note la plus basse ?

```sql 
SELECT MIN(Note) as Note_Basse, MAX(Note) as Note_Haute
FROM Evaluer;
```

explication : 

Resultat : 

+-----------------+---------------+
| note_basse      |  note_haute   |
+-----------------+---------------+
|       6.00      |    19.00      |
+-----------------+---------------+
(1 row)
###### Question 3 : Afficher les moyennes de chaque étudiant dans chacune des matières.

```sql 
SELECT 
      CONCAT(nom, ' ', prenom) as nom_complet,
      CodeMat, 
      ROUND(AVG(Note), 2) as Moyenne_notes
From Evaluer Ev
INNER JOIN Etudient Et ON Ev.NEtudient = Et.NEtudient
GROUP BY CONCAT(nom, ' ', prenom), CodeMat;

```

explication : 

Resultat : 

  nom_complet  | codemat | moyenne_notes
---------------+---------+---------------
 Benali Sara   | BD      |         18.00
 Bernard Lucas | MATH    |          9.00
 Martin Sophie | ANG     |         14.50
 Alaoui Ali    | ANG     |         11.50
 Bernard Lucas | BD      |         10.25
 Martin Sophie | MATH    |         17.50
 Martin Sophie | BD      |         15.75
 Bernard Lucas | ANG     |         11.50
 Benali Sara   | MATH    |         12.00
 Alaoui Ali    | BD      |         14.50
 Alaoui Ali    | MATH    |         14.00
 Benali Sara   | ANG     |          7.50
(12 rows)

###### Question 4 : Quelles sont les moyennes par matière ? On utilisera la requête de la question 3 comme table source

cette question depond de la table de la question precedente donc on doit cree un vue quand va utiliser pour repondre sur ces question la.

```sql 
CREATE VIEW Moyenne_Matiere AS
SELECT 
      CONCAT(nom, ' ', prenom) as nom_complet,
      CodeMat, 
      ROUND(AVG(Note), 2) as Moyenne_notes
From Evaluer Ev
INNER JOIN Etudient Et ON Ev.NEtudient = Et.NEtudient
GROUP BY CONCAT(nom, ' ', prenom), CodeMat;
```

la requete sera 

```sql 
SELECT 
      CodeMat, 
      ROUND(AVG(moyenne_notes), 2) AS Moyenne_Module
FROM moyenne_matiere
GROUP BY CodeMat;
```

Resultat : 

 codemat | moyenne_module
---------+----------------
 ANG     |          11.25
 BD      |          14.63
 MATH    |          13.13
(3 rows)

###### Question 5 : Trouver la moyenne générale de chaque étudiant . On utilisera la requête de la question 3 comme table source

```sql 
SELECT 
      nom_complet,
      ROUND(AVG(moyenne_notes)) AS Moyenne_General 
FROM moyenne_matiere
GROUP BY nom_complet;
```

  nom_complet  | moyenne_general
---------------+-----------------
 Alaoui Ali    |              13
 Bernard Lucas |              10
 Benali Sara   |              13
 Martin Sophie |              16
(4 rows)
###### Question 6 : Quelle est la moyenne générale de la promotion ? On utilisera la requête de la question 5 comme table source

tout d'abord on va cree une view de la table precedente par ce qu'en va se baser sur elle pour repondre sur la question suivants 

```sql 
CREATE VIEW Moyenne_general_PEtudient AS
SELECT 
      nom_complet,
      ROUND(AVG(moyenne_notes)) AS Moyenne_General 
FROM moyenne_matiere
GROUP BY nom_complet;
```


```sql 
SELECT ROUND(AVG(moyenne_general), 2) AS Moyenne_Promotion
FROM moyenne_general_petudient;
```

Resultat : 

+----------------------+
|  moyenne_promotion   |
+----------------------+
|         13.00        |
+----------------------+
(1 row)

###### Question 7 : Quels sont les étudiants qui ont une moyenne générale supérieure ou égale à la moyenne générale de la promotion ?

```sql 
SELECT 
      nom_complet, 
      moyenne_general
FROM moyenne_general_petudient
WHERE moyenne_general >= ( 
      SELECT ROUND(AVG(moyenne_general), 2) AS Moyenne_Promotion
      FROM moyenne_general_petudient
);
      
```

Resultat : 

  nom_complet  | moyenne_general
---------------+-----------------
 Alaoui Ali    |              13
 Benali Sara   |              13
 Martin Sophie |              16
(3 rows)