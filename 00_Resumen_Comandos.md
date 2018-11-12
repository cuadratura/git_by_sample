# Configurar Git

--------------------------------------------------------------------------

## COMANDOS

* Configurar **git**:

  * Añadir nombre del usuario, `git config --global user.name "<user-name>"`.
  * Añadir email del usuario, `git config --global user.email "<user-email>"`.

### Iniciar Proyectos

* Inicializar proyecto en local, `git init` o `git init <directory>`
* Inicializar proyecto en local (bare - No usa carpeta .git), `git init --bare` o `git init --bare <directory>`

### Repositorio en Servidor

* Clonar repositorio, `git clone <repository-location>`
* Cambiar origen repositorio, `git remote add origin <url-repo>`
* Hacer **pull** (Bajar repositorio), `git push -u origin master`
* Incluir repositorio remoto, `git remote add pg <url-repo>`
* Ver listado de repositorios remotos, `git remote` o `git remote -v` para ver la url de los proyectos copiados.

* Actualizar el repositorio a una versión distinta de la **origin**, `git fetch <remote-name>`.
* Hacer **push** (Subir repositorio), `git push <branch-remote-name> <branch-name>`.

> **NOTA**: Este comando solo funciona si se clonó de un repositorio remoto sobre el que se tienen permisos de escritura y si nadie más ha enviado datos por el medio. Si alguien más clona el mismo repositorio que nosotros y envía información antes que nosotros, el envío será rechazado.Nos tendremos que traer el trabajo y combinarlo con el nuestro antes de que podamos enviar datos al repositorio remoto, esto lo hemos visto con git pull.

### Seguimiento de Cambios | Staged

* Tackear archivos `git add <file-name-1> <file-name-2>`, o podemos usar de forma global `git add .`.
* Extraer archivos del **stage**, `git rm --cached <file-name-1> <file-name-2>`, o podemos usar de forma global `git rm --cached .`.
* Marcar cambios para commit:
  * Para añadir un archivo, `git add <file-to-add>`
  * Para eliminar un archivo, `git rm -f <file-to remove>`

### Commits

* Crear un nuevo `git commit -m "<message-commit>"`
* Añadir **Tag** a un commit, `git tag -a <tag-name> -m "<tag-message>"`.
* Añadir **Tag** LightWeight, `git tag <tag-lw-name>`.
* Mostrar **Tag** `git show <tag-name>`.
* Listar **Tags** por patrón `git tag -l "<patron>"`.
* Deshacer commit, `git commit --amend`

### Branch | Ramas

* Listar ramas `git branch`
* Crear nueva rama, `git branch  <new-branch-name>`.
* Cambiar de rama, `git checkout <new-branch-name>`.
* Crear una nueva rama y cambiar a ella, `git checkout -b <new-branch-name>` o `git checkout -b <new-branch-name> <existing-branch-name>`
* Eliminar una rama ya integrada, `git branch -d <branch-name>` (`-d` comprueba que la rama esté integrada)
* Eliminar una rama, `git branch -D <branch-name>` (`-D` no chequea que la rama estaba integrada y lo borra)

* Mostrar diferencias con el índice o con HEAD, `git diff` o `git diff HEAD`
* Mostrar diferencias con otras ramas, `git diff <branch-name>` o `git diff <branch-1-name> <branch-2-name>`

* Usar `gitk` para visualizar el historial de una rama, `gitk <branch-name>`
* Usar `gitk` para visualizar el historial de todas las ramas, `gitk --all`

* Ver histórico de ramas,
  * `git log`, muestra el histórico de nuestro proyecto desde el comienzo hasta el estado actual en el que se encuentra la cabecera.
  * `git log --oneline --decorate`, muestra el histórico de nuestro proyecto pero con la informacón mínima
  * `git log --oneline --decorate --graph --all`, mostrará además de lo que mostraba `git log --oneline --decorate` incluyendo un gráfico.
  * `git log -g`, muestra el histórico de nuestro proyecto global.

* Fusionar ramas, `git merge <branch-name-to-merge>`
* Deshacer merge, `git merge --abort`
* Rebase ramas, `git rebase <branch-name-to-rebase>`

### Extra

* Limpia los commits no asociados, `git gc` (Elimina los commits no asociados)

### Archivo Gitignore

De vez en cuando, hay archivos que no se quiere que Git registre en GitHub. Hay una forma de decirle a Git qué archivos ignorar.

Si se crea un archivo en el repositorio llamado [.gitignore](./.gitignore), Git lo utiliza para determinar qué archivos y directorios ignorar, antes de realizar un commit.

Se debe enviar un archivo .gitignore al repositorio remoto, para compartir las reglas de ignorar del archivo con cualquier otro usuario que clone el repositorio.