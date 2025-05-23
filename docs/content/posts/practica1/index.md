# Practica 1: Analisis de elementos fundamentales de lenguajes de programacion

Fanny lillian Mykytuk Ayvar

## Objetivo

Identificar los conceptos esenciales de los lenguajes de programacion presentes en la aplicacion propuesta:

* Nombres
* Marcos de activacion
* Bloques de alcance
* Administracion de memoria
* Expresiones
* Comandos
* Control de secuencia: Seleccion, iteeracion, recursion
* Subprogramas
* Tipos de datos

## Nombres

Los nombres son identificadores que usamos para variables, funciones, estructuras, etc.

* Variables: static_var, bss_var, bookID, library.
  
* Funciones: addBook, displayBooksRecursive, issueBook
  
* Estructuras: book_t, member_t
  
* Enumeración: genre_t, con valores como FICTION, SCIENCE

## Marcos de Activacion

Cada vez que se llama a una funcion, se crea un marco de activacion (stack frame) que contiene:

* Parametros
* Variables locales
* Direccion de retorno

Al llamar addBook, se crea un marco que incluye new_book, library, count.

## Bloques de ALcance

El bloque de alcance determina la visibilidad de los nombres:

* Variables locales: solo accesibles dentro de su función (e.g., new_book en addBook)
  
* Variables globales: accesibles desde cualquier parte del archivo (e.g., bss_var)

* Variables estáticas: como static int static_var, tienen alcance local pero duración global.

## Administracion de Memoria

En el programa se observa:

* Segmento de datos: static_var (inicializada, duración global)

* Segmento BSS: bss_var (no inicializada, duración global)

* Stack: variables locales como int genre en addBook

* Heap: uso de malloc y realloc para crear objetos dinámicos (book_t, member_t).

Se usa una librería externa (memory_management.h) para contabilizar la memoria asignada/liberada.

## Expresiones

Las expresiones combinan variables, constantes y operadores:

new_book->genre = (genre_t)genre;
memberFound->issued_count++;

## Comandos

* Asignaciones: memberFound->issued_books = realloc(...)

* Llamadas a funciones: displayBooksRecursive(library)

* Sentencias de control: if, while, for, switch.

## Control de secuencia

### Seleccion

* if, else, switch

### Iteracion

* while, for

### Recursion

Funcion displayBooksRecursive se llama a si misma.

## Subprogramas

El codigo esta en funciones con responsabilidades especificas:

* addBook(): agrega un libro

* issueBook(): presta un libro a un miembro

* freeLibrary(): libera la memoria

* genreToString(): convierte un enum en cadena

Esto promueve la reutilizacion y organizacion del codigo.

## Tipos de datos

### Primitivos

* Int , char, float, const char*.

### Compuestos

* Estructuras: book_t, member_t

* Enumeraciones: genre_t

* Punteros: uso extensivo para listas enlazadas y asignación dinámica.
