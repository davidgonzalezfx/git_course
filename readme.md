**Tabla de contenido**

[TOC]

## Introducción: Git y GitHub - [Curso de Platzi](https://platzi.com/git)

Este es el repositorio que se trabajo con Freddy Vega CEO de Platzi, en el curso profesional de Git y Github. Para entender todo lo que se aprendió, intentaré escribir en este readme un pequeño resumen. Sin embargo puedes clonar este repositorio, revisar cada commit, el trabajo con las ramas o ir a [al curso de git y github de Platzi](https://platzi.com/git)

## Qué es git

Git es un software de control de versiones que nos ayuda a mejorar nuestro flujo de trabajo para el desarrollo de proyectos, no unicamente los que son de software, libros también por ejemplo. ¿En qué nos ayuda puntualmente? Seguramente te has enfrentado durante el desarrollo de algún proyecto a una carpeta llena de archivos del mismo tipo con los siguientes nombres:

- final.txt
- final_v1.txt
- final_final.txt
- final_final_v2.txt

Git evita esto. Vas a tener un solo archivo y git se va a encargar de hacer el seguimiento de los cambios en cada versión. Podras revisar los cambios en cada versión, volver a versiones anteriores, crear versiones paralelas (ramas) sin afectar tu versión principal, trabajar con equipos de forma colaborativa sin conflictos, ver quién ha hecho qué cambio y mucho mas.

Git principalmente funciona desde la terminal o línea de comandos, (sin embargo ya hay muchas interfaces gráficas).

## Comandos básicos

Para iniciar con git, primero debes instalar el software en tu computador.

Puedes hacerlo en este [link](https://git-scm.com/downloads)

Si estas en Windows vas a instalar Git Bash, una terminal emulada que funciona con algunos comandos de Linux. Sin embargo puedes configurarlo para que Git funcione solo desde el Git Bash o solo desde la línea de Windows (o desde ambas). En Mac OS vas a usar Git desde la terminal nativa de Mac. Si estás en Linux, sabes de este sistema operativo más que yo :P

#### Comencemos:

Primero que todo debes crear una carpeta, en la que vas a crear los archivos de tu proyecto. Una vez tienes todo listo para iniciar tu proyecto, desde la terminal vas al directorio (con el comando `$ cd`) y alli escribes el siguiente comando:

`$ git init`
Es el comando con el que todo empieza. Le indica a Git que empiece a hacer seguimiento de tu directorio, desde este momento Git podrá hacer el respectivo seguimiento de tu proyecto. 

#### Flujo más básico de trabajo:
Una vez incias a trabajar en tu proyecto y ya tienes la primer versión que quieres guardar con Git, vas a ejecutar el siguiente comando de Git:

`$ git add .`

`git add` lo vamos a usar principalmente cada vez que queremos que Git registre parcialmente los cambios hechos en neustros archivos. Para entender a que me refiero con parcialemente, te voy a explicar tres conceptos esenciales de Git: local - stage - repositorio master

#### Local - Stage - Master

##### Local
##### Stage
##### Master


#### Ramas y `git merge`
##### Solución de conflictos
#### Viaja en el tiempo con `git checkout`
#### `git reset` y `git rm`
## Github
#### Conecta con tu computadora (local)
##### `git clone` 
##### `git remote`
##### `git pull` - `git push`
#### Trabajo colaborativo
##### Añade colaboradores
##### Pull request
##### Fork
#### Github pages
## Todos los comandos que usé en el curso