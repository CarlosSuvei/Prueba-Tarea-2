# 1.- GIT.

## 1.1.- Instalación y configuración inicial. (config)

Para trabajar en Windows con git utilizaremos la terminal: **git bash.**

Instala o comprueba que ya este instalado el servicio: git.

Utiliza **--version** para mostrar la versión.

```
$ git --version
git version 2.42.0.windows.2
```

Utiliza el comando **which git** para saber la ubicación del ejecutable.

```
$ which git
/mingw64/bin/git
```

**Muestra el archivo de configuración global de git.**



El archivo de configuración global de git, si está creado, se encuentra en: **~/.gitconfig.**

Configura de forma global los datos de usuario: **nombre y correo electrónico.**

```
$ git config --global user.name "Carlos"
$ git config --global user.email "carlosbeniaminyt@gmail.com"
```

Muestra el **listado** de las distintas opciones de configuración.

```
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Users/Mañana/AppData/Local/Programs/Git/mingw64/etc/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.name=Carlos
user.email=carlosbeniaminyt@gmail.com
core.autocrlf=true
```

Vuelve a mostrar el archivo de configuración global.

```
$ cat ~/.gitconfig
[user]
        name = Carlos
        email = carlosbeniaminyt@gmail.com
[core]
        autocrlf = true
```

## 1.2.- Crear repositorios locales (init, status, add, commit, log)

Vamos a crear un repositorio llamado despliegue-demo. Crea una carpeta con el mismo nombre que el
repositorio y accede a ella.
```
$ mkdir despliegue-demo 
$ cd despliegue-demo  
```
#### Inicia un repositorio.

Recuerda usar **git status y git log --oneline** para ir comprobando el estado de git y los
registros de commit.

Muestra el estado de git antes de nada.

```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```

Muestra también los registros de commit antes de realizar cambios. Como aún no has hecho ningún commit, debe darte un error.

```
> git log --oneline
fatal: your current branch 'main' does not have any commits yet
```

Crea desde la línea de comandos un archivo README.md que contenga el nombre del repositorio.

```
Puedes crear un archivo desde terminal con el comando echo 'Contenido del archivo' > archivo.md. Si lo que quieres es un archivo vacío puedes usar el comando touch archivo.md y después con nano darle contenido.
```

```
$ echo 'Tarea-2-Carlos-Nuevo' > README.md
```
Vuelve a mostrar el estado de git después de crear un archivo.

```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./
        ../tarea2.md
```

Añade el archivo recién creado al área de intercambio o staged.

```
$ git add README.md
```

Vuelve a mostrar el estado de git después de añadir un archivo al staged.

```
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```

Añade los archivos del área de intercambio al repositorio local con commit.
```
Recuerda poner un mensaje al realizar el commit, con -m "mensaje".
```
```
$ git commit README.md -m "Commit Bueno"
warning: in the working copy of 'despligue-demo/README.md', LF will be replaced by CRLF the next time Git touches it
[main 09b2b87] Commit Bueno
 1 file changed, 1 insertion(+)
 create mode 100644 despligue-demo/README.md
```
Vuelve a mostrar el estado de git después de añadir un archivo al commit.
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```
Muestra los registros de commit después de realizar este primer commit.

```
$ git log --oneline
09b2b87 (HEAD -> main) Commit Bueno
```

## 1.3.- Deshacer cambios 

### 1.3.1.- Cambios en un archivo que ya se ha incluido en algún commit. (diff, restore)

Recuerda usar git diff, git diff HEAD o git diff --cached / git diff --staged para ir viendo las diferencias de los archivos.

Vamos a modificar el archivo README.md. Lo editamos con un editor gráfico o desde el terminal con nano. Insertamos un par de espacios en blanco y ponermos el nombre del módulo: Despliegue de aplicaciones web.

Muestra el contenido del archivo README.md.

```
$ cat README.md
Tarea-2-Carlos-Nuevo



Despliegue aplicaciones web
```
Muestra el estado de git después de las modificaciones
```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```
Muestra las diferencia de los cambios entre el directorio de trabajo y el último commit.

```
$ git diff HEAD
warning: in the working copy of 'despligue-demo/README.md', LF will be replaced by CRLF the next time Git touches it
diff --git a/despligue-demo/README.md b/despligue-demo/README.md
index d8eebf9..14c7afa 100644
--- a/despligue-demo/README.md
+++ b/despligue-demo/README.md
@@ -1 +1,5 @@
 Tarea-2-Carlos-Nuevo
+
+
+
+Despliegue aplicaciones web
```
Añadimos el archivo al staged.
```
$ git add README.md
```
Vuelve a mostrar el estado de git después de añadir un archivo al staged.

```
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```
Vuelve a mostrar las diferencia de los cambios pero esta vez entre el staged y el último commit.
```
$ git diff --cached
diff --git a/despligue-demo/README.md b/despligue-demo/README.md
index d8eebf9..14c7afa 100644
--- a/despligue-demo/README.md
+++ b/despligue-demo/README.md
@@ -1 +1,5 @@
 Tarea-2-Carlos-Nuevo
+
+
+
+Despliegue aplicaciones web
```
Ahora deshaz este cambio y que el cambio se quede en el directorio de trabajo o workspace.

Recuerda utilizar git restore con los parámetros adecuados en lugar de git reset o git checkout. 

```
$ git restore --staged -p
diff --git a/despligue-demo/README.md b/despligue-demo/README.md
index d8eebf9..dbc8840 100644
--- a/despligue-demo/README.md
+++ b/despligue-demo/README.md
@@ -1 +1,5 @@
 Tarea-2-Carlos-Nuevo
+
+
+
+Despliegue de aplicaciones web
(1/1) Unstage this hunk [y,n,q,a,d,e,?]? y
```
Vuelve a mostrar el estado de git después de deshacer los cambios.
```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```
Muestra el contenido del archivo README.md. La línea con el nombre del módulo debe seguir estando ya que hemos deshecho el staged pero aún no hemos restaurado la copia del commit anterior.
```
$ cat README.md
Tarea-2-Carlos-Nuevo



Despliegue de aplicaciones web
```
Ahora sí queremos restaurar la copia del commit anterior. 
```
$ git restore --source HEAD README.md
```
Vuelve a mostrar el contenido del archivo README.md. Ya debe verse como se salvo en el anterior commit.
```
$ cat README.md
Tarea-2-Carlos-Nuevo
```
Muestra el estado de git para comprobar el estado de los cambios en el directorio de trabajo.
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ../tarea2.md
```

### 1.3.3.- Cambios en un commit (revert, reset, show, tag)

Crea un nuevo archivo centro.md con el nombre del instituto y haz un commit.
```
$ echo 'Aguadulce' > centro.md

$ git add centro.md

$ git commit centro.md -m "commit centro"
warning: in the working copy of 'despligue-demo/centro.md', LF will be replaced by CRLF the next time Git touches it
[main e09de9b] commit centro
 1 file changed, 1 insertion(+)
 create mode 100644 despligue-demo/centro.md
```
Muestra los registros de commit.
```
$ git log --oneline
e09de9b (HEAD -> main) commit centro
09b2b87 Commit Bueno
```
Muestra las diferencias entre los dos últimos commit.
```
$ git diff HEAD HEAD~1
diff --git a/despligue-demo/centro.md b/despligue-demo/centro.md
deleted file mode 100644
index 2485727..0000000
--- a/despligue-demo/centro.md
+++ /dev/null
@@ -1 +0,0 @@
-Aguadulce
:...skipping...
diff --git a/despligue-demo/centro.md b/despligue-demo/centro.md
deleted file mode 100644
index 2485727..0000000
--- a/despligue-demo/centro.md
+++ /dev/null
@@ -1 +0,0 @@
-Aguadulce
```
Revierte el último commit.
```
$ git revert e09de9b77d63e308bf79320c3d25522fb3c96c26
[main e4436c8] Revert "commit centro"
 1 file changed, 1 deletion(-)
 delete mode 100644 despligue-demo/centro.md
```
Vuelve a mostrar los registros de commit.
```
$ git log --oneline
e4436c8 (HEAD -> main) Revert "commit centro"
e09de9b commit centro
09b2b87 Commit Bueno
a84478c Tarea-2
```
Muestra el listado de archivos del directorio para comprobar si se ha eliminado el archivo instituto.md.
```
$ ls -la
total 21
drwxr-xr-x 1 Mañana 197121    0 nov. 17 10:06 ./
drwxr-xr-x 1 Mañana 197121    0 nov. 16 09:59 ../
drwxr-xr-x 1 Mañana 197121    0 nov. 24 10:33 .git/
drwxr-xr-x 1 Mañana 197121    0 nov. 24 10:31 despligue-demo/
-rw-r--r-- 1 Mañana 197121   34 nov. 17 10:06 README.md
-rw-r--r-- 1 Mañana 197121 9811 nov. 24 10:34 tarea2.md
```
Añade tu nombre al archivo README.md y haz un commit.
```
$ git commit README.md -m "añado mi nombre"
[main 23601a6] añado mi nombre
 1 file changed, 0 insertions(+), 0 deletions(-)
```
Muestra el nuevo contenido de README.md.
```
$ cat README.md
Carlos Beniamin Suvei
```
Muestra el estado de git para ver que el directorio de trabajo está limpio.
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        tarea2.md
```
Muestra los registro de commit.
```
$ git log --oneline
23601a6 (HEAD -> main) añado mi nombre
e4436c8 Revert "commit centro"
e09de9b commit centro
09b2b87 Commit Bueno
a84478c Tarea-2
```
Elimina el último commit que modificaba el archivo README.md, pero manteniendo los cambios en el directorio de trabajo.
```
$ git reset --mixed 23601a6
```
Vuelve a mostrar los registros de commit para ver que el último commit ha desaparecido.
```
$ git log --oneline
23601a6 (HEAD -> main) añado mi nombre
e4436c8 Revert "commit centro"
e09de9b commit centro
09b2b87 Commit Bueno
a84478c Tarea-2
```
Vuelve a mostrar el estado de git para ver que los cambios están en el directorio de trabajo.
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        tarea2.md
```
Siguiente ejemplo de reset. Añade y haz commit con los cambios que están pendientes.
```
$ git add .

$ git commit -m "cambios pendientes"
[main 4883534] cambios pendientes
 1 file changed, 415 insertions(+)
 create mode 100644 tarea2.md
```
Muestra los registro de commit.
```
$ git log --oneline
4883534 (HEAD -> main) cambios pendientes
23601a6 añado mi nombre
e4436c8 Revert "commit centro"
e09de9b commit centro
09b2b87 Commit Bueno
a84478c Tarea-2
```
Elimina por segunda vez el último commit que modificaba el archivo README.md, pero manteniendo los cambios del staged.
```
$ git reset --soft 4883534
```
Vuelve a mostrar los registros de commit para ver que el último commit ha desaparecido.
```
$ git log --oneline
4883534 (HEAD -> main) cambios pendientes
23601a6 añado mi nombre
e4436c8 Revert "commit centro"
e09de9b commit centro
09b2b87 Commit Bueno
a84478c Tarea-2
```
Vuelve a mostrar el estado de git para ver que los cambios ahora están en el staged.
```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   tarea2.md
```
Último ejemplo de reset. Haz commit con los cambios que están pendientes.
```

```
