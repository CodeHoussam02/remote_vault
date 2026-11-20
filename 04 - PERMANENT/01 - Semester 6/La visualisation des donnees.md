---
tags:
  - coure
  - visualisation
  - power-bi
  - microsoft-fabric
date: 19-02-2025
professor: Pr. Amine
cssclasses:
  - Notebook-page-tan
---

## Plan 

| Chapitre | Description |
| -------- | ----------- |
|          |             |

## Introduction :

- dkdk
- 

## Different type de charts : 


<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px;">
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<img src="240_F_455018573_zxm3FjRQ08iGKKf8XGjGaxVP3sPn26AL.jpg" />
		<h6>Histogramme : </h6>
		- un histogramme est un graphique a barres qui montre la distribution des donnees numeriques en groupes appelees des "Intervalles"
	</div>
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4oM254ZxYJwiMzFID1yQW5mZ-H0suLyHCeQ&s" />
		<h6>Diagram en barres : </h6>
		- Ce graphiques utilisent des barres pour comparer des categories differentes. Plus la barre est longue, plus la valeur est grande.
	</div>
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTeYQwSevYyaohq15Vv6GJqy3biKATMPYcEsw&s"/>
		<h6>Graphique a lignes : </h6>
		- Ce type de graphique relle des points par des lignes pour montrer comment quelque chose change avec le temps.
	</div>
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<img src="https://cdn.pixabay.com/photo/2022/04/12/16/36/pie-chart-7128355_640.png" />
		<h6>Diagramme circulaire : </h6>
		- Diagramme circulaire ou bien ( PieChart ) Un cercle divise en paerts pour montrer les proportions ou pourcentages de differentes categories.
	</div>
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<h6>card : </h6>
	</div>
	<div style="padding: 10px; border: 2px #022F40 solid; border-radius: 8px">
		<h6>card : </h6>
	</div>
</div>


## C'est quoi la difference entre OLAP et OLTP ? 

| aspect                | OLAP                                             | OLTP                                               |
| --------------------- | ------------------------------------------------ | -------------------------------------------------- |
| Objectif              | Gerer les transactions courantes de l'entreprise | Analyse les donnees pour la prise de decision.     |
| Type d'operations     | Insertion, mise a jour, supression, lecture      | Requete complexe, aggregation, analyses.           |
| Utilisateurs          | Employee operationnel, caissiers, agents         | Analystes, decideurs, responsablitie strategiques. |
| Volume des donnees    | Faible a moyenne, donnees actuelles.             | Tres volumineuse, donnees historique.              |
| Temp de reponse       | Millisecondes a secondes ( rapide )              | Securite a minutes ( plus lente )                  |
| Integrite des donnees | Tres elevee, transaction ( ACID )                | Moin critique, favorise la performence             |
| Exemple d'usage       | Systeme boncaire, e-commerce, billetrie.         | Tableau de bord, analyse de ventes, data werhouse. |


# les types d'OLAP ?

- MOLAP : c'est une base de donnes multidimentionnel.
- ROLAP : 
- HOLAP : 