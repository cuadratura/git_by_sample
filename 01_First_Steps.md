# Introducción a Git

**¿Qué debería tener un buen sistema de copias de seguridad para el código?**

* Ser facil de usar.
* Ser intuitiva para nuevos usuarios.
* Integrarse con nuestras herramientas.
* Ser fiable.

--------------------------------------------------------------------------

## SISTEMA DE CONTROL DE VERSIONES

**¿Qué es un Sistema de Control de Versiones Local?** Se desarrolló un **sistema de control de versiones** que contenía una simple base de datos en la que se llevaba registro de todos los cambios realizados sobre los archivos.

**¿Qué pasa si somos varios en el equipo? ...**

**¿Qué es un Sistema de Control de Versiones Centralizado?** Se caracterizan por tener un único servidor que contiene todos los archivos versionados, y varios clientes que descargan los archivos desde ese lugar central, descargando unicamente la última versión.

**¿Que pasa si se cae el servidor? ...**

**¿Qué es un Sistema de Control de Versiones Distribuido?** Los clientes no sólo descargan la última instantánea de los archivos: replican completamente el repositorio.

--------------------------------------------------------------------------

## ¿QUÉ ES GIT? Es uno de los sistemas de Control de Versiones

**¿Diferencia entre Git y Otros Sistemas de Control de Versiones?**

La mayoría de los otros sistemas guardan la información como una **lista de cambios ​​en los archivos**.

Git piensa en sus datos más como una secuencia de copias instantáneas, no copia los archivos que no cambian (los referencia) y **almacena las variaciones de los archivos** (En [.git/](./.git/) almacena los cambios y los metadatos del repositorio).

### GIT GUARDA INSTANTÁNEAS DE LOS ARCHIVOS QUE CAMBIARON MIENTRAS QUE EL RESTO UN REGISTRO DE CAMBIOS**

--------------------------------------------------------------------------

## QUE ES GITHUB

* **GitHub** es una plataforma dedicada a guardar nuestro código basado en Git.
* **GitHub** es una plataforma que aloja repositorios de ciertos proyectos, bundles, componentes en algunos lenguajes.
* **GitHub** es una red social profesional.

### Crear cuenta de Github

Para ello accedermos a [https://github.com](https://github.com).

* **GitHub** dispone de versión gratuita y de pago, además de personal y/o organización.

### GitHub Pro (Pago)

Una alternativa para tener proyectos con acceso privado existen clientes de Git como **Bitbucket** que permite hasta grupos de 5 usuarios y repositorios privados de forma gratuita.

Además **GitHub** dispone de planes para estudiantes (_Student Development Pack_) bastante asequibles e incluso gratuito.

--------------------------------------------------------------------------

## QUE DIFERENCIA EXISTE ENTRE GIT Y GITHUB

* **Git** es una herramienta de la **línea de commandos**, **Git** no necesita de **GitHub**.
* **GitHub** es una plataforma

> **NOTA**: Git dispone también de herramientas gráficas tales como **SourceTree**, **GitKraken**, **GitHub Desktop**, **GitLab**, ...

**¿Qué son los repositorios?** Un repositorio es un lugar donde se almacenan todos los archivos de un proyecto en particular. Cada proyecto tiene su propio repositorio, y se puede acceder a él con una URL única.

**¿Qué significa hacer Forking de un repo?** **"Forking"** es cuando se crea un nuevo proyecto basado en otro proyecto que ya existe. Esta es una característica sorprendente que fomenta enormemente el desarrollo posterior de programas y otros proyectos. Si se encuentra un proyecto en GitHub al que nos gustaría contribuir, podemos hacer forking del repositorio, hacer los cambios que deseemos y lanzar el proyecto revisado como un nuevo repositorio. Si el repositorio original del que se ha hecho forking para crear el nuevo proyecto se actualiza, se puede agregar fácilmente esas actualizaciones al fork actual.

**¿Qué es hacer Pull Request?** Hemos hecho **fork** de un **repositorio**, realizado una gran revisión del proyecto y deseamos que los desarrolladores originales lo reconozcan. Se puede hacer creando una **pull requests**. Los autores del repositorio original pueden ver el trabajo y luego elegir si lo aceptan o no en el proyecto oficial. Cada vez que se emite una **pull requests**, GitHub proporciona un medio perfecto para que nosotros y el autor del proyecto principal se comuniquen.

**¿Qué es el Social Networking?** El aspecto de **red social** de GitHub es probablemente su característica más poderosa, permitiendo que los proyectos crezcan más que cualquier otra característica ofrecida. Cada usuario en GitHub tiene su propio perfil que actúa como un currículum, mostrando su trabajo anterior y contribuciones a otros proyectos a través de **pull requests**.

Las revisiones de proyectos se pueden discutir públicamente, por lo que una gran cantidad de expertos puede aportar conocimiento y colaborar para avanzar un proyecto.

**¿Qué son los ChangeLogs?** Cuando varias personas colaboran en un proyecto, es difícil hacer un seguimiento de las revisiones: quién cambió qué, cuándo y dónde se almacenan esos archivos. GitHub se ocupa de este problema haciendo un seguimiento de todos los cambios que se han enviado al repositorio. **¿Quién hizo qué?**

**¿Qué son los Issues?** Son sistemas que ponen las plataformas de almacenaje para gestionar tareas. Alternativamente las versiones oficiales de código libre lo usa para que la comunidad se implique y planteé soluciones.

**¿Qué es un Branch?** Dentro de nuestro proyecto gestionado por un **Sistema de Control de Versiones** podemos ver el histórico de cambios como si de un árbol se tratase. De esta forma podemos ir abriendo ramas que parten bien de la rama principal (master) o de otra rama (branch).
