---
date: 17-02-2025
professor: Pr. Fouzi
tags:
  - Data-mining
  - Fouille-de-donnnee
  - coure
---

# Table de matier 

| Chapitre         | Description |
| ---------------- | ----------- |
| `  Chapitre 1  ` | -           |
| `  Chapitre 2  ` | -           |
| `  Chapitre 3  ` | -           |
| `  Chapitre 4  ` | -           |
 
### Introduction

Dans ce module on va voir les different proccessus d'extraction des connaissences (patrons) depuis des donnee volumineuse en utilisent des bonnes pratique avec utilisation des algorithme de data minings.

> [!summary]- Data Mining :
> 
> C'est le faites d'extraires les connaissences ou bien *parton* interissantes a partir de grandes de donnee. il signifie aussi d'analyse les donnees pour trouver des patrons cache en utilisent des moyenne automatique.


#### 01. C'est quoi la difference entre *Donnee*, *Information*, *Connaissence* ?


- <font color="#BAFF29" style="font-weight: bold; text-decoration: underline; font-size: 18px">Donnee</font> : les donnee sont des infornformatiomations bruts.
- <font color="#BAFF29" style="font-weight: bold; text-decoration: underline; font-size: 18px">Information</font> : sont des donnees presenter dans un context.
- <font color="#BAFF29" style="font-weight: bold; text-decoration: underline; font-size: 18px">Connaissence</font> : interpretation des donnee pour la prise de decisions

#### 02. Comment Gerer les donnees qui vient de diverse source, pour les rendres utile pour prendre un decision ? 


###### 01. Typologie des methodes de fouille de donnees : 

> [!error]+ Typologie des methodes de fouilles des donnees : 
>  
> La <font color="#ee4545" style="text-decoration: underline; font-weight: bold">Typologie des methodes de fouille de donnees</font> (ou data mining ) repose sur la distinction entre deux grandes categorie de modeles : 

- <font color="#FFE1C6">Modele descriptifs : </font> Un modele descriptif a pour but de <font color="" style="text-decoration: underline; font-weight: bold">decrire</font> ou de <font color="" style="text-decoration: underline; font-weight: bold">resumer</font> les caracteristiques principales des donnees. il permet d'identifier des patternes, des relations ou des structures cachees dans les donnees sans necessairement predire une variable cible.

- <font color="#FFE1C6">Modele predectifs : </font>Un modele predictif vise a <font color="" style="text-decoration: underline; font-weight: bold">prevoir</font> ou a <font color="" style="text-decoration: underline; font-weight: bold">estimer</font>une valeur future ou une variable cible en fonction des donnees disponibles. contrairement aux modeles descriptifs, les modeles predictifs sont orientes vers l'action et permettant de prendre des decisions basees sur des predictions. 

---
###### 02. Les type d'apprentissage : 

- <font color="#3FFC6D9">Apprentissage supervise : </font>
	- est une methode ou le modele est entraine a partir d'un ensemble de donnees etiquetees, c'est a dire que chaque exemple d'entree est associe a une sortie ou une etiquette correcte.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Entrainement d'un modele pour predire si une e-mail est un spam ou non, en utilisent un ensemble de courriels marques comme <font color="#ee4545">"spam"</font> ou <font color="#65B891">"non-spam"</font>
- <font color="#3FFC6D9">Apprentissage semi-supervise :</font> 
	- combiene des donnees annotees (etiquetee) et des donnees non annotees (non-etiquetees) pour entrainer un modele. cette approche est utile lorsque les donnees annotees sont rares ou couteuses a obtenir, mais que beaucoup de donnees non annotees sont desipo.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font> 
		- Entrainement d'un systeme de reconnaissance vocal avec une petite quantite de phrasee etiquetees et une grande quantite de donnees audio non etiquetees.
- <font color="#3FFC6D9">Apprentissage non supervise : </font> 
	- est utilise lorsque les donnees d'entrainement ne sont pas etiquetees. le modele doit decouvrire des structures ou des motifs caches dans les donnees sans aucune indication explicite sur ce qu'il doit apprendre
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font> 
		- Segmenter une base de clients en groupes homogenes sans connaitre a l'avance les criteres de segmentation.
- <font color="#3FFC6D9">Apprentissage par renforcement : </font> 
	- est une methode ou un agent apprend a interagir avec un envirenement en essayant differentes actions et en recompenses ou des penalites selon des choix. l'objectif est de maximiser la recomponse cumulee a long terme. ( utiliser en deepLearning )
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font> 
		- Entrainement d'un robot a jouer un jeu de GO ou a conduire une voiture autonome en maximisent sa perfermance grace au recompenses recues pour les bonnes actions.


 > [!summary]+ Quand on utilise N et N - 1 :
 > on utilise cette relation qu'on ton parle d'un <span style="text-decoration: underline; font-weight: bold">Echantillons</span>.
 > $$ \frac{X_{i}}{N - 1} $$
 > 
 > on utilise cette relation qu'on ton parle d'une <span style="text-decoration: underline; font-weight: bold">population</span>.
 > $$\frac{X_{i}}{N}$$

>[!warning]+ Que signifie $\bar{X}$ et $\bar{Y}$
>- $\bar{X}$ : represente la moyenne des $X_{i}$
>- $\bar{Y}$ : represente la moyenne des $Y_{i}$

---
###### 03. Les differents technique de fouille de donnee : 

- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">La classification :</font> 
	- Consiste a attribuer une etiquette ou une classe a chaque observation en fonction de ses caracteristiques.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Classer un e-mail comme spam ou "non-spam"
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- Arbres de decisions 
		- reseau de neurons
		- SVM (support vector mahcines)
- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">L'estimation : </font>
	- Estimer la distribution de probabilite sous-jacente des donnees.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Comprendre comment les valeurs d'une variable sont reparties dans un ensemble de donnees.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- KDE (Kernel density estimation)
		- Histogrammes.
- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">Le regroupement par similitude :</font> 
	- jsjsj
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- slsl
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- ksksk
- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">Regression : </font> 
	- Predire une valeur continue en fonction des caracteristique des donnees.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Prevoir le prix d'une maison en fonction de sa superficie, du nembre de chembre, etc...
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- Regression Lineaire.
		- Regression Logistique.
		- Arbre de regression.
- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">Clustering : </font>
	- Regrouper des objectifs similaires en clusters (groupes) sans utiliser d'etiquittes preexistantes.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Segmenter une base de clients en groupes homogenes selon leur comportements d'achat.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- K-means
		- clustering hierarchique.
- <font color="#fb8500" style="font-weight: bold; text-decoration: underline; font-size: 18px">Apprentissage profond (Deep Learning) : </font>
	- Utiliser des reseaux neuronaux complexes pour extraire automatiquement des representations a partir des donnees.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Reconnaissence d'image, traitement du langage naturel.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Algorithme :</font>
		- NLP (traitement automatique du langage naturel)
		- word Embeddings.

------
###### 04. L'annalyse univariet 

- <font color="#3FFC6D9">c'est quoi le median ?</font>
	- la mediane est la valeur qui separe les donnees en deux moities egales lorsque celle-ci sont triees par ordre croissant. c'est une mesure de tendance centrale comme moyenne, mais moin sensible aux valeur extraime (Outliers). en generale on utilise le mediane si ona des valeur des extraimes dans notre population ce qui fait la moyenne va etre affecter par c'est <font color="#fb8500" style="text-decoration: underline; font-weight: bold">Outliers</font>.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Calcul :</font>
		- Si le nombre d'observations est impaire, le mediane est la valeur du milieu.
		- Si le nembre d'observations est paire, la mediane est la moyenne des deux valeurs centrales.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exemple :</font>
		- Pour les donnees suivant `[3, 5, 7, 9, 11]` le mediane est 7.
		- pour les donnees suivant `[12, 4, 2, 3]` le mediane est 3
- <font color="#3FFC6D9">c'est quoi la variance ?</font> 
	- la variance mesure egalement la dispersion des donnees, mais contrairement a l'ecart-type, elle est exprimee en unite au carre. Elle represente la moyenne des ecarts quadratiques entre chaque observation et la moyenne.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Relation avec l'ecart-type :</font>
		- La variance est simplement le carre de l'ecart-type.
- <font color="#3FFC6D9">
	- c'est quoi L'ecart-type ?</font> 
	- L'ecart-type represente la dispersion ou la variabilite des valeurs autour de la moyennes, plus l'ecart-type est eleve. plus les donnees sont eloignees en moyenne de leur valeur centrale.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Interpretation :</font>
		- Si l'ecart-type est faible, les donnees sont regroupees pres de la moyenne. Si l'ecart-type est eleve, les donnes sont reparties sur une plage plus large.
- <font color="#3FFC6D9">c'est quoi echantillon ?</font> 
	- Un echantillon est un sous-ensemble de donnees extrait d'une population plus grande. il est utilise pour faire des inderences ou des generalisations sur la population entiere.
 
---
###### 04-1. Calcule de L'ecart-type '$\sigma$' et la variance '$\sigma^2$'

- dans cette etape de l'annalyse univariet on s'interesse a determiner la valeur de :

> [!example]+ la variance $S^2$ et l'eacrt-type $\sigma$ et la moyenne aussi 
> 
> - Avec : 
> $$S^2 = \frac{\sum(X_{i} - X)^2}{N}$$ N en cas d'une population.
> - Et : 
> $$\sigma = \sqrt{S^2}$$


![[Drawing 2025-02-17 21.36.49.excalidraw|800]]

---

###### 05. L'annalyse bivariet : 

- En statistique, plusieur probleme consistent a deifinir la relation qui existe entre deux variable statistique : 
		- Le nembre d'annees d'experience 
		- slsl
	- dans ce genre de probleme les principales questions quxquelles nous voudrons repondre sont les suivants :
		- Existe-il une relation ou une dependance entre les variables statistique ?
		- Cette relation, si elle existe, est-elle lineaire ou non?
		- Si une dependance lineaire existe, de quelle facons peut-on la traduire par une equation mathematique ?
	- Pour repondre a toutes ces questions on doit faire appele au principe de L'annalyse de regression :
		- Plutot que de mettre la difference entre chaque observation et la moyenne au carre, nous multiplions la difference entre chaque observation de la variable x et sa moyenne par la difference entre chaque observation de la variable y et sa moyenne :

> [!hint]+ La relation pour calculer La co-variance : 
> $$COV = \frac{\sum(X_{i}-\bar{X})(Y_{i} - \bar{Y})}{N} = \bar{XY} - (\bar{X}.\bar{Y})$$

- Interpretation des valeurs de la covariance : 
	- Si $cov(x,y) > 0$ <font color="ee4545" style="text-decoration: underline; font-weight: bold">Positive</font> :
		- Les variables X et Y evoluent dans le meme sens.
		- Lorsque X augmentent, Y a tendance d'augmenter aussi
		- Cela indique une relation linieaire positive entre les deux variable 
	- Si $cov(x,y) < 0$ <font color="ee4545" style="text-decoration: underline; font-weight: bold">Negative</font> :
		- Les variable x et y evoluent dans le sens oppose
		- Lorsque x augmente, y a tendance a diminuer
		- Cela indique une relation lineaire negative entre les deux variable
	- Si $cov(x, y) = 0$ <font color="ee4545" style="text-decoration: underline; font-weight: bold">Null</font> :
		- Il n'y a pas de relation lineaire entre x et y
		- Attention : Cela ne signifie pas forcement qu'elles sont independantes, car une relation non lineaire peut exister entre les deux variable. 

---
###### 06. L'annalyse de regression simple :

- L'annalyse de la regression est une methode statistique qui permet d'etudier le type de relation 
- dans notre cas x independente (explictif) et la variable y dependente ( a expliquer ).
- Exemple :
	- Le cout du loyer en fonction du nembre de pieces, du niveau d'etage dans l'ensemble, des services offert :
		- cas d'une regression multiple :
		$$y=f(x_{i},x_{})$$
- Une regression simple : 
	- et dit simple si elle permet de predire les valeurs d;une variable dit <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">dependante (expliquer y)</font> a partir des valeurs prises par une autre variable dit <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">independente (explicative x)</font>
- Une regression Multiple : 
	- ksks
- La regression et une demarche mathematique qui nous aides a determiner la dependences des valeurs.
---
- Nuage de points diagramme de dispersion :
	- C'est la representation graphique dans le plan cartesiene de l'ensemble des paires de donnees $[x_{i, y_{i}}]$ ces donnees proviennent d'une serie statistique de deux valeur obtenue a partir d'une etude menee sur un echantillon ou sur une population 
- Exemple :
	- slsl
	- On utlise une valeur aleatoire de x, y dans la premiere fois mais apres on utlise l'algorithme de <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">"descent de gradient"</font> pour trouver les mailleur valeur de x, et y.
	- En utilisent le pricipe de <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">derive partielle</font> pour trouver la meilleur valeur de a et b pour que $y = ax+b$
###### 07. Le coifficient de corelation :
- Le coefficient de correlation de bravais-pearson est un indice statistique qui exprime l'intensite et le sens (positif ouu negatif) de la relation lineaire entre deux variable quantative, c'est une mesure de la liaison lineaire, c'est a dire la capacite de predire une variable x par une autre y a l'aide d'un modele lineaire:

> [!example]+ Relation pour calculer la coifficient de corelation
> $$r=\frac{cov(x, y)}{\sigma_{x} . \sigma_{y}}$$

- danc le coifficient de corelation comprie entre la l'intervalle $[-1,1]$ 
- la cov determine le sens de r.
- interpretation des resultat : 
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Si r > 0 ( correlation fortes positives ) :</font>
		- Lorsque x augmente, y a tendance a augmenter aussi.
		- plus r est proche de 1,  plus la relation lineaire positive et forte.
		- <font color="#fb8500" style="text-decoration: underline; font-weight: bold">Exemple :</font> La taille et le poids des individus ont generalement une correlation positive.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Si r infer 0 ( correlation fortes negatives ) :</font> 
		- Lorsque x augmentent, y a tendence a diminuer.
		- Plus r est proche de -1, plus la relation lineaire negative est fortes.
		- <font color="#fb8500" style="text-decoration: underline; font-weight: bold">Exemple :</font> le prix d'un produit et sa demande ont souvent une correlation negative.
	- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Si r = 0 ( pas de correlation lineaire ) :</font>
		- Il n'existe pas de relation lineaire entre x et y.
		- <font color="#fb8500" style="text-decoration: underline; font-weight: bold">Attention :</font> cela ne signifie pas qu'il n'y a <font color="#ee4545" style="text-decoration: underline; font-weight: bold">aucune relation</font>. Une relation non lineaire peut exister.

- <font color="#ee4545" style="text-decoration: underline; font-weight: bold">Exemple :</font>
	- Comment peut-on tester la relation lineaire entre deux variable continues ?
	- Par exemple, 
	- lsls
	- sks
	- Apres avoir calculer r l'intensite du lien lineaire entre les variables que l'on 
	- dkdk
	- ddk
- Les etapes a suivres :
	- Y 
	- on minimise la marge d'erreur a travaire la calcul de cette equation : 

> [!example]+ Relation pour calculer la marge d'erreur :  
$$E=\sum(y_{i}-b-ax_{i})$$

> [!example]+ Methode de moindre carre : 
> - Pour calculer la valeur de a on suit la relation suivante : 
> $$a = \frac{\operatorname{cov}(X;Y)}{\operatorname{Var}(x)} = \frac{\bar{XY} - \bar{X}.\bar{Y}}{\bar{X^2} - \bar{X}^2}$$
> - Avec b egale a : 
> $$b = \bar{Y} - a.\bar{X}$$


---

- <font color="#BAFF29" style="text-decoration: underline; font-weight: bold">Exercice 1 : </font>
- Les performences relaisees par 10 coureures sur un semi-marathon et un marathon sont donnees dans le tableau suivant (les etapes sont donnees en minutes )

| Numero i du coureur           | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| ----------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Temp $x_{i}$ au semi-marathon | 68  | 70  | 76  | 80  | 90  | 96  | 104 | 110 | 125 | 138 |
| Temps $y_{i}$ au marathon     | 145 | 150 | 170 | 185 | 200 | 220 | 250 | 285 | 320 | 345 |
1. Represnter le nuage de points Y et X dans un repere orthogonal 
2. Calculer la moyenne, la variance et l'eacrt-type de la serie dans temps ($x_{i}$) **realiser au semi-marathon, puis de la serie des temps ($y_{i}$) realiser au marathon**
3. Calculer la covariance, puis de X et Y et le coefficient de corellation lineaire 
4. Determiner l'equation de la droite de regression lineaire de Y sur X Representer cette droite sur 
5. Esitimer le temp mise sur un maraton 
solution :

1. Determinent $x_{i}$, $y_{i}$, $x_{i}-x$ et $y_{i}-y$

| $X_{i}$ | $Y_{i}$ | $X_{i} - \bar{X}$ | $Y_{i}-\bar{Y}$ | $(Xi-\bar{X})(Y_{i}-\bar{Y})$ | $(X_{i}-\bar{X})^2$ | $(X_{i}-\bar{Y})^2$ |
| ------- | ------- | ----------------- | --------------- | ----------------------------- | ------------------- | ------------------- |
| 68      | 145     | -27.7             | -82             | 2271.4                        |                     | 6724                |
| 70      | 150     | -25.7             | -77             | 1928.9                        | 660.49              | 5989                |
| 76      | 170     | -19.7             | -57             | 1122.9                        | 388.09              | 3249                |
| 80      | 185     | -15.7             | -42             | 659.4                         | 246.49              | 1764                |
| 90      | 200     | -5.7              | -27             | 153.9                         | 32.49               | 729                 |
| 96      | 220     | 0.3               | -7              | -2.1                          | 0.09                | 49                  |
| 104     | 250     | 8.3               | 23              | 190.9                         | 68.89               | 529                 |
| 110     | 285     | 14.3              | 58              | 829.4                         | 204.49              | 3364                |
| 125     | 320     | 29.3              | 93              | 2724.9                        | 858.49              | 8649                |
| 138     | 345     | 42.3              | 118             | 4991.4                        | 1789.29             | 13924               |
- One $\bar{X} = 95.7$ et $\bar{Y} = 227$ , $Somme_{(X_{i}-\bar{X})(Y_{i}-\bar{Y})} = 14923.1$, $Somme_{(X_{i}-\bar{X})} = 5016.1$, $Somme_{(Y_{i}-\bar{Y})} = 44910$ 

$$X_{i}-X = (68 - 95.7) = -27.7$$
$$X_{i}-\bar{X} = (70 - 150) = -25.7$$
$$Y_{i}-\bar{Y} = (145 - 227) = -81$$
$$Y_{i} - \bar{Y} = (150-227) = -77$$
- Calculon la $var(x)$, $var(y)$, $\sigma(x)$ et $\sigma(y)$

$var(x) = \frac{5016.1}{10} = 501.61$
$var(y) = \frac{44910}{10} = 4491$
$E(x) = \sigma(x) = \sqrt{var(x)} = 22.39$
$E(y)= \sigma(y) = \sqrt{var(y)} = 67.01$

--- 

###### 08. Matrice de corelation : 



----
## <font style="text-decoration: underline;"> Chapitre 3 : les regles d'association : </font>

- <font color="#ee4545" style="text-decoration: underline;">Reppel :</font> le machine learning permet d'expliquer le passer et de predire le future a l'aide de l'annalyse des donnees.
- machine learning permet de predire le future a l'aide de la modelisation des donnees collecter dans le passe.
- machine learning est un domaine multidisiolinaire, on trouve donc : la statistique, le data mining, les bases de donnees, et l'informatique
- Les analystes peuvent a l'aide du machine Learning, transformer ces connaissence extraites en produit a vendre a des clients pour segmenter le profit.
- features ( donnes d'entree ethiquter)

1. Apprentissage suppervise : 
	- on possede un ensemble d'exemples d'entrainement ou chaque exemple ( )
	- les phases :
		- Enrainement 
		- Prediction
	- il exsiste deux type d'apprentissage :
		- Apprentissage par modele : construire un modele en se basent sur les valeurs d'entre pour trouve une valeur de sortie. on utilise plus les exemples, d'entrainement une fois le modele et entraine.
		- Apprentissage par exemple : on predire la valeur de "y" en se basent toujour sur notre dataset
	- le modele 
2. Apprentissage non-suppervise :
	- On ne possede que les attributs des exemples d'entrainement, par la valeur de la variable decisionnelle.
	- on cherche a identifier des patrons ( patterns ) cache dans les donnees 
	- Ex : K-means mais le probleme avec cet algorithme c'est qu'ont doit determiner le nembre de class a la base 
3. Apprentissage semi-suppervise :
	- Seulement une partie des exemples d'entrainement est etiqutee ( la valeur de la variable decisionnelle est continue )
	- seulement une partie des donnees sont etiqutee.

#### 01. Les regles d'assocition :

- Une regles d'association est une pattern qui predit qu'un evenement va se realiser avec une certaine probabilite.
- Les regles d'association sont souvent des conditions logique si/alors (if/then), ces conditions permettent de trouver des regles d'association

- Exemple :
	- 80% des clients qui achetent une ordinateur achetent aussi une  imprimeante et un abonnement a internet, et une regle d'association associant l'item ordinateur aux items imprimante et abonnement a internet.
	- Si le client achete du lait alors il va acheter du cereal.

###### 01. Volcabulaire :

- Items : leur definiction depend du domaine d'application, ils peuvent constituer des produits des objects, des patients, des evenements, etc
- Transaction : Un ensemple d'items ( minimum 1 et maximum n ) etiquter avec un identifient unique, les items peuvent
- Itemst : eUn groupe d'items. les itemsets peuvent app
- Support : c'est la probabilite de retrouve un item ou une itemset 
	$$supprt(X) = \frac{x}{total}$$
- Regle : definit le lien entre deux itemsset X et Y n'ayant aucun item en commun, X->Y signifie que si X se trouve dans sune transaction, Y peut apparaitre dans cette meme transaction.
- Supprt d'un regle : Probabilite de trouve les items ou itemsets X et Y dans une transaction. Elle estime par le nembre de foix que X et Y apparaissent dans une transaction.
- Confiance autour d'une regle : Probabilite de trouve l'item ou l'itemset Y dans une transaction, sachant que l'item ou l'itemset X se trouve dans la meme transaction. Elle est estimee par la frequence corresondante observee
$$conf ( C \to A ) = p(A/C) = \frac{P(A \inter C)}{P(C)} = \frac{support(p_1, p_{2})}{support(p_{2})}$$
- Exemple : 
	- calculer conf de p5, p2 :
	$$conf(p_{5}, p_{2}) = \frac{}{}$$
- Lift d'une regle : Le lift d'une regle est le support l'itemset regroupant X et Y divise par le support de X et le support de Y le lift mesure le hasard.
		1 : fortes corelation. ( pas de relation entre X et Y )
		0 : faible corelation c-a-d y'a pas d'influence.
	 -n : une correlation tres rares.
- Exemple :

- support et le lift sont symetrique c-a-d x/y = y/x
- confiance(x/y) != confiance(y/x)
- A -> B = p(B/A) = P(AUB) / p(A)
- Lift = 3 c-a-d la proba d'acheter Y qu'on vous acheter X ce qui fait y'a une forte relation entre X et Y


###### Exemple 1 :

- calculer le  support et la confiance de A et B
	- support = nembre de transaction qui contient a la fois a et b / total 


###### Extraction des regles d'association :

- Certaines regles d'association ne nous interessent pas :
	- skks
	- sls
- L'extraction ne va concerner que les regles d'association ( valides ) dont le support est superieur ou egal au seuil minsupport et dont la confiance est supperieurs ou egale au seuil minconfiance.
- les seuils minsupport et minconfiance 
- Trouver les itemsets frequents : ceux qui ont un support minimum ( superieur a un seuil )
	- un sous-ensemble d'un ensemble frequent et frequent
		- si (AB) est frequent alors (A) et (B) le sont 
		- Si un itemset n'est pas un support minimun, alors aucun itemset l'incluent n'est frequent 
			- si (A) 

##### 01. L'Algorithme Apriori :

- L'algorithme de base Aprori 


# Chapitre 4 : Arbre de decision 

Definition : 
- un arbre de decision est un modele de prediction ou de classification utilise en ML, et plus precisament en apprentissage supervise. un arbre est obtenu a partir d'algorithme tels que le classification and regression tree (CART), Interctive Dichotomie 3 (ID3)
- vers la fin de l'arbre en trouve ou bien les noeuds terminaux contiennent la classe aussi applee classe a predire

##### 01. Comment trouver le meilleur choix :

- comment calculer l'entropie :
$$
E(s) = - p_{+} \log(p_{+}) - p_{-} \log_{2}(p_{-})
$$
- remarque : 
$$
\log_{2}(x) = \frac{\ln(x)}{\ln(2)}
$$
- la valeur max de l'entrepie egale a : 
$$
max(E) = \log(n)
$$
- comment calculer le gain d'information :
$$
GAIN(S,A) = Entrepie(S) - \sum_{v \in Valeur(A)} \frac{\left|S_{v}\right|}{\left|S\right|} Entrepie(S_{v})
$$

# L'arlgorithme K-means 

#### 01. c'est quoi l'algorithme de k-means : 

- k-means et un algorithme qui tente a chercher des patternes (motifs ) chache, il ne predire pas des nouvelles valeurs mais il et seulement utiliser pour regrouper des enregistrement similaire et d'eloigne les enregistrement disimilaire.

- la distance entre deux point represente la desimilarite entre c'est deux point et on cherche a diminuer la distance par la suite la decimilarite.

##### Remarque : 

- La classification : donner avec des ethiquete.
- La segmentation : donner son ethiquete. en generale dans ce cas la le decideur peut annalyse les resulatat en se basent 

- <font style="text-decoration: underline" color="#affc41">Precision :</font> parmi les positives classifier par notre modele combien de vrais positifs predit par notre modele.
$$
Precision = \frac{TP}{TP + FP}
$$
- <font style="text-decoration: underline" color="#affc41">Recall :</font> combien des enregistrement classifier comme positifs parmis les vrais positifs
$$
\mathrm{Re}call = \frac{TP}{TP + FN}
$$
- <font style="text-decoration: underline" color="#affc41"> accuracy :</font> dkd



- Le concept de la decense de gradiant : se base sur le calcule des derivee pour ajuster les poit de notre reseau de neuron. ( se base sur le calcule de la derive partielle pour ajuster les poids )

##### Remarque : 

- recherche sur l'algorithme de # Descente de Gradient et comment l'algorithme ce fonctionne.