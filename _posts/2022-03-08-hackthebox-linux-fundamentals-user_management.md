---
date: 2022-03-07 23:14:22
layout: post
title: Hackthebox /Linux Fundamentals/User_Management
description: " Linux Fundamentals/User_Management respuestas, Linux
  Fundamentals/User_Management Español respuestas"
image: /assets/img/uploads/linux-user-management.jpeg
category: "{{slug}}"
tags:
  - HacktheboxLinux Fundamentals/User_Managementrespuestas
  - Linux Fundamentals/User_Managementrespuestas
  - comoresolverLinux Fundamentals/User_Management
  - Manejodeusuarioslinux
author: Elian Canul
paginate: false
---
# Manejo de usuarios Linux

El manejo de usuarios es una parte esencial de la administración de un sistema linux. A veces nececitamos crear nuevos usuarios o añadir otros usuarios a grupos especificos. Otra posibilidad es ejecutar comandos como un usuario diferente.  Miremos un ejemplo de como ejecutar codigo como un usuario diferente.

### Ejecución como usuario:

<!--StartFragment-->

```shell-session
user@host$ cat /etc/shadow

cat: /etc/shadow: Permission denied
```

<!--EndFragment-->

### Ejecución como root:

<!--StartFragment-->

```shell-session
user@host$ sudo cat /etc/shadow

root:<SNIP>:18395:0:99999:7:::
daemon:*:17737:0:99999:7:::
bin:*:17737:0:99999:7:::
<SNIP>
```

<!--EndFragment-->

###### Aquí tienes una lista para que entiendas mejor el manejo de usuarios ;)

<!--StartFragment-->

| **Command** | **Description**                                                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------------------------------- |
| `sudo`      | Ejecuta el comando como otro usuario. (Por defecto es el super usuario)                                                   |
| `su`        | El comando `su` pide las credenciales de usuario vía PAM y cambia a ese ID del usuario (Por defecto es el Super usuario). |
| `useradd`   | crea un nuevo usuario o sube nueva información de un usuario.                                                             |
| `userdel`   | Borra la cuenta de un usuario y sus archivos relacionados.                                                                |
| `usermod`   | Modifica una cuenta de usuario.                                                                                           |
| `addgroup`  | Añade un grupo al sistema.                                                                                                |
| `delgroup`  | Elimina un grupo del sistema.                                                                                             |
| `passwd`    | Cambia la contraseña de un usuario.                                                                                       |

<!--EndFragment-->

El manejo de usuarios es esencial en cualquier sistema operativo, así que te recomiendo que practiques con estos comandos borrando, creando usuarios, etc. 

### Vamos con unas preguntas del curso Hackthebox/Linux Fundamentals/User Management

Antes de iniciar te recomiendo mirar en tu terminal el -help y el man de los comandos de arriba para ver todas sus características y puedas completar fácilmente las siguientes preguntas.

Ejemplos:

`su --help` `su -h`

`man su`

<!--StartFragment-->

#### Preguntas

* ¿Cual es la opción para crear un directorio home para un nuevo usuario usando el comando `useradd`?

  * \= -m
* ¿Qué opción se necesita para bloquear una cuenta de usuario usando `usermod` command? (Escribe la parte no abreviada del comando)

  * \= --lock
* ¿Qué opción se necesita ejecutar para usar **un solo** comando como un usuario diferente usando el comando `su`?

  * \= --command

<!--EndFragment-->

Estas serían las preguntas del tema de hoy. Hazme saber que te pareció. Cuaquier duda o comentario en serio lo agraecería mucho. Como siempre no olvides que debemos seguir

***En busca del dato.***