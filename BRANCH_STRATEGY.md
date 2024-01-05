
# Estrategia de Ramificación y colaboración

### Ramificación:

Como primer medida se puede usar el branch **`main`** siempre que el proyecto sea chico. A medida que crece el proyecto, la estrategia de ramificacion se vuelve mas compleja.

Una buena práctica para proyectos chicos a medianos es el tener un branch para desarrollo que podría llamarse: **`dev`**, **`devel`**, **`develop`**, etc.

De este modo se reserva el branch **`main`**  para las distintas versiones funcionales que estan en condiciones de ser publicadas/instaladas/presentadas.

Dependiendo del tipo de proyecto puede ser necesario tener un branch extra, **`demo`**, para preparar las demos del sistema cuando aún no está terminado.
```
my-super-proyect

main ----------V1--------v2-----------
 \           /merge      / merge
  dev -C1-C2--C3--C4--C5---C6--C7--C8-
```

### Ramificación Avanzada:

En caso de que el proyecto sea muy complejo, con muchas funcionalidades desarrollandose en simultaneo, es recomendable que se cree un branch particular para cada funcionalidad en especifico y cuando estas están implementadas se mergeen en la ramma dev.

Esto tambien es útil para cuando hay muchos colaboradores en el proyecto, que cada uno trabaja en una rama diferente, hija de la rama dev.

Sin embargo, si no se está muy familiarizado con el trabajo en branchs y no son muchos colaboraores en el proyecto, es recomendable que trabajen directamente sobre la rama dev.

> **NOTA:**
> muchas personas trabajando en un mismo branch roducirá eventualmente conflictos al bajar los cambios  porque 

> **NOTA:**
> Esta es una estrategia de branchs para un proyecto de chico a mediano.
> Para los proyectos grandes, aparecen otras ramas como 
> - QA, 
> - integration y 
> - cada versión se prepara en una rama independiente.

### Buenas prácticas

Si trabajamos localmente con git, no hay mucho que hacer, solo recordar hacer un commit cada vez que terminamos una tarea.

Por otro lado, la principal ventaja de usar git es poder tener un repositorio comun donde varios desarrolladores puedan contribuir. En este escenario se debe:

1. **Hacer PULL y PUSH periodicamente**
   - Esto permitirá tener las version más actualizada del proyecto en el repositorio para que todos puedan accederla.
   - Se recomienda hacer un PULL/PUSH o más por día

2. **Usar mensajes cortos y declarativos**
   - Los mensajes de cada commit debe ser corto y declarativo de lo que se hizo.

3. **No romper la integridad del proyecto**
   - Todo push que se haga al repositorio debe ser funcional, es decir que no debe romper nada de lo que ya está funcionando.
   - Para controlar esto existen sistemas de integración continua (CI) que prueban nuestro proyecto en cada push y nos avisan si está funcionando correctamente o no. Nosotros debemos programar las pruebas para que el sistema de CI determine si funciona o no.


### Corrección de conflictos:

Cuando hay 2 o mas personas empiezan a trabajando en una misma rama y modifican el mismo archivo, el primero que pushee no tendrá problemas pero el segundo no podrá pushear. Al hacer un PULL para bajar la ultima versión, se notificará de un conflicto a resolver en este archivo que tienen en común con cambios.

Pra resolver este conflicto debemos:

1. **Corregir el archivo**
   - para cada archivo con conflictos debemos abrir uno por uno buscando las secciones con conflicto.
   ```
   <<<<<<< HEAD // lo que tenemos localmente
   this is some content to mess with
   content to append
   =======
   totally different content to merge later
   >>>>>>> // lo que viene de afuera
   ```
   Para corregirlo debemos dejar solo lo necesario, es un merge manual.

2. **rastrear el archivo corregido**
   - se hace un `git add {archivo corregido}` para informar a git que ya se resolvieron los conflictos.
   - Se debe repetir para cada archivo con conflictos que corrijamos.

3. **commit del merge**
   - Despues de hacer el add, se debe hacer un commit del merge, `git commit -m'merge commit'`

4. **PUSH**
   - Por último, ya podemos hacer el push de nuestro trabajo con `git push origin {branch}`

### problemas basicos:

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

### Git Stash:

En ocaciones tenemos cambios que no queremos commitear y que nos generan conflictos al querer hacer un PULL. Estos pueden ser cambios para hacer pruebas locales o cambios de configuración entre otros.

Para poder bajar la ultima version sin perder nuestros cambios tenemos 2 opciones:

1. **manual**
   - hacemos una copia de los archivos que modificamos en otra carpeta, hacer un revert/reset de todos los archivos modificados Para luego hacer un pull y volver a aplicar los cambios.
2. **usar Git stash**
   - se guardan temporalmente los archivos modificados en en un area especial de git y se hace un reset del proyecto automáticamente. Cuando usas `git stash`, los cambios en tu directorio de trabajo se guardan en un área especial de Git llamada "stash". El stash actúa como una especie de estantería (shelf) temporal donde puedes guardar tus cambios mientras trabajas en otra tarea.

### Algunos comandos relacionados con `git stash`:

1. **`git stash save "mensaje"`:**
   - Guarda los cambios en el stash con un mensaje descriptivo.

2. **`git stash list`:**
   - Muestra la lista de todos los stashes disponibles.

3. **`git stash apply`:**
   - Aplica el último stash a tu directorio de trabajo sin eliminarlo del stash.

4. **`git stash apply stash@{n}`:**
   - Aplica un stash específico (identificado por su índice n) a tu directorio de trabajo.

5. **`git stash pop`:**
   - Aplica el último stash y lo elimina de la lista de stashes.

6. **`git stash drop`:**
   - Elimina el último stash.

7. **`git stash drop stash@{n}`:**
   - Elimina un stash específico.

8. **`git stash clear`:**
   - Elimina todos los stashes.

La utilización de `git stash` es útil cuando necesitas cambiar de rama, pero tienes cambios sin commitear en tu rama actual. También es útil cuando deseas realizar cambios rápidos en otra parte del código sin realizar un commit temporal.

Por ejemplo, si estás trabajando en una característica en tu rama actual y necesitas corregir un error crítico en la rama principal, puedes usar `git stash` para guardar tus cambios temporales, cambiar a la rama principal, hacer la corrección y luego regresar a tu rama de trabajo actual y aplicar los cambios almacenados en el stash.

### A Continuación

ver ej2.md