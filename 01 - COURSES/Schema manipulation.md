Pour cree une schema : 

```sql
```

Schema par default et set sur "public". Donc pour changer le search path sur cette schema on fait 

```sql 
-- Afficher le search path 
SHOW search_path;

-- changer le path de recherche a cette schema
SET search_path TO myschema;
```

[documentation for psql schema](https://www.postgresql.org/docs/current/ddl-schemas.html)

