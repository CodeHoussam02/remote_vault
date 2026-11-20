> 1. L'bjectif et de cree une fonction qui va nous permet de calculer le factorile d'un nembre donner par l'utilisateur.
##### En utilisent une fonction et loop iteration.

```sql
DROP FUNCTION IF EXISTS uf_fact;
DELIMITER $$

CREATE FUNCTION uf_fact(nbr INT)
RETURNS INT
DETERMINISTIC
BEGIN
    DECLARE x INT DEFAULT 1;
    DECLARE res INT DEFAULT 1;

    loop_default: LOOP
        IF x > nbr THEN 
            LEAVE loop_default;
        END IF;
        SET res = res * x;
        SET x = x + 1;
    END LOOP;

    RETURN res;
END $$

DELIMITER ;

SELECT uf_fact(5);

```
##### En utilisent les procedure en utilisent while 

```sql 
	delete procedure if exists sp_fact;
	delimiter $$
	create procedure sp_fact(in nbr int)
		begin 
			declare x int default 1;
			declate res int default 1;
			while x <= nbr do
				set res = res * x;
				set x = x + 1;
			end while
		select res as resultat_factoriel
		end $$ 
	delimiter ;
	- call the procedure
	call sp_fact(5) --> 120;
```
##### Les declaration inormative en sql 

> ==__Deterministic__==
> cette declaration definie que cette fonction retourne la meme result seulent le meme parametre specifier.

> ==__Reads sql data__==
> cette declaration definie que cette fnc ou bien procedure intergir avec la base de donner son effectuer un changement au niveau des donner.

> ==__Modifies sql data__==
> cette declaration definie que cette func oubien procedure interagisse avec la base de donner et peut aussi effectuer des changement.

```sql 
	drop function if exists uf_test;
	delimitor $$
	create function uf_test(nb int)
		Returns int 
		Reads sql data 
		Diterministic || Not deterministic
	...
	delimiter ;
```
##### Exemple d'une procedure qui affiche le nembre de personne choisie " deterministic "

```sql
drop procedure if exists sp_data 
delimiter $$ 
create procedure sp_date (in num int)
	reads sql data 
	deterministic
begin
	select * 
	from personne
	limit num; 	
end $$ 
delimiter ;
```

##### " The not deterministic version "

> C'est a dire en va sisire un nembre de personne a notre procedure et chaque fois il va nous donner un tableau random des personne seulon le nembre passe.
- _La method qu'on va etuliser_
```sql
	select * from personne order by rand();
	// limite 
	select * from personne order by rand() limit num 
```

- _Exemple_

```sql
drop procedure if exists sp_data 
delimiter $$ 
create procedure sp_date (in num int)
	reads sql data 
	deterministic
begin
	select * 
	from personne 
	order by rand() 
	limit num; 	
end $$ 
delimiter ;
```

