
### Definition de la regression lineaire simple : 

>[!success] Definition de la regression lineare ( simple ) : 
> La régression linéaire simple est une méthode statistique qui permet de modéliser la relation entre une variable indépendante $X$ et une variable dépendante $Y$. Elle consiste à ajuster une droite de la forme $Y=aX+bY$ pour prédire les valeurs de $Y$ à partir de $X$.

#### L'objectif de ce tp : 

- A l'aide de ce tp on va apprendre comment implimenter un algorithme de regression lineaire simple qui fait partie des <font color="#ee4545" style="font-weight: bold; text-decoration: underline; font-size: 15px">algorithme d'apprentissage suppervise</font> pour predire la valeur d'un variable <font style="font-weight: bold; text-decoration: underline; font-size: 15px">dependent [y] ou bien ce qu'on appele le outcome / target </font> en se basent sur un variable <font style="font-weight: bold; text-decoration: underline; font-size: 15px">independent x.</font>

### Exemple de notre en jeux de donnees : 

| x      | Y      |
| ------ | ------ |
| 6.1101 | 17.592 |
| 5.5277 | 9.1302 |
| 8.5186 | 13.662 |
| 7.0032 | 11.854 |
| 5.8598 | 6.8233 |
| 8.3829 | 11.886 |
| ...    | ...    |

#### Etape 1 : Importation des bibliothèques nécessaires

```python 
# importation des biblios 
import pandas as pd 
import matplotlib.pyplot as plt 
import seaborn as sns 
from sklearn import linear_model 
from sklearn import metrics
from sklearn import model_selection

# importation de notre on jeux de donnees 
data = pd.read_csv('./datasetRL.csv')
```

---
#### Etape 2 : Analyse univariet & bivariet des donnees. 

pour comprendre notre base d'apprentissage on va suivre les etapes suivantes : 

```python
data.shape
```

![[Pasted image 20250601224438.png]]

comme vous voyez notre base d'apprentissage contient on generale notre base d'apprentissage ce compose de 97 ligne et 2 colonne.

```python
data.info()
```

![[Pasted image 20250601224646.png]]

aussi on observe que les deux colonnes x et y contient que des valeurs reel et y'a pas de valeur monquant dans notre jeu de donnee.

```python 
data.describe().T
```

![[Pasted image 20250601224937.png]]

resumer statistique de notre base d'apprentissage.

```python
data.isna().sum()
```

![[Pasted image 20250601225257.png]]

via cette ligne on fait une verification sur l'existance des valeur monquantes dans notre on jeu de donnees

```python
plt.xlabel('x')
plt.ylabel('y')
plt.scatter(data['x'], data['y'], marker='+', color='red')
```

![[Pasted image 20250601230448.png]]

on observe de ce nuage de point que y'a une relation fortes positifs entre les deux variable ce qui fait si <font color="#affc41">x augmente y a tendence d'augmenter aussi.</font>

cela signifie que le coifficient de corr 'r' et proche de 1.

pour assumer ce qu'ona dit avant on peut afficher la matrice de corr de notre base d'apprentissage 

```python 
sns.heatmap(data.corr(), annot=True, fmt='.2f', cmap='Reds')
```

![[Pasted image 20250601231643.png]]

---
#### Etape 3 : creation de model de regression lineare simple

| instensiation du model de regression lineaire.

```python
lr = linear_model.LineareRegression()
```

| segmentation des donnees on des donnees de test et des donnnes d'apprentissage.

```python
# isoler les features et les outcomes
outcomes = data['y']
features = data.drop(columns=['y'])
# diviser les donner on des donnees d'apprentissage et de test 
x_train, x_test, y_train, y_test = model_selection.train_test_split(features, outcomes, test_size=.3, random_state=12)
```

```python
lr.fit(x_train, y_train)
```

![[Pasted image 20250601234419.png]]

---
#### Etape 4 : verification et evaluation de model 

| maintenent onva predire les donnees de y et par la suite comparer notre donnees predit avec les donnees reel.

```python 
pred_train = lr.predict(x_train)
```

| <font color="#ee4545">Avant :</font> on va construire l'equation de la droite et comparer par la suite les deux resultat 

```python
ponte = lr.coef_
intercept = lr.intercept_

print(f'ponte a = {ponte}')
print(f'intercept y = {intercept}')
```

![[Pasted image 20250601235045.png]]

| danc l'equation de la droite va secrit sous la forme : 

$$
Y = 1.16080168.x - 3.55699910384382
$$

| petit comparaison entre le resultat via cette fonction et on utilisent la fonction predict

```python
# comparaison
exem_x = 12.2321 
y_1 = ponte*exem_x + intercept
y_2 = lr.predict([[exem_x]])

print(y_1)
print(y_2)
```

![[Pasted image 20250602000140.png]]

on observe qu'onna obtenue les meme resultat on utilisent les deux methode ce qui fait les resultat conforme avec la vrais fonction de droite de regression lineaire.

##### Phase d'evaluation de model 

| pour les algorithme de regression on utilisent on generale les metriques suivant 

<font color="#affc41">1. coefficient de détermination  : </font>

- Le $R^2$ generalement mesure, **la qualité de la prédiction d’un modèle de régression**, on comparent les valeurs predit avec les vrais valeur
- plus que la valeur et proche de 1 plus que le model et tres performent.
- formule de calcule de cette metrique et : 
$$
R^2 = 1- \frac{\frac{1}{N}.\sum(Y_{i} - Y_{predit})^2}{\frac{1}{N}.\sum(Y_{i} - \bar{Y})^2}
$$

```python
predicted_y = lr.predict(x_train)
```

```python
r2 = metrics.r2_score(y_test, predicted_y)
```

![[Pasted image 20250602002509.png]]

| Le $R^2$ score pour les donnees d'entrainement et pour les donnees de tests sont proche. Ce qui signifie qu'il n'y a pas d'overfittting.

---

>[!warning] C'est quoi le ~~overfitting~~ ? 
> Le sur-ajustement se produit lorsque notre modèle capture le bruit (ou les fluctuations aléatoires) en plus de la tendance sous-jacente des données. Ces modèles ont généralement un faible biais et une variance élevée.

>[!warning] C'est quoi le ~~underfitting~~ ? 
> En apprentissage supervisé, le sous-ajustement se produit lorsqu'un modèle n'est pas capable de capturer la tendance sous-jacente des données. Ces modèles ont généralement un biais élevé et une faible variance.

--- 
#### Etape 5 : visualisation de modele avec le nuage de point

```python
plt.xlabel('x')
plt.ylabel('y')
plt.scatter(data['x'], data['y'], marker='+', color='red')
plt.plot(data['x'], lr.predict(data[['x']]))
```

![[Pasted image 20250602003545.png]]