# Ficha de verificación de versión · Grupo 05A

## ¿Qué es esta ficha?

Antes de descargar una distribución hay que comprobar que su versión sirve para el proyecto. Esta ficha es la prueba de que lo comprobamos para cada distribución del grupo (consola, gráfica e imagen base del Dockerfile), respaldada con los enlaces oficiales verificados el día de su diligenciamiento.

* **Distribución de consola (VM):** Fedora Server
* **Distribución gráfica (VM):** Zorin OS
* **Imagen base (Dockerfile):** Ubuntu

---

## Fedora Server (VM de consola)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | Fedora Server 44, lanzada el 21/04/2026 | https://fedoraproject.org/server/download |
| Hasta cuándo recibe actualizaciones de seguridad | Recibe actualizaciones durante aproximadamente 13 meses, hasta el 19/05/2027 | https://docs.fedoraproject.org/en-US/releases/lifecycle/ |
| Requisitos de hardware y si funciona en VirtualBox | Mínimo 2 CPU de 64 bits (2 GHz), 2 GB de RAM y 15 GB de disco (20 GB recomendados). Sí funciona en VirtualBox (configurada con 2 GB de RAM y 2 CPU) | https://docs.fedoraproject.org/en-US/fedora/latest/release-notes/ |
| ¿El instalador permite particionado manual? | Sí. El instalador (Anaconda) tiene la opción «Personalizada» (*Custom*) en Destino de la instalación | https://docs.fedoraproject.org/en-US/fedora/latest/install-guide/ |
| Guía oficial para instalar Docker Engine en esa familia | Sí. Docker cuenta con una guía oficial directa para Fedora usando el gestor de paquetes `dnf` | https://docs.docker.com/engine/install/fedora/ |
| Imagen base del Dockerfile para esa versión | Sí, la imagen oficial existe en Docker Hub con la etiqueta `fedora:44` | https://hub.docker.com/_/fedora |

---

## Zorin OS (VM gráfica)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | Zorin OS 17.3 Core, lanzada el 26/03/2025 | https://zorin.com/os/download/ |
| Hasta cuándo recibe actualizaciones de seguridad | Recibe actualizaciones de software y parches de seguridad hasta el 30/04/2027 | https://help.zorin.com/docs/getting-started/getting-zorin-os/ |
| Requisitos de hardware y si funciona en VirtualBox | Mínimo CPU de doble núcleo de 64 bits a 1 GHz, 1.5 GB de RAM (2 GB recomendados) y 15 GB de disco (20 GB recomendados). Sí funciona en VirtualBox | https://help.zorin.com/docs/getting-started/system-requirements/ |
| ¿El instalador permite particionado manual? | Sí. En la pantalla «Tipo de instalación» del instalador gráfico se selecciona la opción «Más opciones» (*Something else*) para configurar particiones manualmente | https://help.zorin.com/docs/getting-started/install-zorin-os/ |
| Guía oficial para instalar Docker Engine en esa familia | Docker no tiene una página exclusiva para Zorin OS. Al estar basado en Ubuntu, usamos la guía oficial de Ubuntu y lo dejamos documentado | https://docs.docker.com/engine/install/ubuntu/ |
| Imagen base del Dockerfile para esa versión | No existe imagen oficial exclusiva de Zorin OS en Docker Hub; en su lugar se utiliza la imagen oficial de Ubuntu con la etiqueta correspondiente (`ubuntu:22.04` / `ubuntu:24.04`) | https://hub.docker.com/_/ubuntu |

* **RAM asignada a la VM y por qué:** Se asignaron 4 GB de RAM (superando el mínimo de 2 GB exigido) para garantizar fluidez en el entorno de escritorio de Zorin OS y evitar bloqueos al ejecutar el navegador y herramientas de desarrollo simultáneamente.

---

## Ubuntu (imagen base del Dockerfile)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | Ubuntu 24.04 LTS, lanzada el 25/04/2024 | https://ubuntu.com/download/server |
| Hasta cuándo recibe actualizaciones de seguridad | Recibe actualizaciones de seguridad estándar durante 5 años hasta el 31/05/2029 | https://ubuntu.com/about/release-cycle |
| Requisitos de hardware y si funciona en VirtualBox | No aplica instalación en VirtualBox porque se utiliza únicamente como imagen base de contenedor (requiere ~30 MB de disco comprimida y mínimo 128 MB de RAM en ejecución) | https://hub.docker.com/_/ubuntu |
| ¿El instalador permite particionado manual? | No aplica en este proyecto porque no se instala desde ISO en una VM, sino que se descarga como imagen base desde Docker Hub | https://hub.docker.com/_/ubuntu |
| Guía oficial para instalar Docker Engine en esa familia | No aplica, ya que Ubuntu actúa como imagen base dentro del contenedor y no como sistema anfitrión donde se instala Docker Engine | https://docs.docker.com/engine/install/ubuntu/ |
| Imagen base del Dockerfile para esa versión | Sí, la imagen oficial existe en Docker Hub con la etiqueta `ubuntu:24.04` y utiliza `apt` como gestor de paquetes en el Dockerfile | https://hub.docker.com/_/ubuntu |
| Imagen base del Dockerfile para esa versión | Sí, la imagen oficial existe en Docker Hub con la etiqueta `alpine:3.24` y utiliza `apk` como gestor de paquetes en el Dockerfile | [hub.docker.com/_/alpine](https://hub.docker.com/_/alpine) |
