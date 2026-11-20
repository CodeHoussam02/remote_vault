---
tags:
  - coure
  - Securite
  - Securite-informatique
date: 13-02-2025
professor: Pr. Hamime
cssclasses:
---

# Introduction 


----
## _Chapitre 1 :_ 


###### Teminilogie des cle : 

- Chifrement asymetrique :
	- Definition : 
		- chiffreur : 
		- Cle de chiffrement : c'est un cle utiliser pour 
		- plain text : text avant de passer par le processus de chiffrement 
		- chiffrement : 
		- cyphered text : c'est le text chifferer 
		- dechiffrement : c'est le processus de reviendrer a l'etat initial du text avant de 
- cjcj

---

- Chiffrement symetrique Vs Chiffrement asymetrique : 



	- chiffrement symetrique ( reversive ) : sont des processus de chiffrement des donnees en utilisent un algorithme de chiffrement applee <font color="#affc41">Algorithme symetrique</font>
		- Exemple ( des algorithmes de chiffrement symetrique ) : 
			- chiffrement par decalage des alphabet, L'algorithme apple : (algorithme de decalage des lettre) et le cle c'est le nembre de decalge des lettre dans notre cas c'est <font color="#affc41">3</font>
			- <font color="#affc41">Le chiffrement XOR</font> c'est la meme que et logique il se base sur l'opperation xor ou exclusive entre le cle et le plain text pour les chiffrer, xor et appliquer sur chque octet de text et chaque octet sera , c'est la cle et 
				- Exemple XOR :
					- [TASK 1](obsidian://open?vault=remote%20vault&file=02%20-%20Diagrams%2F03%20-%20Securite%20des%20donnees%2FDrawing%202025-02-20%2014.01.46.excalidraw) 
			- <font color="#affc41">Le chiffrement AES</font> : il mellange les donnees 
			- <font color="#affc41">Les etapes de processus de chiffrement :</font>
				- etape 1 : le cle initiale ou original ( ou exclusive pour generer un matrice de 16 bit ( 4 * 4 ))
				- transformation liniere et non linere ( polynomiale ).
				- key schedualing c'est un process pour la generation des sous-cle.
			- Exemple d'application de L'algorithme AES : 
				- comminucation securise ( HTTPS )
				- chiffrement des disque ( gitlocker )
				- chiffrement des base de donnees
				- payement electronique 
				- stockage dans le cloud
				- reseau virtuel ( openvpn )
				- tele communication 
			- le role du vecteur d'initialisation en CBC : 
			- padding en deepLearning 
			- TP python pour simuler le processus de chiffrement AES ( CBC cypher block chaining )
			- Algorithme de chiffremnet ( chacha ) : pour les machine faible 
			- Algorithme de chiffrement ( bluefish )
		
	- bite = octet 



	- chiffrement asymetrique : 
		- cle public : "pour decripter les message"
		- cle public : "pour cripter les messwge ce cle et asseccible par tout le monde".
		- le destinataire qui doit generer le cle pour qu'il soit capable de decripter les message sans aucun probleme 
		- Exemple : 
			- L'algorithme de chiffrement RSA 
				- Gestion des deux NE et NG en se basent sur les nembre premier.
	- 
	

- chiffremnet symetrique ( syncrone ) 
	- AES : 
		- Ce c'est le caractere majeur melange de donnees 
- chiffrement asymetrrique ( asyncrone ) :
	- RSA : 
		- insiste sur la generation des cles.


<div style="display: flex; justify-content: space-between; align-items: top;">
  <div>
	  <font color="#affc41">Chiffrement symetrique</font>
	  <div>
		  sont des processus de chiffrement des donnees en utilisent un algorithme de chiffrement applee <font color="#affc41">Algorithme symetrique</font>
	 </div>
	 <h6 style="text-decoration: underline;">Exemple :</h6>
	 <div>
		 <p>
			 chiffrement par decalage des alphabet, L'algorithme apple : (algorithme de decalage des lettre) et le cle c'est le nembre de decalge des lettre dans notre cas c'est <font color="#affc41">3</font>
		 </p>
		 <p>
			 <font color="#affc41">Le chiffrement XOR</font> c'est la meme que et logique il se base sur l'opperation xor ou exclusive entre le cle et le plain text pour les chiffrer, xor et appliquer sur chque octet de text et chaque octet sera , c'est la cle et 
		 </p>
		 <p><font color="#affc41">Exemple XOR :</font></p>
		 <a>[TASK 1](obsidian://open?vault=remote%20vault&file=02%20-%20Diagrams%2F03%20-%20Securite%20des%20donnees%2FDrawing%202025-02-20%2014.01.46.excalidraw)</a>
	 </div>
  </div>
  <div>
	  <font color="#affc41">Chiffrement symetrique</font>
	  <div>
		  sont des processus de chiffrement des donnees en utilisent un algorithme de chiffrement applee <font color="#affc41">Algorithme symetrique</font>
	 </div>
	 <div>
		<font color="#affc41`">cle public : </font>"pour decripter les message"
		<font color="#affc41`">cle public : </font>"pour cripter les messwge ce cle et asseccible par tout le monde".
	 </div>
  </div>
  <div>
	  <font color="#affc41">Chiffrement symetrique</font>
	  <div>
		  sont des processus de chiffrement des donnees en utilisent un algorithme de chiffrement applee <font color="#affc41">Algorithme symetrique</font>
	 </div>
  </div>
</div>

---

### 02. L'algorithme RSA comment il fonctionne ?

1. choisir d'une maniere aleatoir deux nembre premiers tres grand p et q
2. calculer n = p*q
3. calculer g(n) = (p-1)(q-1)
4. PGCD(e, q(n)) = 1
5. dxe 
6. ckck
7. C = M pow (e)
8. M = c pow (d)

###### 01. TP 1 : implementation de RSA + AES en python :

- Le tp consiste a :
	- Generer une paire de 


---

### Chapitre 2 : Principe de securite des donnees :

#### 01. Fonction de hashage : 

- Si les algorithmes de chiffrement transforment les donnees lisibles en donnees chiffrees reversibles grace a une cle
- un algorithme de hashage, en revenche et une fonction mathematique a sens unique, rendent impossible la recuperation des donnees d'origine ( il prend une donnes en entre et produit hash ) 

#### 02. Critere de conception :

- la fonction de hashage doit 
	- reduire la taille des entrees a n bits (compression)
	- etre facile a calculer 
drawing

- utilisation du hashages 
	- Stockage des mots de passe :
	- Verification de l'integrite des fichiers :
	- Signature numerique et certificat :
	- Blockchain : bitcoin utilisent ( SHA-256 )
- Exemple d'algorithme de hashage 
	- MDS (Message digest algorithme 5)
	- SHA-1 
	- SHA-256 ( Secure Hash Algorithme 256 bits ) :
	- Argon2 
	- Blake2 

#### 03. Connection HTTPS Securise avec RSA + AES + SHA-256

1. Le client se connecte au serveur en utilisent https
2. le client demande au serveur son certificat SSL/TLS
3. Apre generation de pub/priv RSA, le serveur envoie son certificat au client qui contient : 
	- Le cle publique du serveur RSA.
	- Le nom du domaine 
	- La signature de l'authorite de certification (CA) qui contient un hashage du certificat ( chiffrees avec SHA-256 ), qui est ensuite chiffree avec la cle privee de la CA
	
> [!error]+ NB 
> - A ce moment-la, SHA-256 intervient dans la signature du certif, mais ce n'est pas directement utilise pour chiffree les donnees pendant la communication 

4. Le client verifie le certificat SSL/TLS 
5. Le client verifie la signature du certificat a l'aide de la cle pub de 


- Le mecanisme utilise par CA est bien 
	- table
- pourqoui ce ressemble a RSA ?

 ![[Drawing 2025-03-06 12.47.03.excalidraw|800]]
- Principe de hashage par blocs 
	- Un fichier peut etre tres grand ( plusieur Go ). au lieu de tout charger en memoire d'un coup 

###### 01. TP pratique pour implimenter RSA + AES + SHA-256 en python :

- ... 