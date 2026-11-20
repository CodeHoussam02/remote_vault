###### Question 1 : 

definir la structure `Trimonio` avec les 3 attributs a, b, c de type char unsigned

```c 
#include <stdbool.h> 
#include <stdlib.h>
#include <stdio.h> 

typedef struct _Triomino {
	unsigned char a;
	unsigned char b; 
	unsigned char c; 
} Triomino;
```