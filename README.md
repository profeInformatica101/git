# Comandos de Git Esenciales

Este repositorio sirve como una guía rápida y un recordatorio de los comandos más importantes de Git que se utilizan regularmente en el desarrollo de software y el control de versiones.

## Configuración Inicial

- **Configurar Usuario y Correo Electrónico**
  ```bash
  git config --global user.name "Tu Nombre"
  git config --global user.email "tuemail@example.com"
  ```

## Crear y Clonar Repositorios

- **Inicializar un Nuevo Repositorio**
  ```bash
  git init
  ```

- **Clonar un Repositorio Existente**
  ```bash
  git clone [URL]
  ```

## Cambios en los Archivos

- **Verificar el Estado del Repositorio**
  ```bash
  git status
  ```

- **Agregar Archivos al Área de Staging**
  ```bash
  git add [archivo]
  git add .
  ```

- **Realizar un Commit de los Cambios**
  ```bash
  git commit -m "Mensaje del commit"


  ```

## Historial de Commits
En detalle:
```sh
git log --pretty=format:"%h - %an, %ar : %s"

```
%h: Muestra el hash abreviado del commit. Este es un identificador corto para el commit, más fácil de leer y manejar que el hash completo.

%an: Muestra el nombre del autor del commit. Este es el individuo que realizó los cambios y ejecutó el commit.

## Ejemplo de ALIAS

- **Crear un Alias para 'git tree'**
  ```bash
  git config --global alias.tree "log --graph --decorate --all --oneline"
  ```

## Restaurar a un **Commit pasado**
- **Ver el Historial de Commits**
  ```bash
  git log
  
  ```
  **RESTAURAR(Commits)**

```bash
  git reset --hard <id_commit>
  git push --force


```
Si no conoces el hash del commit inicial, puedes encontrarlo usando:

```bash
 git log --reverse


```

Realiza un git pull para traer los cambios del repositorio remoto:

```bash
git pull origin main --rebase


```
## Trabajar con Ramas

- **Listar todas las Ramas**
  ```bash
  git branch -a
  ```

- **Crear una Nueva Rama**
  ```bash
  git branch [nombre-rama]
  ```

- **Cambiar a Otra Rama**
  ```bash
  git checkout [nombre-rama]
  ```

- **Fusionar Ramas**
  ```bash
  git merge [nombre-rama]
  ```

## Sincronización con Repositorios Remotos

- **Subir Cambios al Repositorio Remoto**
  ```bash
  git push [alias] [rama]
  ```

- **Actualizar el Repositorio Local con Cambios Remotos**
  ```bash
 git pull [alias] [rama]

```

## Configuración del Repositorio

- **Cambiar URL del Repositorio Remoto**
```bash
  git remote set-url origin git@github.com:[tu_usuario]/[tu_repositorio].git
```
- **Añadir un Nuevo Repositorio Remoto**
  ```bash
  git remote add origin git@github.com:[tu_usuario]/[tu_repositorio].git
  ```

## Generar Clave Pública y Privada SSH

Para generar una nueva clave SSH, puedes usar el siguiente comando. Asegúrate de reemplazar "tu_email@example.com" con tu dirección de correo electrónico real. Este comando crea una nueva clave SSH, usando el correo electrónico proporcionado como una etiqueta.

 ```bash
  ssh-keygen -t rsa -b 4096 -C "tu_email@example.com"
```

Después de ejecutar el comando, te pedirá que especifiques la ubicación del archivo en el que quieres guardar la clave. Puedes presionar enter para aceptar la ubicación predeterminada. Luego, te pedirá una contraseña segura para la clave.

### Agrega tu clave SSH al ssh-agent:

    - Asegúrate de que el ssh-agent esté en ejecución ejecutando 
     
 ```bash 
      eval "$(ssh-agent -s)".
```
   - Añade tu clave SSH privada al ssh-agent con ssh-add ~/.ssh/tu_clave_privada, sustituyendo tu_clave_privada por el nombre de tu archivo de clave privada (por ejemplo, id_ed25519).

## Comandos Adicionales

- **Comprobar Conexión con Repositorio Remoto**
  ```bash
  ssh -T git@github.com
  ```

- **Diferencias entre Archivos**
  ```bash
  git diff
  ```

- **Comparar Diferencias entre Distintos Repositorios**
  Para comparar diferencias entre distintos repositorios, puedes utilizar el comando `git diff [branch1]..[branch2]`. Esto te permitirá ver las diferencias entre dos ramas, incluso si están en repositorios distintos, siempre que ambos estén correctamente referenciados localmente.

  ```bash
  git diff [branch1]..[branch2]
  ```

- **Reestablecer Archivos del Área de Staging**
  ```bash
  git reset [archivo]
  ```
