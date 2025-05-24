+++
date = '2025-05-23T07:51:06-07:00'
draft = false
title = 'Practica 2 Analisis de codigo en Python'
+++

## Practica 2

## Analisis de codigo en *Python*

Fanny Lillian Mykytuk Ayvar

## Objetivo

* Nombre
* Marcos de activacion
* Bloques de alcance
* administracion de memoria
* Expresiones
* Comandos
* Control de secuencia: Seleccion, itecion y recursion
* Subprogramas
* Tipos de datos

## Nombre

Los nombres (identificadores) son las etiquetas que usamos para referirnos a variables, funciones, clases, etc.  

  **Clases** : Book, Member, Library, DigitalBook, Genre.

  **Variables**: book_id, title, library, member_id.  

  **Metodos**: add_book(), display_books(), issue_book(), mains().  

  Los nombres permiten estructurar el codigo y referirse facilmente a objetos o funciones durante su ejecucion.  

## Marcos de activacion

Los marcos de activacion se generan cuando se llama a una funcion o metodo, almacenando variables locales y el estado de ejecucion.  

* add_book(), se crea un nuevo marco de activacion.  
  
* En main(), cuando el usuario elige una opcion, se activan funciones como library.issue_book(book_id, member_id).  

Estos marcos desaparecen una vez termina la ejecucion de la funcion.

## Bloques de alcance

Los bloques de alcance definen que nombres son accesibles y en donde. EN python, esto se define por indentacion.  

* Variables como book dentro de add_book() solo existen dentro de ese metodo.  

* Atributos como self.books o self.members existen dentro del objeto de la clase Library.  
  
Esto evitaconflictos entre nombres y mantiene organizado el acceso a las variables.

## Administracion de memoria

El programa gestiona explicitamente la memoria con un modulo llamado memory_management.  

* memory_management.increment_heap_allocations(1) → Se usa cuando se crea un objeto (_int*).
* memoru_management.increment_heap+deallocations(1) → Se usa cuando se destruye un objeto (_del*).
* memory_management.display_memory_usage() → Muestra cuanta memoria se esta utilizando.  

Este tipo de control es util para saber cuantos objetos estan activos en memoria.

## Expresiones

Una expresion es cualquier fragmento de codigo que produce un valor.  

* book.quality > → Se usa para verificar si hay libros disponibles.
* int(data["quantity"]) → Convierte una cadena a numero.
* input("Ingresa el ID del miembro: ") → Retorna lo que escribio el usuario.  

Las expresiones se evaluan en condiciones, asignaciones y calculos.

## Comandos

Son las instrucciones que se ejecutan para hacer que el programa funcione.

* Print() → Muestra informacion en pantalla.
* Self.boojs.append(book) → Agrega un libro al arreglo.
* book.quantity -= 1 → Resta uno a la cantidad de libros disponibles.

Estas sentencias permiten ejecutar acciones directas en el programa.

## Control de secuencia

### Seleccion

Permite tomar decisionessegun una condicion.

* if book and member and book.quantity > 0: → Verifica que el libro exista, el miembro exista y haya ejemplares disponibles.
* if is_digital: → Verifica si el libro es digital para crear el objeto correcto.

### Iteracion

Sirven para repetir instrucciones:

* for book in self.books: → Recorre la lista de libros.
* while True: → Ciclo principal del menu, se repite hasta que se elige la opcion de salir.

### Recursion

No hay uso de recursion en el codigo. Todas las operaciones son iterativas o basadas en funciones comunes.

## Subprogramas

Los subprogramas son funciones o metodos que encapsulan una tarea.

* Metodos como add_member, return_book(), sabe_library_to_file() son subprogramas definidos dentro de clases.
* La funcion main() tambien es un subprograma que organiza toda la ejecucion del sistema.

Ayudan a dividir el codigo en partes reutilizables.

## Tipos de datos

El codigo usa barios tipos de datos integrados y personalizados.

### Tipos primitivos

* int: ID's, años de publicacion, cantidades.
* str: titulos, autores, generos, nombres.
* bool: para verificar condiciones (is_digital = ... == 's')
* list: para guardar listas de libros (self.books) o libros prestados (self.issued_books)

### Tipos definidos por el usuario

* Book, DigitalBook, Member, Library: definidos mediante clases para representar objetos del sistema.

El uso de clases permite creaer tipos compuestos con atributos y metodos porpios.
