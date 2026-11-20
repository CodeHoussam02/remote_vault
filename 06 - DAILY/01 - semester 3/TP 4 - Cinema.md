### 01. shema de la base de donnee 

```txt
 FILMS(nofilm, titre, #norealisateur, #noproducteur)
 PROJECTION(#nofilm, nosalle, date_proj, heure)
 JOUER(#nofilm, #noacteur)
 VOIR(#nofilm, #nospect)
 AIMER(#nofilm, #nospect)
 INDIVIDUS (nopers, nompers)
```

![[Pasted image 20251001111202.png]]

#### 02. Operation d'agregations 

1. Nombre de films vus (Alias as nbre_films_vus) par spectateur (nom du spectateur et nombre de films), ordonnés par nom de spectateur.

```sql 
select i.nompers, count(v.nofilm) as nbre_films_vus
from individus as i 
join voir v on v.nospect = i.nopers 
group by i.nompers
order by i.nompers;
```

resultat 

 nompers  | nbre_films_vus 
----------+----------------
 Amirault |             12
 Andreu   |              5
 Arnault  |              6
 Barbot   |              7
 Barre    |              4

2. Numéros, parordre croissant, et noms des acteurs qui ont joué plus de 3 films (strictement)

```sql 
select j.noacteur, i.nompers 
from jouer j 
join individus i on j.noacteur = i.nopers
where j.noacteur in ( 
	SELECT noacteur 
    FROM jouer 
    GROUP BY noacteur 
    HAVING COUNT(nofilm) > 3 )
order by j.noacteur;
```

resultat

noacteur | nompers 
----------+---------
 P12      | Jegou
 P12      | Jegou
 P12      | Jegou
 P12      | Jegou
 P7       | Claveau
 P7       | Claveau
 P7       | Claveau
 P7       | Claveau
 P9       | Arnault
 P9       | Arnault
 P9       | Arnault
 P9       | Arnault


3. Numéros, croissants, et titres des films qui ont été aimés par plus de dix personnes (strictement).

```sql
select a.nofilm numero, f.titre
from aimer a 
join films f on a.nofilm = f.nofilm 
where a.nospect in (
	select nofim
	from aimer 
	group by nofilm 
	having count(nofilm) > 10
)
order by a.nofilm asc; 

-- 

SELECT a.nofilm numero, f.titre
FROM aimer a 
JOIN films f ON a.nofilm = f.nofilm 
WHERE a.nofilm IN (
    SELECT nofilm
    FROM aimer 
    GROUP BY nofilm 
    HAVING COUNT(nospect) > 10    -- ← CORRECTION ICI
)
ORDER BY a.nofilm ASC;

```

 numero | titre 
--------+-------
 F01    | film1
 F01    | film1
 F01    | film1
 F01    | film1
 F01    | film1


4. Titres des films et nombre de spectateurs (Alias as nbre_spectateurs) qui ont été vus par moins de 5 personnes (strictement)

```sql 
select titre, count(v.nospect)
from films f 
join voir v on v.nofilm = f.nofilm 
where v.nospect in (
	select nofilm, nospect 
	from voir v
	group by nospect 
	having count(v.nopect) < 5
);
```