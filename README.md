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
Funcion $ git status
Da el estado en que esta ahora la carpeta. Indica si hay archivos sin enlazar
