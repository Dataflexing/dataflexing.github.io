---
date: 2022-03-27 19:05:48
layout: post
title: Ciclos for en python
description: ¿Como se usan los ciclos for en python? ¿Que es un ciclo for?
image: https://sistemasgeniales.com/wp-content/uploads/2020/10/PYTHONLANG3.jpg
category: "{{slug}}"
tags:
  - python
  - ciclos
  - for
author: Elian Canul
paginate: false
---
## Ciclo for en Python

Los ciclos en Python nos permiten ejecutar bloques de código de forma repetitiva.

Su sintaxis es:

```python
for elem in iterable:
    (tu código)
```

En donde elem es la variable que toma el valor dentro del iterable.
El iterable se refiere a algo que se pueda recorrer, como una lista, un diccionario, tupla, conjunto... 

Veámoslo de forma práctica: 

![](/assets/img/uploads/captura-de-pantalla-2022-03-27-192001.png)

1. Asignamos la variable que en este caso es la que le dará el rango a nuestro ciclo
2. Iniciamos el for y le ponemos una variable para recorrer los números (esta variable es la i, y se usa solo como variable para recorrer, igual es común usar la j, k, etc.), con el "in" le decimos que "verifique los números en", Y por ultimo usamos la función range, la cual hace que recorra todos los números desde 0 hasta la variable que le indiquemos. En nuestro caso era a, que era igual a 13. Entonces recorrerá el ciclo 13 veces.
3. Le indicamos que imprima en pantalla la palabra "Num: " y luego imprima i que es la que está recorriendo los numeros del 0, hasta que termine nuestro ciclo.
4. Sumamos uno a i.

Si vemos todo el recorrido lo que pasa es esto:

![](/assets/img/uploads/drawing-2022-03-27-17.44.00.excalidraw.png)

Igual podemos darle el rango de inicio al range(). Por ejemplo si queremos que inicie en 1 y no en 0 podemos hacer:

```python
range(1,10)
```

O igual si queremos que nuestro rango termine en 10 y no en nueve, tomando el ejemplo de antes podemos hacer: 

```python
range(1,10+1)
```

Eso fue usando la función range() dentro del for. pero en realidad la función se puede usar como un ciclo para cosas más especificas como vemos aquí:

![](/assets/img/uploads/pasted-image-20220327182137.png)

Aquí tenemos 2 Listas. Cada una guarda los valores que vemos ahí. Lo que hace nuestro ciclo for aquí es decir, pues vamos a comparar las listas. Si hay algun numero que esté en c y en b vamos a imprimir b. Veamoslo ilustrado ;)

![](/assets/img/uploads/drawing-2022-03-27-18.24.29.excalidraw.png)

En pocas palabras podemos ver como b se va recorriendo hasta que es igual a c. Cuando es igual a c imprime nuestro codigo y sigue recorriendo la lista c.

Ahora el ejercicio: 

Me tendrás que dibujar la tabla de multiplicar de un numero (El cual será dado por el usuario) y con ese numeró se le mostrará la tabla de ese numero. No te sientas mal si tienes que usar un poco de Google para resolverlo ;)

Ej:

input: 

`2`

output: 

```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6 
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7= 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20 
```

RESPUESTA:

![](/assets/img/uploads/pasted-image-20220327190506.png)