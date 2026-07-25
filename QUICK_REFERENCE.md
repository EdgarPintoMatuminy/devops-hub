# ⚡ Quick Reference - Comandos Más Usados

## Apache

```bash
# Status
systemctl status apache2 | apachectl fullstatus

# Restart
systemctl restart apache2 | apachectl graceful

# Syntax check
apachectl configtest

# Ver logs
tail -f /var/log/apache2/error.log

# Módulos
a2enmod nombre | a2dismod nombre

# Sitios
a2ensite nombre | a2dissite nombre
```

## Nginx

```bash
# Status
systemctl status nginx | ps aux | grep nginx

# Restart
systemctl restart nginx | nginx -s reload

# Syntax check
nginx -t | nginx -T

# Ver logs
tail -f /var/log/nginx/error.log | /var/log/nginx/access.log

# Configuración
grep -r "upstream" /etc/nginx/

# Reconexiones
ss -tlnp | grep nginx
```

## Tomcat

```bash
# Start
$CATALINA_HOME/bin/startup.sh

# Stop
$CATALINA_HOME/bin/shutdown.sh

# Logs
tail -f $CATALINA_HOME/logs/catalina.out

# Procesos
ps aux | grep catalina | jps -l

# Memoria JVM
jstat -gc $(jps -l | grep Catalina | awk '{print $1}')

# Apps desplegadas
ls $CATALINA_HOME/webapps/

# Deploy .war
cp app.war $CATALINA_HOME/webapps/
```

## WebLogic

```bash
# Admin Server Start
cd $DOMAIN_HOME && ./bin/startWebLogic.sh

# Admin Server Stop
cd $DOMAIN_HOME && ./bin/stopWebLogic.sh

# Managed Server
./bin/startManagedWebLogic.sh ms_name t3://localhost:7001

# WLST
wlst.sh script.py

# Connect en WLST
connect('user','pass','t3://localhost:7001')

# Ver aplicaciones
cd('/AppDeployments') && ls()

# Deploy
deploy(appName='app', path='/ruta/app.war', targets='target')

# Logs
tail -f $DOMAIN_HOME/servers/AdminServer/logs/AdminServer.log
```

## Scripts de Monitoreo

```bash
# Health Check
./scripts/healthcheck.sh

# Con alertas
./scripts/healthcheck.sh --email admin@example.com

# Restart servicios
./scripts/restart_services.sh apache
./scripts/restart_services.sh nginx
./scripts/restart_services.sh tomcat
./scripts/restart_services.sh weblogic
./scripts/restart_services.sh all
```

## Git / GitLab

```bash
# Agregar cambios
git add .

# Commit
git commit -m "Mensaje descriptivo"

# Push
git push origin main

# Ver status
git status

# Historial
git log --oneline -10

# Nueva rama
git checkout -b feature/nombre

# Cambiar de rama
git checkout main
```

## Sistema

```bash
# Puertos en uso
netstat -tlnp | ss -tlnp

# Procesos Java
jps -l | ps aux | grep java

# Memoria
free -h | df -h

# Carga
uptime | top

# Logs del sistema
tail -f /var/log/syslog

# Búsqueda en logs
grep -r "ERROR" /var/log/
```

---

## 📋 Checklist Diario (Copiar y Pegar)

```bash
# Verificación de salud
./scripts/healthcheck.sh

# Logs sin errores
grep -i "error" /var/log/apache2/error.log
grep -i "error" /var/log/nginx/error.log
tail $CATALINA_HOME/logs/catalina.out | grep -i error
tail $DOMAIN_HOME/servers/AdminServer/logs/AdminServer.log | grep -i error

# Puertos activos
netstat -tlnp | grep -E "80|443|8080|7001"

# Conexiones activas
ss -an | grep ESTABLISHED | wc -l

# Espacio en disco
df -h /

# Memoria
free -m
```

---

## 🚨 Troubleshooting Rápido

### Apache no inicia
```bash
apachectl configtest
systemctl start apache2
tail -20 /var/log/apache2/error.log
```

### Nginx error
```bash
nginx -t
systemctl status nginx
tail -20 /var/log/nginx/error.log
```

### Tomcat caído
```bash
ps aux | grep catalina
cd $CATALINA_HOME && ./bin/startup.sh
tail -f logs/catalina.out
```

### WebLogic no responde
```bash
ps aux | grep weblogic
netstat -tlnp | grep 7001
kill -9 <PID>
cd $DOMAIN_HOME && ./bin/startWebLogic.sh
```

### Puerto en uso
```bash
netstat -tlnp | grep 8080
lsof -i :8080
kill -9 <PID>
```

---

## ⌨️ Alias Útiles

Agregar a `~/.bashrc`:

```bash
# Apache
alias a-start='sudo systemctl start apache2'
alias a-stop='sudo systemctl stop apache2'
alias a-restart='sudo systemctl restart apache2'
alias a-test='apachectl configtest'

# Nginx
alias n-start='sudo systemctl start nginx'
alias n-stop='sudo systemctl stop nginx'
alias n-restart='sudo systemctl restart nginx'
alias n-test='sudo nginx -t'

# Tomcat
alias t-start='$CATALINA_HOME/bin/startup.sh'
alias t-stop='$CATALINA_HOME/bin/shutdown.sh'
alias t-logs='tail -f $CATALINA_HOME/logs/catalina.out'

# WebLogic
alias w-start='cd $DOMAIN_HOME && ./bin/startWebLogic.sh'
alias w-stop='cd $DOMAIN_HOME && ./bin/stopWebLogic.sh'
alias w-logs='tail -f $DOMAIN_HOME/servers/AdminServer/logs/AdminServer.log'

# Generales
alias healthcheck='./scripts/healthcheck.sh'
alias restart-all='./scripts/restart_services.sh all'
alias log-errors='grep -r ERROR /var/log/'
alias connections='ss -an | grep ESTABLISHED | wc -l'
```

---

## 🔗 Enlaces Rápidos

- [Apache Docs](https://httpd.apache.org/docs/)
- [Nginx Docs](https://nginx.org/en/docs/)
- [Tomcat Docs](https://tomcat.apache.org/tomcat-9.0-doc/)
- [WebLogic Docs](https://docs.oracle.com/en/middleware/weblogic-server/)
- [Git Docs](https://git-scm.com/doc)

---

**Imprime esta hoja y tenla a mano** 📄

*Última actualización: Julio 2026*
