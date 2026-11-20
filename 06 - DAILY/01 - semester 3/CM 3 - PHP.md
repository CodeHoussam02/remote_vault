
comment afficher les elements d'un tableau en php sous forme cle, valeur 

```php 
<? php 
	foreach ( $articles as $cle => $valeur ) {
		
		echo " - ".$cle." = ".$valeur;
	
	}
```


eviter d'ecrire des echo dans votre body, le meilleur methode donc pour afficher c'est d'utiliser la methode suivantes : 

```php 
<?= votre_traitement_ici ?>
```


la boucle for 

```php 
<?php for ($i = 0; $i < 10; $i++): ?>
    <?php $somme++; ?>
<?php endfor; ?>

```

comment faire un tableau multidimentionnel.

```php
$informations = [

            ["age" => 19, "jour" => 1, "reduction": FALSE],

            ["age" => 15, "jour" => 6, "reduction": FALSE],

            ["age" => 10, "jour" => 4, "reduction": TR]

        ];
```

comment je peut boucler sur ce tableau multidimentionnel

```php 
<?php foreach ( $informations as $info ) :?> 
        <? if ( $info["age"] < 14 ) ?>
            <?php $prix = "4€"; ?>
        <? elseif ( $info["age"] >= 14 && $info["age"] < 18 ) ?>
            <?php $prix = "5€"; ?>
        <? elseif ($info["age"] >= 18) ?>
            <?php $prix = "8€" ?>
        <? elseif ($info[""])

        <? endif ;?> 
    <?php endforeach ;?>
```