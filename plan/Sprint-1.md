# Sprint 1 · Montaje – Grupo 05A

## ¿Qué se realiza en este sprint?

En este sprint se realiza la instalación y configuración de dos máquinas virtuales, una con entorno gráfico y otra de consola. También se configura la comunicación entre ambas máquinas, el acceso remoto mediante SSH y las instantáneas para guardar el estado de las instalaciones.

*Distribuciones seleccionadas por el Grupo 05A:*

- *VM gráfica:* Zorin OS 17.3 Core.
- *VM de consola:* Fedora Server 44.
- *Imagen base para Docker:* Ubuntu 24.04 LTS.

*Entregables del sprint:*

- Dos máquinas virtuales instaladas y configuradas.
- Red entre las dos máquinas.
- Conexión SSH.
- Una instantánea por cada máquina virtual.
- Archivo codigo_sprint1.txt guardado en las dos máquinas.
- Video de máximo 3 minutos.
- Dos commits por cada integrante.

---

## 1. VM gráfica (zorin-grafica)

Instalamos Zorin OS 17.3 Core en VirtualBox. Esta distribución se eligió porque ofrece un entorno gráfico sencillo de utilizar y permite trabajar con aplicaciones de escritorio.

Durante la instalación se debe seleccionar el particionado manual para crear las particiones necesarias:

| Partición | Función |
|---|---|
| / | Contiene el sistema operativo y los programas. |
| swap | Espacio de intercambio que ayuda cuando falta memoria RAM. |
| /home | Guarda los archivos y documentos de los usuarios. |

Los tamaños se deben ajustar al disco virtual asignado a esta máquina.

*Programas y herramientas:*

- Firefox.
- Chromium.
- Nano.
- Gedit.

*Comandos para comprobar el almacenamiento y las particiones:*

bash
lsblk
df -h
cat /etc/fstab


Para identificar el usuario, el equipo y la fecha:

bash
whoami
hostname
date


*Evidencias que se deben agregar:*

- [Captura 1: particionado manual durante la instalación de Zorin OS.]
- [Captura 2: resultado de los comandos lsblk, df -h y cat /etc/fstab.]
- [Captura 3: Firefox, Chromium, Nano y Gedit instalados o abiertos.]

---

## 2. VM de consola (fedora-consola)

Instalamos Fedora Server 44 en VirtualBox. Esta máquina se utiliza para trabajar desde la terminal y ejecutar comandos de administración del sistema.

Durante la instalación se debe seleccionar el particionado personalizado para crear las siguientes particiones:

| Partición | Función |
|---|---|
| / | Contiene el sistema operativo. |
| /var | Guarda archivos y datos variables del sistema. |
| swap | Espacio de intercambio de memoria. |
| /home | Guarda los archivos de los usuarios. |

Los tamaños se ajustan al disco virtual disponible.

*Herramientas que se deben instalar:*

- Make.
- Rsync.
- Curl.
- Git.
- Wget.

Para instalarlas utilizamos:

bash
sudo dnf install -y make rsync curl git wget


*Comandos para comprobar las particiones:*

bash
lsblk
df -h
cat /etc/fstab


*Comandos para comprobar las herramientas instaladas:*

bash
make --version
rsync --version
curl --version
git --version
wget --version


Para identificar el usuario, el equipo y la fecha:

bash
whoami
hostname
date


*Evidencias que se deben agregar:*

- [Captura 4: particiones y almacenamiento de Fedora Server.]
- [Captura 5: resultado de los cinco comandos mostrando las versiones de las herramientas.]

---

## 3. Configuración de red

Configuramos dos adaptadores de red en cada máquina virtual mediante VirtualBox.

- *Adaptador 1:* NAT, para permitir el acceso a Internet.
- *Adaptador 2:* red solo-anfitrión (Host-Only), para permitir la comunicación entre las dos máquinas virtuales.

Para comprobar las direcciones IP de cada máquina utilizamos:

bash
ip a


Después identificamos las direcciones IP de la red solo-anfitrión.

*Comprobación de comunicación:*

Desde Zorin OS hacia Fedora:

bash
ping -c 4 DIRECCION_IP_FEDORA


Desde Fedora hacia Zorin OS:

bash
ping -c 4 DIRECCION_IP_ZORIN


Si ambas máquinas reciben respuestas, significa que existe comunicación entre ellas.

*Evidencias que se deben agregar:*

- [Captura 6: direcciones IP de las dos máquinas virtuales.]
- [Captura 7: prueba de ping desde Zorin hacia Fedora y desde Fedora hacia Zorin.]

---

## 4. Conexión SSH

Configuramos SSH para permitir que la máquina gráfica (Zorin OS) pueda ingresar remotamente a la máquina de consola (Fedora Server).

Primero instalamos y activamos el servicio SSH en Fedora:

bash
sudo dnf install -y openssh-server
sudo systemctl enable --now sshd


Permitimos las conexiones SSH en el firewall de Fedora:

bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload


Comprobamos que el servicio esté funcionando:

bash
sudo systemctl status sshd


Después, desde la terminal de Zorin OS, ejecutamos:

bash
ssh USUARIO@DIRECCION_IP_FEDORA


Reemplazamos USUARIO por el usuario principal de Fedora y DIRECCION_IP_FEDORA por la dirección IP correspondiente.

Si aparece una pregunta para confirmar la conexión, escribimos yes y posteriormente ingresamos la contraseña del usuario de Fedora.

*Evidencia que se debe agregar:*

- [Captura 8: conexión SSH establecida desde Zorin OS hacia Fedora Server, mostrando el usuario y el nombre del equipo remoto.]

---

## 5. Instantáneas de las máquinas virtuales

Creamos una instantánea para cada máquina virtual con el objetivo de guardar el estado de la instalación y poder recuperarlo si ocurre algún problema.

Las instantáneas deben tomarse con las máquinas virtuales apagadas y después de terminar su instalación y configuración correspondiente.

*Nombre de la instantánea:*

instalacion-limpia

*Pasos en VirtualBox:*

1. Apagar completamente la máquina virtual.
2. Seleccionar la máquina en VirtualBox.
3. Entrar en la sección Instantáneas.
4. Seleccionar la opción para tomar una instantánea.
5. Escribir el nombre instalacion-limpia.
6. Guardar la instantánea.

Realizamos el mismo procedimiento para Zorin OS y Fedora Server.

*Evidencias que se deben agregar:*

- [Captura 9: instantánea instalacion-limpia de Zorin OS.]
- [Captura 10: instantánea instalacion-limpia de Fedora Server.]

---

## 6. Código del Sprint 1 – Grupo 05A

El docente publicó un código diferente para cada grupo. Según la tabla publicada en el campus, al grupo 5 le corresponde el siguiente código:

*Código asignado: YD05-QZNX*

Este código debe guardarse en un archivo de texto llamado codigo_sprint1.txt en el directorio personal del usuario principal de las dos máquinas virtuales.

*En Zorin OS ejecutamos:*

bash
echo "YD05-QZNX" > ~/codigo_sprint1.txt


Comprobamos que el archivo se haya guardado correctamente:

bash
cat ~/codigo_sprint1.txt
date


*En Fedora Server ejecutamos:*

bash
echo "YD05-QZNX" > ~/codigo_sprint1.txt


Comprobamos nuevamente:

bash
cat ~/codigo_sprint1.txt
date


Es importante verificar que el código aparezca correctamente en las dos máquinas virtuales.

*Evidencias:*

- [Captura 11: archivo codigo_sprint1.txt en Zorin OS mostrando YD05-QZNX y la fecha.]
- [Captura 12: archivo codigo_sprint1.txt en Fedora Server mostrando YD05-QZNX y la fecha.]

---

## 7. Video del Sprint 1

Realizamos un video de máximo 3 minutos mostrando el proceso y las evidencias del sprint.

El video debe ser continuo, sin cortes, y cada integrante debe mostrar su participación.

*Contenido del video:*

1. Presentación de los integrantes y sus nombres.
2. Mostrar la máquina virtual gráfica Zorin OS.
3. Mostrar la máquina virtual de consola Fedora Server.
4. Mostrar las particiones y herramientas instaladas.
5. Mostrar las direcciones IP y las pruebas de comunicación.
6. Mostrar la conexión SSH.
7. Mostrar las instantáneas.
8. Mostrar el archivo codigo_sprint1.txt en las dos máquinas, ejecutando cat ~/codigo_sprint1.txt y date.

*Enlace del video:* [Agregar aquí el enlace de YouTube público o no listado.]

---

## 8. Participación de los integrantes

En esta sección se registra el trabajo realizado por cada integrante del Grupo 05A.

| Integrante | Actividades realizadas | Commits |
|---|---|---|
| Integrante 1 | Instalación y configuración de Zorin OS. | 2 |
| Integrante 2 | Instalación y configuración de Fedora Server. | 2 |
| Integrante 3 | Configuración de red y conexión SSH. | 2 |
| Integrante 4 | Instalación de herramientas, instantáneas, capturas y documentación. | 2 |

Los nombres y las actividades deben actualizarse según la participación real de cada integrante.

---

## 9. Entrega final

Para finalizar el Sprint 1, verificamos que estén incluidos los siguientes elementos:

- [ ] Máquina virtual gráfica Zorin OS instalada.
- [ ] Máquina virtual de consola Fedora Server instalada.
- [ ] Particionado manual comprobado en ambas máquinas.
- [ ] Herramientas instaladas en Fedora Server.
- [ ] Red configurada y comunicación comprobada.
- [ ] Conexión SSH funcionando.
- [ ] Instantánea de Zorin OS.
- [ ] Instantánea de Fedora Server.
- [ ] Código YD05-QZNX guardado en ambas máquinas.
- [ ] Capturas de pantalla completas.
- [ ] Video de máximo 3 minutos.
- [ ] Dos commits por cada integrante.
- [ ] Enlace del sitio publicado en el campus.

---

*Grupo:* 05A  
*Miembros:* Yur Brainer Montenegro Villada - 2560738-2724 y Juan Camilo Ordoñez Castro 2560864-2724
*Proyecto:* Sprint 1 – Montaje  
*Distribuciones:* Zorin OS 17.3 Core y Fedora Server 44  
*Código del grupo:* YD05-QZNX

