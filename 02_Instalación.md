# Instalación 

--------------------------------------------------------------------------

## INSTALACIÓN POR SO

### Linux

Para instalar **Git** en un **S.O.**  Linux (**Ubuntu**) deberemos primero actualizar como usuario administrador (o con permisos de administrador, `sudo su`), el **apt-get** `apt-get update`.

```bash
apt-get update
```

Posteriormente instalaremos **Git** mediante el comando 

```bash
apt-get install git-core
```

### Mac

Hay varias formas de instalar Git en un Mac. La más fácil es, probablemente, instalar las herramientas de línea de comandos de Xcode. En Mavericks (10.9) o superior se puede hacer esto simplemente tratando de ejecutar git desde la Terminal la primera vez.

`$ git --version`

Si no está instalado ya, se pedirá que se instale.

> **NOTA**: En **Windows** unicamente habrá que descargar el paquete de instalación y ejecutarlo.

Source: [https://git-scm.com/download/win](https://git-scm.com/download/win)

--------------------------------------------------------------------------

## CONFIGURACIÓN

[etc/gitconfig](./etc/gitconfig) : contiene los valores aplicados a cada usuario en el sistema y todos sus repositorios. Si se pasa la opción `--system` a `git config`, lee y escribe específicamente desde este archivo. (Debido a que este es un archivo de configuración del sistema, se necesitarían privilegios administrativos o de superusuario para realizar cambios en él).

[~/.gitconfig](~/.gitconfig) o [~/.config/git/config](~/.config/git/config): valores específicos para nosotros, el usuario. Se puede hacer que Git lea y escriba en este archivo específicamente al pasar la opción `--global`, y esto afecta a todos los repositorios con los que se trabaja en el sistema.

[~/.config](~/.config): en el directorio de Git (es decir, [.git/config](./.git/config)) del repositorio que se está utilizando actualmente: específico para ese único repositorio. Se puede obligar a Git a leer y escribir en este archivo con la opción `--local`, pero de hecho es el valor predeterminado. (Como era de esperar, se debe estar ubicado en algún lugar de un repositorio de Git para que esta opción funcione correctamente).

> **NOTA**: Cada nivel anula los valores en el nivel anterior, por lo que los valores en `.git/config` prevalecen sobre los de `/etc/gitconfig`.

--------------------------------------------------------------------------

## EJEMPLO 1 | Instalación

Para este ejercicio, una vez instalado **git** en el **s.o.**, ejecutaremos el comando `git config --global user.name <user-name>` y `git config --global user.email <user-email>` para definir el usuario y email que se usará para la **configuración global de git**.

Posteriormente ejecutaremos el comando `git config --list` para verificar la correcta configuración de la aplicación.

```bash
$ git config --list
core.symlinks=false
core.autocrlf=true
core.fscache=true
color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
help.format=html
rebase.autosquash=true
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
http.sslbackend=openssl
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
credential.helper=manager
user.email=name.lastname@gmail.com
user.name=Name Lastname
core.repositoryformatversion=0
```

Ejecutaremos `git help` para mostrar el **helper** de **git** con todas las opciones posibles de las que dispone la aplicación.

```bash
$ git help
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
```

A continuación podremos ver la ayuda del comando **config** de **git**, mediante el comando de consola `git help config`, el cual abrirá una página de ayuda.

```bash
$ git help config
```

Ahora crearemos una primera carpeta con el contenido de un proyecto estándar.