#### 1. Les Pre-requise pour commencer ce course : 

Pour commencer en sql on doit tout d'abord faire bien organiser notre envirenement de travaille pour qu'il soit trop simple pour nous de faire ecrire des requete sql et voire les resultat simple 

###### 1. Instalation de sql localement ( n'importe qulle moteur ( Postgres, Maria, SQL-Server, MySQL ... ))

dans ce course on va travailler avec "Postgres-SQL" comme BD pour manipuler les differents requetes sql 

1. comment installer Postgres-SQL sur Windows et Linux ?

```bash 
## -- Commande Linux

sudo apt install postgressql-server

## -- Comande Windows 

winget search PostgreSQL

## -- pour installer 

winget intall PostgreSQL.PostgreSQL.17 

## -- verfier l'instaltion 

psql --version # --> postgresql ( version 18.3 ) bla bla ....

```

2. Apres installation 

```bash 

## -- Cree un utilisateur sur postgres 

CREATE USER mon_utilisateur WITH PASSWORD 'mot_de_passe'; # Single quote only

```

```sql 
CREATE USER sam WITH PASSWORD '******'; -- create the new user 
ALTER USER SAM WITH SUPERUSER; -- give it super admin privilage 
CREATE DATABASE sam OWNER sam; -- create database by default connects the user to it
```

3. comment ce connecter a notre base de donnee ? 

```bash 
psql -U user -W  # par default postgresql
pasword : ******** # vous auriez la possiblite de taper le mot de passe. 
```


##### 2. Commandes utils en PostgresSQL :

1. commande de connection & deconnection

+------------------------------+-------------------------------+
| Commande                     | Action                        | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">psql -U user -d dbname</font>       | Pour connecter a une db.      | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\c dbname</font>                    | Pour basculer a une db "x".   | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\conninfo</font>                    | Afficher des info sur la cnx  |
|                              | courrant.                     | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\q</font>                           | Quiter.                       | 
+------------------------------+-------------------------------+

2. commande de listing 

+------------------------------+-------------------------------+
| Commande                     | Action                        | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\l</font>                           | Pour Lister les dbs.          | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\dt</font>                          | Pour lister les tables.       | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\d table</font>                     | Pour decrire et expl une      |
|							   | table.                        | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\du</font>                          | Pour afficher les users/roles.|      
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\dn</font>                          | Pour afficher les #cou .   | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\dv et \di</font>                   | - dv : afficher les views.    |
|                              | - di : afficher les indices.  |
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\df</font>                          | Pour afficher Fonctions.      | 
+------------------------------+-------------------------------+

3. Commandes Utiles en Psql ? 

+------------------------------+-------------------------------+
| Commande                     | Action                        | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\?</font>                           | Pour afficher le menu help des|      |                              | commandes.                    |
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\h</font> <font color="#F61067">CREATE TABLE</font>              | Afficher la doc pour une      |
|                              | commande "x".                 |  
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\i file.sql</font>                  | Pour executer un ficher sql   |
|							   | par ex fichier de creation des|      |                              | tables.                       | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\e</font>                           | cette commande ouvre un menu  |
|                              | edit ( notepad ex ) pour      | 
|                              | editer la dernier commande que| 
|                              | vous avez saisie.             | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\! cls</font>                       | Pour faire clear le window.   | 
+------------------------------+-------------------------------+
| <font color="#F8FFE5">\timing</font>                      | Pour mesurer le temp d'exec.  | 
+------------------------------+-------------------------------+

## STEP 1 : Quering Data ( SELECT )
##### 3. Creation des tables pour ce cours 

pour cree les tables pour ce cours on va importer et executer le code de fichier de creation des tables qui s'appelle ==🟠"init-postgrers-mydatabases"==, qui va nous generer par la suite deux tables : 
+-----------------------+
| <font color="#F8FFE5">Table 1 : Custumers</font>   |
| <font color="#F8FFE5">Table 2 : Orders.</font>     | 
+-----------------------+
apres on execute aussi le deusieme fichier ==🔴""== qui va nous generer aussi les tables suivant : 
+----------------------------+
| <font color="#F8FFE5">Table 1 : Custumers</font>        |
| <font color="#F8FFE5">Table 2 : Orders.</font>          |
| <font color="#F8FFE5">Table 2 : OrdersArchive.</font>   | 
| <font color="#F8FFE5">Table 2 : Products.</font>        | 
+----------------------------+
==🟢 double "=" pour highlighter un text en obsidient. == 

J'ai eu un probleme pour improter les fichier externe avec la commande <font color="#F8FFE5">\i</font> a l'interieur de psql danc au lieu on utilise cette methode : 

==🔵psql -U sam -f D:\PATH==

###### Quelles sonts les clauses qui existes on sql ? 

+-----------------+  
| SELECT          |    
| DISTINCT        |
| TOP             | 
| FROM            | 
| JOIN            | 
| WHERE           | 
| GROUP BY        | 
| HAVING          | 
| ORDER BY        | 
+-----------------+
![[Pasted image 20261104093333.png|277]]


##### Dans cette partie on doit comprendre comment sql execute les requete sql ?

![[Pasted image 20261104093529.png]]

1. selectionner toutes les colonne de notre table 

```sql 
SELECT *
FROM table_x;
```

lors de l'execution la clause from s'execute avant la projection des colonnne 

2. Projection des colonne, pour recuperer un ensemble de colonnes, genre c'est 

```sql 
SELECT name, country
FROM table_x;
```

exemple : recupere toutes les nom des client avec leur pays et leur score

```sql 
SELECT name, coutry, score
FROM customers;
```

###### La clause ==🟠Where== en SQL : 

la clause where permet de filtrer l'ensemble des donnee a recuperer pour satisfer une critere donner "x"

exemple 1 : Recuperer les clients qui ont un score diff de 0 

```sql 
SELECT *
FROM customers 
WHERE score != 0;
```

exemple 2 : recuperer les client allmands 

```sql 
SELECT * 
FROM customers 
WHERE country = 'Germany';
-- OU bien 
SELECT * 
FROM customers 
WHERE country in ('Germany');
```

Resultat : 

 id | first_name | country | score
----+------------+---------+-------
  1 | Maria      | Germany |   350
  4 | Martin     | Germany |   500
(2 rows)

###### La clause "ORDER BY" en SQL ? 

la clause ==🔴ORDER BY== en sql permet de sorter les donnes par default ASC mais en peut aussi sorter les donner DESC ( decroissant ordre ) seulon nos besoin.

exemple 1 : sorter les donne par score on ordre decroissant 

```sql 
SELECT * 
FROM customers
ORDER BY score DESC;
```

exemple 1 : sorter les donne par score on ordre croissant 

```sql
SELECT * 
FROM customers
ORDER BY score ASC;
```

###### ORDER By imbriquer en SQL (Nested Sorting)?

![[Pasted image 20261104100820.png]]

Le nested sorting et toujour utiliser quand ona des donnes repeter dans une colonne par exeple la colonne ==🟡Country== le probleme qui se pose ici que pour les client d'origine "DE" ils sont sorter de : 
"Highest -> Lowest"
et l'iverse pour les client d'origine "US".
c'est pour ca on utilise ce mecanisme pour controller le sorting 

syntax : 

```sql 
SELECT *
FROM table_name 
ORDER BY
      country ASC 
      score DESC;
```

exemple 1 : sorter les donnes par pays, et score decroissant 

```sql
SELECT *
FROM customers 
ORDER BY 
	country ASC,
	score DESC;

```

###### Aggregation des requetes via "GROUP BY" ? 

![[Pasted image 20261104101815.png]]

cette clause nous permet de regrouper les donnes similaire par exemple les client qui vient de la meme pays, etc ...

![[Pasted image 20261104102239.png]]

lors de ==🟢GROUP BY== on utilisent obligatoirement une fonction d'agg 
==🔵<font color="#256EFF">( SUM, AVG, COUNT, etc )</font>== qui permet de combiner toutes les enregistrement qui satisfais un critaire en un seule enregistrement

Aussi les element de groupe non agrege dans la clause <font color="">SELECT</font> doivent aussi etre present dans la clause GROUP BY 

exemple `country --> doit etre dans select et group by`


exemple 1 : Trouver le score total pour chaque pays 

```sql 
SELECT 
	country, 
	SUM(score) as score
FROM customers
GROUP BY country; 
```

Resultat : 

 country | score
---------+-------
 UK      |   750
 USA     |   900
 Germany |   850
(3 rows)

exemple 1 : Trouver le score total pour chaque pays, on ordre decroissant

```sql 
SELECT 
     country, 
     SUM(score) as scores 
FROM customers
GROUP BY country 
ORDER BY scores DESC;
```

Resultat : 

 country | scores
---------+--------
 USA     |    900
 Germany |    850
 UK      |    750
(3 rows)

exemple 2 : trouve le score total et le nembre total des client pour chaque pays 

```sql 
SELECT 
   country, 
   COUNT(*) as total_customers,
   SUM(score) as scores
FROM customers
GROUP BY country;

```

Resultat : 

 country | total_customers | scores
---------+-----------------+--------
 UK      |               1 |    750
 USA     |               2 |    900
 Germany |               2 |    850
(3 rows)


###### La close "HAVING" pour filtrer les donnes aggreger : 

La close ==🔴HAVING== et toujour utiliser avec la close ==🔴GROUP BY== pour filtrer les element de sortie aggreger via <font color="#ee4545" style="font-weight: bold;">GROUP BY</font>. 
En bref la calause <font color="#ee4545" style="font-weight: bold;">WHERE</font> s'utilise q'on ton parle de filtrage d'une table en generale 
Mais qu'on parle d'une table de sortie du "GROUP BY" c'est toujour la clause <font color="#ee4545" style="font-weight: bold;">HAVING</font> qui fait le filtrage des lignes de notre table de sortie.

![[Pasted image 20261104104851.png]]

Question 1 : Affichier les pays par score total si leur score et superieur a 800

```sql 
-- version non correct
SELECT 
      country,
      SUM(score) AS SCORE_TOTAL_PAR_PAYS
FROM customers 
GROUP BY country
HAVING SCORE_TOTAL_PAR_PAYS > 800;


-- # version correct : 
SELECT 
      country,
      SUM(score) AS SCORE_TOTAL_PAR_PAYS
FROM customers 
GROUP BY country
HAVING sum(score) > 800;
```

<font color="#ee4545" style="font-weight: bold;">Remarque :</font> 
1. Toujour la clause HAVING et base sur la fonction d'aggregation comme condition 
2. dans la clause HAVING les colonne calcule comme ici (SCORE_TOTAL_PAR_PAYS) sans pas accepter comme condition par contre on doit utiliser le nom de la colonne avant l'aliasing qui et : <font color="#ee4545" style="font-weight: bold;">"SUM(score)"</font>

Resultat : 

 country | score_total_par_pays
---------+----------------------
 USA     |                  900
 Germany |                  850
(2 rows)

![[Pasted image 20261107193624.png|233]]

##### Quand on utilise WHERE ET HAVING ? 

![[Pasted image 20261107193933.png]]

Si on veut filtrer avant appliquer la fonction d'aggregation dans ce cas la on utilise la clause "WHERE"
Mais quand on travail sur des table generer apres aggregation dans ce cas la on utilise que la clause "HAVING" pour filtrer les donnes.

Resultat : 

+----------+----------------------+
| Country  | score_total_par_pays | 
+----------+----------------------+
|   USA    |         900          | 
+----------+----------------------+

Question 2 : Trouver les score moyenne pour chaque pays, on concideron que les clients avec un score superieur strictement a 0, 
apres renvoyer que ces pays avec une somme moyenne superieur a 430.

```sql 
SELECT 
	country, 
	ROUND(AVG(score), 2) AS SCORE_PER_COUNTRY
FROM customers
WHERE score > 0
GROUP BY country 
HAVING AVG(score) > 430;
```

 country | score_per_country
---------+-------------------
 USA     |            900.00
 UK      |            750.00
(2 rows)

###### DISTINCT clause in SQL : 

![[Pasted image 20261107195516.png|380]]

La clause DISTINCT et utiliser en sql pour eviter les lignes duplique, cette clause permet de selectionner seulement les lignes unique.

<font color="#ee4545" style="font-weight: bold;">Remarque :</font> 

l'utilisation non necessaire de la clause de cette clause peut lentez ta query.

![[Pasted image 20261107200019.png]]

Question 1 : selectioner les pays unique

```sql 
SELECT DISTINCT 
		country
FROM customers;
```

+----------+
|  country | 
+----------+
|    UK    |
+----------+
|    USA   |
+----------+
|  Germany |
+----------+
(3 rows)


###### La CLause LIMIT(TOP) en sql : 

![[Pasted image 20261107200528.png|319]] 

Pour limiter le nembre des lignes renvoyer apres l'execution d'une requetes.  
la clause LIMIT et souvent utiliser dans les pages web pour limiter le nembre dans item renvoyer dans la page et faire paginer la page.

```sql 
SELECT *
FROM customers
LIMIT 3;
```

Le filtrage se fait en se basent sur le nembre de la ligne dans notre table, dans sql chaque ligne et numerote par un nembre.

![[Pasted image 20261107201101.png|422]]

Question 1 : recuperer les meilleur 3 client avec le meilleur score

```sql
SELECT *
FROM customers
ORDER BY score DESC
LIMIT 3;
```

 id | first_name | country | score
----+------------+---------+-------
  2 |  John      | USA     |   900
  3 | Georg      | UK      |   750
  4 | Martin     | Germany |   500
(3 rows)

Question 2 : recuperer les mauvais 2 client en se basent sur leur score.

```sql 
SELECT *
FROM customers
ORDER BY score ASC 
LIMIT 2;
```

 id | first_name | country | score
----+------------+---------+-------
  5 | Peter      | USA     |     0
  1 | Maria      | Germany |   350
(2 rows)

Question 3 : recuperer les plus recentes orders --> Table(Order)

```sql 
SELECT *
FROM orders 
ORDER BY order_date DESC 
LIMIT 2;
```

 order_id | customer_id | order_date | sales
----------+-------------+------------+-------
     1004 |           6 | 2021-08-31 |    10
     1003 |           3 | 2021-06-18 |    20
(2 rows)
##### La clause OFFSET ?

la clause OFFSET et souvent utiliser avec la clause LIMIT pour skipper un nembre de ligne et recuperer que le nembre de ligne limiter par la clause LIMIT 

```sql 
SELECT *
FROM customers
LIMIT 3 OFFSET 0; -- commencer depuis la premier ligne 
-- Exemple 2 
SELECT *
FROM customers
LIMIT 3 OFFSET 1; -- commencer depuis la deusieme ligne 
```


### L'ordre d'execution d'une requete SQL VS CODING ORDER ? 

pour l'ordre d'execution correspond de ce shema : 

![[Pasted image 20261107205023.png]]


#### Technique pratique en SQL ? 

###### 1. Static ( Fixed ) values ? 

On peut nommer des valeur static on feusent le select suivant 

```sql 
SELECT 123 AS VALEUR_STATIC;
SELECT 'HELLO' AS STATIC_STRING;
```

+----------------+
|  static_string | 
+----------------+
|      HELLO     |
+----------------+
(1 row)
+----------------+
|  static_value  | 
+----------------+
|       123      |
+----------------+
(1 row)

Cas 2 : par cette technique on peut aussi ajouter une colonne qui n'existe pas dans notre table de base qui contient un affichage qu'on veut.

```sql
SELECT 
	id, 
	first_name, 
	'nouveau client' AS status
FROM customers;
```

 id | first_name |    status
----+------------+--------------
  1 | Maria      | New Customer
  2 |  John      | New Customer
  3 | Georg      | New Customer
  4 | Martin     | New Customer
  5 | Peter      | New Customer
(5 rows)


## STEP 2 : Data Definition Language ( DDL ) CREATE, ALTER, DROP?

###### 01. Create pour instancier une table : 

pour definir une table en SQL on utilise la claude : <font color="#BAFF29">Create</font> 

```sql 
CREATE TABLE table_user ( 
      column_name Data_type constraint
      column_name Data_type constraint
)
```

![[Pasted image 20261108010503.png|234]]

Exemple :

```sql 
CREATE TABLE Persone (
      id INT NOT NULL PRIMARY KEY, 
      age INT CHECK (AGE BETWEEN 10 AND 20), 
      full_name VARCHAR(30) NOT NULL, 
      birth_date DATE, 
      phone VARCHAR(15) NOT NULL
);
```

##### Copy and exesting table 

```sql 
CREATE TABLE new_table ASTABLE existing_table;

CREATE TABLE new_table ASTABLE existing_table WITH NO DATA;


```
###### 02. la clause ALTER en SQL ?

la clause ALTER et vraiment tres utile pour faire des modification sur la table ( ajouter des colonne, modifier leur type, renomer la table, etc ... )

Exemple 1 : Renemez la table deja cree a "Personne"

```sql 
ALTER TABLE Persone RENAME TO Personne;
```

Exemple 2 : Ajouter une colonne Email a la table personne 

```sql
ALTER TABLE Personne 
ADD Email VARCHAR(40) DEFAULT 'UNKNOWN';

ALTER TABLE Personne
ADD test varchar(20) AFTER phone;  -- Works only for mysql & MariaDB
```

Exemple 3 : Supprimer la colonne Email de la table Personne :

```sql
ALTER TABLE Personne 
DROP COLUMN Email;
```

###### 02. La clause DROP en sql ?

cette clause permet de supprimer soit des enregistrement d'une table ou bien la table entier.

```sql 
DROP TABLE Personne; 
```

Explication : Cette commande permet de supprimer la table Personne entierement.

```sql 
DROP FROM TABLE Personne 
WHERE id = 10;
```

Explication : dans ce cas la on essaye de supprimer un ligne de la table avec l'id = 10;

###### RENAME A column 

```sql 
ALTER TABLE table_name
RENAME COLUMN column_name TO new_column_name;
```

###### ADD contraint ( PK ) After creation 

```sql 
ALTER TABLE table_name 
ADD PRIMARY KEY (column_1, column_2, ...);
```

pour ajouter un check sur une colonne deja existant 

```sql 
ALTER TABLE emps 
ADD CONSTRAINT age_checker CHECK (age > 20);
```
## STEP 3 : Data MANIPULATION Language ( DML ) INSERT, UPDATAE, DELETE?

###### 01. La clause INSERT 

1. Methode manuelle d'insertion.

```sql 
-- Methode 1 : 
INSERT INTO TABLE_NOM (column1, column2, column3) VALUES
('data1', 'data2', 'data3');
-- Methode 2 : 
INSERT INTO TABLE_NOM VALUES 
('column1', 'COLUMN2', 'COLUMN3'), 
('column1', 'COLUMN2', 'COLUMN3'),
('column1', 'COLUMN2', 'COLUMN3');
```

comme ceci on peut inserer des donnes dans une base de donnes avec plusieur methode.

2. Il existe aussi une autre methode pour inserer les donnes dans une table vien d'une table deja existent 
	on utilisent cette methode si on veut par exemple transformer les donnes d'une table source a une autre table target 

![[Pasted image 20261108013738.png]]

Exemple : copy les donnes de la table 'client/customers' vers la table 'Personne' :

```sql 
INSERT INTO Personne
SELECT 
	id, 
	first_name, 
	country, 
	score,
	'Unknown' 
	NULL, 
FROM customers;
```

Resultat : 

 id | full_name | country | score |  phone  | birth_date
----+-----------+---------+-------+---------+------------
  1 | Maria     | Germany |   350 | Unknown |
  2 |  John     | USA     |   900 | Unknown |
  3 | Georg     | UK      |   750 | Unknown |
  4 | Martin    | Germany |   500 | Unknown |
  5 | Peter     | USA     |     0 | Unknown |
(5 rows)


##### 02. La clause UPDATE ? 

la clause update et souvant utiliser pour modifier les valeur d'un enregistrement ou plusieur dans une table 

```sql
UPDATE TABLE nom_table 
SET 
	Column1 = New_value
	Column2 = New_value
	Column3 = New_value
WHERE CONDITION;
```

La clause "WHERE" dans ce cas la et important car si on l'utilisent pas ca va affecter toutes les lignes de la table.

Question 1 : changer le score du client 6 a la valeur 0.

```sql
UPDATE customers 
SET score = 0
WHERE id = 6;
```

Question 2 : changer le score du client avec l'id 10 a 0 et aussi modifier sont pays a "Saudi Arabia".

```sql
UPDATE customers
SET 
	score = 0,
	country = 'Saudi arabia'
WHERE id = 10;
```

  9 | Moulin     | France       |   660
  6 | Jack       | USA          |     0
 10 | Pedro      | Saudi arabia |     0
(10 rows)

Question 3 : changer le score de tout les clients qui ont la valeur NULL a 0 

```sql
UPDATE customers
SET score = 0
WHERE score = NULL;
```

###### 03. La clause DELETE 

Toujour n'oubiliez pas d'utiliser la clause WHERE avec ta query DELETE pour ne pas supprimer toutes les lignes de votre table a la fin.

Question 1 : supprimer toutes les client ayont un id superieur a 5.

```sql 
DELETE FROM customers 
WHERE id > 5;
```

Question 2 : supprimer toutes les lignes de la table personne 

```sql
DELETE FROM personne;
```

Mais y'a aussi une moyenne plus rapide pour vide une table c'est par l'utilisation de la keyword <font color="#BAFF29">TRUNCATE</font>

```sql 
TRUNCATE TABLE personne;
```


# Niveau 2 : Intermidiaire en SQL : 

### 01. Filtrage des donnes en SQL ? 

il existe plusieur operateur de comparaison en sql comme par exemple: 

+-------------------+
|    Operateurs     | 
+-------------------+
|    ==Comparaison==    | --> "=", "!= , <>", ">", "<", ">=", "<="
+-------------------+
|      ==🔵Logique==      | --> "AND", "OR", "NOT"
+-------------------+
|       ==🟢Range==       | --> "BETWEEN"
+-------------------+
|    ==🟢Membership==     | --> "IN", "NOT IN"
+-------------------+
|      ==🔴Search==       | --> "Like"
+-------------------+

![[Pasted image 20261108135128.png]]

###### 01. Les operateurs de comparaison ? 

les operateur de comparaison sont utiliser en sql pour comparer ou evaluer deux valeur 

+-----------------+         +---------------+        +--------------+
|   Expression    | ------- |   Operator    | ------ |  Expression  |
+-----------------+         +---------------+        +--------------+

![[Pasted image 20261108135853.png]]

Question 1 : recuperer les clients german.

```sql 
SELECT *
FROM customers
WHERE country = 'Germany';
```

Question 2 : recuperer les clients qui vient pas de l'allmend

```sql 
-- Methode 1 : 
SELECT * 
FROM customers
WHERE country != 'Germany';

-- Methode 2 : 
SELECT * 
FROM customers
WHERE country <> 'Germany';
```

Question 3 : recuperer les client avec un score superieur a 500 

```sql 
SELECT *
FROM customers 
WHERE score > 500;
```

Question 4 : recuperer les client avec un score inferieur a 500

```sql
SELECT *
FROM customers 
WHERE score < 500;
```

###### 02. Les operateurs Logique "AND, OR, NOT" ?

==🟢AND :== Touts les condition doivent etre vrais.
==🟢OR  :== Au moin une seul condition doivent etre vrais.
==🟢NOT :== Pour faire la negation d'une condition, ou bien exclure les ligne qui evalue la condition.

Question 1 : recuperer les clients qui sont de la "USA", et qui on un score superieur a 500 ( AND ).

```sql
SELECT *
FROM customers
WHERE country = 'USA' AND score > 500;
```

Question 2 : recuperer les clients qui sont de la "USA", ou qui on un score superieur a 500 ( AND ).

```sql
SELECT *
FROM customers
WHERE country = 'USA' OR score > 500;
```

Question 3 : recuperer les clients qui sont pas de la "USA", ou qui on pas un score superieur a 500 ( AND ).

```sql 
SELECT *
FROM customers 
WHERE NOT ( country = 'USA' or score = 500 );
```

Question 4 : recuperer les clients qui ont pas un score inferieur a 500 

```sql
SELECT *
FROM customers 
WHERE NOT ( score < 500 );
```

###### Les operateur de Range ? 

==🟢BETWEEN :== Permet de verifier si une valeur et comprise entre un certain range ou pas 

Question 1 : recuprer les client entre 2 et 4 

```sql 
SELECT *
FROM customers 
WHERE id BETWEEN 2 AND 4;
```

Question 2 : recuperer les clients qui ont un score comprise entre 300 et 700 

```sql 
-- Avec BETWEEN
SELECT *
FROM customers 
WHERE score BETWEEN 300 AND 800;

-- SANS BETWEEN 
SELECT *
FROM customers 
WHERE score >= 300 AND score <= 800;
```

###### 03. Les operateurs de membership ? 

==🟢IN== : l'operateur IN permet de verifier si une valuer existe dans un ensemble donnes
==🟢NOT IN ==: L'operateur NOT IN Permet de verifier si une valeur n'existe pas dans un ensemble donnes.

Question 1 : recuperer les client qui vient de "Germany" et "USA"

```sql 
SELECT *
FROM customers 
WHERE country IN ('USA', 'GERMANY');
```

###### 04. Les operateurs de SEARCH ? 

==🟢LIKE==  : L'operateur like et utiliser pour fouiller dans un text sur qui verifie un pattern donnes ( sensible a la case )
==🟢ILIKE== : L'operateur ILIKE fait le meme boulot de LIKE mais il est pas sensible a la case 

![[Pasted image 20261108144841.png]]

==🟠%== : Signifie 0,1, ou plusieur caractere 
==🟠_== : Signifie un et un seul caractere 

Exemple : recuperer nom qui contient un "S"

```sql 
ILIKE '%S%' -- Contient S 
```

Exemple : donner les nom des client qui ont 'e' comme deusieme caractere 

```sql 
ILIKE '_e%'
```

Question 1 : Trouver toutes les client ayant un nom commence par "M"

```sql 
SELECT *
FROM customers 
WHERE first_name LIKE 'M%';
```

 id | first_name | country | score
----+------------+---------+-------
  1 | Maria      | Germany |   350
  4 | Martin     | Germany |   500
(2 rows)

Question 2 : trouver les client qui on un nom ce termine par "n"

```sql 
SELECT *
FROM customers 
WHERE first_name LIKE '%n';
```

Question 3 : trouver les client qui on un "r" dans leur nom 

```sql 
SELECT *
FROM customers 
WHERE first_name ILIKE '%r%';
```


### 02. Comment combiner les donnes de plusieur Table en SQL ? 

##### 01. Les Jointeures en SQL ( Joins VS SET ) ?

![[Pasted image 20261108151632.png|270]]

Les jointures sont souvant utiliser pour combiner les colonnes de deux tables, tandis que set et utiliser pour combiner les lignes de deux ou plusieur colonne.

![[Pasted image 20261108151909.png]]

###### 01. Les jointeures SQL ? 

Pourquoi on utilisent les jointeures ?

1. Pour combiner les donnes ( par exemple les donnes des client entre toutes les tables ).
2. Pour faire le data enrichment pour avoir plus d'info, la table initiale s'appele table master et la table second s'appelle table reference.
3. Pour verifiez aussi l'existence d'une donnes dans une autre table dans ma base de donnes. Par exemple ici je veux savoir si mon client a fait acheter ou commander ou pas donc je dois absoluement utilisent la table order pour voir si le client a passer une commande ou pas.

![[Pasted image 20261108152453.png|680]]

Pour comprendre les jointures on utilisent souvent ce shema des ensembles : 

![[Pasted image 20261108154411.png|505]]

==🔴Left table / Table gauche== : La table source.
==🔴Right table / Table droit== : La table destination.

souvent on cherche a trouve un des trois scenario ici 

![[Pasted image 20261108154900.png]]

il existe plusieur type de jointures commencent par les jointures basic au jointure avance : 

![[Pasted image 20261108155010.png]]

1. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">NO JOIN</font> : cette jointure permet de retourner les donnes de deux tables sans de les combiner. c'est a dire dans ce cas la on veux voir les donnes de la <font color="#F61067">Table gauche</font> et aussi les donnes de la <font color="#F61067">Table droite</font>, Au meme temp

![[Pasted image 20261109004912.png]]

syntax : 

```sql 
SELECT *
FROM table_a;

SELECT *
FROM table_b;
```

Question 1 : recuperer tout les donnes de la table client et de la table orders separement.

```sql 
SELECT *
FROM customers;
SELECT *
FROM orders;
```

2. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">INNER JOIN</font> : cette jointure permet de retourner les donner commun entre la <font color="#F61067">Table gauche</font> et la <font color="#F61067">Table droite.</font> 
	Aussi dans ce type de jointure on peut joigne les tables dans n'importe quelle ordre.

![[Pasted image 20261109005628.png]]

Syntax : 

```sql 
SELECT *
FROM TABLE_GAUCHE TG
[TYPE] JOIN TABLE_DROITE TD -- Per default INNER
ON TG.key = TD.key; 
```

Question 1 : recuperer les clients avec leur order, seulement les client qui ont passer une commande.

```sql 
SELECT 
	id, 
	first_name, 
	country, 
	score,
	order_id,
	order_date, 
	sales
FROM customers c 
INNER JOIN orders o 
ON c.id = o.customer_id;
```

Resultat : 

 id | first_name | country | score | order_id | order_date | sales
----+------------+---------+-------+----------+------------+-------
  1 | Maria      | Germany |   350 |     1001 | 2021-01-11 |    35
  2 |  John      | USA     |   900 |     1002 | 2021-04-05 |    15
  3 | Georg      | UK      |   750 |     1003 | 2021-06-18 |    20
(3 rows)


> [!error] Remarque
> Si vous joigner deux ou plusieur table c'est mieux de mentionner le nom de la table avant chaque colonne dans la clause select pour eviter l'embiguite de votre requete SQL 
> 
> ==🔴Exemple==:
> ```sql 
> SELECT 
> 	[table1].id
> 	[table1].name
> 	[table1].age
> 	[table2].order_id NUMERO_ORDER
> FROM TABLE1 T1
> INNER JOIN TABLE2 T2 ON T1.id = T2.id;  
> ```

![[Pasted image 20261109012627.png]]

L'utilite de la Joiture : INNER

![[Pasted image 20261109012726.png]]

1. Pour Combiner les donnes vien de plusieur table
2. pour extraire de l'information 
3. pour filtrer aussi les donnes
---
3. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">LEFT JOIN</font> : cette jointure permet de retourner toutes les lignes de la table gauche avec les lignes correspondent a chaque ligne de la table dans la table gauche.

![[Pasted image 20261109064508.png]]

Syntax : 

```sql 
SELECT *
FROM table_gauche TG
LEFT JOIN table_droit TD
ON TG.id = TD.id;
```

Question 1 : recuperer les clients avec leur order, incluent celles qui on pas passer une commande 

```sql 
SELECT 
	C.id, 
	C.first_name, 
	O.customer_id,
	O.order_id,
	O.order_date, 
	O.sales
FROM customers C 
LEFT JOIN orders O 
ON C.id = O.customer_id; 
```

Resultat : 

 id | first_name | customer_id | order_id | order_date | sales
----+------------+-------------+----------+------------+-------
  1 | Maria      |           1 |     1001 | 2021-01-11 |    35
  2 |  John      |           2 |     1002 | 2021-04-05 |    15
  3 | Georg      |           3 |     1003 | 2021-06-18 |    20
  5 | Peter      |             |          |            |
  4 | Martin     |             |          |            |
(5 rows)

![[Pasted image 20261109175446.png]]

4. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">RIGHT JOIN</font> : cette jointure permet de retourner toutes les lignes de la table gauche avec les lignes correspondent a chaque ligne de la table dans la table gauche.

![[Pasted image 20261109175649.png]]

```sql 
SELECT *
FROM table_gauche TG 
RIGHT JOIN table_droit TD 
ON TF.id = TD.id;
```

Question 1 : recuperer toutes les clients, avec leurs command incluent les commandes qui on pas de clients 

```sql 
SELECT 
	id, 
	first_name, 
	order_id,
	sales 
FROM customers C 
RIGHT JOIN orders O
ON C.id = O.customer_id; 
```

Resultat : 

 id | first_name | order_id | sales
----+------------+----------+-------
  1 | Maria      |     1001 |    35
  2 |  John      |     1002 |    15
  3 | Georg      |     1003 |    20
    |            |     1004 |    10
(4 rows)

Qustion 2 : recuperer les clients avec leur commandes en incluent aussi les etudient qui on pas commander en utilisent ( LEFT JOIN )

```sql 
SELECT
	C.id, 
	C.first_name, 
	O.order_id, 
	O.sales
FROM Orders O
LEFT JOIN Customers C ON O.customer_id = C.id;
```

 id | first_name | order_id | sales
----+------------+----------+-------
  1 | Maria      |     1001 |    35
  2 |  John      |     1002 |    15
  3 | Georg      |     1003 |    20
    |            |     1004 |    10
(4 rows)

![[Pasted image 20261111170822.png]]

5. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">FULL JOIN</font> : cette jointure permet de retourner toutes les lignes de la table gauche + tout les lignes de la tables droit.

![[Pasted image 20261111171244.png]]

Syntax : 

```sql
SELECT *
FROM A 
FULL JOIN B on A.key = B.key;
```

Question 1 : recuperer les client et tout les order malgre si y'a pas de match

```sql
SELECT 
	C.id, 
	C.first_name NAME, 
	C.country, 
	O.order_id,
	O.sales
FROM Customers C 
FULL JOIN Orders O ON C.id = O.customer_id;
```

 id |  name  | country | order_id | sales
----+--------+---------+----------+-------
  1 | Maria  | Germany |     1001 |    35
  2 |  John  | USA     |     1002 |    15
  3 | Georg  | UK      |     1003 |    20
    |        |         |     1004 |    10
  5 | Peter  | USA     |          |
  4 | Martin | Germany |          |
(6 rows)

![[Pasted image 20261111172023.png]]


##### Advanced SQL JOINS : 

1. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">LEFT ANTI JOIN</font> : cette jointure permet de retourner toutes les lignes de la table gauche qui on pas de match dans la table droit

![[Pasted image 20261111172434.png]]

Syntax : 

```sql
SELECT **
FROM A 
LEFT JOIN B ON A.key = B.key 
WHERE B.key IS NULL;
```


Question 1 : recuperer les clients qui ont pas fais aucune commande 

```sql 
SELECT 
	*
FROM Customers C
LEFT JOIN Orders O ON C.id = O.customer_id
WHERE O.customer_id IS NULL;
```

2. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">RIGHT ANTI JOIN</font> : cette jointure permet de retourner toutes les lignes de la table droit qui on pas de match dans la table gauche

Syntax : 

```sql 
SELECT *
FROM A 
RIGHT JOIN B ON A.key = B.key 
WHERE A.key IS NULL;
```

Question 1 : recuperer tout les order qui on pas de client 

```sql 
SELECT *
FROM Customers C 
RIGHT JOIN Orders O ON C.id = O.customer_id 
WHERE C.id IS NULL;
```

using LEFT JOIN ONLY 

```sql 
SELECT *
FROM Orders O 
LEFT JOIN Customers C ON O.customer_id = C.id 
WHERE C.id IS NULL;
```


2. <font color="#256EFF" style="font-weight: bold; text-decoration: underline;">FULL ANTI JOIN</font> : cette jointure permet de retourner toutes les lignes de la table droit qui on pas de match dans la table gauche en ignorent les lignes commun entre les deux table ( existe in A not in B | Exist in B and not in A )

![[Pasted image 20261111203717.png]]

Syntax : 

```sql 
SELECT *
FROM A 
FULL JOIN B ON A.key = B.key 
WHERE 
     B.key IS NULL -- ( ONLY A )
OR
     A.key IS NULL -- ( ONLY B )
```

Question 1 : trouver les client sans commandes et les commandes sans client ? 

```sql 
SELECT 
	*
FROM Customers C 
FULL JOIN Orders O ON C.id = O.customer_id 
WHERE 
     O.customer_id IS NULL -- ( customers without oreders )
OR 
     C.id IS NULL; -- ( Orders without client )
```

Result : 

![[Pasted image 20261111204227.png]]

QUIZ : recuperer toutes les client avec leurs commandes mais juste pour les clients qui on passer une commande ( sans utilisation de l'inner join )

[1]. using FULL JOIN

```sql 
SELECT 
	*
FROM Customers C 
FULL JOIN Orders O ON C.id = O.customer_id 
WHERE 
	C.id IS NOT NULL 
AND 
	O.customer_id IS NOT NULL;
```

![[Pasted image 20261111205233.png]]

[2]. using LEFT JOIN

```sql 
SELECT 
	*
FROM Customers C 
LEFT JOIN Orders O ON C.id = O.customer_id 
WHERE 
	O.customer_id IS NOT NULL;
```


> [!NOTE] CROSS JOIN
> cette jointure permet de faire un produit cartesienne de chaque ligne de la table A ( droit ) par toutes les lignes de la table B ( gauche )
> 
> Syntax :
> ```sql 
> SELECT * 
> FROM A 
> CROSS JOIN B;
> ```

![[Pasted image 20261111210330.png]]

Question 1 : generer toutes les compossition possibles des deux tables 

```sql
SELECT 
	*
FROM Customers 
CROSS JOIN Orders;
```

![[Pasted image 20261111210433.png]]

cette jointure et tres utile pour generer par exemple des donnes aleatoire 

QUIZ : Cree la table test a partir de la combination des deux table C et O.

```sql 
CREATE VIEW TEST AS
SELECT 
	*
FROM Customers
CROSS JOIN Orders;
```


### Comment choisir la bonne jointure a partie des jointure qu'on a vue ? 

![[Pasted image 20261111212119.png]]

Dans le domaine de science de donnes c'est vraiment plus probable d'utiliser toujour la jointure LEFT JOIN dans votre process d'analyse.

![[Pasted image 20261111212327.png]]

En generale en peut faire toujour tout just avec la jointure LEFT JOIN

![[Pasted image 20261111212506.png|362]] ![[Pasted image 20261111212541.png|294]]

donc cette jointure va nous permet de Recombiner les donnes de la maniere qu'on veut nous meme pour controller l'affichage et l'interet de l'analyse.

![[Pasted image 20261111212731.png]]

Pour la multi-jointure via INNER JOIN en sql vous orier la shema suivant aussi : 

![[Pasted image 20261111232852.png]]

Question 1 : en utilisent la base de donnes "SalesDB" recuperer une list de toutes les commandes avec leurs clients associer, produit et aussi detail de l'employee
Afficher que : 
- Order ID 
- Customer's name 
- product name
- sales amount 
- product price 
- salesperson name

```sql 
-- Using left join 

SELECT 
	O.orderid ORDER_ID, 
	CONCAT(C.firstname,' ',C.lastname) CUSTOMER_NAME, 
	P.product PRODUCT,
	O.sales SALES_AMOUNT,
	CONCAT(P.price, ' $') PRICE,
	CONCAT(E.firstname,' ',E.lastname) SALES_PERSON
FROM Orders O 
LEFT JOIN Customers C ON O.customerid = C.customerid 
LEFT JOIN Products  P ON O.productid  = P.productid
LEFT JOIN Employees E ON O.salespersonid = E.employeeid;

-- Using INNER JOIN 
SELECT 
	O.orderid ORDER_ID, 
	CONCAT(C.firstname,' ',C.lastname) CUSTOMER_NAME, 
	P.product PRODUCT,
	O.sales SALES_AMOUNT,
	CONCAT(P.price, ' $') PRICE,
	CONCAT(E.firstname,' ',E.lastname) SALES_PERSON
FROM Orders O 
INNER JOIN Customers C ON O.customerid = C.customerid 
INNER JOIN Products  P ON O.productid  = P.productid
INNER JOIN Employees E ON O.salespersonid = E.employeeid;
```

## Combiner les donnes de plusieur table en utilisent les operateurs SET

En gros les operateur d'union permet de combiner les donnes vien de plusieur table en un seule table mais a condition que les donnes doivent etre de meme type et aussi le meme nembre de colonne 

![[Pasted image 20261115212035.png]]


> [!success] Regle 1 : Sql clauses
> SET operateur peuvent etre utiliser avec touts les clauses SQL par exemple : 
> WHERE, JOIN, GROUP BY, HAVING
> 
> Seulement la clause ORDER BY qui peuvent etre utiliser un seule fois dans une requete de type set et ils doivent etre mis a la fin de la requete.

![[Pasted image 20261115212611.png]]


> [!success] Regle 2 : meme nembre de colonne
> Le nembre de colonne a recuperer des table doivent etre le meme.


> [!success] Regle 3 : le type de donnes 
> Le type des donnes des colonnes a recuperer doit etre le meme ou bien compatible sela veut dire on recupere que les donnes de meme type.


> [!success] Regle 4 : Ordre des colonne
> L'ordre des colonne des table doit aussi etre compatible 



> [!success] Regle 5 : Aliasing des colonne
> Le nom de colonnes dans les resultat et determiner par le nom des colonne specifier dans la premier query.
> 
> ![[Pasted image 20261115213918.png]]
> 


> [!success] mapage des colonnes correct
> meme si toutes les regles sont satisfe et SQL n'affiche aucun erreur les resultat peuvent etre fausse
> 
> la selection des colonne fausse peut entaminer a des resultat incoierent par la suite.


#### UNION : 

L'operateur UNION permet de retrourner toutes les distinct lignes des deux requetes.

c'est a dire y'aura pas de lignes duplices.

![[Pasted image 20261115235938.png]]

Question 1 : combiner les deux tables customers et employees en une seule table

```sql 
SELECT 
	firstname, 
	lastname
FROM customers
UNION 
SELECT 
	firstname, 
	lastname 
FROM empoyees;
```

![[Pasted image 20261115235819.png]]

#### UNION ALL 

Cette operateur fait aussi le meme travail que l'operateur UNION la seule difference c'est que y'aura pas de supression des lignes duplice entre les tables.

![[Pasted image 20261116000820.png]]


> [!warning] UNION ALL vs UNION
> L'operateur UNION ALL et plus rapide que l'UNION pcq y'a pas d'extra calcule pour supprimer les lignes duplique.
> 
> ![[Pasted image 20261116001013.png]]
> 
> donc si vous etes sure que dans tes deux tables origine y'a pas de ligne duplice c'est plus efficace de priorizer <font color="#ee4545">UNION ALL</font> sur <font color="#ee4545">UNION</font>
> 
> Aussi vous pouvez utiliser UNION ALL pour verifiez si y'a des lignes duplice.



#### EXCEPT 

L'operateur EXCEPT permet de retourner l'ensemble des lignes disting dans la premier requete qui ont pas dans la deusieme requetes.

![[Pasted image 20261116001853.png]]

Puisque l'ordre des requetes et improtant on peut dire que l'operateur EXCEPT et le seule operateur qu'on doit absolument fait attention avec l'ordr des requetes pcq ca peut affecter le resultat total

![[Pasted image 20261116002117.png]]

exemple : customers that are not employees.

![[Pasted image 20261116002316.png]]

Question 1 : recuperer les employee qui sont pas des clients au meme temps 

```sql 
SELECT 
	firstname, 
	lastname
FROM employees 
EXCEPT 
SELECT 
	firstname, 
	lastname
FROM customers;
```

![[Pasted image 20261116014446.png]]
#### INTERSECT

L'operateur intersect permet de retourner les element commun entre les deux tables.
Aussi il gere les element duplice ca veux dire si y'a jamais une ligne duplice il va etre automatiquement supprimer.

![[Pasted image 20261116193138.png]]


### C'est quoi l'utilite des operateurs set ? 

[1] - Combiner les informations similaire avant analyser les donnes.

![[Pasted image 20261116193622.png|332]]

Au lieu d'exeuter des query sur chaque table qui on les meme types donnes par exemple pour faire un reporting c'est mieur de le faire de cette maniere qui est de 

![[Pasted image 20261116193742.png|340]]

Combiner toutes les donnes similaire en une seule table par exemple "Person" dans notre cas apres on passe pour faire l'analyse

Task : les commandes sont stocker seperament dans les tables ( orders, ordersarchive ) combiner toutes les ordres pour former une seule table sont element duplice.

```sql 
SELECT 
	orderid, 
	productid, 
	customerid, 
	salespersonid, 
	quantity,
	sales
FROM orders 
UNION 
SELECT 
	orderid, 
	productid, 
	customerid, 
	salespersonid, 
	quantity,
	sales
FROM ordersarchive; 
```

[2]. Aussi on peut l'utiliser dans un cas plus pratique pour identifier les nouveau donnes dans nouveau dans une set quand on fait des piplines 

![[Pasted image 20261116195242.png]]

[3]. En peut utiliser aussi les operateurs set pour faire un check sur la completences des donnes. Par exemple l'operateur EXCEPT peuvent etre utiliser pour comparer et aussi detecter l'incoherence ( discrepancies / tanaqodat ) entre les donnes 

![[Pasted image 20261116195636.png]]

Lors de la migration d'une table a une autre pour verifier qu'on a pris toutes les donnes on doit faire le test par l'operateur EXCEPT ( MINUS ) pour voir si toutes les donnes sont identique ou pas 

![[Pasted image 20261116200007.png]]
#### Resumer : 

![[Pasted image 20261116200145.png]]


# Row level function en SQL ?

une fonction en sql et comme un fontion en programmation il prend une valeur d'entre, fait un ensemble de process apres il retourne une valeur de sortie.

en sql il existe plusieur type de fnx : 

<font color="#F61067" style="font-weight: extra-bold">Single row fonctions </font>: ce type des fonction prend une seule valeur comme entre pour produire une valeur de sortie par exemple : 
<font color="#affc41">LOWER()</font>, <font color="#affc41">UPPER()</font>

<font color="#F61067" style="font-weight: extra-bold">Multi row fonctions </font> : ce type des fonction dans l'autre caute prend plusieur valeur comme entre pour produire une valeur de sortie exemple : <font color="#affc41">SUM()</font>, <font color="#affc41">AVG()</font>

![[Pasted image 20261116201017.png]]

#### Le nesting des fonction 

On peut aussi faire nester les fonction en sql comme toutes langages de programtion

![[Pasted image 20261116201207.png]]

```sql 
LOWER(LEFT('Maria', 2)) -- pour recuperer les 2 premier caracter 
LEN(LOWER(LEFT('Maria', 2))) -- pour recup le length
```

#### Les types des fonctions 

![[Pasted image 20261116201448.png]]

les fonction a gauche se fait pour preparer les donnes pour les fonctions a droite 

## Comment manipuler les fonction des string : 

![[Pasted image 20261116201556.png]]

+---- Manipulation --------------------------------------------------+
| <font color="#affc41">CONCAT()</font>  :  
| <font color="#affc41">UPPER()</font>   :
| <font color="#affc41">LOWER()</font>   : 
| <font color="#affc41">TRIM()</font>    :
| <font color="#affc41">REPLACE()</font> :
+--------------------------------------------------------------------+
1 - <font color="#affc41">CONCAT()</font> : pour combiner deux ou plusieur valeur de type string en sql

![[Pasted image 20261116202145.png]]

Task 1 : concatener les prenom des clients avec leur pays d'origine en une seule colonne.

```sql 
SELECT 
	CONCAT(firstname,' ',country) AS NAME_COUNTRY
FROM customers;
```

Resultat :
+----------------+
|  NAME_COUNTRY  |   
+----------------+
| Jossef Germany |
| Kevin USA      |
| Mary USA       |
| Mark Germany   |
| Anna USA       |
+----------------+
(5 rows)

2 - <font color="#affc41">UPPER() & LOWER()</font> : 

![[Pasted image 20261116212719.png]]

Task 1 : transformer le prenom des client a des lower_case 

```sql 
SELECT
     LOWER(firstname) LOWER_CASE, 
     UPPER(firstname) UPPER_CASE
FROM customers;
```

3 - <font color="#affc41">LENGTH() OR LEN() </font> : Pour supprimer les ( white space ) a avant et apres le text 

![[Pasted image 20261116213039.png]]

```sql
SELECT '     SOUkaina' BEFORE;
SELECT TRIM('     SOUkaina') AFTER; 
```

Task 1 : trouver les prenom des client qui contient des espaces vide 

```sql 
SELECT 
	customerid, 
	firstname 
FROM customers 
WHERE TRIM(firstname) <> firstname;

-- second method 
SELECT 
	firstname, 
	LENGTH(firstname) LEN_FIRST_NAME
FROM customers
WHERE LENGTH(firstname) = LENGTH(TRIM(firstname));

-- third methode subtraction 
SELECT 
	firstname, 
	LENGTH(firstname) LEN_FIRST_NAME, 
	LENGTH(firstname) - LENGTH(TRIM(firstname)) FLAG
FROM customers
WHERE LENGTH(firstname) - LENGTH(TRIM(firstname)) = 0;
```

4 - <font color="#affc41">REPLACE()</font>: pour remplacer un ensemble de character par un autre.

![[Pasted image 20261116221702.png]]

Exemple : remplacer les - par des slash / dans la date de naissence.

![[Pasted image 20261116221803.png]]

```sql 
SELECT 
	customerid, 
	CONCAT(firstname, ' ', lastname) FULL_NAME,
	REPLACE()
FROM customers 

-- 
SELECT 
	O.customerid, 
	CONCAT(C.firstname, ' ',C.lastname) FULL_NAME, 
	REPLACE(to_char(O.orderdate), '-', '/') DATE
FROM customers C
LEFT JOIN orders O ON C.customerid = O.customerid;
```


> [!error] Remarque
> La fonction REPLACE() accept que les chaines de charactere.
> 

Exemple : 

```sql
SELECT REPLACE('12-01-2002', '-', '/') BIRTH_DATE;
```

+-------------+
|  birth_date | 
+-------------+
|  12/01/2002 |
+-------------+
(1 row)

Exemple 2 : changer le format d'un fichier stocker dans la base de donnes : 

```sql 
SELECT REPLACE('file.txt', '.txt', '.py') AS FILE_EXTENTION;
```

+---- Calculation ---------------------------------------------------+
| <font color="#affc41">LEN()</font>  :  le nembre des charactere dans une valeur donne.
+--------------------------------------------------------------------+

Exemple : recupere les prenom avec le nembre de caractere qui contient 

```sql 
SELECT 
      firstname, 
      LENGTH(firstname) AS LENGTH 
FROM customers;

```

+---- String Extraction ---------------------------------------------+
| <font color="#affc41">LEFT()</font>       : Permet d'extraire un nembre specifique de character. 
| <font color="#affc41">RIGHT()</font>      : Permet d'extraire un nembre specifique de character.
| <font color="#affc41">SUBSTRING()</font>  : extraire un une partie d'une chaine a une position   | donnes
+--------------------------------------------------------------------+

Exemple : 

```sql
SELECT 
LEFT('SOUKAINA', 3) LEFT_FUNC, 
RIGHT('SOUKAINA', 3) RIGHT_FUNC;
```

Exemple 2 : recuperer les premier 2 character de chaque client 

```sql
SELECT 
    firstname, 
	LEFT(firstname, 2) LEFT_TWO_CHARS, 
	RIGHT(firstname, 2) LAST_CHARS
FROM customers;
```

Exemple SUBSTRING : 

![[Pasted image 20261116225340.png]]

-- Apres le premier caracter recuperer 2 character du prenom 

```sql 
SELECT SUBSTRING('Maria', 3, 2); -- ou -- iclude start and end.
SELECT SUBSTRING('Maria', 3, LENGTH('Maria') - 2); 
```

## 2. Comment manipuler les fonction des numero :


![[Pasted image 20261117175223.png]]

<font color="#affc41">ROUND()</font> : Permet de rounder un nembre en se basent sur le nembre desirer des nembres apres la virgules. Si le nembre superieur a 5 round up sinon on fait lesse le nembre tel quelle et.

```sql 
SELECT 
	4.5378 BASE_NUMBER,
	ROUND(4.5378, 3) ROUNDED_3, -- 4.538
	ROUND(4.5378, 2) ROUNDED_2, -- 4.54
	ROUND(4.5378, 1) ROUNDED_1, -- 4.5
	ROUND(4.5378, 0) ROUNDED_0;  -- 5
```

<font color="#affc41">ABS()</font>  : la valeur absolue d'un nembre, si le nembre et negative ca va changer en un nembre positif, sinon il reste tel quelle et.

```sql 
SELECT 
	-10,          -- -10 
	ABS(-10),     -- 10
	ABS(20);      -- 20
```


## 3. Date & Time manipulation en SQL ? 

##### 1. Date and time

![[Pasted image 20261117180903.png]]

##### 2. Timestamp 

![[Pasted image 20261117181002.png]]


<font color="#affc41">NOW() ( PSQL ) GETDATE() ( OTHERS )</font> : Pour recuperer la date courrant ( Date and time ) au moment de l'execution de la requete. 

```sql 
CREATE TABLE posts (
     id         SERIAL PRIMARY KEY,  -- generate ID
     title      VARCHAR NOT NULL,
     created_at TIMESTAMPTZ DEFAULT Now()
);

INSERT INTO posts (title)
VALUES     ('PostgreSQL NOW function');

```

+-----+-------------------------+---------------------------------+
|  id | title                   |      created_at                 |
+-----+-------------------------+---------------------------------+
|  1  | PostgreSQL NOW function | 2024-01-27 04:20:11.286958+02   |
+-----+-------------------------+---------------------------------+
(1 row)

#### Data and time manipulation : 

![[Pasted image 20261117182730.png]]

#### Les categories des fonctions des dates : 

```sql 
SELECT CURRENT_DATE; 'yyyy-mm-dd'
SELECT CURRENT_TIME; 'hh:mm:ss'
SELECT NOW() || CURRENT_TIMESTAMP; '2026-11-17 18:59:36.75076+01'
```

![[Pasted image 20261117182826.png]]

###### 1. Part extraction : 

En postgres il existe un seule fonction qui fait tout le boulau d'extraction :

<font color="#affc41">date_part(part, Date) -> int</font> : permet de recuperer soit le jour,mois,l'annee
<font color="#affc41">EXTRACT(part FROM date)</font> : Pour extraire une partie de la date

![[Pasted image 20261117184647.png]]

+--------- Les Autres moteurs ( mysql, MariaDB ) --------------------
<font color="#affc41">DAY()</font> : return le jour d'une date donnes
<font color="#affc41">MONTH()</font> : return le mois d'une date donnes
<font color="#affc41">YEAR()</font> : return l'annee d'une date donnes
+--------------------------------------------------------------------

si vous force coder la date ( hard coded date ) vous douvez absolument specifier TIMESTAMP avant la date

```sql
SELECT 
    date_part('day', '2020-12-12'), -- wont work
    date_part('month',TIMESTAMP '2020-10-13'), 
    date_part('year',TIMESTAMP '2020-11-12');
    
```

```sql
SELECT 
   	date_part('year', creationtime) YEAR_, 
	date_part('month', creationtime) Month_,
	date_part('day', creationtime) Day_, 
	date_part('quarter', creationtime) Quarter_, 
	date_part('week', creationtime) Week_ 
FROM orders;

```

<font color="#affc41">TO_CHAR(date, part) -> string</font> : pour recuperer les dates en format nom par exemple : janvier, fevrier, vendredi etc...

<font color="#affc41">DATENAME(date, part) -> string ( for others )</font>

```sql 
SELECT 
    TO_CHAR(creationtime, 'day') DAY_,
    TO_CHAR(creationtime, 'month') MONTH_
FROM orders;
```

<font color="#affc41">DATE_TRUNC(part, date) -> string</font> : pour garder que ce que nous interesse dans notre date 

![[Pasted image 20261117190926.png]]


```sql 
SELECT 
    date_trunc('minute', creationtime) Minutes_
    date_trunc('day', creationtime) Day_
FROM orders;
```

days : reset to 01 -- time : reset to 00

![[Pasted image 20261117191514.png]]

L'utilite de data_trunc c'est au niveau du reporting en peut par exemple regrouper les achats/orders par leur dates d'achat exemple : 

```sql
SELECT 
    DATE_TRUNC('year', creationtime) YEAR_, 
    COUNT(*)
FROM orders 
GROUP BY DATE_TRUNC('year', creationtime);

        year_        | count
---------------------+-------
 2025-01-01 00:00:00 |    10
(1 row)


SELECT 
    DATE_TRUNC('month', creationtime) YEAR_, 
    COUNT(*)
FROM orders 
GROUP BY DATE_TRUNC('month', creationtime);

        year_        | count
---------------------+-------
 2025-02-01 00:00:00 |     4
 2025-03-01 00:00:00 |     2
 2025-01-01 00:00:00 |     4
(3 rows)
```

les fonctions de dates sont tellement important pour faire du reporting

![[Pasted image 20261117202220.png]]


> [!success] Question 1 :
> combien de achats on ete fait chaque annee ?

```sql 
SELECT 
	date_trunc('year', orderdate) YEAR_, 
	COUNT (*) ORDERS
FROM orders 
GROUP BY date_trunc('year', orderdate);
```

> [!success] Question 2 :
> combien de achats on ete fait chaque mois ?

```sql
SELECT 
    date_part('month', orderdate) MONTH_, 
    COUNT(*) ORDERS_PER_MONTH
FROM orders 
GROUP BY date_part('month', orderdate)
ORDER BY MONTH_;

 month_ | orders_per_month
--------+------------------
      1 |                4
      2 |                4
      3 |                2
(3 rows)


--- second approach 
SELECT 
    TO_CHAR(orderdate, 'month') MONTH_, 
    COUNT(*) ORDERS_PER_MONTH
FROM orders 
GROUP BY TO_CHAR(orderdate, 'month');

  month_   | orders_per_month
-----------+------------------
 january   |                4
 march     |                2
 february  |                4
(3 rows)

```

> [!success] Question 3 :
> lister les achat qui ont ete fait lors du moi de fevrier ?

```sql 
SELECT 
   O.orderid, 
   O.productid, 
   P.product PRODUCT,
   O.orderdate MONTH_
FROM orders O
LEFT JOIN products P ON O.productid = P.productid 
WHERE date_part('month', O.orderdate) = 2
ORDER BY MONTH_;

 orderid | productid | product |   month_
---------+-----------+---------+------------
       5 |       104 | Caps    | 2025-02-01
       6 |       104 | Caps    | 2025-02-05
       7 |       102 | Tire    | 2025-02-15
       8 |       101 | Bottle  | 2025-02-18
(4 rows)
```


> [!info] Remarque : 
> Toujour filtrer les donnes de type date en utilisent une format int pcq c'est toujour plus rapide que les autre type 
> 
> ![[Pasted image 20261117204747.png]]

![[Pasted image 20261117204900.png]]

#### comment decider ? 

![[Pasted image 20261117205013.png]]


### Comment formater et caster les dates en SQL ?

'yyyy'-'MM'-'DD' : sont des specificateur de format or ( format specifiers ).

> [!error] Remarque : 
> <font color="#F61067">"MM"</font> : Pour les mois 
> <font color="#F61067">"mm"</font> : Pour les minutes.
> sensible a la case.

### Les standard de representation : 

![[Pasted image 20261117205818.png]]

#### 01. C'est Quoi le formatage ? 

> <font color="#3FFC6D9">Formatage </font> : c'est le faite de changer le format de la date d'une standard a un autre en utilisent des fonction en SQL

![[Pasted image 20261117210121.png]]

> <font color="#3FFC6D9">Casting </font> : c'est le fait de changer le type de donne d'un type a un autre type 
> 
> Exemple : 
> -- Changer le '123' du string a un int 123
> -- date 2024-12-23  a string '2024-12-23'

![[Pasted image 20261117210344.png]]

<font color="#affc41">TO_CHAR(value, format, [, culture*])</font> : La fonction format permet de changer le format d'affichage d'une date ou d'un nembre a une format qu'on specifie il prend 3 parametre le dernier et optionelle.

+ Value  : valeur a formater 
+ format : la format 
+ culture : ( les region : europe, usa ...) <font color="#ee4545">Optionel</font>

Exemple : 

![[Pasted image 20261117210752.png]]

format japan 

![[Pasted image 20261117210812.png]]

format france 

![[Pasted image 20261117210828.png]]

```sql
SELECT 
  TO_CHAR(orderdate, 'DD') DATE_NUM, 
  TO_CHAR(orderdate, 'dy') DATE_SOME, 
  TO_CHAR(orderdate, 'day') DATE_FULL, 
  TO_CHAR(orderdate, 'MM') MONTH_NUM,
  TO_CHAR(orderdate, 'MON') MONTH_3CHAR, 
  TO_CHAR(orderdate, 'MONTH') MONTH_FULL, 
  TO_CHAR(orderdate, 'DD-MMM-YYYY') FR_FORMAT, -- format FR
  TO_CHAR(orderdate, 'MMM-DD-YYYY') US_FORMAT
FROM orders; 
```

>[!success]+ Question 1 : 
> + Afficher la colonne creationtime dans la table orders sous la forme suivantes : 
>   
>   "Day Wed Jan Q1 2024 12:32:23 PM"

```sql
SELECT 
   TO_CHAR(creationtime, 'DD Dy MON Qu YYYY HH:MM:SS PM')
FROM orders; 

-- OR 
SELECT 
	'Day ' || TO_CHAR(creationtime, 'dy MON') || ' Q' || TO_CHAR(creationtime, 'Q ') || TO_CHAR(creationtime, 'YYYY hh:mm:ss PM') CUSTOME_FORMAT
FROM orders; 
```


```sql 
SELECT 
    TO_CHAR(DATE_TRUNC('month', orderdate), 'YYYY Mon') DATE_, 
    COUNT(*) ORDERS_COUNT
FROM orders
GROUP BY TO_CHAR(DATE_TRUNC('month', orderdate), 'YYYY Mon');
```


### La standardisation en sql : 

L'utilite de la dernier partie c'est que en tant que data engineer vous recoi les donnes a partir de diver source ( csv, api, dbs etc ... )
et par fois les donnes dans chaque source prent different format d'affichage donc la standardisation garentille l'unicite des donnes 

![[Pasted image 20261119184926.png]]

les specificateurs de format pour les dates 

![[Pasted image 20261119185125.png]]

les specificateur de format pour les numero 

![[Pasted image 20261119185159.png]]

<font color="#affc41">CAST(value, data_type, [, style*])</font> : Pour convertir une donnes d'un type a un autre, par exemple un numero de int a string etc ...

Exemple 
<font color="#affc41">CAST('123' AS INTEGER)</font> : Convertir le string 123 a une valeur numeric
<font color="#affc41">CAST('01-OCT-2015' AS DATE)</font> : Covertir la date string a une date 

```sql
SELECT CAST('01-February-2020' AS DATE);
SELECT CAST('02-Feb-2002)' AS DATE) 
```

Question : regrouper les order par leur date de creation ('Annee Mois')

```sql
SELECT 
TO_CHAR(CAST(creationtime AS DATE), 'YYYY Mon') CREATION_TIME, 
COUNT(*) AMOUNT
FROM orders
GROUP BY TO_CHAR(CAST(creationtime AS DATE), 'YYYY Mon') ;
```

#### CAST VS COVERT VS FORMAT ?

![[Pasted image 20261119194309.png]]


### Operation mathematique sur les dates en SQL ?

<font color="#affc41">DATEADD(datepart, number, date) (not for psql)</font> : Pour ajouter/sustraire un nembre de jour a une date donnes 

Exemple : 
`DATEADD(month, 2, '2020-12-01')`
`DATEADD(year, 12, '12-02-2002')`


```sql
SELECT 
'2002-10-12' OLD_DATE,
CAST('2002-10-12'::DATE + interval '3 days' AS DATE) NEW_DATE;

-- years 
SELECT 
'10-02-2002' OLD_DATE,
CAST('10-02-2002'::DATE + INTERVAL '20 years' AS DATE) NEW_DATE;
-- OR 


-- before 10 days 
SELECT 
'2002-11-20' OLD_DATE, 
CAST('2002-11-20'::DATE - INTERVAL '10 days' AS DATE) NEW_DATE;
```


<font color="#affc41">DATEDIFF(datepart, number, date) (not for psql)</font> : trouver la diff entre deux date donnes en psql cette fonction n'existe pas au lieu on utilisent l'approche suivant 

```sql
SELECT EXTRACT(MONTH FROM AGE('2024-02-23', '2002-03-20')) AS MONTH_DIFF;
SELECT EXTRACT(YEAR FROM AGE('2024-02-23', '2002-03-20')) AS MONTH_DIFF;
-- OR
SELECT EXTRACT(YEAR FROM ('2024-02-23', '2002-03-20')) AS MONTH_DIFF;

-- OR simpler 
SELECT '2027-10-23'::DATE - '2002-12-01'::DATE DATE_DIFF; -- not clear 
```

Question 1 : calculer l'age des employer dans la base de donnes 

```sql
SELECT 
UPPER(firstname) || ' ' || INITCAP(lastname) FULL_NAME,
gender GENDER,
EXTRACT(YEAR FROM AGE(CAST(NOW() AS DATE), CAST(birthdate AS DATE))) AGE
FROM employees
WHERE lastname IS NOT NULL;
```

Question 2 : trouver la moyenne duration de livraison en jour pour chaque mois 

```sql
SELECT 
	TO_CHAR(shipdate, 'Month') MONTH_, 
	ROUND(AVG(EXTRACT(DAY FROM AGE(CAST(shipdate AS DATE), CAST(orderdate AS DATE)))), 0) || ' day' AVG_DAYS
FROM orders 
GROUP BY TO_CHAR(shipdate, 'Month');
```

Question 3 : trouver le nembre de jour entre chaque order et l'order avant 

```sql 
SELECT 
      orderid ORDER_,
      EXTRACT('day' FROM AGE(CAST(orderdate AS DATE), CAST(orderdate AS DATE))) NEMBRE_DE_JOUR 
FROM orders 
GROUP BY orderid;
```

<font color="#affc41">LAG(colonne_x OVER ( ORDER BY colonne_x)) (not for psql)</font> : cette fonction a une simple question comment je peut comparer une lignes avec la lignes avant.
pour eviter de faire une jointure sur la meme table.

exemple :

```
LAG(price, 1, 0) OVER (ORDER BY date) as prev_price 
1 : revenir par exactement une ligne ( value of rows to look back )
0 : si vous ne trouver rien met 0 au lieu de null. mais sa doit etre le meme type de donnes de la colonne 
-> int -> int 
-> date != int
```

![[Pasted image 20261119210843.png]]

```sql 
SELECT 
   orderid, 
   orderdate CURRENT, 
   LAG(orderdate) OVER (ORDER BY orderdate) PREVIOUS,
   EXTRACT('day' FROM AGE(orderdate, LAG(orderdate) OVER (ORDER BY orderdate))) DAYS
FROM orders;
```

### Date validation 

<font color="#affc41">pg_input_is_valid(value, type) others</font> : cette fonction permet de verifier si une valeur donnes et une date ou peut etre convertir a une date ou pas.

<font color="#affc41">ISDATE(value) others</font> : cette fonction permet de verifier si une valeur donnes et une date ou peut etre convertir a une date ou pas.

```sql 
SELECT pg_input_is_valid('2002-12-01', 'date'); -- t
SELECT pg_input_is_valid('2023-10-12', 'timestamp'); -- t
```


> [!error] Remarque : 
> sql accept que le format international de la date qui et : 
> `2025-12-12` -> `yyyy-mm-dd`

Exemple : requete pour caster les dates et skipper les dates qui ont une format non valid.

```sql
SELECT 
  orderdate, 
  pg_input_is_valid(orderdate, 'date'), 
  CASE WHEN pg_input_is_valid(orderdate, 'date') = 't' THEN CAST(orderdate AS DATE) 
  ELSE '0000-00-00'
  END NewOrderDate
FROM 
(
  SELECT '2020-02-03' AS orderdate UNION
  SELECT '2020-11-02' UNION
  SELECT '2003-03-12' UNION 
  SELECT '2021-02' 
);

```