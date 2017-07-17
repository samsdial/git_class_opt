Optime Univesity - Git 
===================

Bienvendido a la introducción de Git basico y avanzando aquí el contenido de este curso.

Contenido
-------------

 - Configuración de Git

 ### Glosario de Git
 - Git init
 - Git add
 - Git Commit y git .ignore
 - Git status
 - Git log
 - Git diff
 - Git rm
 - Git reset
 - HEAD en Git

 ### Branching con Git
 - Ramas con Git
 - Comandos del branching
 - Merge en Git
 - Deshacer un Merge
 - Resolver conflictos con Git

 ### Remotos en Git
 - Git remote
 - Git push
 - Git tech
 
 ### Hostings en Git

 Configuración De Git
-------------
Los primeros paso sera donde disponemos la información y ayudas con el comando man Git en la consola o terminal además este manual se encuentra en el sitio web <a href="https://www.kernel.org/pub/software/scm/git/docs/" target="_blank">Manual page GIT</a>



```sh
git --help
```
Este comando no da toda la información de ayuda para el uso de git y los comando disponibles para usar está herramienta.


```sh
git help init
```
Si necesitamos información puntual sobre un comando escribimos git help + el comando que requerimos saber su documentación.

```sh
git config
```
Nos permite configurar la instalación git o un en un repositorio individual o particular.

```sh
git config -l 
```
Nos permite listar la configuración dentro de la carpeta a trabajar.

```sh
git config --global user.name "NAME USER"
git config --global user.mail sucorreo@miweb.com
```

Nos permite cambiar la configuración de nombre de usuario y el correo electronico, ademas del editor que normalmente usamos.

Glosario de Git
-------------
 ### Git init

 Crea un repositorio **NUEVO** se puede usar sobre un proyecto existente y no versionado a un repositorio vacio, es el primer comando que se ejecuta en un proyecto nuevo, al ejecutar git init se crea un subdirectorio .git al directorio actual

 ### Git Add

 Añade un cambio al directorio de trabajo al area de preparación, le dice a git que queremos incluir actualizaciones en un archivo en particular en el proximo commit, sin embargo no afecta el repositorio de forma importante los cambios no se guardan hasta que enverdad queremos subir los cambios. +git status, +git add (Guardamos los cambios para el siguiente commit)

 +git add +git commit se conoce como el flujo de trabajo el wordFlow esecial dentro de GIT.

 Basicamente desarrollar un proyecto se centra en el patron basico de :
 - Editar (1ro se editan los Archivos).
 - Preparan (2do se preparan cuando esten listos para guardar los cambios).
 - Confirmar (3ro se confirman los cambios en el repo).

 ### Git Commit

 Este comando confirma la instantanea preparada a los archivos del proyecto, versiones Seguras de un proyecto, acompañado de un mensaje de texto (git commit -m 'MENSAJE del commit').

 ### Git Status

 Muestra el estado del repositorio ademas del area de preparación. Lista que archivos se han preparado, cuales no y cuales no tienen seguimiento, el comando es total mente directo a lo que ocurre con Git add y Git commit, los mensajes de estado tambien incluyen mensajes relevantes para preparar o deshacer los cambios de nuestro repo.

 ### Git log

 Este comando muestra las instantaneas confirmadas, permite hacer un listado de la historia del projecto, filtralo y buscar cambios especificos, mientras que Git status permite inspeccionar el directorio de trabajo y el area de preparación, con git log solo operaremos en la historia confirmada, se puede personalizar está salida del historico de varias formas, de la siguiente manera:

Git log nos muestra la siguiente información:
- commit +hart(el nomero identificactivo del commit)
- autor
- Date

Nos muestra los 3 (editable) commits anteriores.
```sh
    git log -n 3
```

Nos muestra un resumen en una linea

```sh
    git log --oneline
```
Nos muestra que archivos han cambiado y el numero relativo de lineas que se han añadido.
```sh
    git log --stat
```

Nos muestra los commits por autor
```sh
    git log --author="name"
```
Nos muestra los datos de la rama
```sh
    git log --decorarte
```

### Git diff

Cuando editamos o incluimos se efectuan cambios, en caso de no estar muy seguros podemos pedirle a gif si se ha modificado los archivos de nuestro repositorio con el comando git diff
```sh
    git diff
```
 Al igual podemos ver las diferencias en el stage area antes de hacer commit con el comando
```sh
    git diff -staged
 ```

 ### Git rm

Para borrar un archivo de mi repositorio locar y remoto, debo ejecutar el comando git rm archivo.arr + git commit, con esto confirmamos el borrado del el archivo de forma local y remota.

### Git mv

Renombrar archivos desde git, ejecutamos el comando git mv + nombre + nombre y luego un git commit para confirmar el cambio

```sh
    git mv nombre.html nuevo.html
```

Aunque no solo se trata de cambiar el nombre sino también de moverlo dentro de un directorio o viceversa

```sh
    git mv nuevo.html carpeta/
```

### Git reset

REVOCANDO CAMBIOS
Atravez de todos los cambios de nuestro repositorio, podemos enteder como funciona git internatemente un archivo puede estar en tres sitios:

- Working directory.
- Stating index.
- Git directory (Repository).

EJERCICIO:
Tenemos un documento llamado archivo.html su contenido es:
```sh
Primera línea

(Agregamos) Segunda línea
```
luego por comando
```sh
    git status
```
El cual nos muestra el cambio efectuado en la segunda línea si ejecutamos el comando (importante los espacios entre checkout)
```sh
    git checkout -- archivo.html
```
Regresaremos en el tiempo borrando la segunda linea dejando el archivo así

```sh
Primera línea

```
Agregamos un commit con los ajuestes del local para el repo
```sh
    git commit -m "Cambios del archivo.html"
```
Nueva mente hacemos ajustes en el archivo.hmlt agragando la línea como en el paso uno y hacemos un git add . + git status
```sh
    git add .
    git status
```
Este nos mostrara un estado del stage area con el ajuste en verde pero nos pregunta que antes de hacer el commit podemos hacer un git reset HEAD y desacer los cambios antes del commit
```sh
    git reset HEAD archivo.html
```
Es decir que hemos dado un paso hacia atras, literalmente a sacado los archivos del stage area y al hacer un git status nos muestra el que el archivo a sido modificado y que si queremos hacer un git add .  o un git checkout (y borrar los cambios recientes).
Fin Ejemplo

Si es el caso de regresar en el tiempo en un commit debemos hacer ejecutar el siguiente comando 
```sh
    git log --oneline
    git reset --hart c95b07
```

- --hart (retorna a el commit borrando definitivamente todos los posteriores )
- --soft (retorna el commit al stading index )
- --misage (retorna todos en local)

### HEAD en Git

Como sabe git donde estamos que es lo que tiene, el que y donde lo tiene, el HEAD es donde apunta el trabajo en ese momento dependiendo de la rama donde estemos trabajado,
git guarda esa posción.

Todo proyecyo de git en su carpeta HEAD es gurado con un numero de encriptación como referencia.

HEAD es el numero de refencia denominado checksum, es un numero que se forma por la toma de datos de alimentación atravez de un algoritmo que es la suma de la comprobación, SHAA algorimo de encriptación

### Ramas con Git o Branches

Trabajar con las ramas en un proyecto es una de las cosas más importantes que nos vamos a encotrar en **GIT, cuando hablamos de BRANCHING o trabajo con ramas, significa que iniciamos con la rama principal el master, apartir de hay podemos seguir trabajando sin seguir esa rama principal.

En muchos sistemas de control de versiones este proceso es muy costoso pues a menudo significa una copia del codigo.
La forma en que git maneja las ramifcaciones es rapido y sencillo, algo casi instantaneo al igual que el avance y el retorceso entre distintas ramas, lo cual es tremendamente rapido, con git disponenmos de una herramienta que nos permite fucionar de una manera muy sencilla,
para su uso la forma habitual de trabajo con las ramas es que siempre deberiamos de crear una rama a la hora de trabajar un proyecto, la idea es manter el master en un estado estable, mientras que trabajamos de manera aislada con el resto del desarrollo, pudiendo realizar cuantos cambios necesitemos
Al crear una nueva rama nos permite clonar una rama master y aplicar los cambios en esa rama clonada solo cuando nuestro desarrollo este perfectamente podemos fucionar la rama que estemos probando con la rama master, lo que conseguiremos con esto es que siempre estemos seguros de guardar el proyecto
en perfectas condiciones.

####Que es una Rama?

Git no almacena los datos de forma incremental, guardando solo las diferencias de uno u otro archivo si no que los almacena como snapshot, realiza una captura de los archivos completos tal y como se encuentran en esos momentos generamos un punto de control por cada commit lo que llamamos el HEAD por cada punto de control,
de tal manera que si tenemos diferentes archivos en diferentes ramas guardara en el mismo momento tantos **HEADS como necesitemos para retomar nuestro trabajo en el punto donde lo hayamos dejado, simplemente apuntara a ese estado, a ese momento de trabajo que guradamos con el commit, en otras palabras por cada commit git guardara un HEAD independiente de cada
rama en donde nos econtremos, estos nos permitira recumperar ese momento concreto de nuestra historia en el repositorio podemos disponer de tantas ramas como sean necesarias
de tal modo que siempre tengamos control para retomar, para editar, para resetear, para eliminar.

### Comandos del branching

Para controlar el trabajo con las ramas disponemos diferentes comandos que nos proporciona git para gestionar todo el flujo de trabajo dentro de un projecto:
 
 - **Git branch
    Listado de las ramas actuales.
 - **Git branch [NombreRama]
    Crear una nueva rama con el nombre indicado.
 - **Git checkout [nombreRama]
    Cambiamos el estado a esa rama en contreto para trabajar en ella, por lo tanto permite ir moviendonos entre ramas.
    git checkout -b [nombreRama]
        Crea la rama y nos posiciona dentro de ella.
 - **Git merge [rama]
    fuciona dos ramas en una sola
 - **Git branch -d[nombreRama]
    Borrar una rama en concreto.

### Merge en Git

Controlar la fusión de ramas y las herramientas visuales para facilitar su uso.