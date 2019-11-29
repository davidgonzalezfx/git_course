## Introducción a Git y GitHub - [Curso de Platzi](https://platzi.com/git)

Este es el repositorio que se trabajo con Freddy Vega CEO de Platzi, en el curso profesional de Git y Github. Para entender todo lo que se aprendió, intentaré escribir en este readme un pequeño resumen. Sin embargo puedes clonar este repositorio, revisar cada commit, el trabajo con las ramas o ir a [al curso de git y github de Platzi](https://platzi.com/git)

## Qué es git y por qué lo necesitas

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

Si estas en Windows vas a instalar Git Bash, una terminal emulada que funciona con algunos comandos de Linux. Sin embargo puedes configurarlo para que Git funcione solo desde el Git Bash o solo desde la línea de Windows (o desde ambas). En Mac OS vas a usar Git desde la terminal nativa de Mac. Si estás en Linux, sabes de este sistema operativo más que yo 😛

#### Comencemos:

Primero que todo debes crear una carpeta, en la que vas a crear los archivos de tu proyecto. Una vez tienes todo listo para iniciar tu proyecto, desde la terminal vas al directorio (con el comando `$ cd`) y alli escribes el siguiente comando:

`$ git init`
Es el comando con el que todo empieza. Le indica a Git que empiece a hacer seguimiento de tu directorio, desde este momento Git podrá hacer el respectivo seguimiento de tu proyecto. 

#### Flujo más básico de trabajo:
Una vez incias a trabajar en tu proyecto y ya tienes la primer versión que quieres guardar con Git, vas a ejecutar el siguiente comando de Git:

`$ git add .`

`$ git add` lo vamos a usar principalmente cada vez que queremos que Git registre parcialmente los cambios hechos en neustros archivos. 
Para entender a que me refiero con parcialemente, te voy a explicar tres conceptos esenciales de Git: local - stage - repositorio master

Local: Hace referencia a tu directorio y archivos almacenados en el disco duro de tu computador.

Stage: Es un espacio en memoria RAM en donde vas añadiendo y guardando los cambios antes de decirle a Git que los guarde como una versión "oficial".

Repositorio - Master: Hace referencia a los últimos cambios que se guardaron en git. El repositorio principal tiene por nombre "master". Pero de este nombre ya hablaremos en la sección de ramas.

Entendiendo esto, cuando escribimos `$ git add [archivo]` o `$ git add .` (el "." hace que automaticamente se agreguen todos los archivos) lo que hacemos es cargar nustros archivos ya modificados al Stage, es un estado temporal, pero aquí Git ya conoce cuales son las modificaciones de cada archivo. Para guardar el cambio en el repositorio, luego de ejecutar `$ git add .` debemos ejecutar `$ git commit` y así Git guarda en el historial de cambios del repositorio, tus ultimas modificaciones.

`$ git commit -m "mensaje"`

Una vez ejecutamos este comando todos nuestros cambios son guardados en el historial del repositorio, como una nueva versión de nuestro proyecto. La opción `-m "mensaje"` es una buena práctica que nos ayuda a recordar que se ha cambiado en cada versión. 

Quizás esta imagen nos ayude a entenderlo mejor.
![](https://miro.medium.com/max/686/1*diRLm1S5hkVoh5qeArND0Q.png)

Por último, un comando super útil con el que git te va a notificar el estado de tu proyecto es `$ git status`. Al ejecutarlo Git te puede mostrar que tienes archivos que no haz agregado a Stage, o quizás que ya haz modificado algunos archivos y necesitar ejecutar `$ git commit` para esos cambios o que todo está al día y tienes los últimos cambios guardados en el repositorio.

Asi que este es el flujo más básico que debes manejar cuando trabajes con Git.
`$ git init`
`$ git add .`
`$ git commit -m "mensaje"`
`$ git status`

**Repasemos los estados de un archivo:**
- cuando creas un archvio en tu PC pero no has ejecutado `$ git add [archivo]` el archivo esta sin rastrear (untracked)
- cuando ejecutas `$ git add [archivo]` el archivo se esta rastreando (tracked) y esta en Stage
- si haces cambios al archivo nuevamente, pero todavía no ejecutas `$ git add [archivo]` el archivo esta modificado (modified). Asi que Stage es un área temporal de preparación donde se registra cada cambio.
- solo cuando ejecutamos `$ git commit`tus cambios pasan de estar registrados en Stage a guardados en el historial del repositorio master. Cada vez que ejecutas este comando Git internamente entiende que tu estas guardando una nueva versión de tu proyecto. Así que cada commit es una versión. Por lo tanto luego de un nuevo commit, como ya los cambios han sido guardados, el estado de tu archivo pasa a ser "no modificado".
- Es importante reslatar que en cualquiera que se el estado de tu archivo, tu siempre lo puedes eliminar para que Git no lo rastree (untracked) ejecutando `$ git rm [archivo]`

![](https://git-scm.com/book/en/v2/images/lifecycle.png)

#### Ramas, `git merge` y `git checkout`
Por defecto tu vas a estar trabajando en una rama que Git llama "Master". Esta rama es la principal y es donde hasta el momento se están guardando los cambios de tus archivos. Podemos verlo como una línea del tiempo en la que se registran cambios y nuevas versiones con cada `$ git commit`. 

La posibilidad que nos regala Git con la opción de crear diferentes ramas es inmensa. Pero para hacerlo más sencillo, vamos a suponer que en un punto de tu proyecto, tu quieres experimentar algo nuevo sin la posibilidad de que tu proyecto se dañe. En este caso podemos crear la rama "experimento" ejecutando `$ git branch experimento`. Este comando básicamente copia la versión que tu desees de la rama master. Y en ella puedes seguir con el flujo de trabajo, creando comits, modificando tu proyecto y experimentando todo lo que quieres. La rama "experimento" va a ser totalmente diferente a la rama "master". Y para empezar a trabajar en ella vas a ejecutar `$ git checkout experimento` y así git sabe que vas a trabajar en esta rama experimental.

Supongamos que tu ya experimentaste lo que querías y todo funcionó perfecto y ahora quieres integra las caracterisitcas con las que experimentaste, a la rama principal, la rama "master". Conectar dos ramas es lo que conocemos con `merge`, es cuando unes cambios de una rama con otra. El comando para integrar estas dos ramas es `$ git merge experimento` sin embargo, para tener un merge exitoso primero debmos posicionarnos en la rama "master" que es a donde vamos a traer los cambios de "experimento". Asi que primero tenemos que ejecutar `$ git checkout master` y luego si `$ git merge experimento` . Esto va a fusionar correctamente ambas ramas y dentro de "master" va a crear una nueva versión.

Quizás una ayuda gráfica nos ayude más:

![](https://i.stack.imgur.com/83JeN.png)

En la imágen podemos ver en azul lo que te he mencionado como la rama "master" y en verde una rama paralela que puede ser "experimento". Es importante mencionar que mientras tu experimentas en la nueva rama, es completamente posible que en tu línea de tiempo principal "master" (azul) tu sigas trabajando y creando nuevas versiones de tu proyecto. Y luego cuando creas que tienes listo tu experimento y lo quieras integrar a tu rama principal, hacer un `$ git checkout master` - `$ git merge experimento`.

Finalmente, tu puedes tener tantas ramas como quieras y fusionarlas no solo hacia "master" sino a cualquiera de las que hayas creado.

##### Solución de conflictos
Pero es importante que al fusionar dos ramas, seamos cuidadosos, porque es posible que tanto en "master" como en "experimento" hayamos modificado justo la misma parte de un archivo. Esto se conoce como un conflicto. Y se da cuando al hacer un `$ git merge` Git no sabe cual parte dejar si la de la rama "experimento" o la rama "master. En estos casos, la solución es decidir manualmente, modificando el archivo, qué parte quieres dejar. Si esto ocurre trabajando en equipo, tendrás que comunicar el conlficto con tus compañeros y ponerse de acuerdo a qué modificados mantener, si las que tu hiciste experimentando o si las que se venian trabajando en la rama principal "master".

#### Viaja en el tiempo con `git checkout`
Te mencione rapidamente que antes de hacer un `git merge`, era necesario "saltar" nuevamente a master con el comando `$ git checkout master`. Pero la verdad es que `git checkout` nos permite hacer más cosas.

Ademas de moverte entre ramas, con `$ git checkout [identificador_de_commit]` puedes volver a versiones anteriores y traer cambios que quizas son útiles en este momento. Con checkout puedes traerte todos los cambios o solo ciertos cambios o los cambios de solo ciertos archivos. Es como viajar al pasado y traer modificaciones que te son útiles en el presente.

Para conocer cuál es el identificador de cada commit y así poder viajar a la versión exacta de la que quieres extraer modificaciones, haremos uso del comando `$ git log`. Al ejecutarlo se te va a desplegar un historial completo de cada commit o cada versión que has guardado en tu repositorio de Git. 

Hay dos comandos que nos ayudan a ver qué modificaciones hemos hecho a través de cada commit, nos muestran que hemos añadido y que hemos borrado. Son `$ git show` que te muestra el último commit con sus cambios y `$ git diff` el cual según los parametros que le envíes, te muestra las diferencias entre dos commits o diferencias entre distintas versiones en un archivo... Pero para esta parte quiere impulsarte a que tu busque cómo puedes sacarle el mayor provecho y utilidad a estos dos comandos. 
Te dejo la documentación oficial de Git para que explores en este [link](https://git-scm.com/docs/).

De antemano agradezco si has llegado hasta esta parte de esta guía. Y aprovecho para hacer una pausa y motivarte a que todo lo que estas leyendo y aprendiendo, lo practiques tu mismo, en tu computador. Crear carpetas y repositorios, crea muchas ramas, modificalas, fusionalas. Vuelve al pasado y pierde algunos cambios por error, busca cómo solucionar y revertir algunos comandos que ejecutaste mal y vuelve a tu última versión en la que todo funciona perfecto, etc. Solo así lograrás manejar git con total seguridad, practicando todos los comandos.

Veamos lo útlimo y con lo que debes tener más cuidado, para que domines Git como un profesional, cuando trabajes en local.
#### `git reset` y `git rm`

Si en algun momento deseas eliminar alguna versión que ya habías guardado es totalmente posible, pero debes tener bastante cuidado. Los comandos `$ git reset` y `$ git rm` te van a servir pero déjame explicarte cómo puedes usarlos.

`$ git rm` es preciso si lo que deseas es eliminar un archivo de tu proyecto, pero sin borrar su historial. Por la tanto si en algún momento lo quieres recuperar puedes usar `$ git checkout` para "viajar al pasado" y recuperar su contenido. Sin embargo para usar este comando debes elegir entre dos opciones
- `$ git rm --cached` Acá eliminas los archivos del área de Staging y del siguiente commit, pero Git no los borra de tu disco duro.
- `$ git rm --force` Con este comando eliminas los archivos tanto del disco duro, como de Git. Pero gracias al historial de Git, si necesitas recuperarlo luego, es posible.

`$ git reset` es un comando que debrías usar solo en caso de emergencia. Este comando nos va a hacer retroceder en el tiempo pero a diferencia de un `$ git checkout` que nos deja volver "al presente", `git reset` te deja en el "pasado", no podrás volver, ya que se borra todo el historial registrado en Git. Por eso deberias usarlo solo en caso de **emergencia**.

Al igual que `git rm`, `git reset` tiene dos opciones:
- `$ git reset --soft` Borras todo el historial y registros, pero mantienes los cambios y archivos que tengas agregados a Stage. Pierdes el historial, pero puedes mantener el conenido de tus archivos.
- `$ git reset --hard` Borras absolutamente todo! Y no hay Ctrl-Z que te vaya a salvar. Todas las modificaciones, los cambios, los commits, lo que tengas en Stage... todo se borra.

> Si solo quieres sacar un archivo del área de Stage, sin borrarlo, para que no se guarde en el siguiente commit, puedes usar `$ git reset HEAD`.



#### Pequeño resumen de los comandos principales para dominar Git en local.

Asegurate de conocer las banderas o parámetros que cada comando recibe para hacer el mejor uso posible de cada uno. Acá muestro algunos, pero solo son los que yo más uso.

```
git init 

git add . //añade a Stage todos los archivos de tu carpeta
git add [file]

git commit -m "mensaje"
git commit -am "mensaje" //saltas el proceso de git add

git checkout [id_commit1] [id_commit2]
git checkout branch_name

git merge branch

git rm --cached
git rm --force
git reset --hard
git reset --soft

git status
git log
git log --stat
git show
git diff 
``` 

## Github
#### Conecta con tu computadora (local)
##### Https vs SSH
#### Tags y versiones
#### Manejo de ramas en Github
##### `git clone` 
##### `git remote`
##### `git pull` - `git push`
#### Trabajo colaborativo
##### Añade colaboradores
##### Pull request
##### Fork
#### Github pages

 - creditos al maravillos Platzi Team
 - creditos x2
 - algo más para añadir
 - Advice: es genial estudiar tomando mate
 
 Esto es solo para ver como muestra Github las ramas desde "network"
 Entonces vamos a ver si lo verde es por lo cambios hechos desde github.

 Parece que es un simple cuestion de estetica. Uno verde uno rojo, uno verde uno rojo...(Espero que este no tenga conflictos)
