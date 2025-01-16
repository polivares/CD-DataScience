
# Ejercicio Práctico: Explorando los Estados y el Flujo de Trabajo en GIT

## Paso 1: Instalación de GIT

1. **Instala GIT en tu sistema operativo:**
   - En **Linux** (Debian/Ubuntu):
     ```bash
     sudo apt update
     sudo apt install git
     ```
   - En **macOS**:
     ```bash
     brew install git
     ```
   - En **Windows**:
     - Descarga e instala GIT desde [git-scm.com](https://git-scm.com/).
     - Asegúrate de seleccionar las opciones predeterminadas en el instalador.

2. **Verifica que GIT se instaló correctamente:**
   ```bash
   git --version
   ```

---

## Paso 2: Configuración Inicial

1. **Configura tu nombre de usuario y correo electrónico:**
   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
   ```

2. **Verifica la configuración:**
   ```bash
   git config --list
   ```

---

## Paso 3: Crear y Configurar un Repositorio

1. **Crea una carpeta de trabajo y navega a ella:**
   ```bash
   mkdir mi_proyecto
   cd mi_proyecto
   ```

2. **Inicializa un repositorio GIT:**
   ```bash
   git init
   ```

3. **Verifica el estado del repositorio (debería estar vacío):**
   ```bash
   git status
   ```

---

## Paso 4: Flujo de Trabajo Básico

1. **Crea un archivo llamado `mi_archivo.txt` y añade contenido inicial:**
   ```bash
   echo "Este es el contenido inicial" > mi_archivo.txt
   ```

2. **Verifica el estado del archivo (`Untracked`):**
   ```bash
   git status
   ```

3. **Añade el archivo al área de preparación (`Staging`):**
   ```bash
   git add mi_archivo.txt
   ```

4. **Confirma los cambios con un mensaje:**
   ```bash
   git commit -m "Primer commit: Añadido mi_archivo.txt"
   ```

---

## Paso 5: Modificar y Confirmar Cambios

1. **Edita el archivo añadiendo una nueva línea:**
   ```bash
   echo "Nueva línea añadida al archivo" >> mi_archivo.txt
   ```

2. **Verifica el estado (`Modified`):**
   ```bash
   git status
   ```

3. **Revisa las diferencias entre la versión modificada y la última confirmada:**
   ```bash
   git diff
   ```

4. **Prepara los cambios para confirmar:**
   ```bash
   git add mi_archivo.txt
   ```

5. **Confirma los cambios:**
   ```bash
   git commit -m "Segundo commit: Modificada mi_archivo.txt"
   ```

---

## Paso 6: Explorar el Historial de Cambios

1. **Consulta el historial de commits:**
   ```bash
   git log
   ```

2. **Verifica los cambios en detalle:**
   ```bash
   git log -p
   ```

---

## Paso 7: Eliminar y Restaurar Archivos

1. **Elimina el archivo del directorio de trabajo:**
   ```bash
   rm mi_archivo.txt
   ```

2. **Verifica el estado del repositorio (`Deleted`):**
   ```bash
   git status
   ```

3. **Restaura el archivo eliminado desde el repositorio:**
   ```bash
   git checkout mi_archivo.txt
   ```

4. **Confirma que el archivo ha sido restaurado:**
   ```bash
   ls
   cat mi_archivo.txt
   ```

---

## Paso 8: Ignorar Archivos

1. **Crea un archivo `.gitignore` para excluir archivos innecesarios:**
   ```bash
   echo "*.log" > .gitignore
   echo "node_modules/" >> .gitignore
   ```

2. **Añade el archivo `.gitignore` al control de versiones:**
   ```bash
   git add .gitignore
   git commit -m "Añadido archivo .gitignore"
   ```

3. **Verifica que los archivos definidos en `.gitignore` son excluidos:**
   ```bash
   git status
   ```

---

¡Con estos pasos, has explorado el flujo de trabajo básico de GIT! 🚀
