---
date: 2022-03-28 12:01:31
layout: post
title: Listas en python
description: que es una lista en python, parametros de una lista python, python
  listas sintaxis
image: https://s3-us-west-2.amazonaws.com/devcodepro/media/tutorials/listas-python-t1.jpg
category: "{{slug}}"
tags:
  - programación
  - python
author: Elian Canul
paginate: false
---
En python las listas son muy utiles, pero cuando hablamos de data science con python entenderlas en su totalidad es algo muy fundamental. 

Para escribir una lista en python simplemente debemos de declarar una variable y usar corchetes: 

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

Como puedes ver estas se separan por comas y sus datos pueden ser de cualquier tipo.

Si hacemos un print a la lista nos devolverá la lista entera separada por comas. Pero podemos buscar un elemento de la lista mediante su índice.

`>>> print(lista[0])`

`hola`

Como puedes ver nos devolvió la primera entrada de la lista. Esto es debido a que las listas inician en el numero 0.

**Para convertir en python a un tipo lista podemos usar la función list() que está integrada en python.**

### Función len()

Podemos usar la función len() para ver la longitud de una lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> len(lista)`

`5`

Podemos hacer operaciones con el len. 

`>>> len(lista) + 1`

`6`

Esto nos puede ser muy útil para la programación dinámica, cosa que veremos más adelante.

Podemos recorrer la lista igual con numeros negativos. Algo ultil si tenemos muchos datos y queremos ver nuestro ultimo elemento de la lista. 

`>>> lista[-1]`

`43.2`

Igual podemos cambiar un elemento con el indice indicando el lugar.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista[0] = "Adiós"`

`>>> lista[0]`

`'Adiós'`

Así podemos corregir algún elemento de nuestra lista por otro.

### Métodos de listas

Las listas tiene muchos metodos integrados para su manipulación, veamoslos. 

#### .append()

agrega un elemento al final de una lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.append(6)`

`>>> print(lista)`

`['hola', 'listas', 12, 34, 43.2, 6]`

Esto es bueno si queremos solo agregar un elemento. Aunque si queremos juntar más de uno podemos sumar 2 listas.

#### .count()

Recibe un elemento como argumento y nos cuenta la cantidad de veces que aparece en nuestra lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> print(lista.count(12))`

`1`

En nuestro caso si tuviéramos más 12 se iría incrementando.

#### .extend()

Este es parecido al append() pero agrega un elemento iterable al final. Lo que significa que podemos hacer esto: 

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.extend(range(5,8))`

`>>> lista`

`['hola', 'listas', 12, 34, 43.2, 5, 6, 7]`

#### .index()

Este metodo es algo así como un buscador. Recibe un elemento como argumento y devuelve el índice de su primera aparición en la lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.index('hola')`

`0`

Este método admite como argumentos adicionales donde iniciar la búsqueda y donde terminarla:

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.index(12, 1, 3)`

`2`

Esto es útil si queremos un valor repetido en la lista pero no queremos el primer valor por ejemplo. Entonces saltamos el primer valor para que vaya en busca del segundo. 

Este método nos devolverá el `ValueError `si el elemento no se encuentra en la lista o en el rango de la lista.

#### .insert()

Este método agrega un valor a la lista sin eliminar ningún otro a diferencia de los que vimos antes. 

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.insert(1, 'adios')`

`>>> lista`

`['hola', 'adios', 'listas', 12, 34, 43.2]`

Mira que primero toma el index en el que queremos agregar y luego lo que queremos agregar. 

#### .pop()

Devuelve el ultimo elemento de una lista y lo borra de la lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> print lista.pop()`

`43.2`

`>>> lista`

`['hola', 'listas', 12, 34]`

Le podemos especificar que elemento de la lista borrar. 

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> print lista.pop(0)`

`'hola'`

`>>> lista`

`['listas', 12, 34, 43.2]`

#### .remove

Este recibe un elemento y borra su primera aparición en la lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`lista.remove(12)`

`>>>lista`

`['hola', 'listas', 34, 43.2]`

Muy bueno si solo quieres borrar un elemento de la lista. Igual da el error ValueError si no encuentra el elemento en la lista.

#### .reverse()

invierte el orden de los elementos de una lista.

`>>> lista = ['hola', 'listas', 12, 34, 43.2]`

`>>> lista.reverse()`

`>>> lista`

`[43.2, 34, 12, 'listas', 'hola']`

#### .sort()

Este método ordena los elementos de una lista. **Igual algo a tomar en cuenta es que no permite combinar valores numericos y str**.

`>>> a = [32, 6, 3, 4] `

`>>> a.sort()`

`>>> a`

`[3, 4, 6, 32]`

sort admite el paramtro reverse. La cual por defecto es False. Si lo ponemos en True, ordenará la lista al revés.

### Otras funciones

#### Asignar variable dado un rango de lista

Podemos asignar a una variable un rango de la lista:

`a = lista[1::2]`

los valores de lista desde el index 1 hasta el 2 se copiarán en a.

#### Iterar sobre una lista

<!--StartFragment-->

```python
>>> vocales = 'aeiou'
>>> for letra in 'hermosa':
...     if letra in vocales:
...         print letra,
e o a
```

<!--EndFragment-->

#### Iterar sobre una lista

Podemos usar .split() para separar los valores en una lista.

<!--StartFragment-->

```
>>> mensaje = "Hola, como estas?"
>>> mensaje.split() # retorna una lista
['Hola,', 'como', 'estas?']
>>> for palabra in mensaje.split():
...     print palabra
...
Hola,
como
estas?
```

#### Iterar sobre más de 1 secuencia

Podemos usar la función zip() para iterar sobre varias secuencias. 

<!--StartFragment-->

```
>>> preguntas = ['nombre', 'objetivo', 'sistema operativo']
>>> respuestas = ['Juan', 'Aprender Python y Data science', 'Linux']
>>> for pregunta, respuesta in zip(preguntas, respuestas):
...     print '¿Cual es tu {0}?, la respuesta es: {1}.'.format(
...         pregunta, respuesta)
...
¿Cual es tu nombre?, la respuesta es: Juan.
¿Cual es tu objetivo?, la respuesta es: aprender Python y Data science.
¿Cual es tu sistema operativo?, la respuesta es: Linux.
```

<!--EndFragment-->