# 🧠 Laboratorio personal con Proxmox, RDP y Wiki.js

Este repositorio documenta mi experiencia personal al montar un entorno de laboratorio usando **Proxmox VE**. Aunque no hice una documentación exhaustiva en su momento, aquí dejo una descripción general de lo que conseguí, los retos que enfrenté y lo que aprendí.

---

## 📦 Infraestructura creada

- Instalación de **Proxmox VE** en una máquina física
- Creación de:
  - 🪟 Máquina virtual con **Windows** (accesible por RDP)
  - 🐧 Servidor **Debian** para alojar Wiki.js y la base de datos PostgreSQL
  - Configuración de un Daemon básico para que wiki.js se inice automáticamente.
- Securización del servidor:
  - Configuración del servicio **SSH** (puerto personalizado, autenticación por clave, desactivación de acceso root)
  - Reglas básicas con **iptables**

---

## ⚙️ Decisiones técnicas

- Elegí Proxmox por su facilidad para administrar máquinas virtuales y su interfaz web.
- Opté por Debian para el servidor web por ser ligero, estable y bien documentado, con un baso consumo de recursos al renunciar a la interfaz gráfica
- Usé Wiki.js como plataforma de documentación por su integración con Git y su estética moderna.

---

## 🔐 Seguridad aplicada

Aunque fue un laboratorio personal, apliqué medidas básicas de seguridad:

- Activé solo autenticación por clave pública
- Cambié el puerto por defecto del servicio SSH
- Escribí un script sencillo para iptables que:
  - Cierra todos los puertos por defecto
  - Abre solo los necesarios (SSH, HTTP/S)
  - Establece políticas por defecto restrictivas

---

## 💭 Lecciones aprendidas

- La instalación de Wiki.js con PostgreSQL tiene pasos muy específicos. Me llevó varios intentos resolver dependencias y permisos.
- Proxmox me enseñó mucho sobre redes bridged y NAT.
- Aprendí a recuperar acceso a una VM que se quedó sin red por mal configurarla desde el host con `qm terminal`.

---

## 🔧 Mejoras que haría en el futuro

- Automatizar todo el proceso de despliegue con **Ansible**
- Añadir monitoreo con Netdata o Prometheus
- Documentar desde el primer momento cada paso en la Wiki
- Crear snapshots programados de las máquinas virtuales

---

## 🚀 ¿Por qué hice esto?

Principalmente como una práctica para afianzar conceptos de virtualización, administración de sistemas, y seguridad en entornos reales. Todo el entorno lo monté sin guías paso a paso, resolviendo problemas a medida que surgían.

---

## 📝 Notas finales

Este proyecto contiene pocas capturas o scripts porque no fui consciente de documentar todo desde el inicio, pero está aquí como reflejo de lo que fui capaz de montar, aprender y mantener.

