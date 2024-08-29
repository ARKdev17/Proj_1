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
----------------------------------
Day-4:

