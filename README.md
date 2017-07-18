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

**REVOCANDO CAMBIOS**
Atravez de todos los cambios de nuestro repositorio, podemos enteder como funciona git internatemente un archivo puede estar en tres sitios:

- Working directory.
- Stating index.
- Git directory (Repository).

**EJERCICIO:**
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
Este nos mostrara un estado del stage area con el ajuste en verde pero nos pregunta que antes de hacer el commit podemos hacer un git reset HEAD y deshacer los cambios antes del commit
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

Como sabe git donde estamos que es lo que tiene, el que y donde lo tiene, el **HEAD** es donde apunta el trabajo en ese momento dependiendo de la rama donde estemos trabajado,
git guarda esa posción.

Todo proyecyo de git en su carpeta **HEAD** es gurado con un numero de encriptación como referencia.

**HEAD** es el numero de refencia denominado checksum, es un numero que se forma por la toma de datos de alimentación atravez de un algoritmo que es la suma de la comprobación, SHAA algorimo de encriptación

### Ramas con Git o Branches

Trabajar con las ramas en un proyecto es una de las cosas más importantes que nos vamos a encotrar en **GIT**, cuando hablamos de **BRANCHING** o trabajo con ramas, significa que iniciamos con la rama principal el master, apartir de hay podemos seguir trabajando sin seguir esa rama principal.

En muchos sistemas de control de versiones este proceso es muy costoso pues a menudo significa una copia del codigo.
La forma en que git maneja las ramifcaciones es rapido y sencillo, algo casi instantaneo al igual que el avance y el retorceso entre distintas ramas, lo cual es tremendamente rapido, con git disponenmos de una herramienta que nos permite fucionar de una manera muy sencilla,
para su uso la forma habitual de trabajo con las ramas es que siempre deberiamos de crear una rama a la hora de trabajar un proyecto, la idea es manter el master en un estado estable, mientras que trabajamos de manera aislada con el resto del desarrollo, pudiendo realizar cuantos cambios necesitemos
Al crear una nueva rama nos permite clonar una rama master y aplicar los cambios en esa rama clonada solo cuando nuestro desarrollo este perfectamente podemos fucionar la rama que estemos probando con la rama master, lo que conseguiremos con esto es que siempre estemos seguros de guardar el proyecto
en perfectas condiciones.

#### Que es una Rama?

Git no almacena los datos de forma incremental, guardando solo las diferencias de uno u otro archivo si no que los almacena como snapshot, realiza una captura de los archivos completos tal y como se encuentran en esos momentos generamos un punto de control por cada commit lo que llamamos el HEAD por cada punto de control,
de tal manera que si tenemos diferentes archivos en diferentes ramas guardara en el mismo momento tantos **HEADS** como necesitemos para retomar nuestro trabajo en el punto donde lo hayamos dejado, simplemente apuntara a ese estado, a ese momento de trabajo que guradamos con el commit, en otras palabras por cada commit git guardara un **HEAD** independiente de cada
rama en donde nos econtremos, estos nos permitira recumperar ese momento concreto de nuestra historia en el repositorio podemos disponer de tantas ramas como sean necesarias
de tal modo que siempre tengamos control para retomar, para editar, para resetear, para eliminar.

### Comandos del branching

Para controlar el trabajo con las ramas disponemos diferentes comandos que nos proporciona git para gestionar todo el flujo de trabajo dentro de un projecto:
 
 - **Git branch**
    Listado de las ramas actuales.
 - **Git branch [NombreRama]**
    Crear una nueva rama con el nombre indicado.
 - **Git checkout [nombreRama]**
    Cambiamos el estado a esa rama en contreto para trabajar en ella, por lo tanto permite ir moviendonos entre ramas.
    **git checkout -b [nombreRama]**
        Crea la rama y nos posiciona dentro de ella.
 - **Git merge [rama]**
    fuciona dos ramas en una sola
 - **Git branch -d[nombreRama]**
    Borrar una rama en concreto.

### Merge en Git

Controlar la fusión de ramas y las herramientas visuales para facilitar su uso.

 - **Git merge [rama]**
    fuciona dos ramas en una sola

### Deshacer un Merge

Deshacer un merge y volver a un commit, mucha atencion en los pasos que demos, si hacemos un merge de las dos ramas **Siempre debemos hacer un git status** y confirmar así que los todos los cambios se completaron bien, si necesitamos deshacer un merge debemos revisar cual fue el commit anterior a este y con el comando

```sh
    git reset --hard [noCommit]
```

### Remotos en Git

**Git remote**
Inicial mente y en su mayoria todos lo proyecto comienzan con git clone para copiar un repositorio en un servidor denomindado **remoto**, en un grupo de trabajo colaborativo al desarrollo. 

El primer paso vamos a convertir nuestro proyecto este en un servidor remoto:
#### git clone / git remote

Herramienta para gestionar conexiones remotas, ese repositorio remoto sera una copia de nuestro proyecto con el siguente comando hacemos una copia de un repositorio en la nueve:
```sh
    git clone https://github.com/MyREPOENgithub
```
luego podemos revisar con el comando:
```sh
    git remote
    origin
```
El cual nos habla de la conexion con el origen

Con el comando siguente comando:
```sh
    git remote -v
```
Nos mostrara cuales son las direcciones del push y del fetch
#### git push

Luego de efectuar ajustes en local el origen de nuestro repo debe tener los utilmos cambio estos se van a efectuar en master para esto por consola efectuamos el siguiente comando:
```sh
    git status
    git commit -m'prueba'
    git push
```
Esto efectuara los cambios en el repositorio de origen en la nuve.

Ahora si incluimos una rama a nuestro local:
```sh
    git checkout -b ramaNueva
```
Automaticamente por el comando que insertamos nos posiciona en esta rama, para luego agregarla a nuesto remoto en la nuve debemos por consola agerar el siguiente comando:

```sh
    git push origin ramaNueva
```
Si en algun momento decidimos que no necesitamos esa rama en remoto, la podemos eliminar con el siguente comando
```sh
    git push origin :ramaNueva
```
**Importante** Aun la rama esta presente en locar si se desea borrar esta rama debemos estar en master y con el comando:
```sh
    git branch -d ramaNueva
```
Eliminamos del el loca esta rama.
#### git fetch <=> git pull

El comando git fetch es utilizado para actualizar nuestro reposito desde el remoto, lo normal es que si estamos trabajando en un proyecto en conjunto con mas compañeros se vayan efectuando cambios en el repositorio centrar ya que cada cual ira actualizando con sus aportaciones para eso tenemos los comandos fetch y pull, para actualizar al repositorio central y otener la version actualizada de los archivos alojados, podemos utilizar git fetch origin, pero el mas estandarizado y que más vamos usar costantemente es el git pull ya que con este comando nos ahorariamos algunos pasos, ya que el se encarga de realizar el fetch mas el merge, es decir con el con el fetch deberiamos hacer dos pasos, mientras que con el pull esto lo deberia hacer de forma automatica.

En master
```sh
    git pull
```
En otra rama
```sh
    git pull origin otraRama
```

### Protocolos en Git

Normalmente nos conectamos al repositorio atravez de una direccion http, pero exiten muchas otras posibilidades de utilizar conexiones con diferente protocolos dependiendo de nuestros intereses o gustos, los protocolos generales para usar repositorios son:

- **Local** Es decir en local seria el basico podemos alejar nuestro servidor en nuestra maquina y que el resto de personas se conecten a nuestro ordenador.

- **SSH** Hoy en día el más usado, ultimamente el mas estandarizado por diferentes razones, la principal  es la seguridad ya que todas las transferencias van a estar encriptadas y autentificadas, es capas de comprimir los datos para que resulte agil. Se requiere una configuración previa con los permisos necesiarios.

- **GIT** Es muy similar al SSH, pero sin la encriptación ni la autentificación se puede usar de manera puntual para grandes proyectos, para disponer de un trafico muy amplio sin necesidad de la autentificación, requiere de una configuración especial y concreta que usa daemon (proceso que se utiliza en segundo plano sin que nosotros lo controlemos que se dedica a escuchar de manera activa atraves de un puerto concreto).

- **HTTP/S** Generico y publico.

### Git TAG

Se suelen usar para identificar los avances en nuestro proyecto, para cada version publicada de un software o para cada parte concreta de nuestro historial del proyecto, podemos crear una nueva etiqueta para una nueva version de nuestro programa cuando la hacemos publica:

Para agregar por consola agregamos:
```sh
    git tag v1.0
```
Se agrega con el ultimo commit

Podemos ver mas información con el comando
```sh
    git show v1.0
```
Para agregar esta version al remoto por consola se ejecuta el comando
```sh
    git push origin master --tags
```

### Git bare

Disponemos de este comando el --bare disponible con el git init / clone, esto significa que vamos a inicializar un nuevo repositorio de git vacio pero que con este comando va omitir el directorio de trabajo, lo usaremos cuando creemos los repositorios compartidos, siempre hay que crear los repositorios con la opcion --bare
normalmente.
