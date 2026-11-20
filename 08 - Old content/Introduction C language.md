
### When `C` language was invented ?

1. `C` language was invented in 1972 by : `Denis Ritchie`

### The advantages are ?

1. cross platform 
2. compiled : which means the source code is directly transcribed into machine code : `binary code`
3. fast 

### Environment setup :

1. IDE : integrated development environment --> we can use any ide we are confortable with

### Our first c application :

```c
#include <stdio.h>
#incluse <stdlib.h>

int main() {
	printf('Hello world');
	return 0;
}
```

### To compile your C code from terminal ?

1. first we need to install the `build-essetial` package
	1. after that all we need is to : ``

### Data types :

`chaine de character` : can hold many characters 
`charactere` : can hold one char only
`Reel`: this variable can hold floating numbers
`entier` : this variable can hold only non floating numbers 
`boolean` : this variable can hold only true or false 


### Variable & Constant structure :

1. always variables and constants are declared following this structure : 

```
				variable & constant 
				name -> type -> value
```


### Data types in depth : 

1. Int data type

| type            | min value       | max value     | octets num  |
| --------------- | --------------- | ------------- | ----------- |
| `int`           | - 32768         | 32767         | 2 \| 16 bit |
| `long`          | - 2_147_483_648 | 2_147_483_648 | 4 \| 32 bit |
| `unsigned int`  | 0               | 65535         | 2           |
| `unsigned long` | 0               | 4_294...      | 4           |

2. float data type :

| type          | min                | max              | octetcs |
| ------------- | ------------------ | ---------------- | ------- |
| `float`       | 3.4 * 10 ** -32    | 3.4 * 10 ** 32   | 4       |
| `double`      | 1.7 * 10 ** - 308  | 1.7 * 10 ** 308  | 8       |
| `long double` | 3.4 * 10 ** - 4932 | 3.4 * 10 ** 4932 | 10      |

3. character data type 

| type            | min v | max v | octets |
| --------------- | ----- | ----- | ------ |
| `char`          | -128  | 128   | 1      |
| `unsigned char` | 0     | 255   | 1      |

4. Boolean data type

| type   | value  | octets |
| ------ | ------ | ------ |
| `bool` | 0 or 1 | 1      |

#### Exercise 1 :

1. identify the type of each variable in the table below

| Data            | Type                    |
| --------------- | ----------------------- |
| `"d"`           | type : `char`           |
| `-300`          | type : `int` or `float` |
| `"8"`           | type : `char`           |
| `2506.5`        | type : `float`          |
| `6 * 10 ** 802` | type : `long double`    |
| `87`            | type : `int`            |
| `true`          | type : `bool`           |

### Variable declaration 

1. declare a constant :

```c
const type name = value;
const int birth_date = 2012;
```

2. declare a variable in c :

```c 
type name = value;
char sex = "H";
char y;
```

3. to use the boolean data type we need to import `<stdbool.h>` library

```c
#include <stdbool.h>

int main () {
	bool admis ;
	return 0;
}
```


#### Affecting in c language 

| instruction       | A   | B   | C   | D   |
| ----------------- | --- | --- | --- | --- |
| `B = 3;`          |     | 3   |     |     |
| `C = B + 10;`     |     | 3   | 13  |     |
| `A = 4;`          | 4   | 3   | 13  |     |
| `D = A;`          | 4   | 3   | 13  | 4   |
| `B = B * D;`      | 4   | 12  | 13  | 4   |
| `C = B + 5`       | 4   | 12  | 17  | 4   |
| `A = 10 + 4 + C;` | 25  | 12  | 17  | 4   |
| `C = A + B + D;`  | 25  | 12  | 36  | 4   |

### L'instruction d'ecriture printf():

1. the `printf()` statement is usually used to display a message or a variable to the user and it follow's this syntax : 


#### Format specifiers in C :

| format | meaning        |
| ------ | -------------- |
| `%d`   | digit          |
| `%ld`  | long digit     |
| `%s`   | string         |
| `%f`   | float          |
| `%c`   | char           |
| `%p`   | momory address |

```c
printf("text to display", var, const, expr, ...);
---- Exemple -----
printf("Maroc"); --> #Maroc
printf("A = %d", A); --> 1
printf("Les coordonnees sont : %f, %f", x, y)
----
float x, b;
x = 9;
b = 10.23;
```

##### Escape character in C language : 

 `%%` : pour afficher le pourcentage
 `\\` : pour afficher une antislash
 `\n` : retour a la ligne 
`\t`  : tabulation

#### How to control the number of digits after the comma :

```c 
float a, b;
a = 12.23;
b = 23.2323;
printf("a : %.1f , b : %.1f", a, b)
```


### L'instruction de lecture ce qui est saisit par l'user scanf() :

1. the `scanf()` statement is used to get an input form the user and store it in a variable

```c 
---- Syntax 
scanf("format_1", &var_1);

-------------------------------------
| format_1 | specificateur de format | 
| ---------| ------------------------|
| &        | adresse                 | 
|----------| ------------------------| 
| var_1    | le nom de variable      | 
| -----------------------------------|

---- Exemple 
scanf("%d", &x);
scanf("%d%d". &x, &y);
scanf("%d%d%d", &day, &month, &year)
```

#### problem with scanf() and variable of double data type 

```c 
--- Before ---
double a, b;
scanf("%f", &a);
scanf("%f", &b);
--> this code will always output 0.00 for a and b 
---> to fix that we have to perform the following 
--- After  ---
double a, b;
scanf("%lf", &a);
scamf("%lf", &b);
```

##### Exercice 3 : circle surface calcualtor 

```c
#include <stdio.h>
#include <stdbool.h>
int main() {
// calculer l'aire d'un cercle
const float PI = 3.14;
float rayon, aire;
//
printf("Veuiller saisir la valeur du rayon : ");
scanf("%f", &rayon);
aire = rayon * rayon * pi;
printf("L'aire du cercle et %.2f cm\n", aire);
return 0;
}
```

##### Exercice 4 : chiffre d'affaire calculator 

![]('/mnt/houssam/screenshots/structure.png')

La bibliotheque `<stdio.h>` contient les deux fonction `printf() et scanf()`

### Les commentaire en C :

1. single line comment 

```c 
// commentaire en un seule ligne
```

2. multiligne comment 

```c
/*
	plusieur line
*/
```


#### Arithmetic operations

| operation | info                                         |
| --------- | -------------------------------------------- |
| `+`       | addition                                     |
| `-`       | subtraction                                  |
| `*`       | multiplication                               |
| `/`       | division                                     |
| `++`      | pre increment : ++i  & post incriment : i++  |
| `--`      | pre decrement : --i  & post decrement : i -- |
| `%`       | modulous                                     |

2. in order to use the power we can use the library `<math.h>` which has the function `pow()`

```c
#include <math.h>

int main ()
{
	z = pow(1, 2)
	return 0;
}

---- Error ---
to solve the error that will occure when running this peace of code you should add this flag in the command to compile the code 
'-lm'
```

### Logical expressions

```c
And ---> &&
or  ---> ||
not ---> !
```



# Conditions in c language :

1. one condition 

```c 
#include <stdio.h>
int main() {
	float a, b, max;
	printf("Enter a : ");
	scanf("%f", &a);
	printf("Enter b : ");
	scanf("%f", &b);
	max = a;
	if (max < b) max = b;
	printf("Le max et : %.1f\n", max);
	return 0;
}
----
pay attention we dont write semi colon in the end of an if condition in c
```

1. two conditions 

```c
#include <stdio.h>
int main() {
	float a, b;
	printf("Saisir un entier : ");
	scanf("%f", &a);
	if (a > 0) printf("L'entier %.0f et positif\n", a);
	else printf("L'entier %.0f et negatif\n", a);
	return 0;
}
```

1. many conditions 
	1. if / else

```c
#include <stdio.h>

	int main() {
	float a, b;
	printf("Saisir un entier : ");
	scanf("%f", &a);
	if (a > 0) printf("L'entier %.0f et positif\n", a);
	else if (a == 0) printf("L'entier %.0f et null\n", a);
	else printf("L'entier %.0f et negatif\n", a)
	return 0;
}
```

2. switch statement in c

```c
#include <stdio.h>

int main() {
    int a;
    printf("Saisir un entier : ");
    scanf("%d", &a);
    switch (a) {
        case 1: printf("Lundi"); 
            break;
        case 2: printf("Mardi"); 
            break;
        case 3: printf("Mercredi"); 
            break;
        case 4: printf("Jeudi"); 
            break;
        case 5: printf("Vendredi"); 
            break;
        case 6: printf("Samedi"); 
            break;
        case 7: printf("dimanche"); 
            break;
        default : printf("Wrong input");
    }

    return 0;
}
```


## Loops in c language

1. for loop

```c
table de multiplication d'un nembre saisie par l'utilisateur
#include <stdio.h>

int main() {
    int a;
    printf("Saisir un entier : ");
    scanf("%d", &a);
    // la table d'un nembre 
    for (int i=0; i < 10; i++) {
        printf("-> %d x %d = %d\n", a, i, a*i);
    }
}
```

1. while loop

```c
int main() {
    // calcule les 20 premier entier positif
    int a;
    int i = 0;
    printf("Please enter the number : ");
    scanf("%d", &a);
    while (a < 0 || a > 10) {    
        printf("Please enter the number : ");
        scanf("%d", &a);
    }
    while (i < 10) {
        printf("%d x %d = %d\n", a, i, a*i);
        i += 1;
    }
}
```

1. do while

```c
#include <stdio.h>
int main () {
    int trigger = 5;
    do {
        printf("-> current num is %d\n", trigger);
        trigger -= 1;
    }while (trigger > 0);
}
```


# Break , Continue , Goto

1. break : break the current loop and execute the code bellow

```c
int main() {
    float somme = 0;
    int trigger = 0;
    float n;
    while (trigger <= 8) {
        printf("La note de M%d : ", trigger);
        scanf("%f", &n);
        if (n < 0 || n > 20) break;
        somme += n;
        trigger += 1;
    }
    printf("La somme des modules et : %.2f\n", somme);
}
```

3. continue : skip the current iteration

- Ecrire un programme qui calcule la somme de 8 nembre saisi par l'utilisateur si le nembre saisie et negatif la boucle va ignorer ce nombre la

```c
int main() {
    int sum = 0;
    int num;
    for (int i=0; i < 8; i++) {
        printf("Saisir un nembre : ");
        scanf("%d", &num);
        printf("%d\n", num);
        if (num < 0) continue;
        sum += num;
    }
    printf("La somme des nembre et : %d\n", sum);
}
```

1. goto : ignore all the rest and go to a mentioned part of code

__Syntax : __
```c
...
goto etiquiet ;
...
...
etiquiet ;
...
...
```

Example : demander a l'uttilisateur de saisir un nembre entre 1 et 5 jusqu'a ce qu'il fait

```c
#include <stdio.h>
int main() {
    int n ;
    start :
    printf("Saisir la valeur de n : ");
    scanf("%d", &n);
    if (n < 1 || n > 5) goto start;
    printf("Bravoo !");
    return 0;
}
```


## La declaration des tableau en C : 

1. _Definition : Tables are successive elements of the same type it uses many memory cases with the same name for all the cases, the only way to differentiate between then is by index
2. in c language tables can hold only `numbers` or `strings` not both at the same time

- **Declaration syntax : 

```c
meth 1 ---> type nom_table[taille];
---- Declaration and initialisation at the same time
meth 2 ---> type nom_table[taille] = { val1, val2, val3 };
meth 3 ---> type nom_table[] = { val1, val2, val3, ...};
```

![[Pasted image 20240809072734.png]]

#### How to access table elements in c : 

![[Pasted image 20240809073007.png]]

#### Display all table elements : 

![[Pasted image 20240809074020.png]]

###### Exercise : 

1. In this exercise we want you to create an app that can take as input from the user student notes and display the avg at the end

```c
#include <stdio.h>

int main() {
    int length = 10;
    float notes[length];
    float sum, avg;
    // store the notes
    for (int i = 0; i < length; i++){
        printf("Saisir note %d : ", i+1);
        scanf("%f", &notes[i]);
    }
    // display the notes
    sum = 0;
    for (int i=0; i < length; i++) {
        sum += notes[i];
    }
    avg = sum / 10;
    printf("La moyenne et : %.2f\n", avg);
}
```



## Functions in c language :

- always we define function outside the main function, and the function call is inside the main function.

1. Declaration :

![[Pasted image 20240809080526.png]]

###### Les types des function : 

![[Pasted image 20240809080908.png]]

2. Function Call in c :

![[Pasted image 20240809081707.png]]

##### Example :

```c
#include <stdio.h>

void power(int num) {
    printf("The power : %d\n", num * num);
}

int power_two(int num) {
    int power;
    power = num * num;
    return power;
}

int main() {
    int result;
    power(2);
    result = power_two(3);
    printf("Power of 3 is : %d\n", result);
    return 0;
}
```

##### Exercise :

![[Pasted image 20240809085958.png]]

###### Solution : 

```c
#include <stdio.h>

void signe(int a, int b){
    if ( a > 0 && b > 0) printf("%d et %d port meme sign positif\n", a, b);
    else if ( a < 0 && b < 0) printf("%d et %d port meme sign negatif\n", a, b);
    else printf("%d et %d sign different\n", a, b);
}

int min(int a, int b){
    int min = a;
    if (min > b) min = b;
    return min;
}

int max(int a, int b){
    int max = a;
    if (max < b) max = b;
    return max;
}

int main() {
    int a, b;
    printf("Saisir le nembre a : ");
    scanf("%d", &a);
    printf("Saisir le nembre b : ");
    scanf("%d", &b);
    // functions call 
    signe(a, b);
    printf("Le min des deux et : %d\n", min(a, b));
    printf("Le max des deux et : %d\n", max(a, b));
    return 0;
}

```

##### Exercise 2 :

![[Pasted image 20240809093138.png]]

##### Solution : 

```c
#include <stdio.h>
int a, b;

void signe(){
    if ( a > 0 && b > 0) printf("%d et %d port meme sign positif\n", a, b);
    else if ( a < 0 && b < 0) printf("%d et %d port meme sign negatif\n", a, b);
    else printf("%d et %d sign different\n", a, b);
}

void sign_two() {
    if (a*b>0) printf("same signe \n");
    else printf("signe different \n");
}

int min(){
    int min = a;
    if (min > b) min = b;
    return min;
}

int max(){
    int max = a;
    if (max < b) max = b;
    return max;
}

int main() {
    printf("Saisir le nembre a : ");
    scanf("%d", &a);
    printf("Saisir le nembre b : ");
    scanf("%d", &b);
    // functions call 
    signe(a, b);
    sign_two(a, b);
    printf("Le min des deux et : %d\n", min(a, b));
    printf("Le max des deux et : %d\n", max(a, b));
    return 0;
}
```


## <font color="#F92672">Type conversion in c</font>

```c
float x = 3.15;
int new_x = (int)x;
```

# Les pointeurs & passage par valeur & passage par adresse  :

1. activite : dans cette activite en veut echanger la valeur des deux variable donner en utilisent une fonction qui va faire ce travail le problem c'est si en utilise pas les pointeur en ne peuvent pas raialiser ce but 

```c
#include <stdio.h>

void echange(int *x, int *y) {
    int tmp;
    tmp = *x;
    *x = *y;
    *y = tmp;
}

int main() {
    int a, b;
    printf("Saisir la valeur de a : ");
    scanf("%d", &a);
    printf("Saisir la valeur de b : ");
    scanf("%d", &b);
    printf("Avant : a = %d | b = %d\n", a, b);
    echange(&a, &b);
    printf("Apres : a = %d | b = %d\n", a, b);
    return 0;
}
```


## Les pointeurs 
#### <font color="#3D46C4">Qu'est ce que un pointeur ? </font>

_un pointeur :_ et un variable qui contient l'adresse memoire d'un autre variable 
- on utilise le specificateur de format `%p` pour afficher l'adresse d'un variable
- pour cree un pointeur il suffit de faire la suite `int *p;` ou bien `int *p = &a;` comme ca en lui donne une valeur par default

![[Pasted image 20240811105611.png]]

#### Comment cree un pointeur : 

![[Pasted image 20240811113424.png]]

#### Exemple : 

![[Pasted image 20240811114122.png]]

```c
#include <stdio.h>

int main() {
    int a = 1;
    int b = 2;
    int c = 3;
    int *p;
    int *q;
    p = &a;
    q = &c;
    //
    printf("La valeur de p : %p et la valeur de a : %d\n", p, *p);
    printf("La valeur de q : %p et la valeur de c : %d\n", q, *q);
    // affecter la valeur de q a p puis incrimenter la valeur de q
    *p = (*q)++; // *p = 3 et *q = 4
    printf("La valeur de a : %d\n", *p);
    printf("La valeur de c : %d\n", *q);

}
```

### Passage par valeur VS passage par reference 

![[Pasted image 20240811115201.png]]

#### Resume :

- Dans le <font  color="#FF980F">passage par valeur</font> en manipule pas les valeur reel en manipule que les copy
- Dans le <font color="#FF980F">passage pas reference</font> en fait la manipulation des variable reel, c-a-d tout modification sur c'est variable formel va affecter les variable reel.

![[Pasted image 20240811115330.png]]

### Pointeur et Tableau

1. le nom d'un tableau et un pointeur sur le premier element du tableau

![[Pasted image 20240811121221.png]]

##### Exemple : 

```c
#include <stdio.h>

int main() {
    int array [] = {1, 3, 42, 4};

    printf("%d\n", array[0]);
    printf("%p\n", array);
    printf("%p\n", &array[0]);
    printf("%d\n", *array);

    return 0;
}

---- Output -----
1
0x7fff28879a60
0x7fff28879a60
1
```


![[Pasted image 20240812064521.png]]

```c
int *p;
// p fait reference a un element du tableau
++p or p++   -------> utiliser pour naviguer entre les indice [l'indice suivant]
--p or p--   -------> utiliser pour naviguer entre les indice [l'indice precedent]
```

![[Pasted image 20240812064915.png]]

## Arithmetique des pointeur 

###### Qu'est ce que signifie la fonction `sizeof()` ? 
- <font color="">sizeof()</font> fournit la taille ( en octets ) du type ou de la variable qui suit


1. Incrementation ++ 

![[Pasted image 20240812071431.png]]

2. Decrimentation --

![[Pasted image 20240812071731.png]]

3. addition 

 ![[Pasted image 20240812071941.png]]

4. sustraction 

![[Pasted image 20240812072233.png]]

- pour calculer la distance entre deux pointeur 

![[Pasted image 20240812072540.png]]


5. La comparaison 

![[Pasted image 20240812072737.png]]


#### Exercice d'application : 

![[Pasted image 20240812072911.png]]

### Solution : 

![[Pasted image 20240812075027.png]]


### Exercice d'application : 

![[Pasted image 20240812082603.png]]

#### Solution 

```c
#include <stdio.h>

int main() {
    int T[6]; // initialise our table 
    int *p = T;   // initialise our pointer 
    int somme = 0;
    // retrieve elements from the user 
    for (p = T; p < T + 6; p++) {
        printf("T[%ld] : ", p - T + 1);
        scanf("%d", p);
    }
    // la somme 
    for (p = T; p < T + 6; p++) {
        somme += *p;
    }
    printf("La somme des element et : %d\n", somme);
}

```

### Exercice d'application 2 : 

![[Pasted image 20240812082819.png]]

#### Solution 

```c
#include <stdio.h> 

int main() {
    int T[10];
    int *p = T;
    int max = 0; 

    // d'abord on va recuperer les entier de l'utilisateur 
    for (p = T; p < T + 10; p++) {
        printf("Saisir T[%ld] : ", p - T + 1);
        scanf("%d", p); // in first iteraion p = &T[0]
    }
    // loop through the 10 elements of the array and check max
    for (p = T; p < T + 10; p++) {
        if (max < *p) max = *p;
    }
    printf("La valeur maximal et : %d\n", max);
    return 0;
}
```


##### afficher le min et le max d'un tableau : 

```c
#include <stdio.h> 

int main() {
    int T[10];
    int *p = T;
    int max = 0; 
    int min;
    // d'abord on va recuperer les entier de l'utilisateur 
    for (p = T; p < T + 10; p++) {
        printf("Saisir T[%ld] : ", p - T + 1);
        scanf("%d", p); // in first iteraion p = &T[0]
    }
    // loop through the 10 elements of the array and check max
    max = *T;
    min = *T;
    for (p = T; p < T + 10; p++) {
        if (max < *p) max = *p;
        if (min > *p) min = *p;
    }
    printf("La valeur minimal et : %d\n", min);
    printf("La valeur maximal et : %d\n", max);
    return 0;
}

```


# Les chaines de caractere en c

`\0`  --> backslash zero --> et nome caractere null pour specifier en c qu'on travaille avec un string

###### Declaration et Initialisation 

![[Pasted image 20240813083723.png]]

#### L'affectation 

![[Pasted image 20240813083908.png]]

##### chaine de caractere constant

![[Pasted image 20240813084546.png]]

##### Resume 

- Une chaine de caractere peut etre declarer et initialise de plusieur maniere, la plus simple et :

```c 
char chaine [] = "hello";
```

- Aussi une chaine de caractere constant et declarer comme suit :

```c
char *chaine = "hello";
```


## Passent a l'affichage et la lecture

-> `%s` et utiliser comme un indicateur de format pour la chaine de caractere en langage c

```c 
char nom = "ALI";
printf("%s", nom);
```

1. Affichage

![[Pasted image 20240813085345.png]]

2. Ecriture 

![[Pasted image 20240813085603.png]]

mais il y'a des limites avec cette method car si en utilise ou bien en tape la chaine `Ahmed Ali` qui contient un espace entre les deux mots le programme va stocker seulement la premier partie et va ignorer la deusieme 

dans le cas des chaine de caractere en utilise pas le symbole de l'addresse `&` avant le variable car le nom de tableau et aussi un pointeur qui point sur la premier case du tableau

![[Pasted image 20240813090137.png]]

C'est pour cela on utilise pas scanf avec c'est variable la mais en utilise `gets()`

![[Pasted image 20240813090422.png]]

apres le test `gets()` no fonction plus c'est pour cela on doit utilise `fgets()` comme cela : 

```c
#include <stdio.h>

int main() {
    char nom [100];
    printf("Veuillez saisir votre nom : ");
    fgets(nom, sizeof(nom), stdin);
    printf("Votre nom et : %s\n", nom);
}
```


En peut aussi utiliser la fonction `puts()` pour afficher le contenu de la chaine de caractere

![[Pasted image 20240813090610.png]]

## Les fonction avec les chaine de caractere

- pour utiliser les fonction sur les chaine de carctere on doit inclure la bibliotheque `#include <string.h>`

-> `strlen()` : renvoie la taile de la chaine de caractere
-> `strcpy()` : cette fonction permet de copier une chaine a l'interieur d'une autre
-> `strncpy()` : permet de specifier le nembre des element a copier a l'interieur d'un autre variable
-> `strcat()` : permet d'ajouter une chaine a la fin d'une autre
-> `strncat()` : permet d'ajouter un nembre specific d'une chaine a l'autre
-> `strcmp()` : permet de comparer deux chaine de caractere il retourn `0 si les deux identique` | `negatif si la valeur ascii de premier char de 1 var et inf au 2 var` | `positif si la valeur ascii de la premier char de 1 var et sup a celle du 2 var`
-> `strchr()` : pour chercher un char dans une chaine, il renvoi soit le caractere a rechercher jusqu'a la fin du string sur la case chaine si chaine exist sinon, il va renvoi la valeur `null` le recherche se fait de `left --> right`
-> `strrchr()` : meme que `strchr()` seulement la direction de recherche et different `right --> left
-> `strstr()` : c'est une fonction de recherche aussi sauf qu'elle recherche une chaine au lieu d'un caractere
-> `strrev()` : renvoie l'inverse d'une chaine de caractere
-> `strlwr()` : renvoi une chaine d'une format miniscule
-> `strupr()` : rendre les caractere d'une chaine en majuscule 

----
1. `strlen()`
2. `strcpy()`

![[Pasted image 20240813092155.png]]
3. `strncopy()`

![[Pasted image 20240813092452.png]]
4. `strcat()`

![[Pasted image 20240813092745.png]]
5. `strncat()`

```c
strncat(d, c, 2)
```
6. `strcmp()`

![[Pasted image 20240813093612.png]]
6. `strchr()`

![[Pasted image 20240813094640.png]]
7. `strstr()`

![[Pasted image 20240813095251.png]]
8. `strrev()`

![[Pasted image 20240813095509.png]]
9. `strlwr()`

![[Pasted image 20240813095722.png]]
10. `strupr()`

![[Pasted image 20240813095807.png]]

### Exercice 1 : quelle et le resultat du code suivant 

![[Pasted image 20240813101212.png]]

```c
--- le resultat c'est ---
2 --> P + 4 --> Ascii e - ascii a = 69 - 65 = 4
```

## Exercice 2 

![[Pasted image 20240813101459.png]]

#### Solution 

```c
#include <stdio.h>
#include <string.h>

int main() {
    char chaine1 [100];
    char chaine2 [100];
    // recuperer les valeur 
    printf("Saisir la valeur de chaine 1 : ");
    fgets(chaine1, sizeof(chaine1), stdin);
    // copying
    for (int i = 0; chaine1[i] != '\0'; i++){
        chaine2[i] = chaine1[i];
    }
    int len = strlen(chaine2);
    chaine2[len + 1] = '\0';
    printf("La chaine 1 : %s\n", chaine1);
    printf("La chaine 2 : %s\n", chaine2);
}
```


# Memoire allocation 

##### Quelle et la difference entre l'allocation automatique et l'allocation dynamique

<font color="#FD4A73">Problematique : </font>
- On suppose qu'ona un tableau de 40 note qu'onva remplir dans la premier fois avec 40 notes et dans la deusieme fois en veut le remplir sois avec 30 ce qui fait en aura un `gaspillage` de la memoire ou bien avec 50 notes ce qui fait on aura un error lors de l'execution car la taille de tablau peut contien seulement 40 note --> Alors sa c'est qu'on appele `l'allocation automatique` a l'inverse ona `l'allocation dynamique`
- Exemple 

```c
#include <stdio.h>

int main() {
    float T[40];
    for (int i = 0; i < 40; i++) {
        printf("Saisir la note N[%d] : ", i+1);
        scanf("%f", T+i);
    }

    return 0;
}

```
### Les type d'allocation ?

`automatique` : signifie qu'ont va fixer le nembre des element stocker dans la memoire --> ce fait dans la partie `stack` de la memoire 
`dynamique` : signifie qu'ont peut controller le nembre des elements stocker dans la memoire  --> ce fait dans la partie `heap` de la memoire

![[Pasted image 20240826084321.png]]

![[Pasted image 20240823071936.png]]
##### l'allocation dynamique et leur fonction : 

![[Pasted image 20240823072917.png]]

1. d'abord pour pouvoir utiliser c'est fonction la on doit d'abord importer la bibliotheque `stdlib.h` 

| fonction    | fonctionalite                                                                                                                                                                                                                                                                                                                                                             |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `malloc()`  | reserver un espace dans la partie heap de la memoire la valeur par default et `garbage value` renvoi `NULL` si y'a pas acces de memoire pour stocker notre variable ou bien il renvoie le `Pointeur` qui point sur la valeur reserver. <font color="#f00">Aussi Les valeur non inisialise en utiilisent le fonction malloc() vont prendre par defaut garbage value</font> |
| `calloc()`  | reserver un espace dans la partie heap de la memoire la valeur par default et `0`                                                                                                                                                                                                                                                                                         |
| `realloc()` |                                                                                                                                                                                                                                                                                                                                                                           |
| `free()`    | liberer l'espace reserver par le fonction malloc(), calloc(), realloc()                                                                                                                                                                                                                                                                                                   |
|             |                                                                                                                                                                                                                                                                                                                                                                           |
##### La fonction malloc()

![[Pasted image 20240826084659.png]]

```c
---- Classic "Automatic allocation" ----
int a = 9;
---- "Dynamic allocation" ----
#include <stdlin.h>
int *a;
malloc(nembre_d'octet)
p = malloc(sizeof(int));
*p = 12;
---------------------
--- Les tableau -----
---------------------
int *p = malloc(4*sizeof(int));
*(P + 0) = 12;
*(P + 1) = 12;
*(P + 2) = 32;
*(P + 3) = 28;
```

##### La fonction calloc()

![[Pasted image 20240826084814.png]]

```c
#include <stdlib.h>
int *y = calloc(nembre_delement, taille_octet);
```

##### La fonction realloc()

![[Pasted image 20240826084915.png]]

- pour ajouter plus d'espace a un  pointeur deja cree on doit utiliser la fonction `realloc()`

```c
#include <stdlib.h>
int *p = malloc(3 * sizeof(int));
--- changer la taille de ce pointeur 
p = realloc(p, 5 * sizeof(in))
```

##### La fonction free()

```c
free(nom_de_pointeur);
```

### Exercice d'application 

![[Pasted image 20240826090523.png]]

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int amount;
    float somme, moyenne, note;
    float *p = calloc(amount, sizeof(float));
    printf("Saisir la taille : ");
    scanf("%d", &amount);
    if ( p  == NULL ) {
        printf("Espace insuffisent !");
        exit(0);
    } else {
        for (int i = 0; i < amount; i++) {
            printf("Saisir la note N[%d] : ", i+1);
            scanf("%f", &note);
            somme += note;
        }
    }
    printf("La somme des note : %.2f\n", somme);
    moyenne = somme / amount;
    printf("La moyenne des note : %.2f\n", moyenne);
}
```


## Les Tableaux 2D 

```c 
#include <stdio.h> 

// programme qui calcul la moyenne de chaque etudient
// saisi.

int main() {
    float notes [3][3],total = 0, moyenne = 0;

    // remplir le tableau des notes 
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("Saisir la note [%d] de l'etudient %d : ", j+1, i+1);
            scanf("%f", &notes [i][j]);
        }
    }
    // afficher les moyenne des notes
    printf("------- Les moyennes ---------\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            total += notes [i][j];
        }
        moyenne = total / 3;
        total = 0;
        printf("La moyenne de l'etudient %d et : %.2f\n", i+1, moyenne);
    }
}
```