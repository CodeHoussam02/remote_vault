
- start redis service 
	`sudo snap start/enable redis`
- stop redis service 
	`sudo stop redis`
- afficher tout les services running 
	`sudo snap services`


1. pour afficher touts les bases de donne qui exist 

```redis
	config get databases.
```

2. selectionner une base de donne

```redis 
	select 2
```

3. inserer un element a notre base de donne 

```redis 
	set CLE "valeur"
```


4. pour recuperer la valeur de la cle 

```redis 
	get CLE
```

5. enregistrer les modification effectuer sur notre base de donne

```redis
	save
```

6. pour renommer notre base de donne 

```redis 

```