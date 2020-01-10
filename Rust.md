# Note Rust

#### Gestion de la mémoire : 

2 formes : 

- Stack - Pile - Last In Last Out , pile d'assiette.
Pour données dont la taille est connue et n'évoluera pas. Type LIFO.
Plus rapide. Utilisé par les primitives.

- Heap - Tas.
Occupe un certain espace dans la mémoire (dont la taille n'est pas connue à la compilation et retourne un pointeur on parle d'allouer le heap ou allocating)
Plus lent.

### Ownership - (Propriétaire) : 

Lorsqu'on passe une valeur à une fonction la fonction devient "propriétaire" de la valeur, la mémoire est libérée à la fin du scope la fonction. 
Ce qui fait qu'en cas d'appel de la valeur dans le main par exemple cela claquera une erreur, adressage de donnée qui n'existe plus.

Lors du passage d'une variable à une fonction.
La donnée peut être : 

*Copiée (Copy type, complétement la donnée dans la stack), le plus souvent il s'agit de primitive (Integer, ...) 
*Déplacée (Move type, Copy alors TOUTE la donnée qui est présente dans le heap, pour tout ce qui n'est pas primitif, chaine de caractère, slice ... - gourmand en mémoire -)

Pour éviter cela Rust met en place une mécanique un peu comme en C ou l'on accede à la donnée par un système de pret le Borrowing

### Borrowing - (Pret) 

https://learning-rust.github.io/docs/c2.borrowing.html

Deux type de "pointeurs" : 

- Partagé (&T), la donnée peut être partagée entre plusieurs fonction ou variables mais ne peut pas être modifiée.
- Mutable (&mut T), la donnée peut être utilisée uniquement par un seul utilisateur mais ne peut être modifiée que par un seul utilisateur (fonction ou méthode) à la fois (dans le même scope)

On parle alors de durée de vie du pret.
