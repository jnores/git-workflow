# Introduccion a GIT

### Objetivo:
- Comprender los conceptos básicos de Git.
- Aprender a utilizar las funciones esenciales de Git para el control de versiones.

### Qué es git?

Git es un sistema de control de versiones distribuido que permite el seguimiento de cambios en el código fuente durante el desarrollo de software. Permite trabajar en colaboración de manera eficiente y mantener un historial completo de los cambios realizados.

Una ventaja de git es que nos permite crear un repositorio localmente. Es decir que no es obligatorio el uso de sitios como GitHub o Gitlab, entre otros, al menos para empezar.

### Por qué usar versionado?

Usar algún sistema de versionado adecuadamente nos ahorra tiempo y evita la perdida de información.

Además, nos brinda de trazabilidad en el código y simplificar el trabajo colaborativo sobre un mismo proyecto.

### Conceptos clave:

1. **Repositorio:**
   - Un repositorio es un espacio donde se almacena y gestiona el código fuente y su historial de cambios.

2. **Commit:**
   - Un commit es un conjunto de cambios que se realizan en el código. Cada commit tiene un mensaje descriptivo que explica los cambios realizados.
   - Estos cambios deberían estar relacionados a una tarea en específico, y ser puntualizados.

3. **Branch (Rama):**
   - Una rama es una línea de desarrollo independiente. Puedes trabajar en una rama sin afectar el código en otras ramas.

4. **Merge (Combinar):**
   - Combinar dos ramas para incorporar los cambios de una rama en otra.

### Comandos básicos:

1. **`git init`:**
   - Inicia un nuevo repositorio Git en el directorio actual.

2. **`git clone <URL>`:**
   - Clona un repositorio remoto en tu máquina local.

3. **`git add <archivo>`:**
   - Añade cambios al área de preparación para ser incluidos en el próximo commit.

4. **`git commit -m "mensaje"`:**
   - Realiza un commit con un mensaje descriptivo.

5. **`git push`:**
   - Sube los cambios locales al repositorio remoto.

6. **`git pull`:**
   - Obtiene cambios del repositorio remoto y los fusiona con tu rama actual.

7. **`git branch`:**
   - Muestra las ramas disponibles y destaca la rama actual.

8. **`git merge <nombre_rama>`:**
   - Combina los cambios de una rama en la rama actual.

### Flujo de trabajo básico/individual:

1. **Crear un Repositorio:**
   - `git init` para iniciar un nuevo repositorio o `git clone <URL>` para clonar uno existente.

2. **Hacer Cambios:**
   - Modificar archivos en el repositorio.

3. **Realizar Commit:**
   - `git add <archivo>` para añadir cambios y `git commit -m "mensaje"` para realizar un commit.

4. **Subir Cambios:**
   - `git push` para enviar los cambios al repositorio remoto, en caso de haber iniciado con un clone de algun repositorio remoto.

5. **Trabajar con Ramas:**
   - `git branch` para ver las ramas y `git checkout -b <nombre_rama>` para crear y cambiar a una nueva rama.

6. **Combinar Cambios:**
   - `git merge <nombre_rama>` para combinar los cambios de una rama en otra.

### Recursos adicionales:

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)

### A Continuación

ver ej1.md

continuar con BRANCH_STRATEGY.md