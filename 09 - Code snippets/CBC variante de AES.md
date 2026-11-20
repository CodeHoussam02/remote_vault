
### Cryptography en utilisent la variante ( CBC ) de AES : 

##### Etape 1 : Generer une cle AES et le vecteur d'initialisation 

```python
def generate_cle_et_VI() -> tuple :
    key = get_random_bytes(16) # cle AES de 128 bits 
    IV = get_random_bytes(16) # vecteur d'initialisation de 128 bits
    return key, IV
```

##### Etape 2 : Creation d'un fichier text claire 

```python
def create_plain_file(nom_fichier, contenu):
    with open(nom_fichier, 'w') as f:
        f.write(contenu)
    print(f"Le fichier {nom_fichier} a été créé avec succès")
```

##### Etape 3 : Chiffrer un fichier

```python
def chiffrer_fichier(nom_fichier, key, IV):
    with open(nom_fichier, 'r') as f:
        data = f.read()

    cipher = AES.new(key, AES.MODE_CBC, IV)
    data = pad(data.encode(), 16)
    ciphertext = cipher.encrypt(data)
    
    with open(nom_fichier, 'wb') as f:
        f.write(ciphertext)
    
    print(f"Le fichier {nom_fichier} a été chiffré avec succès")
```

###### Etape 4 : 

```python
```