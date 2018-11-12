#### Conceptos Básicos

* **repositorio**: colección de referencias junto con una base de datos de objetos tiene todos los objetos que son alcanzables desde dichas referencias:

    * Puede contener además algunos meta datos adicionales usados por determinas órdenes de git.
    * Puede contener una copia de trabajo de una revisión.

* **repositorio desnudo** (bare): repositorio que no tiene una copia de trabajo.

    * Los de control de git que normalmente estarían presentes en el subdirectorio oculto [.git](./.git) están presentes en el propio directorio del repositorio.

* **árbol de trabajo o copia de trabajo**: Una revisión extraida del repositorio, para poder trabajar con ella.

* **índice**: una colección de ficheros con información de stat(2), cuyos contenidos están almacenados como objetos.
    * El índice es una versión almacenada del árbol de trabajo.

* **rama**: línea activa de desarrollo.
    * El commit más reciente de una rama se denomina la punta de dicha rama. La punta de la rama se referencia por medio de una cabeza.
    * La copia de trabajo está siempre asociada a una rama (la rama "actual" o "checked out") y la cabeza especial “HEAD” apunta a esa rama.

* **cabeza**: una referencia con nombre, que apunta al objeto commit de la punta de una rama.
    * Las cabezas se almacenan en $GIT_DIR/refs/heads/, (salvo que se usen referencias empaquetadas).

* **checkout**: acción de actualizar parte o todo el árbol de trabajo con un objeto árbol o blob desde la base de datos de objeto Además actualiza el índice y la referencia HEAD si se ha cambiado de rama.

* **merge**: fusionar los contenidos de otra rama (potencialmente desde un repositorio externo) en la rama actual.
    * Si la rama es de otro repositorio, primero se hace un fetch* de la rama y después se fusiona en la rama actual.
    * La fusión puede crear un nuevo objeto commit si una de las ramas no es un ancestro de la otra.
    * Si una es ancestro de la otra, simplemente se mueve la referencia de la cabeza de la rama fusionada (fast-forward merge).

--------------------------------------------------------------------------

### Comandos Git

--------------------------------------------------------------------------


#### Clone

Obtener una copia local completa de un repositorio git remoto

> **NOTA**: las cabezas de las ramas remotas son inamovibles

```bash
git clone git://git.moodle.org/moodle.git
git clone ssh://iarenaza@git.moodle.org/moodle.git
git clone http://git.moodle.org/moodle.git
git clone git@github.com:iarenaza/moodle.git
git clone /ruta/a/moodle.git /ruta/a/otro-moodle.git
git clone -o moodle.git git@github.com:iarenaza/moodle.git
```

#### Fetch

Obtener la cabeza de una rama (o varias) desde un repositorio remoto, copiando los objetos falten y moviendo la(s) cabeza(s) remota(s).

* Incorporar nueva rama del repositorio remoto al repositorio local:

```bash
git fetch <repository-name>
git branch <branch-name> \ <repository-name>/<branch-name>
``` 

#### Pull

Hacer un fetch seguido de un merge, con una rama remota dada.

#### Push

Enviar los objetos de la rama local que no están en la rama remota a la que hace referencia el pull, y actualizar la cabeza de la rama remota.

* Es la acción complementaria de pull.
* Si la cabeza de la rama remota no es un ancestro de la cabeza de la rama local, el push falla*.

* Enviar ramas locales al repositorio remoto:

```bash
git push <branch-name> <branch-name>
git push <branch-name> +<branch-name>
```