# LABORATORIO 1: REPOSITORIO EN GITHUB

## Índice
- [1. Git y GitHub](#1-git-y-github)
- [2. Arquitecturas de estados en Git](#2-arquitecturas-de-estados-en-git)
- [3. Flujo básico y comandos](#3-flujo-básico-y-comandos)
- [4. Ramas](#4-ramas)
- [5. Markdown](#5-markdown)
- [6. Estructura del proyecto](#6-estructura-del-proyecto)
- [7. Flujo recomendado del equipo](#7-flujo-recomendado-del-equipo)
- [8. Comandos rápidos](#8-comandos-rápidos)
- [9. Integración de Visual Studio Code con Git y GitHub](#9-integración-de-visual-studio-code-con-git-y-github)
---

# 1. Git y GitHub
Para gestionar proyectos de desarrollo y documentación técnica, es fundamental diferenciar Git y Github, dos herramientas complementarias pero con funciones distintas 

## 🛠️ Git
Sistema de control de versiones que permite registrar y recuperar cambios. Se ejecuta de manera local en el equipo del desarrollador y se encarga de administrar el historial de modificaciones de los archivos del proyecto.

**Funciones principales:**
* **Registro de cambios:** Guarda instantáneas (*commits*) del proyecto a lo largo del tiempo, permitiendo auditar qué se modificó, cuándo y por quién.
* **Gestión de ramas (*Branching*):** Permite aislar ideas, probar funcionalidades o corregir errores en líneas de desarrollo paralelas sin alterar la versión principal.
* **Fusión (*Merging*):** Integra de forma estructurada los cambios generados en distintas ramas de trabajo.
* **Reversión de estado:** Permite regresar el proyecto a cualquier punto previo del historial en caso de fallos.
* **Trabajo sin conexión (*Offline*):** Funciona al 100% en el almacenamiento local sin depender de acceso a Internet.

## ☁️ GitHub
Plataforma para almacenar y compartir repositorios Git de forma remota. Ofrece una interfaz gráfica y servicios adicionales diseñados para alojar proyectos en la red y facilitar la colaboración entre equipos de trabajo

**Funciones principales:**
* **Repositorios remotos:** Mantiene una copia centralizada del proyecto disponible en la red para que cualquier colaborador pueda sincronizar sus cambios.
* **Revisión de código (*Pull Requests*):** Permite proponer cambios, comentarlos, revisarlos en equipo y aprobarlos antes de fusionarlos a la rama principal.
* **Gestión de proyectos:** Proporciona herramientas de organización como seguimiento de errores (*Issues*), tableros visuales tipo Kanban y cronogramas.
* **Flujos de automatización:** Integra pruebas automáticas e integración continua a través de herramientas como *GitHub Actions*.
* **Control de accesos:** Administra permisos de lectura, escritura y roles de seguridad para los integrantes del equipo.

**En resumen:**
```text
Git → trabajo local
GitHub → repositorio remoto
```

---

# 2. Arquitecturas de ESTADOS en Git
El motor de Git organiza el ciclo de vida de los archivos atravesando cuatro entornos diferenciados:

![alt text](image.png)

1. **Directorio de Trabajo (Woring Directoy):** Espacio local donde se crean, editan o eliminan archivos físicamente.
2. **Área de Preparación (Staging Area/Index):** Zona intermedia donde se agrupan únicamente las modificaciones que formarán parte del próximo registro.
3. **Repositorio Local (Local Repository):** Base de datos almacenada en la carpeta oculta .git de tu computadora, conteniendo el historial completo de commits.
4. **Repositorio Remoto (Remote Repository):** Copia del proyecto alojada en la nube (GitHub) accesible para el equipo.

# 3. Flujo básico y Comandos
El flujo fundamental de trabajo en Git está diseñado para gestionar, registrar y sincronizar de manera ordenada los cambios realizados en el proyecto:

* **`git status`**: Muestra el estado actual de los archivos dentro del repositorio. Identifica qué elementos se han editado, cuáles están listos en el área de preparación (*staging area*) y cuáles aún no son rastreados (*untracked*).
* **`git add .`**: Traslada **todos** los archivos modificados o creados en el directorio de trabajo hacia el área de preparación, dejándolos seleccionados para el próximo registro.
* **`git commit -m "mensaje"`**: Representa la confirmación de guardado dentro del repositorio local. Congela una captura instantánea (*snapshot*) de los cambios con un mensaje explicativo sobre lo realizado.
* **`git push`**: Envía los *commits* confirmados desde el entorno local hacia el servidor de GitHub, transfiriendo las actualizaciones a la nube.
* **`git pull`**: Descarga e integra en tu computadora las modificaciones más recientes alojadas en GitHub, sincronizando tu trabajo local con lo subido por el equipo.
<p align="center">
       <img width="322" height="230" alt="Captura de pantalla 2026-08-25 235446" src="https://github.com/user-attachments/assets/fbca02f7-fab3-49df-bae8-b3eb36d9448f" />
</p>
## SECUENCIA LÓGICO DE DESARROLLO: 
`Modificar archivos` → `git status` → `git add .` → `git commit` → `git push` → `GitHub`

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
---

## DETALLES ÚTILES Y HERRAMIENTAS DE INSPECCIÓN

### Diagnóstico del estado (`git status`)

Permite confirmar el estado exacto del proyecto antes y después de seleccionar los archivos a guardar. Se recomienda su uso constante dentro del flujo de trabajo:

```bash
git status    # Muestra el eporte completo de los archivos modificados
git status -s # Muestra el estado en formato corto y compacto 
```
Un flujo habitual de guardado local se ejecuta de la siguiente manera:

### Agregar cambios ('add')

```bash
git status
git add .
git commit -m "docs: Descripción del cambio"
```

### Inspección del historial ('git log')

El comando `git log` permite revisar la cronología de cambios confirmados

```bash
git log                                     # Historial detallado de confirmaciones
git log --oneline                           # Lista compacta mostrando una línea por commit
git log --oneline --graph --decorate --all  # Renderiza una representación gráfica del árbol de cambios
```

# 4. Ramas
Permiten trabajar en nuevas funcionalidades, documentación o corrección de errores en un entorno completamente aislado, garantizando que el código estable de la rama principal (main) no sufra alteraciones. En resumen, Las ramas permiten trabajar sin modificar directamente `main`.

Para manetener una organización clara en el trabajo, se recomienda dar nombres descriptivos a las ramas usando el prefijo 'feature/'.

Ejemplos:

```text
feature/readme
feature/documentacion
feature/prototipo
```

## Comandos fundamentales para el manejor de ramas

### Crear y posicionarse en una nueva rama:

```bash
git switch -c feature/nombre
```

### Cambiar de rama

```bash
git switch main
```

## Listar ramas existentes:

```bash
git branch    # Muestra únicamente las ramas locales
git branch -a # Muestra las ramas locales y las sincronizadas con GitHub
```

### Eliminar una rama (Limpeza local):


```bash
git branch -d feature/nombre
```

---

# 5. Markdown

Markdown nos permite estructurar y dar formato a documentos utilizando texto plano y símbolos sencillos. 

## Jerarquía de Títulos
Se utilizan numerales (`#`) para definir la estructura del documento. La cantidad de símbolos indica el nivel jerárquico del encabezado:

```markdown
# Encabezado Nivel 1 (Título Principal)
## Encabezado Nivel 2 (Sección)
### Encabezado Nivel 3 (Subsección)
```

---

## Formato de Texto
Permite dar énfasis visual a palabras o frases clave dentro del contenido:

```markdown
**Texto en negrita**   <!-- Énfasis fuerte -->
*Texto en cursiva*    <!-- Énfasis suave -->
~~Texto tachado~~     <!-- Cambios obsoletos o descartados -->
```

---

## Estructuración de Listas

### Listas no ordenadas (Viñetas)
Útiles para agrupar elementos sin una jerarquía secuencial:

```markdown
- Elemento o punto clave 1
- Elemento o punto clave 2
  - Sub-elemento secundario
```

### Listas numeradas (Secuenciales)
Para describir pasos estructurados o secuencias lógicas:

```markdown
1. Primer paso de la secuencia
2. Segundo paso de la secuencia
3. Tercer paso de la secuencia
```

### Listas de tareas (Checklists)
Ideales para el seguimiento del estado de actividades dentro del proyecto:

```markdown
- [x] Configuración inicial del repositorio
- [ ] Desarrollo de la documentación técnica
- [ ] Pruebas y validación final
```

---

## Inserción de Enlaces y Recursos Multimedia

### Enlaces externos
Sintaxis para vincular referencias o páginas web (`[Texto a mostrar](URL)`):

```markdown
[Repositorio de GitHub](https://github.com)
```

### Inserción de imágenes locales
Sintaxis para cargar imágenes almacenadas dentro de la estructura del repositorio:

```markdown
![Texto alternativo para la imagen](images/diagrama.png)
```

### Inserción directa de imágenes en GitHub (Servidor Remoto)
Si se prefiere no almacenar archivos de imagen dentro de las carpetas locales del proyecto:
1. Abre el archivo `README.md` directamente desde la interfaz web de **GitHub.com**.
2. Presiona el icono de edición (**Edit** / lápiz).
3. Arrastra y suelta el archivo de imagen directamente dentro del editor web.
4. GitHub procesará la imagen, generará un enlace automático del servidor y renderizará el recurso.
5. Confirma los cambios haciendo clic en **Commit changes...**.

---

## Formato de Código

### Código en línea
Se utiliza para resaltar comandos, variables o nombres de archivos dentro de un párrafo empleando comillas simples invertidas (``` ` ```):

```markdown
Ejecuta el comando `git status` para verificar el estado de los archivos.
```

### Bloque de código multilínea
Para incluir bloques completos de código o comandos, utilizando tres comillas invertidas (``` ``` ```) especificando el lenguaje para activar el resaltado de sintaxis:

````markdown
```bash
git status
git add .
git commit -m "docs: actualizar sintaxis de markdown"
git push
```
````

### Tablas de datos
Para organizar información comparativa, por ejemplo.

```bash
| Integrante | Rol en el Proyecto | Estado de Asignación |
| :--- | :--- | :---: |
| Estudiante 1 | Control de Versiones | Completado |
| Estudiante 2 | Documentación Técnica | En proceso |
```

# 6. Estructura del proyecto

Una estructura simple y ordenada:

```text
proyecto/
├── README.md
├── docs/
├── images/
├── src/
├── data/
└── .gitignore
```

## README.md

Debe contener, de forma resumida:

- Nombre del proyecto.
- Descripción.
- Objetivos.
- Metodología.
- Resultados.
- Imágenes.
- Referencias.

---

# 7. Flujo recomendado del equipo

## Antes de trabajar

Actualizar `main`:

```bash
git switch main
git pull
```

## Crear una rama

```bash
git switch -c feature/nombre
```

## Trabajar y guardar cambios

```bash
git status
git add .
git commit -m "Descripción del cambio"
git push -u origin feature/nombre
```

## Integrar cambios

Crear un **Pull Request** → revisar → aprobar → **Merge**.

---

# 8. Comandos rápidos

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

# 9. Integración de Visual Studio Code con Git y GitHub
Visual Studio Code (VS Code) funciona como el centro de control unificado para el desarrollo del proyecto. Su principal fortaleza reside en integrar el editor de texto, el control de versiones local (**Git**) y la plataforma remota (**GitHub**) dentro de una misma interfaz, eliminando la necesidad de alternar entre múltiples programas o pestañas.

---

## Vinculación de VS Code con Git (Control Local)

VS Code incluye un panel nativo de **Control de código fuente** (*Source Control*) que interactúa directamente con el motor local de Git:

* **Visualización del estado de archivos:** Identifica automáticamente los cambios con un código de colores en el explorador de archivos (verde para elementos nuevos, amarillo para modificados y rojo para borrados).
* **Gestión del Staging Area:** Permite preparar archivos para un *commit* de forma gráfica haciendo clic en el icono `+` (*Stage Changes*) junto a cada documento, equivalente a ejecutar `git add`.
* **Confirmación de cambios (*Commits*):** Dispone de un cajón de texto dedicado para redactar el mensaje descriptivo y un botón principal para congelar el historial localmente (`git commit`).
* **Barra de estado de ramas:** En la esquina inferior izquierda muestra la rama activa y permite alternar entre ramas o crear nuevas (`git switch` / `git branch`) mediante un menú desplegable.

---

## Conexión de VS Code con GitHub (Sincronización Remota)

El editor se conecta de forma nativa a tu cuenta de GitHub para gestionar la transferencia de información hacia el servidor en la nube:

* **Autenticación directa:** Permite vincular tu cuenta de GitHub mediante protocolo seguro (OAuth), autorizando permisos de lectura y escritura sin necesidad de ingresar contraseñas de forma repetitiva.
* **Sincronización en un clic:** Sustituye los comandos `git push` y `git pull` por el botón interactivo **Sincronizar cambios** (o *Publish Branch* si es la primera subida), enviando los registros locales a la red de forma automática.
