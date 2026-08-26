# Informe_Lab01:
## Resumen de lo aprendido:
En la ultima sesion de laboratorio se nos presento los primeros pasos o informacion basica acerca de el manejo de un repositorio a travez de la herramienta de git, para usar Github como un repositorio remoto y el Visual Studio Code como nuestro centro de trabajo, con el objetivo de poder gestionar el repositorio web desde uno remoto, tambien añadiendo extensiones que faciliten y vuelvan mas comodo el trabajo en este mismo como Markdown Preview Enchanched.
### Diferencia entre Git y GitHub:
Aunque, por sus nombres, puedan parecer lo mismo, en escencia Git es una herramienta de software que instalas en tu computadora, mientras que GitHub es una plataforma en la nube que aloja proyectos en línea(en este caso un repositorio).

* **GIT** -> `Sistema de control de versiones que permite registrar y recuperar cambios.`
* **GITHUB** -> `Plataforma para almacenar y compartir repositorios Git de forma remota.`

### Antes de empezar:
Debemos de darle a Git nuestro usuario y correo electronico, el cual debe ser el mismo que el de nustro github sobre todo para que los cambios que realicemos tengan registro de nuestra persona.
```bash
git config --global user.name "Nombre"
git config --global user.email "correo@example.com"
```
Tambien mencionar que es de mucha utilidad inicializar desde el primer momento el VS Code con nuestra cuenta de GitHub.
### Creación de un repositorio:
Para la creación de un repositorio local debemos empezar creando una carpeta en la que estara contenido este mismo y para que GitHub la acepte deberemos de crear por lo menos un archivo dentro de ella, en clase creamos un archivo de texto `README.md`
Una vez abierta la carpeta en el VS Code, debemos inicializar Git en la carpeta, esto creara un repositorio oculto de Git dentro de la carpeta, habilitando el control de versiones local.

```bash
git init
```
### Clonar un repositorio:
Si queremos trabajar con un repositorio ya existente para poder avanzar en conjunto o simplemente clonar uno publico, basta con copiar su URL, se puede hacer desde la terminal, asi como con un atajo de github.

```bash
git clone url_del_repositorio
```
### Flujo basico de trabajo:
```text
Modificar archivos
       ↓
   git status
       ↓
    git add .
       ↓
   git commit
       ↓
    git push
       ↓
     GitHub
```
Para descargar los cambios que hayan en el repositorio remoto actuals se usa el siguiente comando.
↓
```bash
git pull
```
Para poder ver cambios se usa el siguiente comando.
↓
```bash
git status
```
↓
Para poder agregar cambios se usa el siguiente comando.

```bash
git add .
```
↓
Para crear commits se usa el siguiente comando.

```bash
git commit -m "Descripción del cambio"
```
↓
Para subir nuestros cambios a GitHub se usa el siguiente comando.

```bash
git push
```
Cabe resaltar que existen atajos para estas acciones si es que no vemos necesario el uso de terminal.

### Uso de las ramas

Las ramas representan una línea de desarrollo independiente dentro del repositorio, es decir, funciona como un entorno de trabajo separado del código principal `main`, lo que permite realizar modificaciones de manera segura, sin comprometer todo el proyecto.

Crear y cambiar de rama

```bash
git switch -c feature/nombre
```

Ejemplos:

```text
feature/readme
feature/documentacion
feature/prototipo
```

Cambiar de rama

```bash
git switch main
```

Ver ramas

```bash
git branch
```
### Pull Request

Un Pull Request permite revisar los cambios antes de incorporarlos a `main`.

Flujo

```text
Crear rama
    ↓
Trabajar
    ↓
Commit
    ↓
Push
    ↓
Pull Request
    ↓
Revisión
    ↓
Merge
    ↓
main
```

### Markdown
Markdown es uno de los lenguajes de documentacion mas sencillos de usar, lo cual no lo hace malo, sino todo lo contrario, su simplicidad es lo que lo hace brillar, dando como resultado el uso de caracteres simples, para mostrar diversos formatos de presentacion visual; El uso de extensiones lo vuelve mejor, ya que nos brinda mas comodidad como con el Preview.
Títulos

```markdown
# Título principal
## Subtítulo
### Subtítulo secundario
```

Texto

```markdown
**Negrita**
*Cursiva*
```

Listas

```markdown
- Elemento 1
- Elemento 2
- Elemento 3
```

Lista numerada

```markdown
1. Primer elemento
2. Segundo elemento
3. Tercer elemento
```

Lista de tareas

```markdown
- [ ] Pendiente
- [x] Completado
```

Enlaces

```markdown
[GitHub](https://github.com)
```

Código corto:

```markdown
`git status`
```

Bloque:

````markdown
```bash
git status
git add .
git commit -m "Update"
git push
```
````
Tabla

```markdown
| Integrante | Rol | Estado |
|------------|-----|--------|
| Persona 1 | Diseño |  |
| Persona 2 | Código |  |
```
### Markdown Open Overview
Esta extension nos permite tener un vista previa de como se vera nuestro repositorio en github desde VS Code en tiempo real, lo cual es realmente provechoso, ya que nos ayuda a tener noción de como esta quedando visualmente el repositorio, evitandonos tener que modificarlo, ya subido al GitHub.
<img width="1457" height="887" alt="Captura de pantalla 2026-08-25 235256" src="https://github.com/user-attachments/assets/62a2f904-9e36-4ce5-9703-cbf0159ce746" />


### Comandos rápidos

| Acción | Comando |
|---|---|
| Ver estado | `git status` |
| Agregar todo | `git add .` |
| Commit | `git commit -m "mensaje"` |
| Subir cambios | `git push` |
| Descargar cambios | `git pull` |
| Clonar | `git clone URL` |
| Ver ramas | `git branch` |
| Crear rama | `git switch -c nombre` |
| Cambiar rama | `git switch nombre` |
| Ver historial | `git log --oneline` |
