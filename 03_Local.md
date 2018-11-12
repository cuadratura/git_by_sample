# Trabajando en Local

--------------------------------------------------------------------------

## INICIALIZAR UN REPOSITORIO

Para inicializar un repositorio nuevo que aún no disponga de un **sistema de control de versiones** que inspeccione su estado ejecutaremos el comando `git init`.

```bash
$ git init
Initialized empty Git repository in d:/git_by_sample/.git/
```

Veremos que se ha creado una carpeta llamada [.git/](./.git/).

Posteriormente podremos ejecutar el comando `git status` para observar el estado del proyecto.

```bash
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Ahora incluiremos contenido dentro de nuestro proyecto. ([CONTRIBUTING.md](./CONTRIBUTING.md))

Y ejecutamos el comando `git add .` para incluirlo dentro de los archivos con seguimiento (**tracked**), ahora podremos volver a ejecutar `git status` para ver el estado del repositorio.

```bash
$ git add .

$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html
```

Si ejecutamos el comando `git commit -m "first commit"` crearemos nuestro primer commit  llamado **first commit**.  

```bash
$ git commit -m "first commit"
[master (root-commit) b030bf2] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```

Finalmente volveremos a chequear el estado del repositorio usando nuevamnete `git status`.

```bash
$ git status
On branch master
nothing to commit, working tree clean
```

Si agregamos un nuevo archivo [README.md] dentro del proyecto y se ejecuta `git status` veremos veremos el siguiente mensaje:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README

nothing added to commit but untracked files present (use "git add" to track)
```

> **NOTA**: **Untracked files** implica que hay ciertos archivos listados que no disponen de un seguimiento por parte de **git**.

Para incluir el archivo creado al sistema de rastreo de **git** usaremos el comando `git add <file-name>`, `git add README.md`

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
```

Si modificamos el archivo creado inicialmente y ejecutamos `git status`veremos el siguiente mensaje:

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

La sección llamada **Changes not staged for commit** del mensaje anterior nos indica que archivo fue modificado pero no está listo para subirse al siguiente **commit**.

Ahora añadimos este archivo al sistema de **tracked** de **git** mediante el comando `git add CONTRIBUTING.md` y ejecutamos el comando `git status` para ver el siguiente mensaje.

```bash
$ git add CONTRIBUTING.md
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
    modified:   CONTRIBUTING.md
```

Volvemos a modificar el archivo [CONTRIBUTING.md](./CONTRIBUTING.md) que acabamos de añadir al seguimiento de **git** y ejecutamos `git status`.

```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
    modified:   CONTRIBUTING.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```` 

El mismo archivo aparece listo para ser comiteado y no a la misma vez, si ejecutamos `git commit -m "second commit"` y posteriormente `git status`. Veremos que sólo se hizo commit del primer tracked realizado sobre ese archivo.

> **NOTA**: **Git** sólo hace commit de los archivos indicados justo en el momento que se designa ese seguimiento, de forma que si posteriomente se modifica el contenido del archivo esa modificación no se consolidará en el commit realizado.

Ahora podemos usar el comando `git diff`para visualizar los cambios realizados con respecto al último estado consiolidado `commit`.

```bash
$ git diff
diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
index 536c005..76e8508 100644
--- a/CONTRIBUTING.md
+++ b/CONTRIBUTING.md
@@ -1 +1,3 @@
-Primer test de git
\ No newline at end of file
+Primer test de git
+
+Segundo test en el primer archivo
\ No newline at end of file
```

> **NOTA**: Para ver que está listo para ser commiteado utilizaremos el comando `git diff --staged` o `git diff --cached`

## USO DE TAGS

*Git** tiene la posibilidad de marcar ciertos commits como importantes usando **tags**.

Para incluir un tag en un determinado commit ejecutaremos el comando `git tag -a <tag-name> -m "<tag-message>"` mientras nos encontremos trabajando en dicho commit.

> **NOTA**: De no usar el atributo `-m` seguido del mensaje al comando se nos preguntará directamente mediante el editor de código usado por defecto en la configuración de **git**.

```bash
$ git tag -a v0.1 -m "first tag"
```

Ahora para ver los tags empleados durante nuestro proyecto ejecutaremos `git tag`.

```bash
$ git tag
v0.1
```

Para ver toda la información contenida dentro de un tag usaremos `git show <tag-name>`

```bash
$ git show v0.1
tag v0.1
Tagger: Hector Franco <hector.franco.aceituno@gmail.com>
Date:   Sat Nov 3 15:45:49 2018 +0100

first tag

commit db69801bc7cc72bc1c554c3ab01ee0997ce808d4 (HEAD -> master, tag: v0.1)
Author: Hector Franco <hector.franco.aceituno@gmail.com>
Date:   Sat Nov 3 14:26:26 2018 +0100

    first commit

diff --git a/CONTRIBUTING.md b/CONTRIBUTING.md
new file mode 100644
index 0000000..536c005
--- /dev/null
+++ b/CONTRIBUTING.md
@@ -0,0 +1 @@
+Primer test de git
```

Se puede usar el comando `git tag -l "<patron>"` para mostrar un listado de tags utilizads que mantenagan cierto patrón en su nombre.

Usaremos el comando `git tag` para listar todos los tags existentes en el repositorio.

## USO DE TAGS LIGHTWEIGHT

Es un tag que guarda menos información dentro de la base de datos de **git**, para crear una nueva **tag** del tipo **Lightweight** usaremos el comando `git tag <tag-lw-name>`.

Al mostrar la nueva etiqueta **lightweight** veremos que muestra la informacó básica del commit.

```bash
$ git show v1.4-lw
commit ca82a6dff817ec66f44342007202690a93763949
Author: Raul Gimeno <raul@imaginagroup.com>
Date:   Mon Mar 17 21:52:11 2018 -0700

    changed the version number
```

--------------------------------------------------------------------------

## VER HISTORIAL DE COMMITS

Para ver el hsitorial de commits de un proyecto usaremos el comando de consola `git log`

```bash
$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Raul Gimeno <raul@imaginagroup.com>
Date:   Mon Mar 17 21:52:11 2018 -0700

    cambiar el numero de version

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Raul Gimeno <raul@imaginagroup.com>
Date:   Sat Mar 15 16:40:33 2018 -0700

    eliminar pruebas innecesarias

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Raul Gimeno <raul@imaginagroup.com>
Date:   Sat Mar 15 10:31:28 2018 -0700

    Primer commit
```

Si añadimos el atributo `-p` o `--patch` al comando `git log` se nos mostrará la diferencia entre los commits realizados, como por ejemplo `git log -p`.

Para limitar el número máximo de commits a mostrar usaremos el atributo `-2`, como por ejemplo `git log -2`.

```bash
$ git log -p -2
commit ca82a6dff817ec66f44342007202690a93763949
Author: Raul gimeno <rauln@imaginagroup.com>
Date:   Mon Mar 17 21:52:11 2018 -0700

    cambiar el numero de version

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
 spec = Gem::Specification.new do |s|
     s.platform  =   Gem::Platform::RUBY
     s.name      =   "simplegit"
-    s.version   =   "0.1.0"
+    s.version   =   "0.1.1"
     s.author    =   "Scott Chacon"
     s.email     =   "schacon@gee-mail.com"
     s.summary   =   "A simple gem for using Git in Ruby code."

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Raul gimeno <rauln@imaginagroup.com>
Date:   Sat Mar 15 16:40:33 2018 -0700

    eliminar pruebas innecesarias

diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index a0a60ae..47c6340 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -18,8 +18,3 @@ class SimpleGit
     end

 end
-
-if $0 == __FILE__
-  git = SimpleGit.new
-  puts git.show
-end
```

--------------------------------------------------------------------------

## DESHACER COMMIT

Para deshacer un commit una vez sobre ese commit usaremos el comando `git commit --amend`.

Probar antes de hacer cambios y **trackearlos** y luego después de **trakear nuevos cambios**.

```bash
$ git commit -m 'primer commit'
$ git add archivo_olvidado
$ git commit --amend
```

--------------------------------------------------------------------------

## BRANCHES

**¿Qué es un Branch?** Dentro de nuestro proyecto gestionado por un **Sistema de Control de Versiones** podemos ver el histórico de cambios como si de un árbol se tratase. De esta forma podemos ir abriendo ramas que parten bien de la rama principal (master) o de otra rama (branch).

La principal utilidad que tienen los **branch** es la de organizar nuestro tabajo, por ejemplo:

* Para **desarrollar una nueva funcionalidad** sin afectar al master mientras lo hacemos.
* Para hacer un **hotfix** (o **parche**) en una versión que ya ha salido a producción.
* Para hacer un **branch** de **producción**, otro de **pre**, otro de **testing**, … y así ir promoviendo los cambios de uno a otro.

**La rama por defecto en un proyecto es la rama MASTER**

### Crear una rama nueva

Para crear una nueva rama ejecutaremos el comando de consola `git branch <new-branch-name>`.

**¿Cómo sabe Git en que rama nos encontramso en cada momento?** Para ubicarse **git** en la rama actual en uso utiliza un puntero llamado **HEAD**

Se puede ver esto fácilmente ejecutando el comando `git log` que muestra hacia dónde apuntan los punteros de cada rama. La opción del comando es `--decorate`.

```bash
$ git log --oneline --decorate
f30ab (HEAD -> master, testing) add feature #32 - ability toadd new formats to the central interface
34ac2 Fixed bug #1328 - stack overflow under certain conditions
98ca9 The initial commit of my project
```

### Checkout | Cambiar de rama

**checkout**: acción de actualizar parte o todo el árbol de trabajo con un objeto árbol o blob desde la base de datos de objeto Además actualiza el índice y la referencia HEAD si se ha cambiado de rama.

Para cambiar a una rama existente, hay que ejecutar el comando `git checkout <branch-name>`. Este comando moverá el **puntero HEAD** a otra rama.

```bash
$ git checkout testing
```

> **NOTA**: Podemos crear una nueva rama y cambiarnos a ella directamente con el comando `git checkout -b <new-branch-name>`, además podemos crear una nueva rama desde otra en la que no estemos y cambiar el puntero a la nueva mediante el comando `git checkout -b <new-branch-name> <old-branch-name>`.

Ahora hacemos unos nuevos commits en esta rama.

### Merge | Fusionar Ramas

**merge**: fusionar los contenidos de otra rama (potencialmente desde un repositorio externo) en la rama actual.
    * Si la rama es de otro repositorio, primero se hace un fetch* de la rama y después se fusiona en la rama actual.
    * La fusión puede crear un nuevo objeto commit si una de las ramas no es un ancestro de la otra.
    * Si una es ancestro de la otra, simplemente se mueve la referencia de la cabeza de la rama fusionada (fast-forward merge).

Una vez creadas dos ramas, puede darse el caso de que queramos fusionarlas de alguna manera, para ello usaremos el comando `git merge <branch-to-merge>`.

```bash
$ git merge develop
Auto-merging second_file.md
CONFLICT (content): Merge conflict in second_file.md
Automatic merge failed; fix conflicts and then commit the result.
```

Ahora se podrán plantear dos escenarios posibles, que se hayan producido **conflictos** o no.

En el caso anterior podemos ver que si se produjeron conflictos, para solucionarlo será necesario acceder dentro del archivo:

```bash
(master|MERGING) $ cat second_file.md
second file
<<<<<<< HEAD
changed second file
=======
more content
>>>>>>> develop
```

Y realizar los cambios pertinentes.

### Rebase de Ramas

Una alternativa al **merge** de ramas, consiste en realizar un rebase entre ramas, es decir pasar los cambios realizados de una rama a otra sin fusionarlas. Para ello, ejecutaremos el comando de consola, `git rebase <branch-name-to-rebase>`.

> **NOTA**: Este sistema genera un trabajo más limpio y claro, ya que evita la mezcla de ramas lo cual puede en trabajas de gran calibre llevar a confusión y desorden.

### Hacer Stash

Imaginemos la siguiente situación, trabajamos en unos cambios en una rama y necesitamos urgentemente pasar a otra rama para corregir un **bug** pero no queremos hacer commit ni perder el trabajo avanzado. **¿Cómo solucionamos el problema?**

Almacenaremos dichos cambios provisionales en un **stash** que pdoremos recuperar en un momento dado, ya sea en la rama que inicialmente se generaron o en otra distinta.

Para almacenar esos cambios temporalmente usaremos el comando `git stash` o `git stash save`.

Podremos listar los stash guardados mediante el comando `git stash list`.

Para volver a recuperar el stash en una rama, cambiaremos el **HEAD** del proyecto a dicha rama `git checkout <branch-name>` y usamos el comando `git stash apply --index`.

### Cherry Pick

Permite incluir en una rama en concreto en la que nos encontremos un commit realizado en otra, para ello usaremos el comando `git cherry-pick <commit-id>`.

