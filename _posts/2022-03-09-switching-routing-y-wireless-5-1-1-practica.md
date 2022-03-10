---
date: 2022-03-09 11:53:59
layout: post
title: Switching, Routing y wireless 5.1.1 practica
description: En este articulo resolveremos y explicaremos como hicimos
  la   practica para que lo puedas entender a la perfección.
image: /assets/img/uploads/captura-de-pantalla-2022-03-09-113906.png
optimized_image: ""
category: Redes
tags:
  - netacad
  - cisco
  - packet_tracer
author: Elian Canul
paginate: false
---


## Packet tracer - Investigar la prevención de bucles STP

### Objetivos

En este laboratorio, observará los estados del puerto del árbol de expansión y observará el proceso de convergencia del árbol de expansión.

·         Describir el protocolo del árbol de expansión rápida (STP)

· Explicar cómo el protocolo de árbol de expansión evita los bucles de conmutación al tiempo que permite redundancia en redes conmutadas.

### Antecedentes/Escenario

En esta actividad, utilizará Packet Tracer para observar el funcionamiento del protocolo de árbol de expansión en una red conmutada simple que tiene rutas redundantes.

### Parte 1: Observar una instancia de árbol de expansión convergent

#### Paso 1: Verificar la conectividad

Ping de PC1 a PC2 para verificar la conectividad entre los hosts. El comando ping debería enviarse correctamente.

![](/assets/img/uploads/captura-de-pantalla-2022-03-09-114956.png)

#### Paso 2: Ver el estado del árbol de expansión en cada switch.

Utilice el comando show spanning-tree vlan 1 para recopilar información sobre el estado del árbol de expansión de cada switch. Completa la tabla. Para los fines de la actividad, considere únicamente la información sobre los puertos troncal Gigabit. Los puertos Fast Ethernet son puertos de acceso que tienen dispositivos finales conectados y no forman parte del árbol de expansión basado en troncal entre switches.





| <!--StartFragment-->Switch | Puerto | Estado (FWD,BLK..)  | Puente raíz?         |
| -------------------------- | ------ | ------------------- | -------------------- |
| S1                         | G0/1   | FWD                 | No                   |
| S1                         | G0/2   | FWD                 | No                   |
| S2                         | G0/1   | FWD                 | Sí                   |
|  S2                        | G0/2   | FWD                 | Sí                   |
| S3                         | G0/1   | FWD                 | No                   |
|  S3                        | G0/2   | BLK                 | No<!--EndFragment--> |



<!--StartFragment-->

#### ¿Qué crees que significa esta luz de enlace?

\
Indica que el puerto no está reenviando tramas porque está en un estado de árbol de expansión, en este caso el estado de bloqueo. Si te fijas en el diagrama la G0/2 del SW 3 está de color naranja, esto se refiere a que por ese puerto no se van a reenviar las tramas debido a que está en un estado de STP, en este caso de bloqueo, lo que hace que no se permitan las tramas.

#### ¿Qué ruta tomarán las tramas de PC1 a PC2?

Pasarían solo por S1 y S2 que si te fijas sería la ruta más rápida. 

#### ¿Por qué los marcos no viajan a través de S3?

Porque el STP puso en modo bloqueo el G0/2 en S3. No se envía ni recibe nada por ese puerto

#### ¿Por qué el árbol de expansión ha colocado un puerto en estado de bloqueo?

 Para evitar los bucles de conmutación que afectan al rendimiento de la red. Si no hiciéramos estos los paquetes se reenviarían  y así se crean los bucles.



<!--EndFragment-->

<!--StartFragment-->

### Parte 2: Observar la convergencia del árbol de expansión

#### Paso 1: Retire la conexión entre S1 y S2.

a. Abra una ventana CLI en el switch S3 y ejecute el comando **`show spanning-tree vlan 1`**. Dejen esta ventana abierta.

b. Seleccione la herramienta de eliminación en la barra de menús y haga clic en el cable que conecta S1 y S2.

#### Paso 2: Observe la convergencia del árbol de expansión.

a. Vuelva rápidamente al indicador CLI en el switch S3 y ejecute el comando **`show spanning-tree vlan 1`** .

b. Utilice la tecla de flecha hacia arriba para recuperar el comando **`show spanning-tree vlan 1`** y ejecutarlo repetidamente hasta que la luz naranja del cable se vuelva verde. Observe el estado del puerto G0/2.

#### ¿Qué ve que sucede con el estado del puerto G0/2 durante este proceso?



Primero es BLK, luego pasa a LSN que significaría que está escuchando, luego pasa a LRN que es el aprendizaje y luego pasa a FWD para el reenvío.

Lo que vimos fueron los pasos que se toman para pasar del estado de bloqueo al estado de renvío.

#### c. Verifique la conectividad haciendo ping de PC1 a PC2. El comando ping debería enviarse correctamente.



#### ¿Hay algún puerto que muestre una luz de enlace naranja que indique que el puerto está en un estado de árbol de expansión distinto del reenvío? ¿Por qué o por qué no?

Ya no hay luces anaranjadas por que ya no son rutas que reenvíen en la red.

<!--EndFragment-->