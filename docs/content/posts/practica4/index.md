+++
date = '2025-05-29T18:21:54-07:00'
draft = true
title = 'Practica 4: El paradigma lógico'
weight = 4
+++

---

## Introducción

En esta práctica exploramos el paradigma lógico mediante el uso del lenguaje de programación Prolog. Aprendimos desde la instalación del entorno, la escritura de hechos, reglas y consultas, hasta la creación de aplicaciones más complejas que hacen uso de estructuras, listas, y técnicas como recursión y backtracking.

---

## Primera sesión: Instalación e introducción a Prolog

### Instalación del entorno

1. Descargamos SWI-Prolog desde su sitio oficial:  
   [https://www.swi-prolog.org/download/stable](https://www.swi-prolog.org/download/stable)
2. Instalamos el entorno y verificamos su correcto funcionamiento ejecutando la terminal interactiva de Prolog.

### Hechos y reglas

Aprendimos a declarar hechos simples, como:

```
girl(priya).
girl(natasha).
girl(jasmin).
can_cook(priya).
```

Y reglas:

```
listens_to_music(ana) :- sing_a_song(ana).
happy(ana). :- sing_a_song(ana).
```

### Consultas básicas

Se realizaron consultas como:

```
?- girl(priya)
?- girl(gael)
?- plays_guitar(ana)
```

### Base de conocimientos

Creamos bases de conocimientos en archivos como `kb1.pl`, `kb2.pl` y `kb3.pl`, para practicar con hechos, reglas y consultas.

**kb1.pl**

```
girl(priya).
girl(natasha).
girl(jasmin).
can_cook(priya).
```

**kb2.lp**

```
sing_a_song(ana).

listens_to_music(rodrigo).

listens_to_music(ana) :- sing_a_song(ana).  

happy(ana). :- sing_a_song(ana).  

happy(rodrigo) :- listens_to_music(rodrigo).  

plays_guitar(rodrigo) :- listens_to_music(rodrigo).  
```

**kb3.pl**

```
can_cook(priya).
can_cook(jasmin).
can_cook(timoteo).

like(priya, jasmin) :- can_cook(jasmin).
like(priya, timoteo) :- can_cook(timoteo).
```

---

## Segunda sesión: Continuación de programación en Prolog

### Relaciones familiares

Desarrollamos relaciones familiares como:

```prolog
parent(pam, bob).
mother(X,Y) :- parent(X,Y), female(X).
```

También usamos variables anónimas y recursión para definir relaciones como `predecessor/2`.

### Operadores y estructuras de control

Exploramos:

- Operadores aritméticos: `+`, `-`, `*`, `/`, `mod`, etc.
- Toma de decisiones con if-then-else.
- Bucles usando recursión.
- Entrada y salida de datos.

### Listas

Realizamos operaciones con listas, incluyendo:

- Longitud
- Miembros
- Concatenación
- Inserción/eliminación
- Ordenamiento
- Permutaciones y subconjuntos

---

## Tercera sesión: Aplicaciones en Prolog

### Problemas resueltos

Desarrollamos varias aplicaciones lógicas, incluyendo:

- Árbol genealógico
- Circuitos resistivos
- Segmentos de recta
- Torre de Hanoi
- El mono y el plátano

### Conceptos clave

- **Backtracking:** para encontrar múltiples soluciones.
- **Recursión:** especialmente en listas y árboles.
- **Estructuras de datos:** listas, árboles y relaciones anidadas.

---

## Archivos desarrollados en clase

- `kb1.pl`

```prolog
girl(priya).
girl(natasha).
girl(jasmin).
can_cook(priya).
```

- `kb2.pl`

```prolog
sing_a_song(ana).

listens_to_music(rodrigo).

listens_to_music(ana) :- sing_a_song(ana).  

happy(ana). :- sing_a_song(ana).  

happy(rodrigo) :- listens_to_music(rodrigo).  

plays_guitar(rodrigo) :- listens_to_music(rodrigo). 
```

- `kb3.pl`

```prolog
can_cook(priya).
can_cook(jasmin).
can_cook(timoteo).

like(priya, jasmin) :- can_cook(jasmin).
like(priya, timoteo) :- can_cook(timoteo).
```

- `family.pl`

```prolog
female(pam). 
female(liz). 
female(pat). 
female(ann). 
male(jim). 
male(bob). 
male(tom). 
male(pete). 
parent(pam,bob). 
parent(tom,bob). 
parent(tom,liz). 
parent(bob,ann). 
parent(bob,pat). 
parent(pat,jim). 
parent(pete,jim). 
mother(X,Y):- parent(X,Y),female(X). 
father(X,Y):- parent(X,Y), male(X). 
haschild(X):- parent(X,_). 
sister(X,Y):- parent(Z,X), parent(Z,Y),female(X),X\==Y. 
brother(X,Y):- parent(Z,X), parent(Z,Y), male(X), X\==Y. 23

```

- `family_ext.pl`

```prolog
% copia el contenido de family.pl aquí 
% ... 
grandparent(X,Y):-parent(X,Z),parent(Z,Y). 
grandmother(X,Z):-mother(X,Y),parent(Y,Z). 
grandfather(X,Z):-father(X,Y),parent(Y,Z). 
wife(X,Y):-parent(X,Z),parent(Y,Z),female(X),male(Y). 
uncle(X,Z):-brother(X,Y),parent(Y,Z). 
```

- `family_rec.pl`

```prolog
% copia el contenido de family.pl aquí 
% ... 
predecessor(X, Z) :- parent(X, Z). 
predecessor(X, Z) :- parent(X, Y),predecessor(Y, Z). 
```

- `operadores.pl`

```prolog
calc :- X is 100 + 200,write('100 + 200 is '),write(X),nl, 
Y is 400 - 150,write('400 - 150 is '),write(Y),nl, 
Z is 10 * 300,write('10 * 300 is '),write(Z),nl, 
A is 100 / 30,write('100 / 30 is '),write(A),nl, 
B is 100 // 30,write('100 // 30 is '),write(B),nl, 
C is 100 ** 2,write('100 ** 2 is '),write(C),nl, 
D is 100 mod 30,write('100 mod 30 is '),write(D),nl. 
```

- `loop.pl`

```prolog
count_to_10(10):-write(10),nl. 
count_to_10(X):- 
write(X),nl, 
YisX+1, 
count_to_10(Y). 
```

- `list_basics.pl`

```prolog
list_member(X,[X|_]). 
list_member(X,[_|TAIL]) :- list_member(X,TAIL). 
list_length([],0). 
list_length([_|TAIL],N) :- list_length(TAIL,N1), N is N1 + 1. 
list_concat([],L,L). 
list_concat([X1|L1],L2,[X1|L3]) :- list_concat(L1,L2,L3). 
list_append(A,T,T) :- list_member(A,T),!. 
list_append(A,T,[A|T]). 
list_delete(X, [X], []). 
list_delete(X,[X|L1], L1). 
list_delete(X, [Y|L2], [Y|L1]) :- list_delete(X,L2,L1). 
list_insert(X,L,R) :- list_delete(X,R,L). 

```

- `list_repos.pl`

```prolog
list_delete(X,[X|L1], L1). 
list_delete(X, [Y|L2], [Y|L1]) :- list_delete(X,L2,L1). 
list_perm([],[]). 
list_perm(L,[X|P]) :- list_delete(X,L,L1),list_perm(L1,P). 
list_concat([],L,L). 
list_concat([X1|L1],L2,[X1|L3]) :- list_concat(L1,L2,L3). 
list_rev([],[]). 
list_rev([Head|Tail],Reversed) :- list_rev(Tail, RevTail),list_concat(RevTail, [Head],Reversed). 
list_shift([Head|Tail],Shifted) :- list_concat(Tail, [Head],Shifted). 
list_order([X, Y | Tail]) :- X =< Y, list_order([Y|Tail]). 
list_order([X]). 
list_subset([],[]). 
list_subset([Head|Tail],[Head|Subset]) :- list_subset(Tail,Subset). 
list_subset([Head|Tail],Subset) :- list_subset(Tail,Subset). 
list_member(X,[X|_]). 
list_member(X,[_|TAIL]) :- list_member(X,TAIL). 
list_union([X|Y],Z,W) :- list_member(X,Z),list_union(Y,Z,W). 
list_union([X|Y],Z,[X|W]) :- \+ list_member(X,Z), list_union(Y,Z,W). 
list_union([],Z,Z). 
list_intersect([X|Y],Z,[X|W]) :- list_member(X,Z), list_intersect(Y,Z,W). 
list_intersect([X|Y],Z,W) :- \+ list_member(X,Z), list_intersect(Y,Z,W). 
list_intersect([],Z,[]). 46
```

- `list_misc.pl`

```prolog
parent(pam, bob).
mother(X,Y) :- parent(X,Y), female(X).
```

- `option.pl`

```prolog
% If-Then-Else statement 
gt(X,Y) :- X >= Y,write('X is greater or equal'). 
gt(X,Y) :- X < Y,write('X is smaller'). 
% If-Elif-Else statement 
gte(X,Y) :- X > Y,write('X is greater'). 
gte(X,Y) :- X =:= Y,write('X and Y are same'). 
gte(X,Y) :- X < Y,write('X is smaller'). 
```

- `conj_disj.pl`

```prolog
parent(jhon,bob). 
parent(lili,bob). 
male(jhon). 
female(lili). 
% Conjunction Logic 
father(X,Y) :- parent(X,Y),male(X). 
mother(X,Y) :- parent(X,Y),female(X). 
% Disjunction Logic 
child_of(X,Y) :- father(X,Y);mother(X,Y). 
```

---

## Conclusión

Esta práctica nos permitió familiarizarnos con el paradigma lógico y su implementación en Prolog. A lo largo de las sesiones, desarrollamos una comprensión práctica de cómo representar el conocimiento mediante hechos, reglas y consultas. Además, aplicamos conceptos avanzados como recursión y listas para resolver problemas complejos. Prolog se presenta como una poderosa herramienta para el desarrollo de sistemas basados en lógica.

---
