# 🗂️ Guía de Git y GitHub —

> Sigue esta guía para configurar tu entorno, clonar el repositorio y trabajar con Git de forma correcta desde el primer día.

---

## 📺 Videos recomendados — Ver antes de empezar

| Tema                         | Canal        | Link                                                          |
| ---------------------------- | ------------ | ------------------------------------------------------------- |
| ¿Qué es Git y GitHub?        | freeCodeCamp | [Ver en YouTube](https://www.youtube.com/watch?v=mBYSUUnMt9M) |
| Instalar Git y Git Bash      | Roelcode     | [Ver en YouTube](https://www.youtube.com/watch?v=p9S1wSChtSo) |
| Cómo usar GitHub paso a paso | MoureDev     | [Ver en YouTube](https://www.youtube.com/watch?v=3GymExBkKjE) |
| Comandos Git esenciales      | Fazt         | [Ver en YouTube](https://www.youtube.com/watch?v=HiXLkL42tMU) |

---

## 1️⃣ Instalar Git Bash

Git Bash es la terminal que usarás para ejecutar todos los comandos de Git en Windows.

### Pasos:

1. Entra a [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Descarga la versión para **Windows**
3. Ejecuta el instalador — deja todas las opciones **por defecto**
4. Al terminar, busca **"Git Bash"** en el menú de inicio y ábrelo
5. Verifica que funcionó escribiendo:

```bash
git --version
```

Debe mostrarte algo como: `git version 2.x.x`

---

## 2️⃣ Configurar tu identidad en Git

Haz esto **una sola vez** después de instalar Git Bash.  
Usa tu nombre real y el email de tu cuenta de GitHub.

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

Verifica que quedó bien:

```bash
git config --list
```

---

## 3️⃣ Clonar el repositorio CiberGenIA

Esto descarga el proyecto completo a tu computadora.

```bash
# 1. Navega a la carpeta donde quieres guardar el proyecto
cd Documents

# 2. Clona el repositorio
git clone https://github.com/Eviix90s/CiberGenIA.git

# 3. Entra a la carpeta del proyecto
cd CiberGenIA
```

Solo necesitas clonar una vez. Las próximas veces solo actualizas (ver sección 5).

---

## 4️⃣ Flujo de trabajo — Cómo subir tus cambios

Sigue siempre este orden cada vez que trabajes en el proyecto:

```bash
# PASO 1 — Actualiza tu copia local antes de empezar
git pull origin main

# PASO 2 — Haz tus cambios (edita archivos, agrega contenido, etc.)
# ... trabaja en tus archivos ...

# PASO 3 — Revisa qué archivos modificaste
git status

# PASO 4 — Agrega los archivos que quieres subir
git add .                    # agrega TODOS los cambios
git add nombre-archivo.html  # o agrega solo un archivo específico

# PASO 5 — Crea el commit con un mensaje descriptivo
git commit -m "tipo: descripción corta de lo que hiciste"

# PASO 6 — Sube tus cambios a GitHub
git push origin main
```

---

## 5️⃣ Comandos esenciales de referencia

### Información y estado

```bash
git status          # ver qué archivos cambiaron
git log --oneline   # ver historial de commits resumido
git diff            # ver exactamente qué líneas cambiaron
```

### Sincronización

```bash
git pull origin main   # descargar cambios del equipo
git push origin main   # subir tus cambios al repo
```

### Agregar y confirmar cambios

```bash
git add .                    # agregar todos los cambios
git add carpeta/archivo.md   # agregar un archivo específico
git commit -m "mensaje"      # crear un commit
```

### Ramas (avanzado)

```bash
git branch                   # ver en qué rama estás
git checkout -b nombre-rama  # crear y cambiar a una nueva rama
git checkout main            # volver a la rama principal
git merge nombre-rama        # fusionar una rama con main
```

---

## 6️⃣ Formato de mensajes de commit

Usa este formato para que el historial quede ordenado y profesional:

```
tipo: descripción corta en español
```

| Tipo       | Cuándo usarlo                                      |
| ---------- | -------------------------------------------------- |
| `feat`     | Agreas contenido nuevo (módulo, actividad, página) |
| `fix`      | Corriges un error                                  |
| `docs`     | Actualizas documentación o README                  |
| `style`    | Cambios de diseño sin afectar contenido            |
| `refactor` | Reorganizas archivos o carpetas                    |

### Ejemplos:

```bash
git commit -m "feat: agrego módulo 1 de IA Generativa"
git commit -m "fix: corrijo enlace roto en módulo Ciberseguridad"
git commit -m "docs: actualizo README con nuevos colaboradores"
git commit -m "style: mejoro estilos CSS de la página principal"
```

---

## 7️⃣ Errores comunes y cómo resolverlos

### ❌ "Please tell me who you are"

```bash
# Falta configurar tu identidad — ejecuta esto:
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

### ❌ "rejected — non-fast-forward"

```bash
# Hay cambios nuevos en el repo que no tienes — primero actualiza:
git pull origin main
# Luego vuelve a intentar el push
git push origin main
```

### ❌ "Permission denied"

```bash
# No tienes acceso al repo — pídele a Ale que te agregue como colaborador
# en Settings → Collaborators
```

### ❌ Subiste algo por error y quieres revertir el último commit

```bash
git revert HEAD
```

---

## 8️⃣ Reglas del equipo

- ✅ Siempre hacer `git pull` antes de empezar a trabajar
- ✅ Un commit = un cambio concreto (no mezclar cosas distintas)
- ✅ Mensajes de commit en español y descriptivos
- ✅ Avisar en el grupo si van a modificar un archivo que otro está usando
- ❌ No subir archivos pesados (videos, instaladores, imágenes > 5MB)
- ❌ No hacer push directo sin probar que el contenido funciona

---

<div align="center">

**CiberGenIA · Instituto Tecnológico de Tlalnepantla · 2026**  
¿Dudas? Pregunta en la junta del viernes 🗓️

</div>
