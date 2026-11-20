### Exercice 1 :

![[Pasted image 20240809095306.png]]

###### Solution : 

```c
#include <stdio.h>

int age_calculator(int year){
    int age;
    age = 2024 - year ;
    return age;
}

int main () {
    int birth;
    printf("Enter your birth year : ");
    scanf("%d", &birth);
    printf("You are : %d\n", age_calculator(birth));
    return 0;
}
```

## Exercice 2 : 

![[Pasted image 20240809102143.png]]


```c
#include <stdio.h>

float longeur, largeur;

float surface() {
    float s;
    s = longeur * largeur;
    return s;
}

float perimetre() {
    float p;
    p = 2 * (longeur + largeur);
    return p;
}

int main() {
    printf("Saisir la longeur [cm]: ");
    scanf("%f", &longeur);
    printf("Saisir la largeur [cm]: ");
    scanf("%f", &largeur);
    printf("La surface de rectangle et : %.2f cm\n", surface(longeur, largeur));
    printf("Le perimetre du rectangle et : %.2f cm\n", perimetre(longeur, largeur));
}
```


### Exercice 3 :

![[Pasted image 20240809104623.png]]


```c
#include <stdio.h>
#include <math.h>

int x, y;

int power() {
    return pow(x, y);
}

int main() {
    printf("Saisir x : ");
    scanf("%d", &x);
    printf("Saisir y : ");
    scanf("%d", &y);
    printf("%d\n", power());
    return 0;
}
```

### Exercice 4 : 

![[Pasted image 20240809112500.png]]

_Remarque : <font color="#f00">Toujour ajouter un espace avant le specificateur de format dans le cas d'un charactere : </font> `%c`

```c 
#include <stdio.h>

int x, y;
char operation;

int addition() {
    return x + y;
}

int subtraction() {
    return x - y;
}

int multiplication() {
    return x * y;
}

int division() {
    if (y == 0) {
        printf("Zero devision error");
        return 0;
    } else {
        return x / y;
    }
}

int main() {
    printf("Saisir x : ");
    scanf("%d", &x);
    printf("Saisir y : ");
    scanf("%d", &y);
    printf("Saisir l'operation : ");
    scanf(" %c", &operation);
    //
    if (operation == '+') printf("La somme : %d\n", addition());
    else if (operation == '-') printf("La sustraction : %d\n", subtraction());
    else if (operation == '*') printf("La multiplication : %d\n", multiplication());
    else if (operation == '/') printf("La division : %d\n", division());
    else printf("Unvalid operation\n");
    return 0;
}
```


### Exercice 5 :


![[Pasted image 20240810214554.png]]

##### Solution : 

```c
#include <stdio.h>

int main () {
    float note [5];
    float somme;
    // recuperer les notes;
    for (int i = 0; i < 5; i++) {
        printf("Inserer la note N%d : ", i+1);
        scanf("%f", &note[i]);
    }
    // afficher la somme des notes
    somme = 0;
    for (int i = 0; i < 5; i++) {
        somme += note[i];
    }
    printf("La moyenne et : %.2f\n", somme / 5);
}
```


## Exercice 6: 

![[Pasted image 20240811080559.png]]


#### Solution 

```c
#include <stdio.h>
#include <math.h> 


int main() {
    float rayon, volume;
    const float PI = 3.14;

    // recuperer la valeur du rayon 
    printf("Saisir le rayon [cm] : ");
    scanf("%f", &rayon);

    // valume = 4*pi*r**3 / 4
    volume = (4*PI*pow(rayon, 3)) / 3;
    printf("Le volume de sphere et : %.2f cm\n", volume);

    return 0;
}
```



## Exercice 7:

![[Pasted image 20240811082746.png]]


#### Solution 

```c
#include <stdio.h>

int main() {
    int a, b, c;

    // recuperer la valeur des deux entier 
    printf("La valeur de a : ");
    scanf("%d", &a);
    printf("La valeur de b : ");
    scanf("%d", &b);
    // avant swapping 
    printf("Avant la valeur de a : %d et b : %d\n", a, b);
    // swapping 
    c = a;
    a = b; 
    b = c;
    // afficher le deux variable 
    printf("Apres La valeur de a : %d et b : %d\n", a, b);
    return 0;
}
```


## Exercice 8:

![[Pasted image 20240811083432.png]]


#### Solution


```c
#include <stdio.h>

int main() {
    int a, b;

    // recuperer la valeur des deux entier 
    printf("La valeur de a : ");
    scanf("%d", &a);
    printf("La valeur de b : ");
    scanf("%d", &b);
    // avant swapping 
    printf("Avant la valeur de a : %d et b : %d\n", a, b);
    // swapping 
    a += b;
    b = a - b;
    a = a - b;
    // afficher le deux variable 
    printf("Apres La valeur de a : %d et b : %d\n", a, b);
    return 0;
}
```


## Exercice 9 :

![[Pasted image 20240811084245.png]]


#### Solution 

```c
#include <stdio.h>

int main() {
    int temp;
    double heure, minute, second;
    // recuperer la valeur des deux entier 
    printf("Saisir le temp en second : ");
    scanf("%d", &temp);
    /*
        s -> h ==> ...s / 3600
        s -> m ==> (...s / 3600) / 60
    */
    heure = temp / 3600;
    minute = (temp % 3600) / 60;
    second = (temp % 3600) % 60;
    // afficher le deux variable 
    printf("La conversion de %ds et %.0fh:%.0fm:%0.fs\n", temp, heure, minute, second);
    return 0;
}
```


## Exercice 10 

![[Pasted image 20240811101542.png]]

```c
#include <stdio.h>
#include <math.h>

int main() {
    float x1, y1, x2, y2, distance;
    // recuperer les cordonnes
    printf("Saisir la valeur de x1 : ");
    scanf("%f", &x1);
    printf("Saisir la valeur de y1 : ");
    scanf("%f", &y1);
    printf("Saisir la valeur de x2 : ");
    scanf("%f", &x2);
    printf("Saisir la valeur de y2 : ");
    scanf("%f", &y2);
    // distance = sqrt(pow((x2 - x1), 2) + pow((y2 - y1), 2))
    distance = sqrt(pow((x2 - x1), 2) + pow((y2 - y1), 2));
    printf("La distance entre les deux point a et b c'est : %.2f\n", distance);
}
```


## Exercice 11 : 





### Solution 

```c 
#include <stdio.h>

int main() {
    int R1, R2, R3;
    float ser, para;
    printf("Saisir la valeur de R1 : ");
    scanf("%d", &R1);
    printf("Saisir la valeur de R2 : ");
    scanf("%d", &R2);
    printf("Saisir la valeur de R3 : ");
    scanf("%d", &R3);
    //
    ser = R1 + R2 + R3; 
    para = ( R1 * R2 * R3 ) / ((R1 * R2) + (R1 * R3) + (R2 * R3));
    printf("En series : %.2f\n", ser);
    printf("En parallele : %.2f\n", para);

    return 0;
}
```


#### Exercice 12 

![[Pasted image 20240812101224.png]]

#### solution 

```c
#include <stdio.h>

int main() {
    int num1, num2;
    printf("Saisir le nembre 1 : ");
    scanf("%d", &num1);
    printf("Saisir le nembre 2 : ");
    scanf("%d", &num2);
    // condition 
    if (num1 * num2 > 0) printf("Les deux nembre a y'ont meme sign\n");
    else printf("Les deux nembre a y'ont une signe differente\n");

    return 0;
}
```


## Exercice 13 

![[Pasted image 20240812101917.png]]


```c 
#include <stdio.h>

int main() {
    int num1, num2, c, d;
    printf("Saisir le nembre 1 : ");
    scanf("%d", &num1);
    printf("Saisir le nembre 2 : ");
    scanf("%d", &num2);
    
    if (num1 * num2 > 0) {
        num1 += num2;
        num2 = num1 - num2;
        num1 = num1 - num2;
    } else {
        c = num1 + num2;
        d = num2 * num1;
        num1 = c;
        num2 = d;
    }
    printf("Numero 1 : %d\n", num1);
    printf("Numero 2 : %d\n", num2);
    return 0;
}
```


## Exercice 14

![[Pasted image 20240812102513.png]]


### Solution 

```c
#include <stdio.h>

int main() {
    int amount;
    float chargingPrice;
    printf("Veuillez saisir le nembre de photocopy : ");
    scanf("%d", &amount);
    
    if (amount <= 10) chargingPrice = amount * 0.30;
    else if (amount > 10 && amount <= 30 ) chargingPrice = (10 * 0.30) + ((amount - 10) * 0.25);
    else if ( amount > 30) chargingPrice = (10 * 0.30) + (20 * 0.25) + ((amount - 30) * 0.20);

    printf("Price is : %.2f Euro\n", chargingPrice);

	return 0;
}
```


## Exericice 15

![[Pasted image 20240813104339.png]]

#### Solution 

```c
#include <stdio.h> 

int main() {
    int age;
    printf("Veuillez saisir l'age : ");
    scanf("%d", &age);
    if (age >= 6 && age <= 7) printf("Poussin\n");
    else if (age >= 8 && age <= 9) printf("Pupille\n");
    else if (age >= 10 && age <= 11) printf("Minime\n");
    else if (age >= 12) printf("Cadet\n");
}
```


## Exercice 16

![[Pasted image 20240813104507.png]]


#### Solution 

```c
#include <stdio.h> 

int main() {
    float note [3], somme, moyenne;
    for (int i = 0; i < 3; i++) {
        printf("Saisir la note N%d : ", i+1);
        scanf("%f", &note[i]);
        somme += note[i];
    }
    printf("La somme et : %.2f\n", somme);
    moyenne = somme / 3;
    printf("La moyenne et : %.2f\n", moyenne);
    if (moyenne < 10) printf("Insufisant\n");
    else if (moyenne >= 10 && moyenne < 12) printf("Passable\n");
    else if (moyenne >= 12 && moyenne < 14) printf("Assez bien\n");
    else if (moyenne >= 14 && moyenne < 16) printf("Bien\n");
    else if (moyenne >= 16 ) printf("Tres Bien\n");
    else if (moyenne > 20 || moyenne < 0) printf("Les donner sont fausse");
    return 0;
}
```


## Exercice 17 :

![[Pasted image 20240813114712.png]]

### Solution 

```c
#include <stdio.h> 
#include <math.h> 

int main() {
    int a, b, c, delta;
    printf("Veuillez saisir a, b et c : \n");
    scanf("%d%d%d", &a, &b, &c);
    // calcule delta
    delta = pow(b, 2) - 4 * ( a * c);
    printf("La valeur de Delta : %d\n", delta);
    if (delta == 0) {
        printf("Exist une seule solution : %d\n", -b / 2 * a );
    } else if (delta > 0) {
        printf("Il exist deux solution dans R\n");
        printf("X1 : %.2f\n", (-b + sqrt(delta)) / (2 * a));
        printf("X1 : %.2f\n", (-b - sqrt(delta) )/ (2 * a));
    } else if (delta == 0) {
        printf("Solution vide");
    }

    return 0;
}
```


## Exercice 18

![[Pasted image 20240814131933.png]]

#### Solution 

```c
#include <stdio.h>
#include <stdbool.h>

int main() {
    int age;
    char sex;
    bool C1, C2;
    // get the age and the sex
    printf("Veuillez saisir votre age : ");
    scanf("%d", &age);
    printf("Saisir votre Sex [H/F] : ");
    scanf(" %c", &sex);
    // condition 
    C1 = age >= 20 && sex == 'H'
    C2 = age > 16 && age <= 35 && sex == 'F'
    if ( C1 || C2 ) printf("Imposable\n");
    else printf("Non imposable\n");
}
```


## Exercice 19:

![[Pasted image 20240814134438.png]]

##### Solution 

```c 
#include <stdio.h> 

int main() {
    float PHT, TTC;
    char  CAT;
    printf("Saisir le prix hors tax : ");
    scanf("%f", &PHT);
    printf("Saisir la categorie : ");
    scanf(" %c", &CAT);
    // condition
    // if (CAT == 'A') TTC = PHT + ( PHT * 0.07 );
    // else if (CAT == 'B') TTC = PHT + ( PHT * 0.20 );
    // else if (CAT == 'C') TTC = PHT + ( PHT * 0.30 );
    
    // switch case 
    switch (CAT) {
        case 'A' : TTC = PHT + ( PHT * 0.07 );
                break;
        case 'B' : TTC = PHT + ( PHT * 0.20 );
            break;
        case 'C' : TTC = PHT + ( PHT * 0.30 );
            break;
        default  : printf("Category n'existe pas");
            break;
    }
    
    printf("Le Prix Tous Tax Compris et : %.2f DH\n", TTC);

    return 0;
}
```


## Exercice 25

![[Pasted image 20240814140254.png]]

### Solution 

```c
#include <stdio.h>

int main() {
    int nembre, trigger;
    printf("Saisir un nembre : ");
    scanf("%d", &nembre);
    // utilisent while 
    trigger = 0;
    //
    while (trigger < 10) {
        nembre++;
        trigger++;
        printf("%d ", nembre);
    }
    // utilisent do while 
    do {
        nembre ++;
        trigger ++;
        printf("%d ", nembre);
    } while (trigger < 10);
}
```


## Exercice 26 : 

![[Pasted image 20240814141321.png]]

#### Solution 

```c
#include <stdio.h>

int main() {
    float somme = 0;
    int n;
    printf("Saisir la valeur de n : ");
    scanf("%d", &n);
    for (float i = 1; i <= n; i ++) {
        somme = somme + 1/i;
    }
    printf("La somme et : %.2f\n", somme);
}
```



## Exercice :


#### Solution

```c
#include <stdio.h>

int main() {
    int num, count = 0, rest;
    printf("saisir un nembre : ");
    scanf("%d", &num);
    for (int i = 0; i <= num; i++) {
        if (num != 0) {
            printf("%d\n", num / 10);
            num = num / 10;
            count ++;
        }
    }
    printf("Le nembre des entier dans ce nembre et : %d\n", ++count);
    return 0;
}
```

### Les pointeurs 

#### Exercice 1:

![[Pasted image 20240826094335.png]]
##### Solution 

```c
#include <stdio.h>

int main() {
    int T [100], n;
    int *p = T;
    printf("Veuillez saisir le nembre des elements : ");
    scanf("%d", &n);
    for (p = T; p < T+n; p++) {
        printf("Saisir la valeur de T[%ld] : ", p - T + 1);
        scanf("%d", p);
    }
    // afficher les element 
    for (p=T; p < T+n; p++) {
        printf("T[%ld] = %d\n", p-T+1, *p);
    }
    return 0;
}
```


#### Exercice 2 :

![[Pasted image 20240826101132.png]]
##### Solution

```c
#include <stdio.h>

int main() {
    int T [100], n;
    int *P1 = T, *P2, X;
    // la taille du tableau
    printf("Saisir la taille du tableau : ");
    scanf("%d", &n);
    // lire l'entier x de l'utilisateur
    printf("Saisir la valeur de x : ");
    scanf("%d", &X);
    printf("----------------\n");
    // remplir le tableau
    for (P1=T; P1 < T+n; P1++) {
        printf("Saisir la valeur de T[%ld] : ", P1-T+1);
        scanf("%d", P1);
    }
    // eliminer les occurence
    P2 = T; 
    for (P1=T; P1 < T+n; P1++) {
        *P2 = *P1;
        if (*P2 != X) {
            P2 ++;
        }
    }
    // changer la taille de n pour afficher seulement les element sans les autres
    n = P2 - T;
    for (P1 = T; P1 < T+n; P1++) {
        printf("T[%ld] = %d\n", P1-T+1, *P1);
    }
}
```


#### Exercice 3:

![[Pasted image 20240826123147.png]]

##### Solution 

```c
#include <stdio.h>

int main() {
    int T[100], TMP, taille;
    int *P1 = T, *P2;
    // la taille du tableau
    printf("Saisir la taille du tableau : ");
    scanf("%d", &taille);
    // recuperer les valeur du tableau T
    for (P1=T; P1<T+taille;P1++) {
        printf("Saisir la valeur de T[%ld] : ", P1-T+1);
        scanf("%d", P1);
    }
    // swapping
    P2 = T;
    for (P1=T; P1<T+taille;P1++) {
        ++ P2;
        TMP = *P1;
        *P1 = *P2;
        *P2 = TMP;
        printf("TMP : %d | P1 : %d | P2 : %d\n", TMP, *P1, *P2);
        printf("---------\n");
    }
    // method 2 
    // for (P1=T, P2=T+taille-1; P1<P2;P1++, P2--) {
    //     TMP = *P1;
    //     *P1 = *P2;
    //     *P2 = TMP;
    //     printf("TMP : %d | P1 : %d | P2 : %d\n", TMP, *P1, *P2);
    //     printf("---------\n");
    // }
    //
    for (P1 = T; P1 < T+taille; P1++) {
        printf("T[%ld] = %d\n", P1-T+1, *P1);
    }
    return 0;   
}

```


#### Exericice 4:

![[Pasted image 20240826123327.png]]

```c
#include <stdio.h>

int main() {
    int A[100], B[100], N, M;
    int *PA, *PB;
    // saisir la dimention des deux 
    printf("Saisir le dimention de A : ");
    scanf("%d", &N);
    printf("Saisir la dimention de B : ");
    scanf("%d", &M);
    // remplir les deux tableau
    for (int i = 0; i < N; i++) {
        printf("Saisir l'element A[%d] : ", i+1);
        scanf("%d", A+i);
    }
    printf("----------\n");
    for (int i = 0; i < M; i++) {
        printf("Saisir l'element B[%d] : ", i+1);
        scanf("%d", B+i);
    }
    //
    for (PA = A+N, PB = B; PB < B + M; PB++, PA++){
        *PA = *PB;
    }
    // afficher 
    for (PA = A; PA < A + ( M + N); PA++) {
        printf("A[%ld] = %d\n", PA - A + 1, *PA);
    }

    return 0;
}
```


### Exercice 4:

![[Pasted image 20240827065316.png]]

##### Solution 

-> Ordre croissant

```c
#include <stdio.h>

int main() {
    int T[100], N;
    int *P1, *P2, TMP;

    // Saisir la dimension de notre tableau
    printf("Saisir la dimension de T : ");
    scanf("%d", &N);

    // Remplir le tableau
    for (P1 = T; P1 < T + N; P1++) {
        printf("Saisir T[%ld] : ", P1 - T + 1);
        scanf("%d", P1);
    }

    // Tri du tableau
    for (P1 = T; P1 < T + N - 1; P1++) {  // Loop until the second last element
        for (P2 = P1 + 1; P2 < T + N; P2++) {  // Loop from the next element to the end
            if (*P1 > *P2) {
                TMP = *P1;
                *P1 = *P2;
                *P2 = TMP;
            }
        }
    }

    // Affichage du tableau trié
    for (P1 = T; P1 < T + N; P1++) {
        printf("T[%ld] = %d\n", P1 - T + 1, *P1);
    }

    return 0;
}
```

-> Ordre decroissant 

```c
#include <stdio.h>

int main() {
    int T[100], N;
    int *P1, *P2, TMP;

    // Saisir la dimension de notre tableau
    printf("Saisir la dimension de T : ");
    scanf("%d", &N);

    // Remplir le tableau
    for (P1 = T; P1 < T + N; P1++) {
        printf("Saisir T[%ld] : ", P1 - T + 1);
        scanf("%d", P1);
    }

    // Tri du tableau
    for (P1 = T; P1 < T + N - 1; P1++) {  // Loop until the second last element
        for (P2 = P1 + 1; P2 < T + N; P2++) {  // Loop from the next element to the end
            if (*P1 < *P2) {
                TMP = *P1;
                *P1 = *P2;
                *P2 = TMP;
            }
        }
    }

    // Affichage du tableau trié
    for (P1 = T; P1 < T + N; P1++) {
        printf("T[%ld] = %d\n", P1 - T + 1, *P1);
    }

    return 0;
}

```

## Les chaines de caractere 

### Exercice 1 : 

![[Pasted image 20240827074327.png]]
##### Solution 

```c
#include <stdio.h> 

int main() {
    char name[100];
    printf("Saisir votre nom : ");
    fgets(name, sizeof(name), stdin);
    printf("-> Nom : %s", name);
}
```


### Exercice 2 :

![[Pasted image 20240827074742.png]]
##### solution 

`Remarque` : plusieur string fonction sont pas supporter sur linux

```c
#include <stdio.h>
#include <string.h>

int main() {
    char nom1[100], nom2[100];
    int HAM = 0, *P1, *P2; 
    printf("Saisir nom1 : ");
    fgets(nom1, sizeof(nom1), stdin);
    printf("Saisir nom2 : ");
    fgets(nom2, sizeof(nom2), stdin);
    // comparer les deux mots
    if (strlen(nom1) != strlen(nom2)) {
        printf("Les deux mots non pas la meme taille !");
        return 0;
    } else {
        for (int i = 0; i < strlen(nom1); i++) {
            if (nom1[i] != nom2[i]) HAM ++;
        }
    }
    printf("La distance hamming : %d\n", HAM);
    return 0;
}
```





##### Solution : 

```c 
#include <stdio.h> 
#include <string.h>

int main() {
    char mot[100];
    int count = 0;
    printf("Saisir un mots : ");
    fgets(mot, sizeof(mot), stdin);
    // caluculer le nembre des caracters
    for (int i = 0; mot[i] != '\0'; i++) {
        count ++;
    }
    printf("Le nembre des characters : %d\n", count);
    printf("utilisent strlen : %ld\n", strlen(mot));
}

```


### Exercice 5 :

![[Pasted image 20240827092100.png]]

#### solution : 

```c 
#include <stdio.h> 
#include <string.h>

int main() {
    char mot[30];
    int freq[30];
    int count = 0, max;
    // recuperer le mot 
    printf("Saisir le mot : ");
    fgets(mot, sizeof(mot), stdin);
    for (int i = 0; i < 30; i++) {
        freq[i] = -1;
    }
    // looping 
    for (int i = 0; i < strlen(mot); i++) {
        count = 1;
        for (int j = i+1; j < strlen(mot); j++) {
            if (mot[i] == mot[j]) {
                count ++;
                freq[j] = 0;
            }
            if (freq[i] != 0) freq[i] = count;
        }
    }
    // recuperer la valeur max 
    for (int i = 0; i < strlen(mot); i++) {
        max = freq[0];
        if (freq[i] > max) max = freq[i];
    }
    printf("La valeur de repition et : %d\n", max);

    return 0;
}
```


### Exercice 6 : 

- programe qui retourn l'inverse d'une mot donne comme parametre 

##### Solution 

```c
#include <stdio.h>
#include <string.h>

int main() {
    char word[100], reversed[100];
    int len, ind = 0;
    // get the word from user 
    printf("Saisir un mot : ");
    fgets(word, sizeof(word), stdin);
    // comencer a reverser 
    len = strlen(word);
    for (int i = len - 1; i >= 0; i--) {
        printf("%c", word[i]);
    }
    printf("\n");
    return 0;
}


```


### Exercice 7 :

![[Pasted image 20240829090308.png]]

#### Solution 

```c
#include <stdio.h>
#include <string.h>

int main() {
    char word1[100];
    int valid = 1;
    // les deux mots 
    printf("Saisir le mot 1 : ");
    scanf("%s", word1);
    // comparer les deux mots 
    for (int i = 0, j = strlen(word1) - 1; i < strlen(word1); i++, j--) {
    if (word1[i] != word1[j]) {
        valid = 0;
        break; // If the strings do not match, we can break out of the loop early
    }
}
    if (valid) printf("Le mot %s et pallindrom\n", word1);
    else printf("Le mot %s et non pallindrom\n", word1);
}

```


### Exercice 7


#### Solution 

```c
#include <stdio.h>
#include <string.h>

int main() {
    char A[100], B[100];
    char *PA = A, *PB = B;

    // words 
    printf("Saisir la valeur de A : ");
    fgets(A, sizeof(A), stdin);
    printf("Saisir la valeur de B : ");
    fgets(B, sizeof(B), stdin);
    // remouve new line from both words 
    A[strcspn(A, "\n")] = 0;
    B[strcspn(B, "\n")] = 0;
    //
    for (PA = A + strlen(A), PB = B; *PB != '\0'; PA++, PB ++) {
        *PA = *PB;
    }
    printf("%s\n", A);
}
```


### Exercice 8 : 


#### solution

```c
#include <stdio.h>
#include <stdlib.h> 
#include <math.h>

int main() {
    float *vente = calloc(1, sizeof(float));
    float *revien = calloc(1, sizeof(float));
    float *resultat = calloc(1, sizeof(float));

    // les donne 
    printf("Saisir le prix de vente : ");
    scanf("%f", vente);
    printf("Saisir le prix de revien : ");
    scanf("%f", revien);

    free(vente);
    free(revien);

    // 
    resultat = *revien - *vente;
    if (resultat > 0) printf("Le benifis et de : %.2f $\n", fabs(resultat));
    else printf("La valeur de pert et : %.2f $\n", fabs(resultat));
}

```
\

### Exercice 9 

![[Pasted image 20240829104414.png]]


### solution 

```c
#include <stdio.h> 
#include <stdlib.h> 

int main() {
    int *N = malloc(sizeof(int));
    if (N == NULL) {
        printf("Memory allocation failed for N\n");
        free(N);
        exit(1);
    }
    int *somme = malloc(sizeof(int));
    if ( somme == NULL ) {
        printf("Memory allocation failed for somme\n");
        free(somme);
        exit(1);
    }
    // get n 
    printf("Saisir le nembre n : ");
    scanf("%d", N);

    *somme = 0;
    // perform our callculation 
    for (int i = 0; i <= *N; i++) {
        if ( i % 2 != 0 ) *somme += i;
        else continue;
    }

    printf("La somme des nembre de 1 a %d = %d\n", *N, *somme);

    // 
    free(N);
    free(somme);

    return 0;

}
```


### Exercice 10 : 

![[Pasted image 20240829124923.png]]

#### Solution

```c
#include <stdio.h> 
#include <stdlib.h>


int main() {
    int *nums = calloc(100, sizeof(int));
    int *N = malloc(1*sizeof(int));
    int *max = malloc(sizeof(int));

    // 
    if ( nums == NULL || N == NULL || max == NULL ) {
        printf("Memory allocation failed !");
        free(nums);
        free(N);
        free(max);
        exit(1);
    }


    // la taille du tableau 
    printf("Saisir le nembre des entier : ");
    scanf("%d", N);
    // remplir le tableau
    for (int i = 0; i < *N; i++) {
        printf("T[%d] = ",i+1);
        scanf("%d", &nums[i]);
    }
    *max = nums[0];
    for (int i = 0; i < *N; i++) {
        printf("%d ", nums[i]);
        if (*max < nums[i]) *max = nums[i];
        continue;
    }
    printf("\n");
    printf("Le nembre max : %d\n", *max);

    return 0;
}
```



### Exercice 11 : 

![[Pasted image 20240829132940.png]]


#### Solution 

```c
#include <stdio.h>
#include <stdlib.h> 

int main() {
    int *nums = NULL;
    int *N = malloc(sizeof(int));
    int *somme = malloc(sizeof(int));
    int *moyenne = malloc(sizeof(int));
    int *resp = malloc(sizeof(int));

    // check if memory alloc failed 
    if (N == NULL || somme == NULL || moyenne == NULL || resp == NULL) {
        printf("Memory allocation failed !");
        free(N);
        free(somme);
        free(moyenne);
        free(resp);
        exit(1);
    }

    do {
        // avoir la taille du tableau 
        printf("Saisir la taille du tableau : ");
        scanf("%d", N);

        nums = realloc(nums, (*N) * sizeof(int));

        // remplir le tableau
        for (int i = 0; i < *N; i++) {
            printf("T[%d] = ", i+1);
            scanf("%d", &nums[i]);
        }

        // afficher le tableau est la moyenne 
        *somme = 0;
        for (int i = 0; i < *N; i++) {
            printf("%d ", nums[i]);
            *somme += nums[i];
        }
        printf("\n");
        *moyenne = *somme / *N;
        printf("La moyenne et : %d\n", *moyenne);
        // check if user wants to quit or not 
        printf("1. Press one to rerun the program\n2. Press 0 to quit \n answer : ");
        scanf("%d", resp);

    } while (*resp);

    printf("Bon journee \n");
    free(nums);
    free(somme);
    free(moyenne);
    free(resp);

    return 0;
}
```


## Exercice 12 


#### Solution 

```c 
#include <stdio.h>
#include <stdlib.h>

void sort(int *T, int n) {
    int tmp;
    for (int i = 0; i < n, i++) {
        for (int j = i+1; j < n; j++) {
            if (*(T + i) < *( T + j)) {
                tmp = *( T + i);
                *(T + i) = *(T + j);
                *(T + j) = tmp;
            }
        }
    }
    printf("Tri croissant : ")
    for (int i = 0; i < n ; i++) {
        printf("%d ", *(T+i));
    }
}

void reverse(int *P1, int *P2) {

}


int main() {
    int *nums = NULL;
    int *N = calloc(1, sizeof(int));
    // int *P1 = nums, *P2 = nums;

    // 
    if (N == NULL ) {
        printf("Memory allocation was failed !");
        free(nums);
        free(N);
        exit(1);
    }

    // recuperer la taille du tableau;
    printf("Saisir la taille du tableau : ");
    scanf("%d", N);

    // allocat nums array
    nums = calloc((*N), sizeof(int));

    // remplir le tableau
    for (int i = 0; i <= *N - 1; i++) {
        printf("T[%d] = ", i+1);
        scanf("%d", &nums[i]);
    }

    // afficher le tableau avant 
    printf("Tableau : ");
    for (int i = 0; i <= *N - 1; i++) {
        printf("%d ", nums[i]);
    }
    printf("\n");

    sort(nums, N);

    // afficher le tableau trier 
    printf("ordre croissant : ");
    for (int i = 0; i <= *N - 1; i++) {
        printf("%d ", nums[i]);
    }
    printf("\n");
}
```