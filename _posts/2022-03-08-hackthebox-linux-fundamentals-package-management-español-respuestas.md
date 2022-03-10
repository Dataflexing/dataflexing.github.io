---
date: 2022-03-08 11:52:24
layout: post
title: Hackthebox/Linux fundamentals/Package Management Español Respuestas
subtitle: Linux fundamentals/Package Management Español Respuestas
description: Resolvemos y explicamos en español todo el funcionamiento de los
  administradores de paquetes y sus funciones.
image: /assets/img/uploads/ti2vr6r.jpg
category: "{{slug}}"
tags:
  - Linux
  - Package_Manager
  - Hackthebox
author: Elian Canul
paginate: false
---
## Manejo de paquetes en Linux

Siempre que estamos trabajando como un administrador, manteniendo nuestras maquinas, o construyendo/actualizando o manteniendo nuestra distribución de Pentesting es crucial comprender como funcionan los administradores de packetes de Linux, en realidad hay muchas formas de usuarlos y en lo personal es algo crucial para poder sobrevivir siendo nuevo sin tener tantos errores de por medio. 

### ¿Qué son los paquetes?

Los paquetes son archivos que contienen código binario de software, archivos de configuración, información sobre dependencias y son los encargados de mantener nuestras actualizaciones y mejoras. 

### ¿Qué hacen?

Bueno pues sus funciones son:

<!--StartFragment-->

* Descarga de paquetes.

  * Descarga el software que tu necesites por medio de paquetes.
* Instalación común y ubicaciones de configuración.

  * Fácil de descargar y ubicar tus descargas.
* Control de calidad.

  * Son seguras y efectivas en la mayoría de los casos.
* Resolución de dependencia

  * Si detecta alguna falla en las dependencias, que requiera algún otro archivo adicional para ejecutar el programa no hay problema, este se instalará de forma automática. 
* Un formato de paquete binario estándar

  * Buscará si faltan archivos o paquetes si lo faltan le informará al administrador e igual buscara en su repositorio por actualizaciones.
* Configuración y funcionalidad adicionales relacionadas con el sistema

  * Puedes actualizar tu sistema y sus funciones!! Esto es algo muy bueno debido a que podremos modificar nuestra SO a nuestro gusto personal si así lo deseamos. Espero hablar de eso en algún otro post.

<!--EndFragment-->

Podemos usar muchos sistemas de administración de paquetes diferentes que cubren diferentes tipos de archivos como ".`deb`", "`.rpm`" y otros. El software se integra directamente en el sistema y sus diversos directorios se distribuyen en todo el sistema. Los cambios en el software de administración de paquetes en el sistema para instalar el paquete se toman del paquete y el software de administración de paquetes los implementa. Si el software de administración de paquetes reconoce que se requieren paquetes adicionales para el correcto funcionamiento del paquete que aún no se ha instalado, se incluye una dependencia y advierte al administrador o intenta recargar el software que falta desde un repositorio, por ejemplo, e instalarlo por adelantado.

Si se ha eliminado un software instalado, el sistema de administración de paquetes retoma la información del paquete, la modifica en función de su configuración y elimina los archivos. Hay diferentes programas de administración de paquetes que podemos usar para esto. Aquí hay una lista de ejemplos de tales programas:

<!--StartFragment-->

| **Comando** | **Descripción**                                                                                                                                                                                                                            |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `dpkg`      | `dpkg` es una herramienta para instalar, construir, eliminar y administrar paquetes Debian. El front-end primario y más fácil de usar para `dpkg` es aptitude.                                                                             |
| `apt`       | `Apt`proporciona una interfaz de línea de comandos de alto nivel para el sistema de administración de paquetes.                                                                                                                            |
| `aptitude`  | `Aptitude` es una alternativa a `apt` y es una interfaz de alto nivel para el administrador de paquetes.                                                                                                                                   |
| `snap`      | Instale, configure, actualice y elimine "`snap`" (paquetes instantáneos). Los snaps permiten la distribución segura de las últimas aplicaciones y utilidades para la nube, servidores, computadoras de escritorio e Internet de las cosas. |
| `gem`       | `Gem` es el front-end de RubyGems, el administrador de paquetes estándar para Ruby.                                                                                                                                                        |
| `pip`       | `Pip` es el instalador de paquetes de Python y es recomendado usarlo cuando no hay paquetes en el achivo debian. Previenelas instalaciones parciales descargando todos los requisitos antes de iniciar la instalación.                     |
| `git`       | `Git` es un sistema de control de revisión rápido, escalable y distribuido con un conjunto de comandos inusualmente rico que proporciona operaciones de alto nivel y acceso completo a los internos.                                       |

<!--EndFragment-->

Como siempre te recomendamos jugar con estos archivos para entenderlos un poco mejor, trata instalar algún paquete. Ahora trataremos de instalar Git usando `Apt`.

## Advanced Package Manager (APT)

Las distribuciones de Linux basadas en Debian utilizan el administrador de paquetes `APT`. Un paquete es un archivo que contiene múltiples archivos "`.deb`". La utilidad `dpkg` se usa para instalar programas desde el archivo "`.deb`" asociado. `APT` facilita la actualización e instalación de programas porque muchos programas tienen dependencias. Al instalar un programa desde un archivo "`.deb`" independiente, podemos encontrar problemas de dependencia y debemos descargar e instalar uno o varios paquetes adicionales. `APT` hace que esto sea más fácil y más eficiente al empaquetar todas las dependencias necesarias para instalar un programa.

Cada distribución de Linux utiliza repositorios de software que se actualizan con frecuencia. Cuando actualizamos un programa o instalamos uno nuevo, el sistema consulta estos repositorios para el paquete deseado. Los repositorios pueden etiquetarse como estables, de prueba o inestables. La mayoría de las distribuciones de Linux utilizan el repositorio más estable o "principal". Esto se puede verificar viendo el contenido del archivo `/etc/apt/sources.list`. La lista de repositorios para Parrot OS está en `/etc/apt/sources.list.d/parrot.list`.

<!--StartFragment-->

```shell-session
username@host$ cat /etc/apt/sources.list.d/parrot.list

# parrot repository
# this file was automatically generated by parrot-mirror-selector
deb http://htb.deb.parrot.sh/parrot/ rolling main contrib non-free
#deb-src https://deb.parrot.sh/parrot/ rolling main contrib non-free
deb http://htb.deb.parrot.sh/parrot/ rolling-security main contrib non-free
#deb-src https://deb.parrot.sh/parrot/ rolling-security main contrib non-free
```

<!--EndFragment-->

`APT` utiliza una base de datos llamada caché `APT`. Esto se utiliza para proporcionar información sobre los paquetes instalados en nuestro sistema fuera de línea. Podemos buscar en la memoria caché `APT`, por ejemplo, para encontrar todos los paquetes relacionados con Impacket.

<!--StartFragment-->

```shell-session
username@host$ apt-cache search impacket

impacket-scripts - Links to useful impacket scripts examples
polenum - Extracts the password policy from a Windows system
python-pcapy - Python interface to the libpcap packet capture library (Python 2)
python3-impacket - Python3 module to easily build and dissect network protocols
python3-pcapy - Python interface to the libpcap packet capture library (Python 3)
```

<!--EndFragment-->

Veamos información adicional sobre un paquete.

<!--StartFragment-->

```shell-session
username@host$ apt-cache show impacket-scripts

Package: impacket-scripts
Version: 1.4
Architecture: all
Maintainer: Kali Developers <devel@kali.org>
Installed-Size: 13
Depends: python3-impacket (>= 0.9.20), python3-ldap3 (>= 2.5.0), python3-ldapdomaindump
Breaks: python-impacket (<< 0.9.18)
Replaces: python-impacket (<< 0.9.18)
Priority: optional
Section: misc
Filename: pool/main/i/impacket-scripts/impacket-scripts_1.4_all.deb
Size: 2080
<SNIP>
```

<!--EndFragment-->

También podemos enumerar todos los paquetes instalados.

<!--StartFragment-->

```shell-session
username@host$ apt list --installed

Listing... Done
accountsservice/rolling,now 0.6.55-2 amd64 [installed,automatic]
adapta-gtk-theme/rolling,now 3.95.0.11-1 all [installed]
adduser/rolling,now 3.118 all [installed]
adwaita-icon-theme/rolling,now 3.36.1-2 all [installed,automatic]
aircrack-ng/rolling,now 1:1.6-4 amd64 [installed,automatic]
<SNIP>
```

<!--EndFragment-->

Si nos faltan algunos paquetes, podemos buscarlo e instalarlo con el siguiente comando.

<!--StartFragment-->

```shell-session
username@host$ sudo apt install impacket-scripts -y

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  impacket-scripts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,080 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Get:1 https://euro2-emea-mirror.parrot.sh/mirrors/parrot rolling/main amd64 impacket-scripts all 1.4 [2,080 B]
Fetched 2,080 B in 0s (15.2 kB/s)
Selecting previously unselected package impacket-scripts.
(Reading database ... 378459 files and directories currently installed.)
Preparing to unpack .../impacket-scripts_1.4_all.deb ...
Unpacking impacket-scripts (1.4) ...
Setting up impacket-scripts (1.4) ...
Scanning application launchers
Removing duplicate launchers from Debian
Launchers are updated
```

<!--EndFragment-->

## Git

Ahora que tenemos instalado `git`, podemos usarlo para descargar herramientas útiles de Github. Uno de esos proyectos se llama 'Nishang'. Nos ocuparemos y trabajaremos con el proyecto en sí más adelante. Primero, debemos navegar al repositorio del proyecto y copiar el enlace Github antes de usar `git` para descargarlo.

<!--StartFragment-->

![image](https://academy.hackthebox.com/storage/modules/18/git-nishang.png "nishang repositorio")

<!--EndFragment-->

Antes de descargar el proyecto y sus scripts y listas, debemos crear una carpeta en particular.

<!--StartFragment-->

```shell-session
username@host$ mkdir ~/nishang/ && git clone https://github.com/samratashok/nishang.git ~/nishang

Cloning into '/opt/nishang/'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 1691 (delta 4), reused 6 (delta 2), pack-reused 1676
Receiving objects: 100% (1691/1691), 7.84 MiB | 4.86 MiB/s, done.
Resolving deltas: 100% (1055/1055), done.
```

Por si no comprendiste del todo, primero usamos el comando `mkdir` para crear un directorio y le ponemos el nombre "nishang" luego con el comando `&&` le decimos que después de crear el directorio ejecute un `git clone` con la URL del repositorio en Github y en cuestión de segundos tendremos en nuestro nueva carpeta un archivo de Github recién salido del horno ;) 

<!--EndFragment-->

## DPKG

También podemos descargar los programas y herramientas de los repositorios por separado. En este ejemplo, descargamos '`strace`' para Ubuntu 18.04 LTS .

<!--StartFragment-->

```shell-session
username@host$ wget http://archive.ubuntu.com/ubuntu/pool/main/s/strace/strace_4.21-1ubuntu1_amd64.deb

--2020-05-15 03:27:17--  http://archive.ubuntu.com/ubuntu/pool/main/s/strace/strace_4.21-1ubuntu1_amd64.deb
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.88.142, 91.189.88.152, 2001:67c:1562::18, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.88.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 333388 (326K) [application/x-debian-package]
Saving to: ‘strace_4.21-1ubuntu1_amd64.deb’

strace_4.21-1ubuntu1_amd64.deb       100%[===================================================================>] 325,57K  --.-KB/s    in 0,1s    

2020-05-15 03:27:18 (2,69 MB/s) - ‘strace_4.21-1ubuntu1_amd64.deb’ saved [333388/333388]
```

<!--EndFragment-->

<!--StartFragment-->

Ahora podemos usar `apt` y `dpkg` para instalar el paquete. Veamos a `dpkg` en el próximo ejemplo.

<!--StartFragment-->

```shell-session
username@host$ sudo dpkg -i strace_4.21-1ubuntu1_amd64.deb 

(Reading database ... 154680 files and directories currently installed.)
Preparing to unpack strace_4.21-1ubuntu1_amd64.deb ...
Unpacking strace (4.21-1ubuntu1) over (4.21-1ubuntu1) ...
Setting up strace (4.21-1ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

<!--EndFragment-->

<!--EndFragment-->

Con esto, ya hemos instalado la herramienta y podemos probar si funciona correctamente. Ejecutando `-help` para ver si nos muestra sus subcomandos. Si no lo hace entonces no lo hemos instalado correctamente.<!--StartFragment-->

```shell-session
username@host$ strace -h

usage: strace [-CdffhiqrtttTvVwxxy] [-I n] [-e expr]...
              [-a column] [-o file] [-s strsize] [-P path]...
              -p pid... / [-D] [-E var=val]... [-u username] PROG [ARGS]
   or: strace -c[dfw] [-I n] [-e expr]... [-O overhead] [-S sortby]
              -p pid... / [-D] [-E var=val]... [-u username] PROG [ARGS]

Output format:
  -a column      alignment COLUMN for printing syscall results (default 40)
  -i             print instruction pointer at time of syscall
```

<!--EndFragment-->

Ejercicio opcional: Busque la herramienta "`evil-winrm`" en Github e instálela en nuestras instancias interactivas. https://academy.hackthebox.com/module

`gem install evil-winrm`

## Conclusión

Ahora sabemos que son los paquetes, que es un administrador de paquetes, como instalar paquetes, pero hay muchas otras cosas que podemos aprender como por ejemplo a como actualizar nuestro SO con un administrador, o como actualizar nuestro repositorios, todo eso son cosas que deberemos hacer en el futuro y mientras más pronto las aprendamos mucho mejor. 

Es un gusto compartir información contigo y como siempre

***Sigamos en busca del dato.***