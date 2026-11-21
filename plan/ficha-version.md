# Ficha de verificación de versión · Grupo 05A

---

## Rocky Linux (VM de consola)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
| --- | --- | --- |
| Versión elegida y fecha de lanzamiento | Rocky Linux 9.9, lanzada el 18/11/2026 | [rockylinux.org/download](https://rockylinux.org/download) |
| Hasta cuándo recibe actualizaciones de seguridad | Soporte activo hasta el 31/05/2027 y actualizaciones de seguridad (EOL) hasta el 31/05/2032 | [docs.rockylinux.org/9/releases](https://docs.rockylinux.org/9/releases/) |
| Requisitos de hardware y si funciona en VirtualBox | Mínimo 1 CPU de 64 bits (arquitectura x86_64-v2 a 1.1 GHz), 1.5 GB de RAM (2 GB recomendados) y 10 GB de disco (20 GB recomendados). Sí funciona en VirtualBox (configurada con 2 GB de RAM y 2 CPU) | [docs.rockylinux.org/.../minimum_hardware_requirements](https://docs.rockylinux.org/9/guides/minimum_hardware_requirements/) |
| ¿El instalador permite particionado manual? | Sí. El instalador (Anaconda) tiene la opción «Personalizada» (*Custom*) en Destino de la instalación | [docs.rockylinux.org/9/guides/installation](https://docs.rockylinux.org/9/guides/installation/) |
| Guía oficial para instalar Docker Engine en esa familia | Docker no tiene una página propia para Rocky Linux. Usamos la guía oficial de la familia CentOS/RHEL y lo dejamos documentado | [docs.docker.com/engine/install/centos](https://docs.docker.com/engine/install/centos/) |
| Imagen base del Dockerfile para esa versión | La imagen oficial existe en Docker Hub con las etiquetas de la serie 9 | [hub.docker.com/_/rockylinux](https://hub.docker.com/_/rockylinux) |

---

## Xubuntu (VM gráfica)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
| --- | --- | --- |
| Versión elegida y fecha de lanzamiento | Xubuntu 26.04 LTS, lanzada el 23/04/2026 | [xubuntu.org/download](https://xubuntu.org/download/) |
| Hasta cuándo recibe actualizaciones de seguridad | Recibe actualizaciones de seguridad durante 3 años hasta el 29/04/2029 | [xubuntu.org/release](https://xubuntu.org/release/) |
| Requisitos de hardware y si funciona en VirtualBox | Mínimo 1 GB de RAM (2 GB recomendados), procesador de doble núcleo de 64 bits (1.5 GHz) y 8.6 GB de disco (20 GB recomendados). Sí funciona en VirtualBox | [docs.xubuntu.org/.../installation.html](https://docs.xubuntu.org/current/user/C/installation.html) |
| ¿El instalador permite particionado manual? | Sí. En el tipo de instalación del instalador gráfico se selecciona la opción «Más opciones» (*Something else* / particionado manual) | [docs.xubuntu.org/.../installation.html](https://docs.xubuntu.org/current/user/C/installation.html) |
| Guía oficial para instalar Docker Engine en esa familia | Docker no tiene una página exclusiva para Xubuntu. Al ser una variante oficial de Ubuntu, usamos la guía oficial de Ubuntu y lo dejamos documentado | [docs.docker.com/engine/install/ubuntu](https://docs.docker.com/engine/install/ubuntu/) |
| Imagen base del Dockerfile para esa versión | No existe imagen oficial exclusiva de Xubuntu en Docker Hub; en su lugar se utiliza la imagen oficial de Ubuntu con la etiqueta 26.04 | [hub.docker.com/_/ubuntu](https://hub.docker.com/_/ubuntu) |

- **RAM asignada a la VM y por qué:** Se asignaron 2 GB de RAM (superando el mínimo de 1 GB exigido) para garantizar fluidez en el entorno de escritorio XFCE y evitar bloqueos al ejecutar el navegador y herramientas de desarrollo simultáneamente.

---

## Alpine (imagen base del Dockerfile)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
| --- | --- | --- |
| Versión elegida y fecha de lanzamiento | Alpine Linux 3.24.0, lanzada el 28/05/2026 | [alpinelinux.org/downloads](https://alpinelinux.org/downloads/) |
| Hasta cuándo recibe actualizaciones de seguridad | Recibe actualizaciones de seguridad durante 2 años hasta el 01/05/2028 | [alpinelinux.org/releases](https://alpinelinux.org/releases/) |
| Requisitos de hardware y si funciona en VirtualBox | No aplica instalación en VirtualBox porque se utiliza únicamente como imagen base de contenedor (requiere ~130 MB de disco y mínimo 128 MB de RAM en ejecución) | [alpinelinux.org/about](https://alpinelinux.org/about/) |
| ¿El instalador permite particionado manual? | No aplica en este proyecto porque no se instala desde ISO en una VM, sino que se descarga como imagen base desde Docker Hub | [hub.docker.com/_/alpine](https://hub.docker.com/_/alpine) |
| Guía oficial para instalar Docker Engine en esa familia | No aplica, ya que Alpine actúa como imagen base dentro del contenedor y no como sistema anfitrión donde se instala Docker Engine | [docs.docker.com/engine/install](https://docs.docker.com/engine/install/) |
| Imagen base del Dockerfile para esa versión | Sí, la imagen oficial existe en Docker Hub con la etiqueta `alpine:3.24` y utiliza `apk` como gestor de paquetes en el Dockerfile | [hub.docker.com/_/alpine](https://hub.docker.com/_/alpine) |
