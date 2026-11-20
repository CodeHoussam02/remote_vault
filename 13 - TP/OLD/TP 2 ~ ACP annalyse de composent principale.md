

#### L'objectif : 

l'objectif de cette travail et de mieux comprendre le role de l'acp dans le domaine l'intelligence artificielle car par cette technique on peut reduire d'une maniere mathematique le nembre de colonnes ou bien la dimmention de notre base d'apprentissage pour mieux faciliter la representation dans un repere on guardent la dispertion entre les point et a condition que y'a une forte correlation entre les points.

---

#### Etape 1 : importation des modules & base d'apprentissage 

```python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns 
from sklearn import decomposition
from sklearn import metrics
from sklearn import model_selection
from sklearn import preprocessing # pour code les valeur non numerique
from sklearn import decomposition

# importation des donnees 
df = pd.read_excel('./autos_acp_pour_python.xlsx')
df
```

![[Pasted image 20250603184639.png]]

##### Analyse simple de notre jeux de donnees :

```python
df.shape
```

![[Pasted image 20250603184754.png]]

Notre base d'apprentissage contient 18 lignes avec 7 colonnes pour chaque ligne.

```python
df.info()
```

![[Pasted image 20250603184904.png]]

La majorité des colonnes du tableau contient des valeurs numériques, à l’exception de la colonne <font color="#affc41">Modele</font>, qui est une chaîne de caractères représentant la marque de chaque voiture.

On remarque également qu’il n’y a aucune valeur manquante dans les données. Cependant, les variables n'étant pas toutes sur la même échelle, il est nécessaire de les standardiser avant d’appliquer l’Analyse en Composantes Principales (ACP).

Pour cette raison, nous allons adopter l’approche d’une **ACP normée**, qui repose sur les données centrées et réduites.

###### Encodage de la colonne Modele : 

```python 
# on doit encoder tout d'abord les valeur non numerique 
le = preprocessing.LabelEncoder()
df['Modele_encoded'] = le.fit_transform(df['Modele'])
df
```

![[Pasted image 20250603185629.png]]

Maintenent on doit standardiser les donner sur les colonnees <font color="#256EFF">"CYL", "PUISS", "LONG", "LARG", "POIDS", "V_MAX"</font>

le code python pour standariser les donnees et : 

```python
# on doit standariser les donnees pour les metre dans le meme echelle 
sc = preprocessing.StandardScaler()
colonnes_numeriques = ['CYL', 'PUISS', 'LONG', 'LARG', 'POIDS', 'V_MAX']
df_standariser = pd.DataFrame(sc.fit_transform(df[colonnes_numeriques]), columns=colonnes_numeriques)
df_standariser
```

![[Pasted image 20250603191956.png]]

###### Est ce que c'est possible d'abord d'appliquer l'acp dans ce cas ?

pour savoir est ce qu'il est possible d'appliquer l'acp on doit visualiser la correlation entre les variable s'il y'a une fortes correlation entre les variable sa veut dire que l'acp et applicable.

```python
sns.heatmap(df_standariser.corr(), annot=True ,fmt='.2f', cmap='Reds')
```

![[Pasted image 20250603192302.png]]

commme vous voyez ici ona une fortes corr entre <font color="#ee4545">"PUISS" ~ "V_MAX"</font>, <font color="#ee4545">"LONG" ~ "LARG"</font> aussi entre <font color="#ee4545">"POIDS" ~ "CYL"</font> etc ... 
danc on peut appliquer l'acp dans ce cas la.

#### Etape 3 : initialisation de l'algorithme ACP 

```python
# appliquant maintenent l'acp pour reduire la dimention de notre jeux de donnes
acp = decomposition.PCA()

# application de l'acp no-norme sur 
coord = acp.fit_transform(df_standariser)

# afficher le nemnbre de composent 
print(f'Nembre de composent : {acp.n_components_}')
```

![[Pasted image 20250603200002.png]]

##### 3.1 ~ Analyse de la variance expliquer pour chaque cp 

dans cette phase on cherche a garder que les composents principale qui ont ou bien qui garde le maximum d'information et on supprime les autres.

```python
# afficher les variances expliquer 
print(f'Variance expliquer : {acp.explained_variance_}')

# barplot des variances expliquer 
list_cp = ['CP1', 'CP2', 'CP3', 'CP4', 'CP5', 'CP6']
df_acp  = pd.DataFrame(list_cp, columns=['ACP'])
df_acp["variance_explique"] = acp.explained_variance_

# affichage de notre barplot 
plt.figure(figsize=(6, 4))
sns.barplot(x="ACP", y="variance_explique", data=df_acp, color='r')
plt.title('la variance expliquee par chaque composent principale')
plt.show()
```

>[!example] variance explique pour chaque cp :
> [4.68090853 0.90641889 0.39501114 0.22650574 0.09826011 0.04583676]

![[Pasted image 20250603200506.png]]

alors on observe que le <font color="#256EFF">"CP1", "CP2", "CP3"</font> guarde la plus part de l'information mais pour assumer on doit tracer la courbe de la Variance expliquée cumulée

##### 3.2 ~ Variance expliquée cumulée

```python
# variance expliquee cumulee 
plt.plot(list_cp, np.cumsum(acp.explained_variance_ratio_))
plt.title('Variance explique pour chaque cp')
plt.xlabel('Composent principale')
plt.ylabel('variance cumule')
plt.show()
```

![[Pasted image 20250603202557.png]]

on observe dans ce graphe que les 4 composent principale "CP1", "CP2", "CP3" gurde "0.90" de l'information initiale

##### 3.3 ~ creation d'un dataframe avec les 3 premier composent principale

```python
pca_df_3 = pd.DataFrame({
    "Dim1": coord[:, 0], 
    "Dim2": coord[:, 1], 
    "Dim3": coord[:, 2]
})

pca_df_3
```

![[Pasted image 20250603202924.png]]

##### 3.4 ~ Cercle de correlation 

```python
# circle de coorelation 
pcs = acp.components_
n_features = df_standariser.shape[1]

plt.figure(figsize=(8,8))
for i in range(n_features):
    plt.arrow(0, 0, 
        pcs[0, i], pcs[1, i], 
        head_width=0.03, head_length=0.03, fc='r', ec='r')
    plt.text(pcs[0, i]*1.1, pcs[1, i]*1.1, df_standariser.columns[i], color='g', ha='center', va='center')
```

![[Pasted image 20250603203016.png]]

##### 3-5 ~ Visualisation des données dans un repère orthonormé 2D et 3D 

```python
fig, axes = plt.subplots(figsize=(8, 8))
axes.set_xlim(-6, 6)
axes.set_ylim(-6, 6)

# Placement des étiquettes
for i in range(len(coord)):
    axes.annotate(df_standariser.index[i], (coord[i, 0], coord[i, 1]))

# Ajout des axes
axes.axhline(0, color='silver')
axes.axvline(0, color='silver')

# Titre et affichage
axes.set_title('Projection des individus dans un plan à 2 dimensions')
plt.show()
```

![[Pasted image 20250603204609.png]]

```python
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')

# Coordonnées des 3 premières composantes
x = coord[:, 0]
y = coord[:, 1]
z = coord[:, 2]

# Scatter des points
ax.scatter(x, y, z, color='skyblue')

# Ajouter les étiquettes (noms des voitures)
for i in range(len(coord)):
    ax.text(x[i], y[i], z[i], df_standariser.index[i], fontsize=8)

# Titres des axes
ax.set_xlabel('PC1')
ax.set_ylabel('PC2')
ax.set_zlabel('PC3')
ax.set_title('Projection des individus dans l’espace à 3 dimensions')

plt.show()
```

![[Pasted image 20250603212534.png]]