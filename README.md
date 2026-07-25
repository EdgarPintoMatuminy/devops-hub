# 🔧 DevOps Hub - Comandos Diarios

Hub centralizado de comandos, scripts y notas para la administración y troubleshooting de **Apache**, **Nginx**, **WebLogic** y **Tomcat**.

## 📁 Estructura del Repositorio

```
├── README.md                 # Este archivo
├── .gitignore               # Archivos a ignorar
├── apache/                  # Comandos y scripts Apache
├── nginx/                   # Comandos y scripts Nginx
├── weblogic/                # Comandos y scripts WebLogic
├── tomcat/                  # Comandos y scripts Tomcat
├── scripts/                 # Scripts reutilizables
└── cheat-sheets/            # Resúmenes rápidos
```

## 🚀 Tecnologías

| Tecnología | Versión | Uso Principal |
|-----------|---------|---------------|
| **Apache** | 2.4.x | Servidor Web / Proxy Reverso |
| **Nginx** | 1.x+ | Load Balancer / Reverse Proxy |
| **WebLogic** | 12c | Servidor de Aplicaciones |
| **Tomcat** | 9.x+ | Servidor Java / Aplicaciones |

## 📋 Contenido

### Apache
- Configuración de Virtual Hosts
- Módulos y habilitación
- Health checks
- Troubleshooting

### Nginx
- Balanceo de carga
- Proxy reverso
- SSL/TLS
- Optimización de performance

### WebLogic
- Administración de dominios
- Deployment de aplicaciones
- Monitoreo y logs
- Backup y recuperación

### Tomcat
- Startup/Shutdown
- Gestión de aplicaciones
- Configuración de memoria
- Logs y debugging

## 🎯 Cómo Usar

1. **Busca la tecnología** que necesitas en las carpetas
2. **Consulta los comandos** en los archivos .md
3. **Copia los scripts** si necesitas automatizar
4. **Adapta** según tu entorno

## ✏️ Actualización

Agrega comandos nuevos que descubras:
```bash
git add .
git commit -m "Agrega comando: [descripción breve]"
git push origin main
```

## 🔍 Búsqueda Rápida

```bash
# Busca en todos los archivos
grep -r "comando" .

# Por tecnología específica
grep -r "comando" apache/
```

---

**Última actualización:** Julio 2026  
**Autor:** Edgar  
**Estado:** En desarrollo activo
