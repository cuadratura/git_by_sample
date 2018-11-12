# EJERCICIO | Branch

## PRIMEROS PASOS

Para la realización de este ejercicio crearemos un nuevo proyecto vacío usando el comando de consola `git init`.

```bash
$ git init
Initialized empty Git repository in D:/sample_git/.git/
```

Creamos un primer archivo con contenido `echo hello world > readme.md`.

```bash
(master)$ echo hello world > readme.md
```

Visualizamos el estado del royecto `git status`, para ver que nos encontramos en la rama máster y se detecta un nuevo archivo creado no trackeado.

```bash
(master)$ git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.md
nothing added to commit but untracked files present (use "git add" to track)
```

Añadimos el archivo al sistema de tracking usando `git add readme.md`

```bash
(master)$ git add readme.md
warning: LF will be replaced by CRLF in readme.md.
The file will have its original line endings in your working directory.
```

Visualizamos el estado del proyecto `git status` para ver los cambios, y vemos que podemos hacer un commit con ese archivo trackeado, que no hay ya archivos sueltos sin trackear y que podemos eliminar el seguimiento (unstage) del archivo usando el comando `git rm --cached <file>`.

```bash
(master)$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   readme.md
```

Probamos que ocurre haciendo **unstage** del archivo seleccionado, `git rm --cached readme.md` para a continuación volver a comprobar el estado del proyecto.

```bash
(master) $ git rm --cached readme.md
rm 'readme.md'

(master) $ git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.md
nothing added to commit but untracked files present (use "git add" to track)
```

Añadimos el archivo nuevamente pero de forma global, es decir usando `git add .`, este comando añadirá al seguimiento de **git** a todos los archivos que hayan sufrido cambios (o hayan sido creados) desde el commit inicial.

> **NOTA** si el proyecto no tuvo ningún commit aún tomará como estado principal el proyecto vacío.

```bash
(master) $ git add .
warning: LF will be replaced by CRLF in readme.md.
The file will have its original line endings in your working directory.
```

Volvemos a ejecutar `git status`.

```bash
(master) $ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   readme.md
```

Consolidamos los cambios con un **commit**, `git commit -m "first commit"`.

```bash
(master) $ git commit -m "first commit"
[master (root-commit) 3b1a6ad] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 readme.md
```

Creamos un segundo archivo con contenido [second_file.md](./second_file.md), y lo trackeamos `git add .`.

```bash
(master) $ echo "second file" >> second_file.md
(master) $ git add .
warning: LF will be replaced by CRLF in second_file.md.
The file will have its original line endings in your working directory.
```

Si ahora volviesemos añadir contenidoa  dicho archivo `echo "more content" >> second_file.md`, y ejecutamos un `git status` veremos que el archivo se encuentra tanto en **staged** como no.

```bash
(master) $ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   second_file.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   second_file.md
```

**¿Por qué ocurre esto?** **Git** realiza capturas del estado de cada archivo cada vez que se **trackea** de forma que si posteriormente se modifica, esa variación no se recoge.

**¿Qué ocurriría si hicieramos un commit?** Se consolidaría en el commit la versión del archivo "fotografiada" cuando se hizo **tracked** sobre él.

```bash
(master) $ git commit -m "second commit"
[master 67635ae] second commit
 1 file changed, 1 insertion(+)
 create mode 100644 second_file.md

(master) $ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   second_file.md
no changes added to commit (use "git add" and/or "git commit -a")
```

## CREACIÓN DE UNA NUEVA BRANCH

Ahora crearemos una nueva branch a partir del último commit realizado.

Para crear la nueva rama usaremos el sigueinte comando `git checkout -b <new-branch-name>`.

```bash
(master) $ git checkout -b develop
Switched to a new branch 'develop'
M       second_file.md

(develop) $
```

> Veremos que se nos informa de que dentro de la segunda rama hay una modificación commutada, eso quiere decir que ahora mismo al encontrarse la cabecera del proyecto **HEAD** sobre la rama **develop** esa modificación de **trackearse** y **commitarse** se haría en **develop**.

Ahora ejecutaremos el comando `git log` para visualizar el histórico de cambios que ha sufrido nuestro proyecto hasta el momento actual.

```bash
$ git log
commit 67635ae44014a7e5dd1812864cbef37d56c64457 (HEAD -> develop, master)
Author: Hector Franco <hector.franco.aceituno@gmail.com>
Date:   Sun Nov 4 11:53:42 2018 +0100

    second commit

commit 3b1a6ad6f72cd577d50bc148e0621a15d7c4fbf7
Author: Hector Franco <hector.franco.aceituno@gmail.com>
Date:   Sun Nov 4 11:44:52 2018 +0100

    first commit
```

Creamos un nuevo archivo con contenido [third_file.md](./third_file.md), usando el comando `echo "third file" > third_file.md`, hacemos **staged** sobre ellos, `git add .` y un commit `git commit -m "third commit"`.

```bash
(develop) $ echo "third file" > third_file.md

(develop) $ git add .
warning: LF will be replaced by CRLF in second_file.md.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in third_file.md.
The file will have its original line endings in your working directory.

(develop) $ git commit -m "third commit"
[develop efeab2c] third commit
 2 files changed, 2 insertions(+)
 create mode 100644 third_file.md
```

Y hacemos `git status` y un posterior `git log --oneline --decorate --graph --all`.

```bash
(develop) $ git status
On branch develop
nothing to commit, working tree clean

(develop) $ git log --oneline --decorate --graph --all
* efeab2c (HEAD -> develop) third commit
* 67635ae (master) second commit
* 3b1a6ad first commit
```

Ahora cambiamos de **branch** y ejecutamos una modificación que commitearemos.

```bash
(develop) $ git checkout master
Switched to branch 'master'

(master) $ echo "changed second file" >> second_file.md

(master) $ git add .
warning: LF will be replaced by CRLF in second_file.md.
The file will have its original line endings in your working directory.

(master) $ git commit -m "new commit in master"
[master 5ed1079] new commit in master
 1 file changed, 1 insertion(+)
```

Si ahora ejecutamos el comando `git log --oneline --decorate --graph --all`, veremos como se nos dibja en terminal la estructura de ramas de nuestro proyecto.

```bash
(master) $ git log --oneline --decorate --graph --all
* 5ed1079 (HEAD -> master) new commit in master
| * efeab2c (develop) third commit
|/
* 67635ae second commit
* 3b1a6ad first commit
```

Ahora fusionamos las ramas **master** y **develop** con el comando `git merge <branch-name-to-merge>`.

```bash
$ git merge develop
Auto-merging second_file.md
CONFLICT (content): Merge conflict in second_file.md
Automatic merge failed; fix conflicts and then commit the result.
```` 

Se nos informa de la existencia de un conflicto, accedemos al archivo y vemos que ocurre.

Accedemos a visualizar el contenido del archivo que contiene conflictos usando el comando `cat second_file.md`.

```bash
(master|MERGING) $ cat second_file.md
second file
<<<<<<< HEAD
changed second file
=======
more content
>>>>>>> develop
```

Ahora deberíamos entrar dentro del archivo y asegurarnos de que los conflictos se resuelven correctamente.

Si efectuamos un `git status` veremos la siguiente información.

```bash
(master|MERGING) $ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)
Changes to be committed:
        new file:   third_file.md
Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   second_file.md
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .second_file.md.swp
```

Podremos deshacer el merge con el comando `git merge --abort`.