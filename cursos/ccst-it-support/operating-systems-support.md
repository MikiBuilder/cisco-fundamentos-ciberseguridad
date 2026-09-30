[← Volver a la página principal del repositorio](../../README.md)

# Operating Systems Support

> **Objetivo del curso:** diagnosticar y resolver problemas comunes en Windows, macOS, Linux y sistemas operativos móviles: fallos de arranque, cierres de aplicaciones, problemas de conectividad, instalaciones de software y compatibilidad entre plataformas.

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [0. Introducción al curso](#0-introducción-al-curso)
- [Módulo 1 — Troubleshooting the Windows Operating System](#módulo-1--troubleshooting-the-windows-operating-system)
  - [1.1 Troubleshooting Display and Power Issues](#11-troubleshooting-display-and-power-issues-problemas-de-pantalla-y-energía)
  - [1.2 Assisting Users with Accessibility Features](#12-assisting-users-with-accessibility-features-funciones-de-accesibilidad)
  - [1.3 Securing and Maintaining Windows System Integrity](#13-securing-and-maintaining-windows-system-integrity-seguridad-e-integridad-del-sistema)
  - [1.4 Assisting Users with Cloud-Based Backup Tools](#14-assisting-users-with-cloud-based-backup-tools-copias-de-seguridad-en-la-nube)
  - [1.5 Troubleshooting Boot and Startup Issues](#15-troubleshooting-boot-and-startup-issues-problemas-de-arranque)
  - [1.6 Resumen del Módulo 1](#16-resumen-del-módulo-1)
- [Módulo 2 — Troubleshooting Linux and macOS](#módulo-2--troubleshooting-linux-and-macos)
  - [2.1 Linux and macOS Tools and Features](#21-linux-and-macos-tools-and-features-herramientas-y-características)
  - [2.2 Linux and macOS Best Practices](#22-linux-and-macos-best-practices-buenas-prácticas)
  - [2.3 Linux Virtualization](#23-linux-virtualization-virtualización)
  - [2.4 Basic Linux Commands Used in Troubleshooting](#24-basic-linux-commands-used-in-troubleshooting-comandos-linux-para-diagnóstico)
  - [2.5 Troubleshooting macOS](#25-troubleshooting-macos)
  - [2.6 Resumen del Módulo 2](#26-resumen-del-módulo-2)
- [Módulo 3 — Troubleshooting Mobile Devices and Applications](#módulo-3--troubleshooting-mobile-devices-and-applications)
  - [3.1 Mobile Device Features](#31-mobile-device-features-características-de-los-dispositivos-móviles)
  - [3.2 Troubleshooting Process for Mobile Devices](#32-troubleshooting-process-for-mobile-devices-proceso-de-diagnóstico)
  - [3.3 Managing Mobile OS Security](#33-managing-mobile-os-security-seguridad-del-so-móvil)
  - [3.4 Common Issues and Solutions for Mobile Devices](#34-common-issues-and-solutions-for-mobile-devices-problemas-comunes)
  - [3.5 Mobile Device Apps](#35-mobile-device-apps-aplicaciones-móviles)
  - [3.6 Troubleshooting Mobile Device App Issues](#36-troubleshooting-mobile-device-app-issues-fallos-de-aplicaciones)
  - [3.7 The Cloud](#37-the-cloud-la-nube)
  - [3.8 Resumen del Módulo 3](#38-resumen-del-módulo-3)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del apartado correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Este curso aplica el proceso de troubleshooting de 8 pasos visto en [IT Customer Support Basics](it-customer-support-basics.md); repásalo antes de empezar.

---

# 0. Introducción al curso

Segundo curso de la serie orientada al CCST IT Support. Mientras el primero cubría la atención al cliente y el método de troubleshooting, este aplica ese método a los sistemas operativos que el técnico encontrará a diario: Windows, macOS, Linux, Android e iOS.

Funciones del sistema operativo que conviene tener claras desde el principio, porque todo el diagnóstico se apoya en ellas:

- Administración de la memoria RAM.
- Planificación de procesos en la CPU.
- Control del sistema de archivos.
- Gestión de periféricos y controladores (drivers).
- Gestión de usuarios, permisos y seguridad.

[⬆ Volver al índice](#índice)

---

# MÓDULO 1 — Troubleshooting the Windows Operating System

**(Resolución de problemas en Windows)**

Windows es el sistema con más presencia en entornos corporativos, y por eso concentra el mayor volumen de tickets. El módulo recorre los problemas más frecuentes que llegan a un help desk: pantalla y energía, accesibilidad, seguridad, copias de seguridad y arranque.

---

## 1.1 Troubleshooting Display and Power Issues (Problemas de pantalla y energía)

- **Pantalla:** sin imagen, resolución incorrecta, parpadeos, varios monitores mal detectados. Comprobaciones habituales: cableado y conectores, monitor correcto como principal, resolución y frecuencia adecuadas, actualización o reinstalación del controlador gráfico (Administrador de dispositivos).
- **Energía:** el equipo no enciende, se apaga solo o la batería dura poco. Herramientas: planes de energía (Panel de control / Configuración), estados de suspensión e hibernación, diagnóstico de batería (`powercfg /batteryreport`).
- Distinguir siempre si el fallo es de hardware (monitor, cable, batería) o de software (driver, configuración) antes de actuar.

### Para el examen
- Un monitor externo que funciona descarta la tarjeta gráfica y apunta a la pantalla del portátil.
- Driver gráfico corrupto: arrancar en modo seguro y reinstalar desde el Administrador de dispositivos.

## 1.2 Assisting Users with Accessibility Features (Funciones de accesibilidad)

Windows incluye herramientas de accesibilidad que el técnico debe saber activar y configurar para asistir a usuarios con necesidades visuales, auditivas o motrices:

- **Narrador (Narrator):** lector de pantalla integrado.
- **Lupa (Magnifier):** ampliación de zonas de la pantalla.
- **Contraste alto y filtros de color.**
- **Subtítulos (Live Captions).**
- **Teclado en pantalla, teclas especiales (Sticky Keys, Filter Keys)** y control por voz.

Se accede desde Configuración → Accesibilidad. Parte del trabajo de soporte es empatizar con el usuario y dejar las opciones configuradas a su medida, no solo activarlas.

## 1.3 Securing and Maintaining Windows System Integrity (Seguridad e integridad del sistema)

- **Windows Update:** mantener el sistema y los drivers al día; solucionar actualizaciones bloqueadas.
- **Windows Security / Microsoft Defender:** antivirus, firewall y protección en tiempo real.
- **Cuentas y permisos:** cuentas locales frente a cuentas Microsoft, tipos de usuario (administrador / estándar) y UAC (Control de cuentas de usuario).
- **Herramientas de integridad del sistema:**

| Herramienta | Uso |
|---|---|
| `sfc /scannow` | Comprueba y repara archivos de sistema dañados |
| `DISM /Online /Cleanup-Image /RestoreHealth` | Repara la imagen de Windows cuando SFC no puede |
| `chkdsk` | Comprueba errores en el disco |
| Visor de eventos (Event Viewer) | Registros del sistema y aplicaciones para diagnosticar fallos |
| Administrador de tareas (Task Manager) | Procesos, rendimiento y programas de inicio |

### Para el examen
- Orden habitual de reparación de archivos del sistema: primero `sfc /scannow`, y si falla, `DISM`.
- El Visor de eventos es la primera parada para diagnosticar cierres inesperados de aplicaciones (app crashes).
- Una cuenta estándar no puede instalar software que requiera privilegios: el UAC pedirá credenciales de administrador.

## 1.4 Assisting Users with Cloud-Based Backup Tools (Copias de seguridad en la nube)

- **OneDrive** como herramienta principal de respaldo en la nube en Windows: sincronización de Escritorio, Documentos e Imágenes, historial de versiones y recuperación de archivos.
- Configurar la copia de seguridad de carpetas, resolver conflictos de sincronización y liberar espacio con "Archivos a petición".
- Alternativas y complementos: Historial de archivos (File History), puntos de restauración del sistema y copias de imagen completa.
- Regla general de respaldo: los datos del usuario deben existir en más de un sitio antes de tocar un equipo con problemas.

### Para el examen
- Antes de cualquier reparación agresiva (restablecer Windows, reinstalar), verificar que hay copia de seguridad de los datos del usuario.
- Historial de versiones de OneDrive permite recuperar un archivo sobrescrito o cifrado por ransomware.

## 1.5 Troubleshooting Boot and Startup Issues (Problemas de arranque)

Fallos de arranque (boot failures), de lo más crítico que atiende un técnico:

- **Secuencia de arranque:** firmware (BIOS/UEFI) → gestor de arranque (Windows Boot Manager) → carga del kernel → inicio de sesión. Localizar en qué fase falla orienta el diagnóstico.
- **Herramientas de recuperación (WinRE, Entorno de recuperación de Windows):**
  - Reparación de inicio (Startup Repair).
  - Modo seguro (Safe Mode) para arrancar con lo mínimo y aislar el fallo.
  - Restaurar sistema (System Restore) a un punto anterior.
  - Símbolo del sistema para reparaciones manuales (`bootrec /fixmbr`, `bootrec /fixboot`, `bootrec /rebuildbcd`).
  - Restablecer este PC (Reset this PC) como último recurso, conservando o no los archivos.
- Errores típicos: pantalla azul (BSOD) en el arranque, "Bootmgr is missing", bucles de reinicio.

### Para el examen
- Si Windows no arranca pero el modo seguro sí funciona, el problema es de software (driver o programa de inicio), no de hardware.
- WinRE se abre automáticamente tras varios arranques fallidos, o manualmente con Shift + Reiniciar.
- Orden lógico: Startup Repair → Modo seguro → Restaurar sistema → Reset this PC. De lo menos a lo más destructivo.

## 1.6 Resumen del Módulo 1

El módulo cubre los cinco frentes de soporte más habituales en Windows: pantalla/energía, accesibilidad, seguridad e integridad (Update, Defender, SFC/DISM, Visor de eventos), copias en la nube con OneDrive y recuperación del arranque con WinRE. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Troubleshooting Linux and macOS

**(Resolución de problemas en Linux y macOS)**

Ambos sistemas comparten raíz Unix, así que muchos conceptos (terminal, permisos, estructura de directorios) se estudian juntos.

---

## 2.1 Linux and macOS Tools and Features (Herramientas y características)

- **Linux:** distribuciones (Ubuntu, Fedora, Debian…), entornos de escritorio, la terminal como herramienta central de administración, gestores de paquetes (`apt`, `dnf`).
- **macOS:** Finder, Preferencias/Ajustes del Sistema, Spotlight, Terminal (zsh), App Store.
- Herramientas de monitorización equivalentes entre sistemas:

| Función | Windows | Linux | macOS |
|---|---|---|---|
| Procesos | Task Manager | `top` / `htop` / `ps` | Monitor de Actividad |
| Registros | Event Viewer | `journalctl`, `/var/log` | Consola (Console.app) |
| Discos | Disk Management | `lsblk`, `df` | Utilidad de Discos |

## 2.2 Linux and macOS Best Practices (Buenas prácticas)

- Mantener el sistema actualizado (gestor de paquetes en Linux; Actualización de Software en macOS).
- Trabajar con usuario estándar y elevar privilegios solo cuando toca (`sudo`).
- Copias de seguridad: **Time Machine** en macOS; herramientas como `rsync` o soluciones de la distribución en Linux.
- Gestión de permisos de archivos (usuario/grupo/otros, `chmod`, `chown`) como base de la seguridad.

## 2.3 Linux Virtualization (Virtualización)

- Uso de máquinas virtuales para ejecutar Linux sin tocar el sistema anfitrión: VirtualBox, VMware, Hyper-V.
- Conceptos: hipervisor (tipo 1 y tipo 2), máquina virtual, snapshot, recursos asignados (CPU, RAM, disco).
- Utilidad para el técnico: probar soluciones, reproducir fallos y practicar sin riesgo. Las snapshots permiten volver a un estado anterior en segundos.

### Para el examen
- Hipervisor tipo 1 corre directamente sobre el hardware (bare metal); tipo 2 corre sobre un SO anfitrión (VirtualBox, VMware Workstation).
- Una snapshot no sustituye a una copia de seguridad.

## 2.4 Basic Linux Commands Used in Troubleshooting (Comandos Linux para diagnóstico)

Comandos esenciales que el curso trabaja para diagnóstico (la referencia completa está en [recursos/linux-commands-reference.md](../../recursos/linux-commands-reference.md)):

| Ámbito | Comandos |
|---|---|
| Navegación y archivos | `pwd`, `ls`, `cd`, `cat`, `find`, `grep` |
| Sistema y procesos | `ps`, `top`, `kill`, `systemctl`, `journalctl` |
| Discos y memoria | `df -h`, `du -sh`, `free -h` |
| Red | `ip addr`, `ping`, `ss`, `traceroute`, `dig` |
| Permisos y usuarios | `chmod`, `chown`, `sudo`, `whoami`, `id` |

### Para el examen
- `journalctl` consulta los registros del sistema en distribuciones con systemd.
- `df -h` espacio en disco; `du -sh` tamaño de un directorio; `free -h` memoria.
- `sudo` ejecuta un comando con privilegios de root sin iniciar sesión como root.

## 2.5 Troubleshooting macOS

- **Problemas de arranque:** modo seguro (Safe Mode), recuperación de macOS (Recovery, Cmd+R), reinstalación del sistema, restauración desde Time Machine.
- **Aplicaciones que no responden:** Forzar salida (Cmd+Opt+Esc), Monitor de Actividad para localizar procesos problemáticos.
- **Mantenimiento:** Utilidad de Discos (Primera ayuda), gestión de elementos de inicio de sesión, permisos de apps en Privacidad y Seguridad.
- **Gestión de software:** instalación desde App Store o archivos `.dmg`/`.pkg`, Gatekeeper y apps de desarrolladores no identificados.

### Para el examen
- Time Machine es la herramienta nativa de copia de seguridad de macOS.
- Recovery (Cmd+R al arrancar) da acceso a Utilidad de Discos, reinstalación y restauración desde Time Machine.
- Forzar salida de una app colgada: Cmd + Opción + Esc.

## 2.6 Resumen del Módulo 2

Linux y macOS comparten fundamentos Unix: terminal, permisos y estructura de archivos. El técnico debe manejar las herramientas nativas de cada sistema (gestores de paquetes, Time Machine, Utilidad de Discos), los comandos básicos de diagnóstico y la virtualización como entorno de pruebas. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Troubleshooting Mobile Devices and Applications

**(Resolución de problemas en dispositivos y aplicaciones móviles)**

El soporte a móviles y tablets (Android e iOS) es ya parte del día a día del help desk, tanto en dispositivos corporativos como personales (BYOD).

---

## 3.1 Mobile Device Features (Características de los dispositivos móviles)

- Diferencias de plataforma: Android (Google, abierto, múltiples fabricantes) frente a iOS (Apple, ecosistema cerrado).
- Conectividad: Wi-Fi, datos móviles, Bluetooth, NFC, hotspot personal.
- Configuración habitual gestionada por soporte: cuentas de correo corporativo, certificados, redes Wi-Fi de empresa.

## 3.2 Troubleshooting Process for Mobile Devices (Proceso de diagnóstico)

El mismo método de 8 pasos del primer curso aplicado a móviles. Comprobaciones básicas antes de nada: reinicio del dispositivo, nivel de batería, versión del sistema, espacio libre, modo avión activado por error, conectividad.

## 3.3 Managing Mobile OS Security (Seguridad del SO móvil)

- Bloqueo de pantalla: PIN, patrón, huella, reconocimiento facial.
- Actualizaciones del sistema y parches de seguridad.
- Cifrado del dispositivo y localización/borrado remoto (Find My / Encontrar mi dispositivo).
- Gestión corporativa: MDM (Mobile Device Management) para aplicar políticas, distribuir apps y borrar datos de empresa.
- Riesgos: apps de orígenes desconocidos (sideloading), permisos excesivos, redes Wi-Fi abiertas.

### Para el examen
- MDM permite al departamento de TI gestionar y borrar remotamente dispositivos corporativos.
- El sideloading (instalar apps fuera de la tienda oficial) es el principal vector de malware en Android.

## 3.4 Common Issues and Solutions for Mobile Devices (Problemas comunes)

| Problema | Comprobaciones habituales |
|---|---|
| Batería se agota rápido | Apps en segundo plano, brillo, salud de la batería |
| Sobrecalentamiento | Carga + uso intensivo simultáneos, apps problemáticas |
| Sin conexión Wi-Fi/datos | Modo avión, olvidar y reconectar red, reinicio, APN |
| Bluetooth no empareja | Visibilidad, eliminar emparejamiento y repetirlo |
| Pantalla no responde | Reinicio forzado (combinación de botones según fabricante) |
| Almacenamiento lleno | Caché de apps, fotos/vídeos a la nube, apps sin uso |

## 3.5 Mobile Device Apps (Aplicaciones móviles)

- Ciclo de vida: instalación desde tiendas oficiales (Google Play / App Store), actualizaciones, permisos, desinstalación.
- Tipos de app: nativas, web e híbridas.
- Gestión de permisos (cámara, micrófono, ubicación…) como parte del soporte y de la privacidad del usuario.

## 3.6 Troubleshooting Mobile Device App Issues (Fallos de aplicaciones)

Secuencia estándar ante una app que falla o se cierra (app crash), de menos a más agresiva:

1. Cerrar la app por completo y reabrirla.
2. Reiniciar el dispositivo.
3. Buscar actualizaciones de la app y del sistema.
4. Borrar la caché de la app (Android).
5. Borrar los datos de la app o reinstalarla (implica perder configuración local).
6. Comprobar compatibilidad de la app con la versión del SO.

### Para el examen
- El orden importa: siempre de la acción menos destructiva a la más destructiva.
- Borrar caché no elimina datos del usuario; borrar datos sí.

## 3.7 The Cloud (La nube)

- Sincronización y copia de seguridad del móvil en la nube: Google (Android) e iCloud (iOS).
- Qué se respalda: contactos, fotos, ajustes, apps y sus datos.
- Restauración de un dispositivo desde la copia en la nube (cambio o pérdida de terminal).
- Modelos de servicio en la nube que el curso introduce: SaaS, PaaS, IaaS.

### Para el examen
- iCloud respalda dispositivos iOS; la cuenta de Google respalda Android.
- SaaS = software listo para usar (Gmail, Office 365); IaaS = infraestructura (servidores, almacenamiento); PaaS = plataforma para desarrollar.

## 3.8 Resumen del Módulo 3

El soporte móvil aplica el mismo método de troubleshooting con particularidades propias: seguridad gestionada por MDM, fallos típicos de batería/conectividad/almacenamiento, diagnóstico de apps por pasos de menor a mayor impacto y respaldo en la nube como red de seguridad. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El curso cierra con el **Operating Systems Support Course Final Exam** (y una encuesta de satisfacción que no puntúa). Repasa especialmente:

1. Herramientas de integridad de Windows: `sfc /scannow`, `DISM`, `chkdsk`, Visor de eventos.
2. Recuperación del arranque: WinRE, modo seguro, Startup Repair, `bootrec`, y su orden de aplicación.
3. Equivalencias de herramientas entre Windows, Linux y macOS (procesos, logs, discos).
4. Comandos Linux de diagnóstico y qué hace cada uno.
5. macOS: Time Machine, Recovery (Cmd+R), Forzar salida.
6. Móviles: MDM, secuencia de resolución de fallos de apps, copia en la nube (iCloud / Google).
7. Hipervisores tipo 1 y tipo 2; snapshot frente a copia de seguridad.
8. Modelos cloud: SaaS, PaaS, IaaS.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1 — Windows:** *display driver · power plan · Safe Mode · accessibility (Narrator, Magnifier, Sticky Keys) · Windows Update · Microsoft Defender · UAC · standard vs. administrator account · `sfc /scannow` · DISM · chkdsk · Event Viewer · Task Manager · OneDrive · File History · System Restore · WinRE · Startup Repair · `bootrec` · BSOD · boot failure*

**Módulo 2 — Linux y macOS:** *distribution · package manager (apt, dnf) · terminal · `sudo` · file permissions (`chmod`, `chown`) · `journalctl` · `systemctl` · `df` / `du` / `free` · virtualization · hypervisor type 1/2 · virtual machine · snapshot · Time Machine · Disk Utility · Activity Monitor · Recovery Mode · Gatekeeper · Force Quit · Spotlight*

**Módulo 3 — Móviles:** *Android · iOS · BYOD · MDM (Mobile Device Management) · screen lock · device encryption · remote wipe · Find My · sideloading · app permissions · app crash · clear cache vs. clear data · APN · NFC · hotspot · iCloud backup · Google backup · SaaS · PaaS · IaaS*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **App crash** | Cierre inesperado de una aplicación. Se diagnostica con registros (Visor de eventos, Console, logs de la app) y se resuelve por pasos de menor a mayor impacto. |
| **BIOS/UEFI** | Firmware que inicializa el hardware y cede el control al gestor de arranque. UEFI es el sucesor moderno de BIOS. |
| **Boot failure (fallo de arranque)** | Incapacidad del sistema para completar la secuencia de arranque. Se diagnostica identificando la fase en la que se detiene. |
| **BSOD (Blue Screen of Death)** | Pantalla azul de error crítico de Windows; el código de detención (stop code) orienta el diagnóstico. |
| **BYOD (Bring Your Own Device)** | Política que permite usar dispositivos personales para el trabajo, normalmente gestionados parcialmente por MDM. |
| **chkdsk** | Comando de Windows que comprueba y repara errores del sistema de archivos en disco. |
| **DISM** | Herramienta de Windows que repara la imagen del sistema cuando `sfc` no puede completar la reparación. |
| **Driver (controlador)** | Software que permite al sistema operativo comunicarse con un componente de hardware. |
| **Event Viewer (Visor de eventos)** | Consola de Windows que registra eventos del sistema, seguridad y aplicaciones. |
| **Gatekeeper** | Mecanismo de macOS que restringe la ejecución de aplicaciones no firmadas o de desarrolladores no identificados. |
| **Hipervisor** | Software que crea y ejecuta máquinas virtuales. Tipo 1: sobre el hardware directamente. Tipo 2: sobre un SO anfitrión. |
| **IaaS / PaaS / SaaS** | Modelos de servicio cloud: infraestructura, plataforma y software, respectivamente. |
| **journalctl** | Comando de Linux (systemd) para consultar los registros del sistema. |
| **MDM (Mobile Device Management)** | Plataforma de gestión remota de dispositivos móviles: políticas, apps, cifrado y borrado remoto. |
| **Modo seguro (Safe Mode)** | Arranque con el mínimo de drivers y servicios, usado para aislar fallos de software. Existe en Windows, macOS y Android. |
| **OneDrive** | Servicio de almacenamiento y copia de seguridad en la nube de Microsoft, integrado en Windows. |
| **Recovery (macOS)** | Entorno de recuperación de macOS (Cmd+R al arrancar): Utilidad de Discos, reinstalación y restauración de Time Machine. |
| **Sideloading** | Instalación de aplicaciones fuera de la tienda oficial; principal vector de malware en móviles. |
| **sfc /scannow** | Comando de Windows que verifica y repara archivos de sistema dañados. |
| **Snapshot** | Captura del estado de una máquina virtual en un momento dado, que permite volver a ese estado. |
| **System Restore (Restaurar sistema)** | Función de Windows que devuelve el sistema a un punto de restauración anterior sin afectar a los archivos personales. |
| **Time Machine** | Herramienta nativa de copia de seguridad de macOS. |
| **UAC (User Account Control)** | Mecanismo de Windows que solicita confirmación o credenciales de administrador ante acciones con privilegios. |
| **Virtualización** | Ejecución de sistemas operativos completos en máquinas virtuales sobre un mismo hardware físico. |
| **WinRE** | Entorno de recuperación de Windows: Startup Repair, modo seguro, System Restore, símbolo del sistema y Reset this PC. |

[⬆ Volver al índice](#índice)

---

Manual de repaso del curso Cisco NetAcad «Operating Systems Support», segundo curso de la serie alineada con el CCST IT Support cursado desde Barcelona Activa. Material libre para compartir con la clase.
