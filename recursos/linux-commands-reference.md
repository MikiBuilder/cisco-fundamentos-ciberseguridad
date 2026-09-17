# 🐧 Linux Command Line Reference Manual

Guía completa y estructurada de comandos en Linux para consulta rápida, administración de sistemas, redes, seguridad y gestión de paquetes.

> Versión original publicada como [gist](https://gist.github.com/MikiBuilder/5fe9f0713efacd38b7edcf20e21cc72a). Esta es la versión mantenida dentro del repositorio.

---

## 📑 Índice

- [1. Navegación e Inspección del Sistema de Archivos](#1-navegación-e-inspección-del-sistema-de-archivos)
- [2. Gestión de Archivos y Directorios](#2-gestión-de-archivos-y-directorios)
- [3. Visualización y Edición de Contenido de Archivos](#3-visualización-y-edición-de-contenido-de-archivos)
- [4. Permisos, Propietarios y Atributos](#4-permisos-propietarios-y-atributos)
- [5. Gestión de Procesos y Control del Sistema](#5-gestión-de-procesos-y-control-del-sistema)
- [6. Redes, Transferencia e Inspección de Puertos](#6-redes-transferencia-e-inspección-de-puertos)
- [7. Gestión de Usuarios, Grupos y Sesiones](#7-gestión-de-usuarios-grupos-y-sesiones)
- [8. Almacenamiento, Sistemas de Archivos y Monitoreo de Disco](#8-almacenamiento-sistemas-de-archivos-y-monitoreo-de-disco)
- [9. Compresión, Archivado y Empaquetado](#9-compresión-archivado-y-empaquetado)
- [10. Gestión de Paquetes](#10-gestión-de-paquetes-debianubuntu-rhelfedora-arch-linux)
- [11. Conexiones Remotas y Administración SSH](#11-conexiones-remotas-y-administración-ssh)
- [12. Seguridad, Cortafuegos y Auditoría](#12-seguridad-cortafuegos-y-auditoría)
- [13. Información del Sistema y Diagnóstico Hardware](#13-información-del-sistema-y-diagnóstico-hardware)

---

## 1. Navegación e Inspección del Sistema de Archivos

| Comando | Descripción |
| :--- | :--- |
| `pwd` | Muestra la ruta absoluta del directorio de trabajo actual. |
| `ls -la` | Lista todos los archivos y directorios, incluidos los ocultos, con formato detallado. |
| `cd [dir]` | Cambia el directorio de trabajo actual a la ruta especificada. |
| `tree -L [n]` | Muestra la estructura de directorios en forma de árbol hasta un nivel `n` de profundidad. |
| `stat [file]` | Muestra información detallada sobre el estado de un archivo (mtime, atime, ctime, inode, permisos). |
| `realpath [file]` | Resuelve y muestra la ruta absoluta canónica de un archivo o directorio. |

---

## 2. Gestión de Archivos y Directorios

| Comando | Descripción |
| :--- | :--- |
| `mkdir -p [path]` | Crea un directorio y todos los directorios padre necesarios en la ruta indicada. |
| `rm -rf [path]` | Elimina de forma recursiva y forzada archivos o directorios sin solicitar confirmación. |
| `cp -r [src] [dest]` | Copia archivos o directorios de forma recursiva del origen al destino. |
| `mv [src] [dest]` | Mueve o renombra archivos y directorios. |
| `touch [file]` | Crea un archivo vacío o actualiza las marcas de tiempo de acceso y modificación de uno existente. |
| `ln -s [target] [link]` | Crea un enlace simbólico que apunta al archivo o directorio de destino. |
| `find [path] -name "[pattern]"` | Busca archivos y directorios dentro de la ruta especificada según el patrón indicado. |
| `rsync -avz [src] [dest]` | Sincroniza y copia archivos entre rutas o hosts remotos manteniendo permisos y comprimiendo datos. |

---

## 3. Visualización y Edición de Contenido de Archivos

| Comando | Descripción |
| :--- | :--- |
| `cat [file]` | Concatena y muestra el contenido completo de un archivo en la salida estándar. |
| `less [file]` | Abre un archivo para visualización paginada interactiva con navegación hacia adelante y atrás. |
| `head -n [N] [file]` | Muestra las primeras `N` líneas de un archivo. |
| `tail -f [file]` | Muestra las últimas líneas de un archivo y sigue en tiempo real las nuevas entradas. |
| `grep -rn "[pattern]" [path]` | Busca recursivamente un patrón de texto dentro de archivos e indica el número de línea. |
| `sed 's/[old]/[new]/g' [file]` | Editor de flujo para buscar y reemplazar patrones de texto en un archivo. |
| `awk '{print $1}' [file]` | Lenguaje de procesamiento de patrones para extraer y manipular columnas de texto. |
| `diff -u [file1] [file2]` | Compara dos archivos y muestra las diferencias en formato unificado. |

---

## 4. Permisos, Propietarios y Atributos

| Comando | Descripción |
| :--- | :--- |
| `chmod [mode] [file]` | Cambia los permisos de acceso de un archivo o directorio (modo octal o simbólico). |
| `chown -R [user]:[group] [path]` | Cambia el propietario y el grupo de un archivo o directorio de forma recursiva. |
| `umask [mode]` | Establece la máscara predeterminada para la creación de archivos y directorios. |
| `chattr +i [file]` | Modifica atributos avanzados de archivos en sistemas ext4/xfs (ej. `+i` lo hace inmutable). |
| `lsattr [file]` | Lista los atributos avanzados de archivos en el sistema de archivos. |

---

## 5. Gestión de Procesos y Control del Sistema

| Comando | Descripción |
| :--- | :--- |
| `ps aux` | Muestra una instantánea detallada de todos los procesos en ejecución en el sistema. |
| `top` | Muestra la actividad del sistema y los procesos en tiempo real de forma dinámica. |
| `htop` | Monitor interactivo de procesos avanzado con interfaz gráfica basada en texto. |
| `kill -9 [PID]` | Envía una señal `SIGKILL` para finalizar forzadamente un proceso por su ID. |
| `killall [process_name]` | Finaliza todos los procesos que coincidan con el nombre especificado. |
| `pkill -f [pattern]` | Envía señales a procesos basándose en un patrón de búsqueda dentro de la línea de comandos. |
| `systemctl status [service]` | Muestra el estado operativo de un servicio administrado por systemd. |
| `journalctl -u [service] -f` | Muestra y sigue en tiempo real los registros del sistema (logs) para un servicio específico. |
| `bg` / `fg` | Mueve un proceso en segundo plano al primer plano o viceversa. |
| `nohup [command] &` | Ejecuta un comando inmune a la señal de desconexión (SIGHUP) en segundo plano. |

---

## 6. Redes, Transferencia e Inspección de Puertos

| Comando | Descripción |
| :--- | :--- |
| `ip addr show` | Muestra la configuración de las interfaces de red y direcciones IP asociadas. |
| `ip route` | Muestra y manipula la tabla de enrutamiento IP del sistema. |
| `ss -tulpn` | Muestra los sockets de red abiertos, puertos en escucha y los procesos asociados. |
| `ping -c [N] [host]` | Envía paquetes ICMP ECHO_REQUEST a un host de red para verificar la conectividad. |
| `curl -i [URL]` | Transfiere datos desde o hacia un servidor utilizando diversos protocolos de red. |
| `wget [URL]` | Descarga archivos desde la web de forma no interactiva a través de HTTP, HTTPS o FTP. |
| `traceroute [host]` | Muestra la ruta que siguen los paquetes de red hasta llegar al host de destino. |
| `dig [domain]` | Herramienta de consulta DNS para diagnosticar y verificar registros de nombres de dominio. |
| `nc -zv [host] [port]` | Abre conexiones arbitrarias TCP/UDP para realizar pruebas de puertos y escaneo. |
| `netstat -an` | Muestra conexiones de red, tablas de enrutamiento y estadísticas de interfaz (herramienta heredada). |

---

## 7. Gestión de Usuarios, Grupos y Sesiones

| Comando | Descripción |
| :--- | :--- |
| `whoami` | Muestra el nombre del usuario efectivo actual. |
| `id [user]` | Muestra los identificadores de usuario (UID), de grupo (GID) y grupos a los que pertenece el usuario. |
| `useradd -m [user]` | Crea una nueva cuenta de usuario y crea su directorio home. |
| `usermod -aG [group] [user]` | Modifica una cuenta de usuario (ej. agrega un usuario a un grupo secundario). |
| `passwd [user]` | Cambia o establece la contraseña del usuario especificado. |
| `su - [user]` | Cambia la identidad del usuario actual a la cuenta especificada con su entorno de inicio de sesión. |
| `sudo [command]` | Ejecuta un comando con los privilegios de seguridad del superusuario (root). |
| `w` | Muestra quién está conectado actualmente y qué está haciendo cada usuario. |

---

## 8. Almacenamiento, Sistemas de Archivos y Monitoreo de Disco

| Comando | Descripción |
| :--- | :--- |
| `df -h` | Muestra el espacio en disco usado y disponible en todos los sistemas de archivos montados. |
| `du -sh [path]` | Muestra la estimación del espacio en disco utilizado por un archivo o directorio de forma resumida. |
| `lsblk` | Muestra información sobre todos los dispositivos de almacenamiento de bloque disponibles. |
| `fdisk -l` | Muestra las tablas de particiones de los dispositivos de almacenamiento en bloque. |
| `mount [dev] [dir]` | Monta un sistema de archivos en el directorio especificado. |
| `umount [dir]` | Desmonta un sistema de archivos activo del punto de montaje. |
| `free -h` | Muestra la cantidad de memoria RAM y SWAP libre y utilizada en el sistema. |
| `uptime` | Muestra cuánto tiempo ha estado funcionando el sistema y la carga promedio. |

---

## 9. Compresión, Archivado y Empaquetado

| Comando | Descripción |
| :--- | :--- |
| `tar -czvf [file.tar.gz] [path]` | Crea un archivo comprimido en formato tar.gz a partir de un directorio o archivo. |
| `tar -xzvf [file.tar.gz]` | Extrae el contenido de un archivo comprimido en formato tar.gz. |
| `zip -r [file.zip] [path]` | Comprime archivos y directorios de forma recursiva en formato zip. |
| `unzip [file.zip]` | Extrae archivos comprimidos en formato zip. |
| `gzip [file]` | Comprime un archivo individual reemplazándolo por una versión con extensión `.gz`. |

---

## 10. Gestión de Paquetes (Debian/Ubuntu, RHEL/Fedora, Arch Linux)

| Comando | Descripción |
| :--- | :--- |
| `apt update && apt upgrade` | Actualiza la lista de repositorios y actualiza todos los paquetes instalados (Debian/Ubuntu). |
| `apt install [package]` | Descarga e instala un paquete nuevo junto con sus dependencias (APT). |
| `apt remove --purge [package]` | Desinstala un paquete y elimina completamente sus archivos de configuración. |
| `dnf install [package]` | Instala paquetes en distribuciones basadas en RHEL/Fedora/CentOS. |
| `dnf update` | Actualiza los paquetes del sistema a la última versión (Fedora/RHEL). |
| `pacman -Syu` | Sincroniza los repositorios y actualiza todo el sistema (Arch Linux). |
| `pacman -S [package]` | Instala un paquete específico en Arch Linux. |
| `pacman -Rs [package]` | Elimina un paquete y las dependencias que ya no son necesarias. |
| `dpkg -i [package.deb]` | Instala directamente un paquete en formato deb local. |
| `rpm -ivh [package.rpm]` | Instala directamente un paquete en formato RPM local. |

---

## 11. Conexiones Remotas y Administración SSH

| Comando | Descripción |
| :--- | :--- |
| `ssh [user]@[host]` | Conecta a un servidor remoto a través del protocolo seguro SSH. |
| `ssh -i [key.pem] -p [port] [user]@[host]` | Conecta por SSH especificando un archivo de clave privada y un puerto personalizado. |
| `ssh-keygen -t ed25519 -C "[email]"` | Genera un par de claves criptográficas SSH (pública/privada) seguras. |
| `ssh-copy-id [user]@[host]` | Copia la clave pública SSH al servidor remoto para permitir inicio de sesión sin contraseña. |
| `scp -P [port] [file] [user]@[host]:[path]` | Copia archivos de forma segura entre hosts locales y remotos a través de SSH. |
| `sftp [user]@[host]` | Inicia una sesión interactiva de transferencia de archivos segura sobre SSH. |
| `ssh -L [local_port]:localhost:[remote_port] [user]@[host]` | Crea un túnel SSH (Local Port Forwarding) para redirigir tráfico remoto a la máquina local. |

---

## 12. Seguridad, Cortafuegos y Auditoría

| Comando | Descripción |
| :--- | :--- |
| `ufw enable / ufw status` | Habilita y muestra el estado del cortafuegos simplificado (Uncomplicated Firewall). |
| `ufw allow [port]/tcp` | Permite el tráfico entrante a un puerto TCP específico en UFW. |
| `firewall-cmd --add-port=[port]/tcp --permanent` | Agrega una regla permanente para permitir un puerto en Firewalld (RHEL/CentOS/Fedora). |
| `iptables -L -n -v` | Lista las reglas activas de filtrado de paquetes del cortafuegos iptables de forma detallada. |
| `fail2ban-client status` | Muestra el estado del servicio Fail2ban y las jaulas de protección activas. |
| `nmap -sV [target]` | Escanea puertos abiertos y detecta versiones de servicios ejecutándose en un host de destino. |
| `openssl x509 -in [cert.crt] -text -noout` | Inspecciona y muestra los detalles completos de un certificado SSL/TLS en formato PEM. |
| `sha256sum [file]` | Calcula y verifica el checksum SHA-256 de un archivo para validar su integridad. |

---

## 13. Información del Sistema y Diagnóstico Hardware

| Comando | Descripción |
| :--- | :--- |
| `uname -a` | Muestra información detallada sobre el sistema operativo y la versión del kernel Linux. |
| `hostnamectl` | Muestra o modifica el nombre de host del sistema y la configuración asociada. |
| `dmesg -T` | Muestra los mensajes del búfer del kernel con marcas de tiempo legibles. |
| `lscpu` | Muestra información detallada sobre la arquitectura de la CPU y sus características. |
| `lspci` | Lista todos los dispositivos conectados al bus PCI del sistema. |
| `lsusb` | Lista todos los dispositivos USB conectados al sistema. |

[⬆ Volver al índice](#-índice)
