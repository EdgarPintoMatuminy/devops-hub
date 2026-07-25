# 🚀 Configuración del Repositorio en GitLab

## Preparación Inicial

### 1. Crear Repositorio en GitLab

```bash
# Acceder a GitLab
# https://gitlab.com/dashboard

# Crear nuevo proyecto
# Botón "New project"
# Nombre: devops-hub (o el que prefieras)
# Visibilidad: Private o Public según necesites
# NO inicializar con README (ya tenemos)
```

### 2. Configurar Git Localmente

```bash
# Clonar el repositorio vacío
git clone https://gitlab.com/tu_usuario/devops-hub.git
cd devops-hub

# O inicializar repositorio local si usas existing folder
git init
git remote add origin https://gitlab.com/tu_usuario/devops-hub.git
```

### 3. Agregar archivos y hacer commit

```bash
# Agregar todos los archivos
git add .

# Verificar qué se va a commitear
git status

# Primer commit
git commit -m "Initial commit: Agregar hub de comandos diarios"

# Cambiar rama a main si es necesario
git branch -M main

# Push al repositorio
git push -u origin main
```

## 📋 Estructura Final del Repositorio

```
devops-hub/
├── README.md                              # Documentación principal
├── GITLAB_SETUP.md                        # Este archivo
├── .gitignore                             # Archivos a ignorar
│
├── apache/
│   └── APACHE.md                          # Comandos de Apache
│
├── nginx/
│   └── NGINX.md                           # Comandos de Nginx
│
├── tomcat/
│   └── TOMCAT.md                          # Comandos de Tomcat
│
├── weblogic/
│   └── WEBLOGIC.md                        # Comandos de WebLogic
│
└── scripts/
    ├── healthcheck.sh                     # Verificación de salud
    └── restart_services.sh                # Reinicio de servicios
```

## 🔄 Flujo de Trabajo Diario

### Agregar nuevos comandos

```bash
# 1. Crear rama para cambios
git checkout -b feature/nuevo-comando

# 2. Editar archivos (ej: apache/APACHE.md)
nano apache/APACHE.md

# 3. Verificar cambios
git status
git diff apache/APACHE.md

# 4. Agregar y commitear
git add apache/APACHE.md
git commit -m "Agrega: comando para limpiar caché Apache"

# 5. Push a GitLab
git push origin feature/nuevo-comando

# 6. Crear Merge Request en GitLab
# (Se sugiere en el output después del push)
# Merge en main cuando esté listo
```

### Actualizar desde repositorio remoto

```bash
# Traer cambios remotos
git fetch origin

# Actualizar rama local
git pull origin main
```

## 🔐 Autenticación con GitLab

### Usando SSH (Recomendado)

```bash
# 1. Generar clave SSH
ssh-keygen -t ed25519 -C "tu_email@example.com"

# 2. Copiar clave pública
cat ~/.ssh/id_ed25519.pub

# 3. En GitLab:
# Perfil -> Preferencias -> SSH Keys
# Pegar clave pública

# 4. Cambiar URL del repositorio
git remote set-url origin git@gitlab.com:tu_usuario/devops-hub.git

# 5. Probar conexión
ssh -T git@gitlab.com
```

### Usando HTTPS + Token Personal

```bash
# 1. Crear Personal Access Token en GitLab
# Perfil -> Preferencias -> Access Tokens
# Nombre: devops-hub
# Scope: api, read_repository, write_repository

# 2. Cambiar URL
git remote set-url origin https://gitlab.com/tu_usuario/devops-hub.git

# 3. Git pedirá usuario/password
# Usuario: tu_usuario
# Password: (pegar token)
```

## 💾 Backup del Repositorio

```bash
# Clonar espejo completo
git clone --mirror https://gitlab.com/tu_usuario/devops-hub.git devops-hub.git

# Actualizar espejo
cd devops-hub.git
git remote update --prune

# Exportar como tarball
cd ..
tar czf devops-hub-backup-$(date +%Y%m%d).tar.gz devops-hub.git
```

## 📖 Colaboración en Equipo

### Agregar colaboradores

```bash
# En GitLab:
# Proyecto -> Miembros
# Invitar usuario
# Role: Developer (para commit) o Reporter (solo lectura)
```

### Resolver conflictos de merge

```bash
# Si hay conflicto al hacer pull
git pull origin main

# Editar archivos con <<<<<<, ======, >>>>>>
nano archivo_conflictivo.md

# Resolver manualmente y agregar
git add archivo_conflictivo.md
git commit -m "Resolver conflicto en archivo_conflictivo.md"
git push origin main
```

## 🎯 Buenas Prácticas

### Commits

```bash
# Commits descriptivos
git commit -m "Agrega: healthcheck para WebLogic"
git commit -m "Fix: corrige error en proxy reverso Nginx"
git commit -m "Docs: actualiza guía de deployment Tomcat"
git commit -m "Refactor: reorganiza comandos en Apache.md"

# NO hacer
git commit -m "fix"
git commit -m "cambios"
```

### Ramas

```bash
# Nombres descriptivos
git checkout -b feature/nuevo-script-backup
git checkout -b fix/nginx-ssl-config
git checkout -b docs/weblogic-troubleshooting

# NO hacer
git checkout -b feature1
git checkout -b test
```

### Push regular

```bash
# Hacer push frecuentemente (al menos daily)
git push origin main

# Evitar cambios sin pushear por días
```

## 🆘 Solucionar Problemas

### Revertir último commit (sin haber hecho push)

```bash
git reset --soft HEAD~1
# O forzar
git reset --hard HEAD~1
```

### Recuperar commit borrado

```bash
git reflog
git checkout <commit-hash>
```

### Ver historial

```bash
git log --oneline -10
git log --graph --all --oneline
```

### Limpiar cambios locales

```bash
# Ver qué cambió
git status

# Descartar cambios
git checkout -- archivo.md

# O todos los cambios
git reset --hard HEAD
```

## 📱 Acceder desde GitLab Web

Una vez pusheado, verás en GitLab:

- **Files**: Todos tus archivos organizados
- **Commits**: Historial de cambios
- **Branches**: Ramas del proyecto
- **Wiki**: Documentación adicional (opcional)
- **Issues**: Tareas o mejoras a hacer

## 🎓 Referencias

- [Git Documentation](https://git-scm.com/doc)
- [GitLab Docs](https://docs.gitlab.com/)
- [GitLab CLI](https://docs.gitlab.com/ee/editor_extensions/gitlab_cli/)

---

**¡Listo!** Tu repositorio está configurado y listo para usar.

Para más información sobre cómo trabajar con Git:
```bash
git help
git help <comando>
```

**Última actualización:** Julio 2026
