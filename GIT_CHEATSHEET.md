# 🧠 GIT CHEATSHEET — Comandos más usados

---

## 🏁 CONFIGURACIÓN INICIAL

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@dominio.com"
git config --global init.defaultBranch main
git config --global color.ui auto
git config --list --global          # Ver configuración global
```

---

## 🗂️ INICIAR O CLONAR REPOSITORIO

```bash
git init                            # Inicia un nuevo repositorio
git clone <url>                     # Clona un repositorio remoto
git remote add origin <url>         # Conecta tu repo local al remoto
git remote -v                       # Muestra los remotos configurados
```

---

## 🔍 ESTADO Y DIFERENCIAS

```bash
git status                          # Muestra archivos modificados, staged, etc.
git diff                            # Cambios no preparados (unstaged)
git diff --staged                   # Cambios preparados (staged)
git log --oneline                   # Historial corto de commits
git log --graph --oneline --decorate --all  # Historial visual
```

---

## 🧱 AGREGAR Y CONFIRMAR CAMBIOS

```bash
git add <archivo>                   # Agrega archivo al stage
git add .                           # Agrega todos los cambios
git restore --staged <archivo>      # Quita un archivo del stage
git commit -m "feat: mensaje claro" # Crea un commit
git commit --amend -m "nuevo mensaje" # Edita el último commit
```

---

## 🌿 RAMAS (BRANCHES)

```bash
git branch                          # Lista ramas locales
git branch -r                       # Lista ramas remotas
git switch -c <nombre-rama>         # Crea y cambia a una nueva rama
git switch <nombre-rama>            # Cambia a otra rama existente
git branch -d <nombre-rama>         # Elimina rama (segura)
git branch -D <nombre-rama>         # Elimina rama forzadamente
```

---

## 🚀 SUBIR Y TRAER CAMBIOS (REMOTOS)

```bash
git fetch                           # Descarga metadatos del remoto
git pull                            # Descarga y mezcla cambios
git pull --rebase                   # Reescribe tu rama encima del remoto
git push                            # Envía commits al remoto
git push -u origin <nombre-rama>    # Envía y asocia una nueva rama
```

---

## 🔄 MERGE Y REBASE

```bash
git merge <rama>                    # Fusiona rama en la actual
git rebase <rama-base>              # Reescribe commits sobre otra rama
git rebase --continue               # Continúa rebase tras resolver conflictos
git rebase --abort                  # Cancela un rebase
```

---

## 🧰 STASH (GUARDAR TRABAJO TEMPORAL)

```bash
git stash                           # Guarda cambios no commiteados
git stash list                      # Lista stashes guardados
git stash pop                       # Recupera y elimina el último stash
git stash apply                     # Aplica un stash sin eliminarlo
```

---

## 🧹 LIMPIAR Y REVERTIR CAMBIOS

```bash
git restore <archivo>               # Revierte cambios en el working directory
git clean -fd                       # Borra archivos no trackeados
git reset --soft HEAD~1             # Revierte commit, conserva cambios staged
git reset --hard HEAD~1             # Borra commit y cambios (⚠️ peligroso)
git revert <hash>                   # Crea un commit inverso a otro
```

---

## 🏷️ TAGS Y VERSIONES

```bash
git tag                             # Lista tags existentes
git tag v1.0.0                      # Crea tag simple
git tag -a v1.0.0 -m "Release 1.0"  # Crea tag anotado
git push --tags                     # Envía tags al remoto
```

---

## 🧭 INSPECCIÓN Y DEPURACIÓN

```bash
git blame <archivo>                 # Muestra quién modificó cada línea
git show <hash>                     # Muestra contenido de un commit
git reflog                          # Historial de movimientos del HEAD
git log -p                          # Muestra cambios línea a línea
git bisect start                    # Empieza búsqueda binaria de bugs
```

---

## 🔐 AUTENTICACIÓN Y ACCESO

### 🔑 Por HTTPS (token personal)
```bash
git remote set-url origin https://github.com/<usuario>/<repo>.git
```

### 🧭 Por SSH (recomendado)
```bash
ssh-keygen -t ed25519 -C "tu.email@dominio.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
# Copia la clave pública y agrégala en GitHub > Settings > SSH Keys
```

---

## ⚙️ ALIAS ÚTILES

```bash
git config --global alias.st "status -sb"
git config --global alias.co "checkout"
git config --global alias.br "branch"
git config --global alias.cm "commit -m"
git config --global alias.lg "log --oneline --graph --decorate --all"
git config --global alias.last "log -1 --stat"
```

---

## 💡 FLUJO TÍPICO DE TRABAJO

```bash
# 1. Clonar o crear repo
git clone <url>
cd <repo>

# 2. Crear rama nueva
git switch -c feature/nueva-funcionalidad

# 3. Hacer cambios y commits
git add .
git commit -m "feat: agrega nueva funcionalidad"

# 4. Actualizar desde main
git fetch origin
git rebase origin/main

# 5. Subir al remoto
git push -u origin feature/nueva-funcionalidad

# 6. Crear Pull Request en GitHub
```

---

## 📦 ARCHIVOS ÚTILES

```bash
# Ignorar archivos innecesarios
echo "venv/
node_modules/
__pycache__/
.env
dist/
.DS_Store
" > .gitignore

# Archivo README básico
echo "# Proyecto GCP-MDM 🚀
Pipeline con Pub/Sub, Eventarc, Cloud Workflow, Cloud Storage y Cloud Run" > README.md
```

---

## 🧩 COMANDOS DE SOCORRO

```bash
git reflog                         # Recupera commits perdidos
git checkout <hash> -- <archivo>   # Recupera versión de un archivo
git reset --hard origin/main       # Volver al estado remoto (⚠️ peligroso)
```

---

## 🧭 RESUMEN VISUAL DE COMANDOS CLAVE

| Acción | Comando rápido |
|--------|----------------|
| Inicializar repo | `git init` |
| Clonar repo | `git clone <url>` |
| Ver estado | `git status` |
| Agregar cambios | `git add .` |
| Confirmar cambios | `git commit -m "mensaje"` |
| Subir cambios | `git push` |
| Bajar cambios | `git pull` |
| Crear rama | `git switch -c rama` |
| Fusionar rama | `git merge rama` |
| Guardar temporalmente | `git stash` |
| Ver historial | `git log --oneline` |
| Revertir commit | `git revert <hash>` |
| Ver quién cambió algo | `git blame archivo` |

---

## ✨ Buenas prácticas
- Escribe **mensajes de commit claros** (`feat`, `fix`, `refactor`, `docs`, etc.).
- Usa **ramas separadas** para nuevas funcionalidades o fixes.
- Realiza **pull antes de push**.
- No hagas `rebase` en ramas compartidas sin coordinar.
- Usa `.gitignore` para evitar archivos innecesarios.
- Crea **tags** para releases (`v1.0.0`, `v2.1.3`, etc.).

---

📘 **Autor:** Equipo de desarrollo  
📅 **Última actualización:** Octubre 2025  
📍 **Referencia:** [https://git-scm.com/docs](https://git-scm.com/docs)
