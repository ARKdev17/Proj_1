Day-2: Inicie el repositorio de Git con comando git init en Gitproj folder
Para vincular Git al repositorio primero hay que identificarnos (de quien es este repositorio)

  1. Indicar el nombre del repositorio de GitHub
ambro@DESKTOP-RJ17PMT MINGW64 /c/users/ambro/Desktop/Git/GitProj (master)
$ git config user.name "ARKdev17"

  2. Vincular con direccion de mail
ambro@DESKTOP-RJ17PMT MINGW64 /c/users/ambro/Desktop/Git/GitProj (master)
$ git config user.email "ambXXXXXXX@gmail.com"

3. Conceder acceso remoto a tu proyecto de GitHub y que permanezcan enlazados. En teoria automaticamente se guarda todo lo que hagas en tu PC
ambro@DESKTOP-RJ17PMT MINGW64 /c/users/ambro/Desktop/Git/GitProj (master)
$ git remote add origin "https://github.com/ARKdev17/Proj_1"

Esto se enlaza con el proyecto 1. El del que se indica como origin por convencion
Si se carga un archivo nuevo no pude hacer que se cargue en el repositorio. Averiguar como hacerlo

Fin clase 3
---------------------
Day-3:
Probar subir un nuevo archivo. Fallo. Ahi va la secuencia paso a paso:
=============================================================
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/GitProj (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Test1.txt
nothing added to commit but untracked files present (use "git add" to track)

======== Este comando te tira el status de la carpeta (que cosas hay). Si hay algo en rojo (Test1.txt) es que el acrhivo es nuevo y no se cargo =======
=============================================================
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/GitProj (master)
$ git add Test1.txt
======== Este comnado "add" agrega el archivo. Pero lo hace PROVISORIAMENTE. Si no lo "anclas" y luego lo subis manualmente no se carga al repositorio
=============================================================
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/GitProj (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   Test1.txt
======== Este comando te tira el status de la carpeta (que cosas hay). Ahora Test1.txt aparece en verde y SI se cargo =======
=============================================================
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/GitProj (master)
$ git commit -m "probar aprendido dia 2"   (((lo escrito "probar aprendido dia 2" es algo que uno pone como referencia que indica que se cambio en esta rama))) 
[master 3473784] probar aprendido dia 2
 1 file changed, 1 insertion(+)
 create mode 100644 Test1.txt
========= Este comando pasa de forma DEFINITIVA (no provisoria) al repositorio. Esto indica que el archivo forma parte del proyecto y que solo falta agregarlo al repositorio vitrual (deberia estar en el local).o====
=============================================================
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/GitProj (master)
$ git push -u origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 287 bytes | 287.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/ARKdev17/Proj_1
   c2e18d1..3473784  master -> master
branch 'master' set up to track 'origin/master'.
==== El comando PUSH ($ git push) sirve para pasar nuestro archivo al repositorio remoto. Es decir pasa de un repositorio local a uno remoto=====
=============================================================
Clase 5: Git clone + git pull
Como traer un repositorio de otra persona o propio pero abriendolo desde otra computadora para poder trabajar en un proyecto nuestro sin la PC que se uso para hacerlo

== Comando $git clone: Se usa cuando se quiere trabajar en una PC nueva y se quiere copiar TODO el repositorio tal cual esta en GitHub
== al poner el comando hay que poner la URL del repositorio
Ej.:
$ git clone "ttps://github.com/ARKdev17/Proj_1/edit/main/README.md"
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone
$ git clone "https://github.com/ARKdev17/Proj_1"
Cloning into 'Proj_1'...
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 24 (delta 4), reused 6 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (24/24), 6.40
===========================
== Comando $ git pull: Sirve para cuando se trabaja en varios archivos a la vez y se hacen modificaciones entre varios poder descargar la ultima version cargada en el repositorio.
requiere de dos comandos importantes
1. el apodo que le hayamos puesto a nuestro repositorio. En este caso se llama origin.
2. hay que inicar que rama es la que estamos utilizando. Por ahora solo estamos en el main/master branch. Pero si se ramifica, se deberia indicar la rama especifica.
Ej.:
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git pull origin master
From https://github.com/ARKdev17/Proj_1
 * branch            master     -> FETCH_HEAD
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint:
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint:
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
fatal: Need to specify how to reconcile divergent branches.
=== En este try fallo porque falle en la rama. Puse master y era main al corregirla se puede ver abajo que se agregó el nuevo archivo.

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git pull origin main
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 3.45 KiB | 294.00 KiB/s, done.
From https://github.com/ARKdev17/Proj_1
 * branch            main       -> FETCH_HEAD
   d53afc7..caf38b7  main       -> origin/main
Updating d53afc7..caf38b7
Fast-forward
 README.md             | 57 +++++++++++++++++++++++++++++++++++++++++++++++++--
 Test git pull command |  2 ++
 2 files changed, 57 insertions(+), 2 deletions(-)
 create mode 100644 Test git pull command

De esta forma se logro importar un archivo desde un repositorio digital. No hace falta agregar nada. Solo actualiza lo que esta en ese branch.

  Fin dia 3
---------------------------------------------------------------------------------------------------------------------
Day-4: BRANCHES
Las ramas permiten guardar varias versiones diferentes de un mismo proyecto
Permite hacer un seguimiento de un proyecto en la medida que avanza. Es decir si venis con un codigo  que viene andando bien y luego tenes que agregar una funcionalidad o hacer un rework para mejorarlo se puede abrir una BRANCH nueva que nos permite guardar o tener el proyecto que teniamos y probar cosas nuevas en la rama nueva. 
Si funciona se deja, si no funciona, se vuelve al anterior. Es una especie de backup y de control de cambios. Pero tambien permite diversificar un trabajo para hacerlo en partes por diferentes personas o lugares. <<Es una linea independiente de desarrollo>>
Tambien se pueden tener ramas para probar diferentes funciones (una de desarrollo, otra de test, etc)
[Objetivo de aprendizaje en Git: Como crear una rama y como intercambiar entre ramas]

Comando: $ git branch - Nos dice en que rama estamos trabajando
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch
* main
En este caso es la MAIN (tambien aparece en el directorio?)

Como crear una rama nueva. Ej. RAMA_1
Comando: $ git branch (interte nombre)
Ej:
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch RAMA_1
Al apretar ENTER se crea la rama- Pero como sabemos que ramas hay o en cual estamos? Volver a usar el comando $ git branch
Ej.
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch
  RAMA_1
* main                            (main aparece en verde, lo que nos indica que estamos ahi)

Hasta aca nos dice que tenemos dos ramas y que estamos parados en la main
----
¿Como renombrar una rama?
Comando: $ gut branch -m (nombre de la rama original) (nombre de la rama nuevo)   (los nombres van sin parentesis)
Ej.
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch RAMA2

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch
  RAMA2
  RAMA_1
* main

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch -m RAMA2 RAMA_2

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git branch
  RAMA_1
  RAMA_2
* main

Nueva rama renombrada de RAMA2 a RAMA_2
----
¿Como hacemos para cambiar de rama?
Comando: $ git checkout (nombre de la rama a la que quiero ir)
Ej.
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (main)
$ git checkout rama_2
Switched to branch 'rama_2'

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (rama_2)  --> Notar q aparece en la posicion que estamos en rama_2
$ git branch
  RAMA_1
  RAMA_2
  main

OJO!!!! Por error puse en minusculas rama_2. Eso creó como una nueva rama pero no aparece listada cuando tiras $ git branch. No se para que sirve, pero hay que tenerlo en cuenta. Si distinguen MAYUS de MINUS

Ej. (ahora bien hecho)
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (rama_2)  --> Notar que estamos en rama_2 (MINUS)
$ git checkout RAMA_2
Switched to branch 'RAMA_2'     --> Cambiamos a RAMA_2, la que ya habiamos creado inicialmente

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_2)
$ git branch
  RAMA_1
* RAMA_2                --> Ahora si aparece RAMA_2 en verde y arriba en direccion nos figura (RAMA_2)
  main
---
¿Como eliminar una rama?
Comando: git branch -d (nombre de la rama)             --> Sin parentesis
Ej.
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_2)
$ git branch -d RAMA_2
error: cannot delete branch 'RAMA_2' used by worktree at 'C:/Users/ambro/Desktop
/Git/Clone/Proj_1'                  --> Aca nos indica que no podemos borrar una rama si estamos parados en esa rama

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_2)
$ git checkout RAMA_1               --> Cambiamos a otra rama (puede ser main tambien)
Switched to branch 'RAMA_1'

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git branch -d RAMA_2                   --> Probamos borrar la RAMA_2
Deleted branch RAMA_2 (was caf38b7).     __> RAMA_2 confirmado que fue borrada

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git branch                             --Corroboramos que no este mas la rama
* RAMA_1
  main

Efectivamente acabamos de borrar la rama RAMA_2
----
== ¿Como crear archivos en una nueva rama? NO van estar en la master/main ==
Comando: $ touch "(ingresar nombre y .tipo Ej. texto.txt)"
Ej.

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ touch "texto.txt"

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ touch "texto1.txt"

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ touch "texto2.txt"
--> Hasta aca acabo de crear 3 archivos .txt en la carpeta Proj_1

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git checkout master
branch 'master' set up to track 'origin/master'.
Switched to a new branch 'master'
--> Cuando cambiamos a master vemos que los archivos siguen ahi. Eso es porque nunca indicamos que los .txt creados esten asignados en RAMA_1 solamente
--> Para hacerlo hay que agregar y luego commitear (commit) para que los cambios hechos sean exclusivos de la RAMA_1

Comando: $ git add .    --> agrega todos los archivos que estamos trabajando en esta rama
         $ git commit -m "insertar un mensaje referido al cambio"
Ej.
ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git add .    --> Agrego los archivos (todos)

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git commit -m "commit de los archivos .txt"    --> al intentar commitear (asignar a un repositorio) fallo autenticacion
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'ambro@DESKTOP-RJ17PMT.(none)')

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ ^C

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git config --global user.email "ambrosiork@gmail.com"

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git config --global user.name "ARKdev_17"            --> Autenticacion completa

ambro@DESKTOP-RJ17PMT MINGW64 ~/Desktop/Git/Clone/Proj_1 (RAMA_1)
$ git commit -m "commit de los archivos .txt"             --> Se agregaron los archivos al repositorio 
[RAMA_1 c7d8590] commit de los archivos .txt
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 texto.txt
 create mode 100644 texto1.txt
 create mode 100644 texto2.txt

Ahora al cambiar de rama en la carpeta del proyecto (ejemplo de RAMA_1 a main) deberian desaparecer los archivos.

WOW! Efectivamente funciona casi como magia.

Ahora solo falta ver como agregar lo que se trabaja en las ramas en el master/main

Fin dia 4
------------------------------------------------------------------------------------------------------------------------
Day 5: DIFF y MERGE
Son comandos que nos permiten ver diferencias que hay entre las distintas ramas
DIFF: permite ver diferencias entre ramas
MERGE: Une el contenido de ramas para que todos queden contenidos en una rama unificada

¿Como ver que diferencias hay entre dos ramas?
Comando: $ git diff (nombre rama 1) (nombre rama 2)
Ej.
Se puede comprarar entre ramas. En rejo aparece lo que no tiene la rama (deleted) y en verde (lo que se agrego nuevo)
Tambien indica si hay o no archivos nuevos/deleted segun donde se compare

Como unir todo a la rama master?
Comando MERGE: $ git merge ramaOrigen ramaDestino  
Unifica dos ramas
 --> OJO! respetar la sintaxis, la podes cagar. Primero se pone la rama que trabajaste (Ej. RAMA_1). Terminaste y la queres agregar a la principal. Bueno Pones la ramaDestion (Ej. main o master)
 



