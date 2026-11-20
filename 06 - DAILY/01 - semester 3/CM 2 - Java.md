
code simple pour recuperer le nom, prenom, age de l'utilisateur avec java :

```java
import java.util.*;

public class demo {

    public static void main(String[] args) {

        // declaration des variables 
        String prenom, nom; 
        int age = 0;

        // initialisation de la class scanner 
        Scanner sc = new Scanner(System.in);

        // recuperer les information de l'utilisateur 
        System.out.print("Saisir votre nom : ");
        nom = sc.nextLine();
        System.out.print("Saisir votre prenom : ");
        prenom = sc.nextLine();
        System.out.println("Saisir votre age : ");
        if (sc.hasNextInt()) {
            age = sc.nextInt();
        } else {
            System.err.println("Erreur : format unvalid! ");
        }

        // affichage des resultat au utilisateur 
        System.out.println("Nom : "+nom+"\nPrenom : "+prenom+"\nAge : "+age);

        sc.close();
    }
}

```

--- 

petit programme java qui permet de calculer la surface en se basent sur les deux parametre passe la longeur et la largeurs 

```java
import java.util.*;

public class rect {
    
    public static void main(String[] args) {
        double longu, larg, surf;
        longu = 0;
        larg  = 0;
        surf  = 0;

        // initialisation de scanner 
        Scanner sc = new Scanner(System.in);
        // demander a l'utilisateur de saisir les donnees 
        // demander la longeur 
        System.out.print("Saisir la longueur : ");
        if (sc.hasNextDouble()) {
            longu = sc.nextDouble();
        }else {
            System.err.println("Erreur : unvalid input!");
            sc.close();
            return;
        }
        // demander la largeur 
        System.out.print("Saisir la largeur : ");
        if (sc.hasNextDouble()) {
            larg = sc.nextDouble();
        }else {
            System.err.println("Erreur : unvalid input!");
            sc.close();
            System.exit(1);
        }
        // calculer la surface 
        surf = longu * larg;
        System.out.println("La surafce egale a : "+surf);
        
        sc.close();
    }
}
```

---

code pour calculer la moyenne des notes 

```java 
import java.util.*;

public class Moy {
    
    public static void main(String[] args) {
        double math, phy, ang, fran, moy;
        Scanner sc = new Scanner(System.in);
        // lire les notes 
        math = lireNote("math", sc);
        phy  = lireNote("phy", sc);
        ang  = lireNote("ang", sc);
        fran = lireNote("fran", sc);
        // calcule de la moyenne 
        moy = (math + phy + ang + fran) / 4;
        System.out.println("La moyenne des notes egale a : "+moy);
        sc.close();
    }

    // methode pour lire les notes 
    public static double lireNote(String matiere, Scanner sc) {
        double note = 0;
        boolean valide = false;

        while (!valide) {
            System.out.print("Saisir la note "+matiere+" comprise entre 0 et 20 : ");
            if (sc.hasNextDouble()) {
                note = sc.nextDouble();
                if (note >= 0 && note <= 20){
                    valide = true;
                } else {
                    System.out.println("Erreur : la note et non valide!");
                }
            } else {
                System.out.println("Erreur : note unvalid saisir un nembre");
            }
        }
        return note;
    }

}
```

programme qui indique si l'etudient et valide ou non en se basent sur sa note 

```java
import java.util.*;

public class valid {
    
    public static void main(String[] args) {
        // declarer un variable note 
        double note;
        String mentien = "Rattrapage";
        // demander a l'utilisateur de saisir une note 
        System.out.print("Saisir une note : ");
        // initialiser notre scanner
        Scanner sc = new Scanner(System.in);
        // recuperer et valider les donnees de l'utilisateur 
        if (sc.hasNextDouble()) {
            note = sc.nextDouble();
            if (note >= 0 && note <= 20) {
                if (note >= 10) {
                    mentien = "Valide";
                    System.out.println("Mentien et : "+mentien);
                }else { 
                    System.out.println("Mentien et : "+mentien);
                }
            } else {
                System.out.println("Erreur : note doit etre entre 0 et 20.");
            }
        } else {
            System.out.println("Erreur : Note non valide");
        }
        sc.close();
    }
}
```

programme java qui permet de trouver le nembre max de trois nembre saisie 

```java
import java.util.*;

public class demo {
    
    public static void main(String[] args) {
        int a, b, c, max;
        max = a = 0;
        // initialiser Scanner 
        Scanner sc = new Scanner(System.in);
        // demander les valeurs 
        // sasire la valeur de a 
        System.out.print("Saisir la valeur de a : ");
        a = sc.nextInt();
        // sasire la valeur de b 
        System.out.print("Saisir la valeur de b : ");
        b = sc.nextInt();
        // sasire la valeur de c
        System.out.print("Saisir la valeur de c : ");
        c = sc.nextInt();
        // afficher le nembre max 
        if (b > a && b > c ) {
            max = b;
            System.out.println("B : "+b+ " et le max.");        
        } else if (c > a && c > b) {
            max = c;
            System.out.println("C : "+c+ " et le max.");        
        } else { 
            System.out.println("A : "+a+ " et le max.");        
        }
    }
}
```

La valeur absolut d'un nembre saisie 

```java
import java.util.*;

public class demo {

    public static void main(String[] args ) {
        double old, newn;
        old = newn = 0;
        // demander de saisir le nembre 
        Scanner sc = new Scanner(System.in);
        System.err.print("Saisir un nembre : ");
        // affecter la valeur de a 
        old = sc.nextInt();
        // si a < 0
        if (old < 0) newn = old * -1;
        // afficher le resultat
        System.out.println("La valeur absolue de "+old+" et "+newn);
    }
}
```

calcule de prix des photocopie 

```java
import java.util.*;

public class demo {

    public static void main(String[] args) {
        double prix, nembrePhoto;
        prix = nembrePhoto = 0;
        // initisaliser notre scanner 
        Scanner sc = new Scanner(System.in);
        // demander le nembre de photocopie 
        System.out.print("Saisir le nembre de photocopie : ");
        nembrePhoto = sc.nextDouble();
        System.out.println("---"+nembrePhoto);
        // calcule de prix 
        if (nembrePhoto <= 10 ) {
            System.out.println("Prix : "+(nembrePhoto*.5)+" Dh");
        } else if ( nembrePhoto <= 30 ) {
            // pour les dix premiers 
            prix = 10 * .5;
            nembrePhoto -= 10;
            // le rest 
            prix += nembrePhoto * .25;
            System.out.println("Prix : "+prix+" Dh");
        } else {
            // pour les dix premiers 
            prix = 10 * .5;
            nembrePhoto -= 10;
            // les 20 premiers
            prix += 20 * .25;
            nembrePhoto -= 20;
            // le rest 
            prix += nembrePhoto * .1;
            System.out.println("Prix : "+prix+" Dh");
        }
    }
}
```


### TP 1 : revision 

version 1 : 

```java 
import java.util.*;

public class demo {
    public static void main(String[] args) {
        int i, j, amount;
        i = j = amount = 0;
        // recuperer le nembre de ligne 
        Scanner sc = new Scanner(System.in);
        System.out.print("Saisir le nembre des lignes : ");
        // 
        amount = sc.nextInt();
        System.out.println("Amount = "+amount);
        // outer loop
        for (i = 0;i < amount;i++) {
            String stars = "";
            // inner loop
            for (j = i+1;j <= i+1;j++) {
                stars = "*".repeat(j);
                System.out.println("|"+stars);
                stars = "";
            };
        };
    }
}
```

version 2 : la version optimiser du code 

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        int i, j, amount;
        i = j = amount = 0;
        // recuperer le nembre de ligne 
        Scanner sc = new Scanner(System.in);
        System.out.print("Saisir le nembre des lignes : ");
        // 
        amount = sc.nextInt();
        System.out.println("Amount = "+amount);
        // optimised version 
        for (i=0; i<amount;i++) {
            String stars = "";
            stars = "*".repeat(i+1);
            System.out.println("|"+stars);
            stars = "";
        }
    }
}
```

Task 2 : 

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        int i, j, amount, reversed;
        i = j = amount = 0;
        // recuperer le nembre de ligne 
        Scanner sc = new Scanner(System.in);
        System.out.print("Saisir le nembre des lignes : ");
        // 
        amount = sc.nextInt();
        System.out.println("Amount = "+amount);
        reversed = amount-1;
        // optimised version 
        for (i=0;i<=amount;i++) {
            if (reversed >= 0) {
                String stars = "";
                String xes   = "";
                stars = "*".repeat(i+1);
                xes   = "X".repeat(reversed);
                System.out.println(stars);
                System.out.println(xes);
                stars = "";
                xes   = "";
                reversed -= 1;
            } else {
                System.out.print("");
            }
            
        }
    }
}
```


--- 

###### Task 4 : 

programmme qui permet de recuperer le nom et l'age de la personne et le stock dans une liste apres les afficher a l'utilisateur.

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        // initialisation d'un tableau 
        int i;
        int size = 0;
        String names [] = null;
        int ages [] = null;
        // initialiser notre scanner 
        Scanner sc = new Scanner(System.in);
        // recuperer le size 
        System.out.print("Saisir le nembre des noms : ");
        // checker si c'est valable ou non 
        if (sc.hasNextInt()){
            size = sc.nextInt();
            if (size != 0) {
                // initialiser le size des deux tableaux 
                names = new String[size];
                ages  = new int[size];
                // boucle pour recuperer les noms et les ages
                for (i=0;i<size;i++) {
                    // recuperer les noms et les ages 
                    System.out.print("-> Saisir le nom : ");
                    sc.nextLine();
                    names[i] = sc.nextLine();

                    System.out.print("-> Saisie l'age de "+names[i]+" : ");
                    ages[i] = sc.nextInt();
                };
                // aficher les noms et les ages 
                System.out.println(names[0]);
                String pattern = "-".repeat(30);
                System.out.println(pattern);
                for (i=0;i<size;i++) {
                    System.out.println("| Nom : "+names[i]+"\n| Age : "+ages[i]);
                }
            } else {
                System.out.println("Erreur : saisir un nembre diff de 0!");
            }
        } else {
            System.out.println("Erreur : veuillez saisir un nembre valide.");
        }
    }
}
```


###### Programme 5 : 

realiser un programme qui permet de recuperer un nembre "n" des entiers apres les affichers a l'utilisateurs 

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        // declaration du size de notre tableau 
        int size = 0;
        int numbers [];
        // initialiser et recuperer les elements 
        Scanner sc = new Scanner(System.in);
        System.out.print("Saisir le nembre des element : ");
        if (sc.hasNextInt()) {
            // recuperer les element un par un 
            size = sc.nextInt();
            if (size > 0) {
                int i;
                // initialiser le size de notre tableau 
                numbers = new int[size];
                // recuperer les nembre un par un 
                for (i=0;i<size;i++) {
                    System.out.print("Saisir le "+i+" nembre : ");
                    numbers[i] = sc.nextInt();
                }
                // afficher les nembre 
                System.out.print("Les nembre sont : [ ");
                for (i=0;i<size;i++) {
                    if (i!=size-1) {
                        System.out.print(numbers[i]+",");
                    } else {
                        System.out.print(numbers[i]);
                    }
                }
                System.out.print(" ]");
            } else {
                System.out.println("Saisir un nembre > 0.");
            }
        } else {
            System.out.println("Erreur : veuillez saisir un nembre.");
        }
    }
}
```


###### Programme 7 : 

version 1 : simple

realiser un programme qui permet de parcourir une listes des nembres et apres determiner le nembre max et le nembre min de ce tablaux.

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        // declaration des variables
        int[] numbers = {12, 3, 4, 5, 15, 6, 1923, 0};
        int max = numbers[0];
        int min = numbers[0];
        int i   = 0;
        // parcourire la list et determinier le min et le max 
        System.out.print("Les element sont : [ ");
        while (i<numbers.length) {
            if (max < numbers[i]) {
                max = numbers[i];
            }
            if (min > numbers[i]) {
                min = numbers[i];
            }
            System.out.print(" "+numbers[i]+" ");
            i++;
        }
        System.err.print(" ]\n");
        // les resultat 
        System.out.println("| Le nembre min : "+min);
        System.out.println("| Le nembre max : "+max);
    }
}
```

version 2 : compliquer 

dans cette version le programme doit afficher les nembre max et min dans une liste avec leurs position, aussi si y'a plusieur occurence d'un nembre dans la list ( soit pour le min ou bien le max ) le programme doit afficher que la position de la dernier occurence dans la list pour les valeurs max et la premier position pour les valeurs mins.

```java 
import java.util.*;

public class demo {
    public static void main(String[] args) {
        // declaration des variables
        int[] numbers = {0, 0, 0, 19, 23, 442, 9, 29, 90, 23, 442};
        int max = numbers[0];
        int min = numbers[0];
        int i   = 0;
        int maxPosition = 0;
        int minPosition = 0;
        // parcourire la list et determinier le min et le max 
        System.out.print("Les element sont : [ ");
        while (i<numbers.length) {
            if (max <= numbers[i]) {
                max = numbers[i];
                maxPosition = i+1;
            }
            if (min > numbers[i]) {
                min = numbers[i];
                minPosition = i+1;
            }
            System.out.print(" "+numbers[i]+" ");
            i++;
        }
        System.err.print(" ]\n");
        // les resultat 
        System.out.println("| Le nembre min : "+min);
        System.out.println("| Position du nembre min : "+minPosition);
        System.out.println("| Le nembre max : "+max);
        System.out.println("|Position du nembre max : "+maxPosition);
    }
}
```


--- 

## Les concepts de base de la POO ? 

--- 

Le constructeur en java et une fonction specifique qui porte le meme nom que la classe et qui et pour role de cree ou bien instensier des nouvelle instance ( objets ) de la classe 

Exemple :

```java 
public class Etudient {
	// -- constructeur de la class 
	public Etudient() {
		<votre code>
	}
}
```

comment passer des valeurs par default a une constructeur. pour ceci on doit cree un autre constructeur vide

```java 
// 
```

les accesseurs et les modificateurs (getters & setter)

exemple :

![[Pasted image 20250923113841.png]]

Exemple 2 : 

![[Pasted image 20250923114204.png]]

![[Pasted image 20250923114233.png]]


---
#### TP 1 : 

que signifie la colonne temps ? 

formule de calcule de la distance entre deux points on se basent sur latitude et la longitude

comment declarer une list en java ?ta

```java 
- [x] taille dynamique et adapte au contenu de fichier
- [x] methode pratique pour manipuler les donnees 
- [x] compatible avec lapi collections
- [x] Meilleure maintenebilite
      
```

```java 
List<String> lignesList = new ArrayList<>()
lignes.add("22");
lignes.add("12");
...
```


comment declarer une arrayList en java ? 

```java 
// tout d'abord on fait importer la biblio java 
import java.util.*;

public class test {
	
	// initialisation 
	ArrayList<String> names = new ArrayList<>();
	// comment ajouter des elements au lisr 
	names.add("name1");
	// comment accder au donner de notre arrayList 
	String element1 = names.get(0);
	
	// accder au dernier element de la lisr
	String dernier1 = names.get(names.size() - 1);
	
	// comment modifier un element de la list 
	names.set(0, "testone") // par son indice 
	
	// supprimer un element de l'arrayList 
	names.remove(0) // par indice 
	names.remove("test1") // par valeur

	// verfier si la list et vide 
	boolean estvide = names.isEmpty();
}
```

Les types qu'on peut stocker dans un arrayList sont : 

```java 
- [x] int 
- [x] double 
- [x] float 
- [x] boolean
- [x] Point
- [x] Object 
```


--- 

<font color="#BAFF29" style="font-size=18;text-decoration:underline;">Gestion des fichers on java</font>

Lire un fichier

```java 
// Lecture de file 
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.*;
import java.io.IOException;

public class Lecturefile {
	public static void main(String[] args) {
		try {
		// Lire toutes les lignes 
		List<String> lignes = Files.readAllLines(Paths.get("file.csv"));
		for (String ligne : lignes ) {
			System.out.println(lignes);
		}
		// Lire en tant que String unique 
		String contenu = File.readAllbytes(Paths.get("file.csv"));
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}

```

Ecrire sur un fichier

```java 
import java.nio.file.Files;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;
import java.io.IOException;
import java.util.Arrays;
import java.util.List;

public class EcritureFiles {
    public static void main(String[] args) {
        List<String> lignes = Arrays.asList("Ligne 1", "Ligne 2", "Ligne 3");
        
        try {
            // Écrire une liste de lignes
            Files.write(Paths.get("output.txt"), lignes);
            
            // Ajouter à un fichier existant
            Files.write(Paths.get("output.txt"), 
                       Arrays.asList("Nouvelle ligne"), 
                       StandardOpenOption.APPEND);
            
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

Les fichiers binaires ( images, pdf, etc ... )

```java 
import java.io.FileInputStream;
import java.io.IOException;

public class LectureBinaire {
    public static void main(String[] args) {
        try (FileInputStream fis = new FileInputStream("image.jpg")) {
            byte[] buffer = new byte[1024];
            int bytesLus;
            
            while ((bytesLus = fis.read(buffer)) != -1) {
                // Traiter les données binaires
                System.out.println("Bytes lus: " + bytesLus);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```


### Java <font style="text-decoration: underline;">stack</font> ou bien pile : 

en java `Stack` class et une class de la collection du framework, qui implimente les `List interface` et qui extand les `Vector class` cette class represente le LIFO stack objects

voila comment faire appele cette objet 

```java 
Stack<E> stack = new Stack<E>();
```

dans le quelle `E` represent le type d'objet.

##### Les Methodes du Java Stack 

```java 
- [x] empty() -> boolean : // cette methode check si le stack et vide ou non 
- [x] peek() -> Object : // retourn l'element qui et on top du stack 
- [x] pop() -> Object : // supprime l'element qui ce retrouve dans le top du stack 
- [x] push() -> Object : // ajouter un element au Queue ( la fin du stack )
- [x] search() -> int : // methode qui permet de retourner la distance entre l'element et l'element dans le debut du stack, sinon -1 si l'element n'existe pas.
```

##### Exemple du code de stack 

```java 
import java.util.Stack;

public class myStackTest2 {
	
	public static void main(String[] args) {
		
		Stack myStack = new Stack<>();
		
		// Step 1 : check if stack is empty 
		System.out.println("Is my stack empty ? "+myStack.empty());
		
		//  Step 2 : push elements into the stack 
		myStack.push("Element 1");
		myStack.push("Element 2");
		myStack.push("Element 3");
		
		// Step 3 : print all the elements in the stack 
		System.out.println("Elements in stack : "+ mystack);
		System.out.println("Is my stack empty : "+ myStack.empty());
		
		while(!mystack.empty()) {
			myStack.pop();
			System.out.println("Elements in stack : "+ mystack);
			System.out.println("Is my stack empty : "+ myStack.empty());
		}
	}
	
}

```

Voila l'output de ce programme la 

```txt
Is my stack empty? true
Elements in Stack: [Orange Ball, Violet Ball, Green Ball]
Is my stack empty? false
Elements in Stack: [Orange Ball, Violet Ball]
Is my stack empty? false
Elements in Stack: [Orange Ball]
Is my stack empty? false
Elements in Stack: []
Is my stack empty? true
```

puisque le stack inherits du vector class et il impliment les List, le stack dans l'autre caute 



--- 
>[summary]+ note 
>
	un tableau et une structure de donnees de taille fixe, ce qui fait les tableau ou bien ( List ) en python son pas des tableau en peut dire qu'ils sont des Array list


--- 

## Les HashMap en java 

les <font color="#fb8500" style="text-decoration:underline">HashMap</font> et une structure de donnee similaire au <font color="#fb8500" style="text-decoration:underline">Dictionnaire</font> en python.

comment cree une HashMap en java ?

```java 
Map<String, String> languages = new HashMap<>();
```

les methodes pour manipuler les hashMap() ?

```java
- [x] put(cle, valeur) // methode pour ajouter un document a notre hash
- [x] putAll(Map) // inserer toutes les entres (cle/valeur) du map fourni
- [x] get(cle) // retourn la valeur en se basent sur le cle correspondent
- [x] getOrDefault(k, defaultValue) // retourn une valeur si se ne trouve pas retourn une valeur par default
- [x] replace(cle, valeur) // pour remplacer une valeur et une autre valeur
- [x] remove(k) // pour supprimer un entree du map
- [x] keySet() // retourn l'ensemble des cles
- [x] values() // retourn l'ensemble des valeurs
- [x] entrySet() // retourn l'ensemble cle, valeur
```

comment parcourir un HashMap > 

```java 
HashMap<Integer, String> map = new HashMap<>();
map.put(1, "Houssam");
map.put(2, "Ali");
map.put(3, "Sara");

for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println("Clé: " + entry.getKey() + ", Valeur: " + entry.getValue());
}
```


- application simple qui implimente les arraylist pour cree une petit application pour recuperer stocker et aussi supprimer les noms des utilisateurs deja stocker dans l'application

```java
public static void App() {

        ArrayList<String> names = new ArrayList<>();

        String[] options = {"[1]. Ajouter nom", "[2].Retirer un nom", "[3].Afficher les noms", "[4]. Quitter."};

        Scanner sc = new Scanner(System.in);

        while (true) {

            // Afficher le menu

            System.out.println("\n=== MENU ===");

            for (String opt : options) {

                System.out.println(opt);

            }

            // Récupérer l'option

            System.out.print("Choisir une option : ");

            if (sc.hasNextInt()) {

                int choix = sc.nextInt();

                sc.nextLine(); // Consommer le \n restant

                if (choix == 1) {

                    System.out.print("Saisir un nom : ");

                    String user = sc.nextLine();

                    names.add(user);

                    System.out.println("✓ Utilisateur ajouté avec succès!");

                } else if (choix == 2) {

                    if (names.isEmpty()) {

                        System.out.println("❌ Aucun nom dans la liste.");

                        continue;

                    }

                    System.out.println("Liste des noms :");

                    for (int i = 0; i < names.size(); i++) {

                        System.out.println((i + 1) + ". " + names.get(i));

                    }

                    System.out.print("Saisir le numéro du nom à supprimer : ");

                    if (sc.hasNextInt()) {

                        int index = sc.nextInt();

                        sc.nextLine(); // Consommer le \n restant

                        if (index >= 1 && index <= names.size()) {

                            String nomSupprime = names.get(index - 1);

                            System.out.println("Suppression de " + nomSupprime + " ...");

                            try {

                                Thread.sleep(2000);

                            } catch (InterruptedException e) {

                                e.printStackTrace();

                            }

                            names.remove(index - 1);

                            System.out.println("✓ Utilisateur supprimé avec succès.");

                        } else {

                            System.out.println("❌ Numéro invalide.");

                        }

                    } else {

                        System.out.println("❌ Veuillez saisir un numéro valide.");

                        sc.nextLine(); // Nettoyer l'entrée invalide

                    }

                } else if (choix == 3) {

                    if (names.isEmpty()) {

                        System.out.println("❌ Aucun nom dans la liste.");

                    } else {

                        System.out.println("\n=== LISTE DES NOMS ===");

                        for (String nom : names) {

                            System.out.println("- " + nom);

                        }

                    }

                } else if (choix == 4) {

                    System.out.println("Au revoir! 👋");

                    try {

                        Thread.sleep(1000); // Réduit à 1 seconde pour les tests

                    } catch (InterruptedException e) {

                        e.printStackTrace();

                    }

                    break;

                } else {

                    System.out.println("❌ Ce choix n'existe pas. Veuillez choisir entre 1 et 4.");

                }

            } else {

                System.out.println("❌ Veuillez saisir un nombre valide.");

                sc.nextLine(); // Nettoyer l'entrée invalide

            }

        }

        sc.close();

    }
```


### Implimentation des HashMap

- comprendre comment declarer les hashMaps, comment les parcourirs