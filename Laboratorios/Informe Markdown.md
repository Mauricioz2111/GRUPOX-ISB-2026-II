#README PRINCIPAL

#Guía rápida: Git, GitHub, VS Code y Markdown

## Índice
- [1. Git y GitHub](#1-git-y-github)
- [2. Crear o clonar un repositorio](#2-crear-o-clonar-un-repositorio)
- [3. Flujo básico](#3-flujo-básico)
- [4. Ramas](#4-ramas)
- [5. Pull Request](#5-pull-request)
- [6. Markdown](#7-markdown)
- [7. Estructura del proyecto](#9-estructura-del-proyecto)
- [8. Flujo recomendado del equipo](#10-flujo-recomendado-del-equipo)
- [9. Comandos rápidos](#11-comandos-rápidos)

---

# 1. Git y GitHub

## Git
Sistema de control de versiones que permite registrar y recuperar cambios.

## GitHub
Plataforma para almacenar y compartir repositorios Git de forma remota.

**En resumen:**
```text
Git → trabajo local
GitHub → repositorio remoto
```

---

# 2. Crear o clonar un repositorio

## Crear repositorio local

```bash
mkdir mi-proyecto
cd mi-proyecto
git init
```

## Clonar desde GitHub

```bash
git clone URL_DEL_REPOSITORIO
cd nombre-del-repositorio
```

---

# 3. Flujo básico

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

## Ver cambios

```bash
git status
```

## Agregar cambios

```bash
git add .
```

## Crear commit

```bash
git commit -m "Descripción del cambio"
```

## Subir a GitHub

```bash
git push
```

## Descargar cambios

```bash
git pull
```

---

# 4. Ramas

Las ramas permiten trabajar sin modificar directamente `main`.

## Crear y cambiar de rama

```bash
git switch -c feature/nombre
```

Ejemplos:

```text
feature/readme
feature/documentacion
feature/prototipo
```

## Cambiar de rama

```bash
git switch main
```

## Ver ramas

```bash
git branch
```

---

# 5. Pull Request

Un Pull Request permite revisar los cambios antes de incorporarlos a `main`.

## Flujo

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

---

# 7. Markdown

Markdown permite dar formato a archivos `.md`.

## Títulos

```markdown
# Título principal
## Subtítulo
### Subtítulo secundario
```

## Texto

```markdown
**Negrita**
*Cursiva*
```

## Listas

```markdown
- Elemento 1
- Elemento 2
- Elemento 3
```

## Lista numerada

```markdown
1. Primer elemento
2. Segundo elemento
3. Tercer elemento
```

## Lista de tareas

```markdown
- [ ] Pendiente
- [x] Completado
```

## Enlaces

```markdown
[GitHub](https://github.com)
```

## Código

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

## Tabla

```markdown
| Integrante | Rol | Estado |
|------------|-----|--------|
| Persona 1 | Diseño |  |
| Persona 2 | Código |  |
```

Usar:

```markdown
![Imagen del proyecto](images/proyecto.png)
```

## Imagen directamente desde GitHub

En `README.md`:

1. Presionar **Edit **.
2. Arrastrar la imagen al editor.
3. GitHub generará el enlace.
4. Hacer **Commit changes**.

---

# 9. Estructura del proyecto

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

# 8. Flujo recomendado del equipo

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

# 9. Comandos rápidos

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
