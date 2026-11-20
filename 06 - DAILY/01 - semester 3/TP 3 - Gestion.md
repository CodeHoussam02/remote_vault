1. lister les facture disctinct par ordre croissant des numeros, en indiquant pour chaque facture son numero et le nom du client.

```sql
select distinct c.nom, f.nofacture
from interventions i 
join clients c on c.noclient = i.noclient
join factures f on f.nofacture = i.nofacture;
```
resultat 

              nom                 | nofacture 
--------------------------------+-----------
 Provent                        |      1008
 Provent                        |      1002
 Rivoire                        |      1003
 Dallalon                       |      1005
 Rivoire                        |      1006
 Dallalon                       |      1009
 Rivoire                        |      1010
 Rivoire                        |      1001
 Favero                         |      1007
 Labric                         |      1011


2. Numeros distinct des factures non regles, en ordre croissant, et nom du client correspondant.

```sql
select f.nofacture, c.nom 
from interventions i 
join factures f on f.nofacture = i.nofacture
join clients  c on c.noclient  = i.noclient
where f.etat ilike 'r'
order by f.nofacture asc;
```

resultat 

 nofacture |              nom               
-----------+--------------------------------
      1001 | Rivoire                       
      1002 | Provent                       
      1002 | Provent                       
      1003 | Rivoire                       
      1005 | Dallalon                      
      1006 | Rivoire                       
      1007 | Favero                        
      1007 | Favero                        
      1008 | Provent         


3. Numéros et dates des factures réglées du client Rivoire, avec en plus numéros et date des factures en cours du client Dallalon.

```sql 
select c.nom, f.nofacture, f.datefacture 
from interventions i 
join factures f on i.nofacture = f.nofacture
join clients  c on i.noclient = c.noclient
where c.nom = 'Rivoire' and f.etat ilike 'R'
union 
select c.nom, f.nofacture, f.datefacture 
from interventions i 
join factures f on f.nofacture = i.nofacture 
join clients c  on c.noclient  = i.noclient 
where c.nom = 'Dallalon' and f.etat = 'C';
```

resultat 

              nom                 | nofacture   | datefacture 
--------------------------------+-----------+-------------
 Dallalon                       |      1009 | 2019-07-22
 Rivoire                        |      1001 | 2019-02-12
 Rivoire                        |      1003 | 2019-04-24
 Rivoire                        |      1006 | 2019-07-08


4. Liste de toutes les références de produits par ordre décroissant des quantités remplacées, en indiquant pour chaque produit sa référence, le numéro de l’intervention, et leur quantité remplacée. Même les références de produits qui n’ont jamais été remplacés doivent y figurer. Remarques : 
	1. • Moodle necomprendpasles RIGHT JOIN. Vous ne pouvez utiliserque LEFT JOIN. 
	2. • PostGreSQLplace les null en début de classement, mais SQLite les place à la fin

```sql 
select p.reference, r.nointerv, r.qteremplacee
from produits p 
left join remplacements r on p.reference = r.reference 
order by r.qteremplacee;
```

resultat 

 reference | nointerv | qteremplacee 
-----------+----------+--------------
 DT802     |     1043 |            1
 DT180     |     1043 |            1
 DT205     |     1044 |            1
 DT010     |     1045 |            1
 DT310     |     1046 |            1
 DT015     |     1048 |            1
 DT711     |     1043 |            2
 DT120     |     1047 |            2
 DT125     |     1045 |            2
 DT121     |          |             
 DT122     |          |             

5. Liste de toutes les factures en ordre croissant des numéros de facture, en indiquant les numéros d’interventions correspondants. Même les factures n’ayant pas donné lieu à une intervention doivent apparaître dans le résultat. Remarque : Moodle ne comprend pas les RIGHTJOIN.Vous ne pouvez utiliserque LEFTJOIN.

```sql 
select f.nofacture, i.nointerv 
from factures f 
left join interventions i on i.nofacture = f.nofacture 
order by f.nofacture asc;
```

resultat 

 nofacture | nointerv 
-----------+----------
      1000 |         
      1001 |     1039
      1002 |     1041
      1002 |     1040
      1003 |     1042
      1004 |         
      1005 |     1043
      1006 |     1044
      1007 |     1046
      1007 |     1045
      1008 |     1047
      1009 |     1048
      1010 |     1049
      1011 |     1052
      1011 |     1051
      1011 |     1050
      1012 |         
      1013 |        


6. Numéros distincts des factures pour lesquelles à la fois Bonnaz et Saultier sont intervenus.

```sql 
select f.nofacture 
from interventions i 
join factures f on f.nofacture = i.nofacture
join clients c on c.noclient = i.noclient 
where c.nom = 'Bonnaz' or c.nom = 'Saultier';
```

resultat 

7. Désignation des produits qui n’ont jamais été remplacés. Vous pouvez proposer jusqu’à quatre solutions : l’une avec NOT IN, une autre avec <font color="#BAFF29">NOT EXISTS</font>, une avec <font color="#BAFF29">LEFT JOIN</font> et IS <font color="#BAFF29">NULL</font> et enfin uneavecEXCEPT (propre à Post GreSQL). Une seule solution sera déposée sur Moodle.

###### <font color="#3FFC6D9">proposition 1 : Left join</font>

```sql 
select p.designation 
from  produits p
left join remplacements r on r.reference = p.reference
where r.reference is null;
```

resultat 

                    designation                     
----------------------------------------------------
 Connecteur1                                       
 Connecteur2      

###### <font color="#3FFC6D9">proposition 1 : not exists</font>

```sql 
select p.designation 
from produits p 
where not exists ( select 1 from replacements r where p.reference = r.reference );
```

                    designation                     
----------------------------------------------------
 Connecteur1                                       
 Connecteur2       


###### <font color="#3FFC6D9">proposition 3 : is null</font>

```sql
```

resultat 



8. Liste desclients (numéro et nom), par ordre croissant de numéro,qui n’ont jamais eu d’intervention. Proposeztrois solutions : l’une avec NOT IN, une autre avec NOT EXISTS et une dernière avec LEFT JOIN et IS NULL. Une seule solution sera déposée sur Moodle.

###### <font color="#3FFC6D9">proposition 1 : left join + is null </font>

```sql
select c.noclient, c.nom, i.nointerv 
from clients c 
left join interventions i on i.noclient = c.noclient 
where i.nointerv is null
order by c.noclient;
```

resultat 

 noclient |              nom               | nointerv 
----------+--------------------------------+----------
      108 | Usturritz                      |         
      109 | Lavalee                        |         

<font color="#3FFC6D9">proposition 1 : left join + is null </font>

```sql 
select c.noclient, c.nom
from client c 
where not exists ( select 1 from interventios i where c.noclient = i.noclient );
```

resultat 

 noclient |              nom               
----------+--------------------------------
      108 | Usturritz                     
      109 | Lavalee     


9. Liste des références et désignations des produits qui ont été remplacés dans toutes les interventions (COUNT INTERDIT). Avec le jeu de données actuel, cette requête ne retourne aucun tuple.

```sql 
select p.reference, p.designation 
from produits p
left join remplacements r on r.reference = p.reference

```