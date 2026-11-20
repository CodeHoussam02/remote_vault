
### Quiz numero 1 : 



----

### Quiz numero 2 : 

On considère l'expression valide pour un "SIMILAR TO" suivante :

```sql
**(A|B){2}[[:digit::]]{3}**
```

Quelles sont les chaînes acceptées par cette expression ?  

Question 1Réponse

```sql
- [x] a.AB3  

- [x] b.(AB)333  

- [x] c.AA222  

- [x] d.AB123  

- [x] e.A1B4A3  
```


### Question 2

Terminé

Marquer la question

#### Texte de la question

On considère les chaînes de caractères suivantes

ABC123

DFG436

JLG666

Parmi les expressions ci-dessous, valides pour l'opérateur SIMILAR TO, déterminez celle qui accepte toutes les chaines.  

Question 2Réponse

a.

([[:upper:]]|[[:digit:]]){3}  

b.

([[:upper:]][[:digit:]]){3}  

c.

[[:upper:]][[:digit:]]{3}  

d.

[[:upper:]]{3}[[:digit:]]{3}  


#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  
lors d'un accident, avec un certain degré de gravité.

### Question 3

Terminé

#### Texte de la question

Sélectionnez le ou les attributs constituant la clé primaire de la table VEHPART :  

Question 3Réponse

a.

noveh

b.

noacc


#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  
lors d'un accident, avec un certain degré de gravité.

### Question 4

#### Texte de la question

Sélectionnez le ou les attributs qui est|sont clé(s) étrangère(s) de la table BLESSE :  

Question 4Réponse

a.

nopers

b.

gravite  

c.

noacc


#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  

lors d'un accident, avec un certain degré de gravité.

### Question 5

#### Texte de la question

numéros croissants d'accidents dans le 85 (type entier)

Réponse :(régime de pénalités : 20, 40, 60, 80, 100 %)

![Full screen](https://moodle.univ-lr.fr/2025/theme/image.php/boost_lruniv/qtype_coderunner/1758705680/fullscreen "Full screen")

#### Feedback

||Test|Résultat attendu||
|---|---|---|---|
||-- TEST|noacc<br>-----<br>9<br>10||

#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  
lors d'un accident, avec un certain degré de gravité.

### Question 6

#### Texte de la question

Liste des numeros d'accidents et type des véhicules ayant participés, ordonnée par numero puis type croissants

Réponse :(régime de pénalités : 20, 40, 60, 80, 100 %)

#### Feedback

||Test|Résultat attendu|Résultat obtenu||
|---|---|---|---|---|
||-- TEST|noacc  type<br>-----  ------<br>1      500<br>1      CHIRON<br>1      IBIZA<br>1      ZOE<br>2      525<br>2      CHIRON<br>2      ZOE<br>4      CHIRON<br>4      DS<br>5      500<br>5      DS<br>6      525<br>7      IBIZA<br>8      ZOE<br>9      CHIRON<br>10     DS|noacc  type<br>-----  ------<br>1      500<br>1      CHIRON<br>1      IBIZA<br>1      ZOE<br>2      525<br>2      CHIRON<br>2      ZOE<br>4      CHIRON<br>4      DS<br>5      500<br>5      DS<br>6      525<br>7      IBIZA<br>8      ZOE<br>9      CHIRON<br>10     DS||

Tous les tests ont été réussis ! 

#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  
lors d'un accident, avec un certain degré de gravité.

### Question 7

#### Texte de la question

Écrivez une requête SQL permettant d'afficher les prénoms des blessés avec une gravité supérieure ou égale à 2, triés par ordre alphabétique des prénoms.

Réponse :(régime de pénalités : 20, 40, 60, 80, 100 %)

![Full screen](https://moodle.univ-lr.fr/2025/theme/image.php/boost_lruniv/qtype_coderunner/1758705680/fullscreen "Full screen")

#### Feedback

||Test|Résultat attendu|Résultat obtenu||
|---|---|---|---|---|
||-- TEST|prenom     gravite<br>---------  -------<br>ANTHONY    2<br>ANTHONY    2<br>JEAN-LOUP  2<br>KARELL     2<br>VINCENT    2|prenom     gravite<br>---------  -------<br>ANTHONY    2<br>ANTHONY    2<br>JEAN-LOUP  2<br>KARELL     2<br>VINCENT    2||

Tous les tests ont été réussis ! 

#### Texte informatif

Ci-dessous le schéma relationnel issu de l'analyse d'une société d'assurance.  
  
PERSONNES(nopers, nom, prenom, adresse)  
VEHICULES(noveh, marque, type)  
CONDUCTEURS(nopers,noveh)  
ACCIDENTS(noacc,date,dpt)  
VEHPART(noacc,noveh)  
BLESSES(noacc,nopers,gravite)  
  
La table CONDUCTEURS permet d'associer un véhicule à une personne :  
il s'agit de son conducteur.  
  
La table ACCIDENTS permet de répertorier les accidents.  
  
La table VEHPART permet d'identifier les véhicules ont participé aux accidents.  
  
La table BLESSES permet d'identifier les personnes qui ont été blessées  
lors d'un accident, avec un certain degré de gravité.

### Question 8

#### Texte de la question

Écrivez une requête SQL permettant d'afficher les numéros des accidents, par ordre croissant, et la gravité des blessures, y compris lorsqu'il n'y a pas de blessé.

Réponse :(régime de pénalités : 20, 40, 60, 80, 100 %)
