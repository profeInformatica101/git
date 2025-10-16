# 🧠 Git Cheat Sheet + Chuleta Markdown

📘 **Chuleta Markdown para tu README:**  
https://profeinformatica101.github.io/git/Markdown

---

# 🧬 La carpeta `.git`: el cerebro de tu repositorio

> “Git no es una nube ni una aplicación externa.  
> **Git eres tú, tu código y una carpeta llamada `.git`.**”  
> - Anónimo (inspirado en Linus Torvalds)

Cuando ejecutas `git init`, Git no crea magia: simplemente genera una carpeta oculta llamada **`.git/`**, que **es el repositorio en sí mismo**.  
Todo lo que hace Git (commits, ramas, merges, reverts) sucede ahí dentro.

### 🧩 Estructura básica

| Carpeta / Archivo | Función | Analogía |
|--------------------|----------|----------|
| `.git/config` | Configuración local del repositorio | Tu libreta de direcciones |
| `.git/HEAD` | Indica en qué rama estás | Tu “posición actual” |
| `.git/refs/` | Referencias a ramas y etiquetas | Los nombres de tus commits |
| `.git/objects/` | Archivos comprimidos con el contenido y los commits | Tu memoria de largo plazo |
| `.git/index` | Zona de *staging* | Tu lista de tareas antes de confirmar |
| `.git/logs/` | Registro interno de tus movimientos | Tu diario de cambios |
| `.git/hooks/` | Scripts que se ejecutan en eventos (commit, push…) | Tus reflejos automáticos |

👉 Si borras `.git/`, pierdes todo el historial.  
Tu carpeta se convierte en un simple conjunto de archivos, **sin historia, sin ramas, sin alma.**

---

# 🧰 Comandos de Git Esenciales

Este repositorio sirve como guía rápida de los comandos más útiles de Git para el desarrollo y control de versiones.

## 🛠️ Configuración Inicial

1. **Configurar Usuario y Correo Electrónico**
   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
   ```

2. **Ver la Configuración Actual**
   ```bash
   git config --list
   ```

3. **Instalar Oh My Zsh (opcional, para mejorar tu experiencia en la terminal)**
   ```bash
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

---

## 📂 Gestión de Repositorios

### 1. Crear un Repositorio

- **Inicializar un Nuevo Repositorio**
  ```bash
  git init
  ```

### 2. Clonar un Repositorio Existente

- **Clonar un Repositorio**
  ```bash
  git clone [URL]
  ```

---

## ✏️ Gestión de Cambios

### 1. Ver el Estado

```bash
git status
```

### 2. Preparar Archivos para un Commit

```bash
git add [archivo]
git add .
```

### 3. Registrar Cambios

```bash
git commit -m "Mensaje del commit"
```

---

## 🕒 Historial y Restauración

### 1. Ver el Historial

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

### 2. Restaurar Cambios

```bash
git reset --hard <id_commit>
git push --force
```

---

## 🌱 Trabajo con Ramas

### 1. Gestión de Ramas

```bash
git branch -a        # Listar ramas
git branch nueva      # Crear nueva rama
git checkout nombre   # Cambiar de rama
```

### 2. Fusionar Ramas

```bash
git merge [nombre-rama]
git mergetool
```

---

## 🌐 Repositorios Remotos

### 1. Sincronización

```bash
git push [alias] [rama]
git pull [alias] [rama]
git fetch [alias]
```

### 2. Configuración de Remotos

```bash
git remote add origin git@github.com:[usuario]/[repo].git
git remote set-url origin git@github.com:[usuario]/[repo].git
```

---

## 🔒 Claves SSH

```bash
ssh-keygen -t rsa -b 4096 -C "tu_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/tu_clave_privada
```

---

# 🚀 ¿`git fetch` o `git pull`? ¡No te confundas!

| Comando      | ¿Qué hace?                                           | ¿Afecta tu código local? |
|--------------|------------------------------------------------------|---------------------------|
| 🟢 `git fetch` | 🔎 Solo descarga los cambios remotos (sin mezclar)   | ❌ No                     |
| 🟠 `git pull`  | 🔄 Descarga y fusiona automáticamente los cambios    | ✅ Sí                     |

---

# 🔀 Importar una rama desde otro repositorio (no fork) y subirla al tuyo

**Objetivo:** Traer la rama `curl_SwingMavenBase` del repo de otra cuenta y publicarla en tu repo.

```bash
git remote add <usuarioGitHub> https://github.com/<usuarioGitHub>/miapp.git
git fetch <usuarioGitHub>
git checkout -b curl_SwingMavenBase <usuarioGitHub>/curl_SwingMavenBase
git push origin curl_SwingMavenBase
git checkout main
git merge --no-ff curl_SwingMavenBase
git push origin main
git remote remove <usuarioGitHub>
```

💡 Usa `--no-ff` para conservar el commit de merge, y si hay conflictos:
```bash
git add .
git commit
```

---

## 🛠️ Utilidades Adicionales

```bash
ssh -T git@github.com                # Comprobar conexión SSH
git diff [branch1]..[branch2]       # Comparar cambios
git config --global alias.tree "log --graph --decorate --all --oneline"
```

---

## 💡 Comandos Avanzados y Prácticas Recomendadas

```bash
git branch -d [nombre-rama]          # Eliminar rama local
git push origin --delete [rama]      # Eliminar rama remota
git stash                            # Guardar cambios temporales
git stash pop                        # Recuperar stash
```

---

## 💡 Verifica tus remotos actuales

```bash
git remote -v
```

---

# 🧠 En resumen

> “El repositorio no es GitHub, ni el código, ni la nube.  
> Git es la historia completa guardada dentro del `.git/`.  
> Lo demás son interfaces.” — *Anónimo (inspirado en Linus Torvalds)*
