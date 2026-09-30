[← Volver a la página principal del repositorio](../../README.md)

# Security and Connectivity Support

> **Objetivo del curso:** diagnosticar y resolver problemas de conectividad de todo tipo (periféricos, red local, recursos compartidos) y construir una base sólida de ciberseguridad: identificar amenazas, reconocer tácticas de ingeniería social y aplicar las políticas de la empresa para proteger los datos.

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [0. Introducción al curso](#0-introducción-al-curso)
- [Módulo 1 — Troubleshooting Common Services and Peripheral Connectivity Issues](#módulo-1--troubleshooting-common-services-and-peripheral-connectivity-issues)
  - [1.1 Directory Services and Shared Drives](#11-directory-services-and-shared-drives-servicios-de-directorio-y-unidades-compartidas)
  - [1.2 User Connectivity Issues](#12-user-connectivity-issues-problemas-de-conectividad-del-usuario)
  - [1.3 Peripheral Connectivity](#13-peripheral-connectivity-conectividad-de-periféricos)
  - [1.4 Resumen del Módulo 1](#14-resumen-del-módulo-1)
- [Módulo 2 — Troubleshooting Common Network Connectivity Issues](#módulo-2--troubleshooting-common-network-connectivity-issues)
  - [2.1 Network Types](#21-network-types-tipos-de-redes)
  - [2.2 Wired Networks](#22-wired-networks-redes-cableadas)
  - [2.3 Wireless Networks](#23-wireless-networks-redes-inalámbricas)
  - [2.4 IP Addressing](#24-ip-addressing-direccionamiento-ip)
  - [2.5 Communicating Between Networks](#25-communicating-between-networks-comunicación-entre-redes)
  - [2.6 DNS and DHCP](#26-dns-and-dhcp)
  - [2.7 Firewalls](#27-firewalls-cortafuegos)
  - [2.8 Using Commands to Verify and Troubleshoot Connectivity](#28-using-commands-to-verify-and-troubleshoot-connectivity-comandos-de-diagnóstico)
  - [2.9 Resumen del Módulo 2](#29-resumen-del-módulo-2)
- [Módulo 3 — Troubleshooting Common Security Issues](#módulo-3--troubleshooting-common-security-issues)
  - [3.1 Current State of Cybersecurity](#31-current-state-of-cybersecurity-estado-actual-de-la-ciberseguridad)
  - [3.2 Threat Actors](#32-threat-actors-actores-de-amenaza)
  - [3.3 Malware](#33-malware)
  - [3.4 Common Network Attacks](#34-common-network-attacks-ataques-de-red-comunes)
  - [3.5 Help Desk Technician Security Awareness](#35-help-desk-technician-security-awareness-concienciación-del-técnico)
  - [3.6 Security Incident Response](#36-security-incident-response-respuesta-a-incidentes)
  - [3.7 Protecting Data](#37-protecting-data-protección-de-datos)
  - [3.8 Resumen del Módulo 3](#38-resumen-del-módulo-3)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del apartado correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. El Módulo 2 conecta directamente con la práctica de [Packet Tracer y redes básicas](../../recursos/packet-tracer-redes-basicas.md) del repositorio; repásala en paralelo.

---

# 0. Introducción al curso

Tercer curso de la serie de 4 del *IT Support Specialist Career Path*, orientado al CCST IT Support. La premisa del curso: conectividad y seguridad son dos caras de la misma moneda, porque cada conexión es también una vulnerabilidad potencial.

Tres bloques: conectividad de servicios y periféricos (Módulo 1), conectividad de red (Módulo 2) y seguridad (Módulo 3).

[⬆ Volver al índice](#índice)

---

# MÓDULO 1 — Troubleshooting Common Services and Peripheral Connectivity Issues

**(Resolución de problemas de servicios comunes y conectividad de periféricos)**

Los tickets más frecuentes del help desk: el usuario no puede acceder a una carpeta compartida, no puede iniciar sesión o la impresora no responde.

---

## 1.1 Directory Services and Shared Drives (Servicios de directorio y unidades compartidas)

- **Servicios de directorio:** base de datos centralizada de usuarios, equipos y recursos de la organización. El estándar en empresas es **Active Directory (AD)** de Microsoft, con autenticación centralizada mediante **dominio**.
- Conceptos: dominio, unidad organizativa (OU), cuenta de usuario y de equipo, grupos y pertenencia a grupos, políticas de grupo (GPO).
- **Unidades compartidas y permisos:** carpetas de red compartidas, mapeo de unidades (letra de unidad → ruta UNC `\\servidor\recurso`), permisos de recurso compartido frente a permisos NTFS.
- Fallos habituales: usuario sin permiso al recurso (pertenencia a grupos), unidad mapeada que no conecta (credenciales caducadas, servidor inaccesible), bloqueo de cuenta por intentos fallidos.

### Para el examen
- Ruta UNC: `\\servidor\carpeta`. Mapear una unidad: `net use Z: \\servidor\carpeta`.
- Si un usuario no accede a un recurso compartido, comprobar primero su pertenencia a los grupos con permiso.
- Cuenta bloqueada (account lockout) ≠ contraseña caducada: son incidencias distintas con soluciones distintas.

## 1.2 User Connectivity Issues (Problemas de conectividad del usuario)

- Diagnóstico por capas, de lo físico a lo lógico: ¿tiene enlace el cable o el Wi-Fi? → ¿tiene IP válida? → ¿resuelve nombres? → ¿llega al recurso?
- Problemas típicos: sin conexión tras cambiar de sitio (roseta/puerto), IP de autoconfiguración (APIPA 169.254.x.x) por fallo de DHCP, proxy o VPN mal configurados, credenciales de dominio caducadas.
- Aplicar el proceso de troubleshooting de 8 pasos del [primer curso](it-customer-support-basics.md), documentando cada comprobación.

### Para el examen
- Una IP 169.254.x.x (APIPA) indica que el cliente no ha podido contactar con el servidor DHCP.
- Orden de diagnóstico: físico → IP → DNS → aplicación.

## 1.3 Peripheral Connectivity (Conectividad de periféricos)

- **Tipos de conexión:** USB (versiones y conectores), Bluetooth, red (impresoras IP), audio/vídeo (HDMI, DisplayPort).
- **Impresoras**, el periférico estrella del help desk: instalación local frente a impresora de red, colas de impresión atascadas (reiniciar el servicio Print Spooler), drivers incorrectos, impresora sin conexión.
- Otros periféricos: teclado/ratón, monitores, auriculares, escáneres, webcams. Comprobaciones: cable y puerto, driver, dispositivo predeterminado del sistema, permisos de la app (cámara/micrófono).
- Bluetooth: emparejamiento, visibilidad, distancia e interferencias, eliminar y volver a emparejar.

### Para el examen
- Cola de impresión atascada en Windows: reiniciar el servicio **Print Spooler**.
- Si un dispositivo USB no responde, probar en otro puerto y en otro equipo para aislar si falla el dispositivo o el puerto.

## 1.4 Resumen del Módulo 1

El módulo cubre el acceso a recursos corporativos (Active Directory, unidades compartidas, permisos), el diagnóstico de conectividad del puesto de usuario por capas y el soporte de periféricos, con las impresoras como caso más habitual. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Troubleshooting Common Network Connectivity Issues

**(Resolución de problemas comunes de conectividad de red)**

Fundamentos de redes aplicados al soporte: entender cómo viaja el tráfico para poder diagnosticar dónde se corta.

---

## 2.1 Network Types (Tipos de redes)

- **LAN** (red local), **WAN** (red de área amplia, interconecta LANs), **WLAN** (LAN inalámbrica), **PAN** (área personal, Bluetooth).
- Dispositivos de red y su función: **switch** (conmuta tramas dentro de la LAN, capa 2), **router** (encamina paquetes entre redes, capa 3), **punto de acceso** (AP, extiende la LAN por Wi-Fi), módem/ONT (acceso al proveedor).

## 2.2 Wired Networks (Redes cableadas)

- Cableado de cobre de par trenzado (categorías 5e/6/6a), conector RJ-45, fibra óptica para enlaces troncales.
- Velocidades Ethernet habituales: 100 Mbps / 1 Gbps / 10 Gbps.
- Diagnóstico físico: luces de enlace (link/activity) en la tarjeta y el switch, cables dañados, rosetas y latiguillos, puerto del switch deshabilitado.

## 2.3 Wireless Networks (Redes inalámbricas)

- Estándares **802.11** (Wi-Fi 4/5/6: n, ac, ax) y bandas de **2,4 GHz** (más alcance, más interferencias) frente a **5 GHz** (más velocidad, menos alcance).
- Conceptos: SSID, canal, intensidad de señal, itinerancia entre APs.
- Seguridad inalámbrica: **WPA2 / WPA3** (nunca WEP ni redes abiertas para uso corporativo).
- Problemas típicos: señal débil (distancia, obstáculos), interferencias (canal saturado), contraseña incorrecta, filtrado MAC, banda incompatible con el dispositivo.

### Para el examen
- 2,4 GHz = alcance; 5 GHz = velocidad. Comparación clásica.
- WEP está obsoleto e inseguro; el estándar actual es WPA3 (WPA2 aún aceptado).

## 2.4 IP Addressing (Direccionamiento IP)

- **IPv4:** 32 bits, notación decimal con puntos. Partes de red y de host definidas por la **máscara de subred** (`255.255.255.0` = `/24`).
- Direcciones **privadas** (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) frente a **públicas**; **NAT** traduce entre ambas.
- Direcciones especiales: loopback (127.0.0.1), broadcast, APIPA (169.254.0.0/16).
- **IPv6:** 128 bits, notación hexadecimal con dos puntos; convive con IPv4 (dual stack).
- Asignación **estática** frente a **dinámica** (DHCP).

### Para el examen
- Reconocer los tres rangos privados de IPv4 y saber que necesitan NAT para salir a internet.
- 127.0.0.1 = loopback: probarlo verifica la pila TCP/IP local, no la red.

## 2.5 Communicating Between Networks (Comunicación entre redes)

- Para salir de la subred, el host envía el tráfico a su **default gateway** (la interfaz del router en su red).
- El router encamina paquetes entre redes consultando su **tabla de enrutamiento**.
- Repaso del modelo de referencia: MAC (capa 2, local) frente a IP (capa 3, extremo a extremo); ARP resuelve IP → MAC dentro de la subred.
- Práctica relacionada del repositorio: [Packet Tracer y redes básicas](../../recursos/packet-tracer-redes-basicas.md) (enrutamiento entre dos subredes con un router).

### Para el examen
- Sin default gateway configurado, el host solo se comunica dentro de su propia subred.
- ARP funciona solo en la red local; los routers no reenvían broadcasts.

## 2.6 DNS and DHCP

| Servicio | Qué hace | Fallo típico |
|---|---|---|
| **DHCP** | Asigna automáticamente IP, máscara, gateway y DNS al cliente (proceso DORA: Discover, Offer, Request, Acknowledge) | Cliente con APIPA 169.254.x.x; ámbito agotado |
| **DNS** | Traduce nombres de dominio a direcciones IP | "Funciona el ping a la IP pero no al nombre" |

- Comandos de diagnóstico: `ipconfig /release` y `/renew` (renovar DHCP), `ipconfig /flushdns` (vaciar caché DNS), `nslookup` (consultar resolución de nombres).

### Para el examen
- Si `ping 8.8.8.8` funciona pero `ping google.com` no, el problema es DNS.
- DORA: la secuencia de mensajes DHCP, en ese orden.

## 2.7 Firewalls (Cortafuegos)

- Filtran el tráfico según reglas (puertos, protocolos, orígenes/destinos permitidos o bloqueados).
- Tipos: firewall de red (perímetro) y firewall de host (Windows Defender Firewall, `ufw` en Linux).
- Impacto en soporte: una app que no conecta puede estar bloqueada por regla de firewall; verificar reglas antes de culpar a la red.
- Puertos habituales que conviene memorizar:

| Puerto | Servicio |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 67/68 | DHCP |
| 80 / 443 | HTTP / HTTPS |
| 3389 | RDP |
| 25/587, 143/993, 110/995 | SMTP, IMAP, POP3 |

### Para el examen
- El firewall de host puede bloquear una app aunque la red funcione perfectamente.
- HTTPS = 443; HTTP = 80. Aparecen constantemente.

## 2.8 Using Commands to Verify and Troubleshoot Connectivity (Comandos de diagnóstico)

| Comando (Windows) | Uso |
|---|---|
| `ipconfig /all` | Ver IP, máscara, gateway, DNS y MAC del equipo |
| `ping [host]` | Probar alcance a un host (ICMP) |
| `tracert [host]` | Ver la ruta salto a salto hasta el destino |
| `nslookup [nombre]` | Comprobar la resolución DNS |
| `netstat -an` | Conexiones activas y puertos en escucha |
| `arp -a` | Tabla ARP local |
| `net use` | Unidades de red mapeadas |

Equivalentes en Linux/macOS: `ip addr`, `ping`, `traceroute`, `dig`, `ss` (referencia completa en [recursos/linux-commands-reference.md](../../recursos/linux-commands-reference.md)).

**Secuencia clásica de diagnóstico de conectividad:**

1. `ipconfig /all` — ¿tengo IP válida?
2. `ping 127.0.0.1` — ¿funciona mi pila TCP/IP?
3. `ping` al default gateway — ¿llego a mi router?
4. `ping` a una IP externa (8.8.8.8) — ¿salgo a internet?
5. `nslookup` / `ping` a un nombre — ¿funciona el DNS?

### Para el examen
- Memoriza la secuencia anterior; las preguntas de escenario piden el siguiente comando lógico.
- `tracert` (Windows) = `traceroute` (Linux/macOS).

## 2.9 Resumen del Módulo 2

El módulo recorre los fundamentos de red que necesita el soporte: tipos de red y dispositivos, medios cableados e inalámbricos, direccionamiento IP, enrutamiento entre redes, DNS/DHCP, firewalls y la batería de comandos para diagnosticar conectividad paso a paso. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Troubleshooting Common Security Issues

**(Resolución de problemas comunes de seguridad)**

El técnico de soporte es la primera línea de defensa: detecta incidentes, orienta a los usuarios y aplica las políticas de seguridad de la empresa.

---

## 3.1 Current State of Cybersecurity (Estado actual de la ciberseguridad)

- Panorama de amenazas: los ataques crecen en volumen y sofisticación, y el factor humano sigue siendo el eslabón más débil.
- La tríada **CIA**: **Confidencialidad** (solo accede quien debe), **Integridad** (los datos no se alteran sin autorización) y **Disponibilidad** (los sistemas funcionan cuando se necesitan).
- Coste de las brechas: pérdida de datos, interrupción del negocio, sanciones (RGPD en Europa) y daño reputacional.

### Para el examen
- CIA = Confidentiality, Integrity, Availability. Saber clasificar un incidente según qué principio viola.

## 3.2 Threat Actors (Actores de amenaza)

| Actor | Perfil y motivación |
|---|---|
| **Script kiddies** | Sin conocimientos profundos; usan herramientas de otros por diversión o notoriedad |
| **Hacktivistas** | Motivación ideológica o política |
| **Cibercriminales** | Motivación económica; el grupo más activo |
| **Insiders (amenaza interna)** | Empleados o exempleados, por malicia o negligencia |
| **Estados / APT** | Grupos patrocinados por estados, ataques persistentes y sofisticados |

- Sombreros: white hat (hacking ético autorizado), black hat (malicioso), gray hat (zona intermedia).

## 3.3 Malware

| Tipo | Característica |
|---|---|
| **Virus** | Se adjunta a archivos legítimos; requiere ejecución del usuario |
| **Gusano (worm)** | Se propaga solo por la red, sin intervención del usuario |
| **Troyano** | Se disfraza de software legítimo |
| **Ransomware** | Cifra los datos y exige rescate |
| **Spyware / keylogger** | Espía la actividad y roba información |
| **Adware** | Publicidad no deseada, a menudo con rastreo |
| **Rootkit** | Se oculta con privilegios elevados; muy difícil de detectar |

- Señales de infección: lentitud repentina, ventanas emergentes, procesos desconocidos, tráfico de red anómalo, archivos cifrados.
- Respuesta básica del técnico: aislar el equipo de la red, no pagar rescates, escanear con el antivirus corporativo y escalar según el protocolo.

### Para el examen
- Virus necesita al usuario; el gusano se propaga solo. Distinción clásica.
- Ante ransomware: aislar el equipo y escalar de inmediato; la copia de seguridad es la mejor defensa.

## 3.4 Common Network Attacks (Ataques de red comunes)

- **Ingeniería social:** manipular personas para obtener acceso o información. Variantes:
  - **Phishing** (correo masivo fraudulento), **spear phishing** (dirigido a una persona concreta), **whaling** (dirigido a directivos), **smishing** (SMS), **vishing** (llamadas).
  - **Pretexting** (inventar un escenario creíble), **baiting** (cebo, p. ej. USB abandonado), **tailgating** (colarse físicamente tras un empleado).
- **Ataques técnicos:** denegación de servicio (**DoS/DDoS**), **man-in-the-middle** (interceptar la comunicación), ataques de contraseña (fuerza bruta, diccionario, relleno de credenciales), suplantación (spoofing) de IP/MAC/DNS.

### Para el examen
- Saber clasificar el escenario: correo falso del banco = phishing; llamada del "soporte técnico" pidiendo la contraseña = vishing + pretexting; USB en el parking = baiting.
- Ningún departamento de TI legítimo pide contraseñas por teléfono o correo.

## 3.5 Help Desk Technician Security Awareness (Concienciación del técnico)

- El técnico maneja credenciales e información sensible: es objetivo prioritario de la ingeniería social.
- Buenas prácticas: verificar la identidad de quien llama antes de actuar sobre cuentas, no compartir credenciales jamás, bloquear la sesión al levantarse, cumplir la política de contraseñas (longitud, unicidad, gestor de contraseñas) y activar **MFA** (autenticación multifactor).
- Principio de **mínimo privilegio**: cada cuenta solo con los permisos imprescindibles.
- Reconocer intentos de manipulación dirigidos al propio help desk (restablecimientos de contraseña fraudulentos).

### Para el examen
- Antes de restablecer una contraseña por teléfono: verificar la identidad del solicitante según el procedimiento de la empresa.
- MFA combina dos o más factores: algo que sabes, algo que tienes, algo que eres.

## 3.6 Security Incident Response (Respuesta a incidentes)

- Qué es un **incidente de seguridad** y en qué se diferencia de una incidencia normal de TI.
- Papel del técnico de nivel 1: **detectar, contener lo inmediato (aislar el equipo), documentar y escalar** al equipo de seguridad según el plan de respuesta; no investigar por su cuenta ni destruir evidencias.
- Fases habituales de la respuesta a incidentes: preparación → detección y análisis → contención → erradicación → recuperación → lecciones aprendidas.
- Importancia de registrar todo: hora, síntomas, acciones tomadas, personas notificadas.

### Para el examen
- El técnico de soporte no elimina el malware por su cuenta en un incidente corporativo: contiene, documenta y escala.
- Apagar el equipo puede destruir evidencia; la pauta general es aislarlo de la red y seguir el protocolo.

## 3.7 Protecting Data (Protección de datos)

- **Cifrado:** en reposo (BitLocker, FileVault) y en tránsito (HTTPS, VPN).
- **Copias de seguridad:** regla **3-2-1** (3 copias, 2 soportes distintos, 1 fuera de las instalaciones); probar la restauración periódicamente.
- **Clasificación de la información** (pública, interna, confidencial) y manejo según la política de la empresa.
- **Normativa:** protección de datos personales (RGPD en Europa); el técnico debe tratar los datos de usuarios con confidencialidad.
- Borrado seguro de soportes antes de desechar o reutilizar equipos.

### Para el examen
- Regla 3-2-1 de backups: aparece con frecuencia.
- Cifrado en reposo (disco) frente a cifrado en tránsito (comunicaciones): saber cuál aplica en cada escenario.

## 3.8 Resumen del Módulo 3

El módulo forma al técnico como primera línea de defensa: entender el panorama de amenazas (actores, malware, ataques e ingeniería social), aplicar hábitos seguros en el propio puesto, actuar correctamente ante un incidente (contener, documentar, escalar) y proteger los datos con cifrado, copias y cumplimiento normativo. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El curso cierra con el **Security and Connectivity Support Course Final Exam** (y una encuesta de satisfacción que no puntúa). Repasa especialmente:

1. Active Directory, rutas UNC, permisos de recursos compartidos y bloqueos de cuenta.
2. La secuencia de diagnóstico de conectividad con comandos (`ipconfig` → loopback → gateway → IP externa → DNS).
3. APIPA 169.254.x.x = fallo de DHCP; ping a IP funciona pero a nombre no = fallo de DNS.
4. Rangos IP privados, NAT, default gateway y el papel de ARP.
5. 2,4 GHz frente a 5 GHz y seguridad Wi-Fi (WPA2/WPA3).
6. Puertos: SSH 22, DNS 53, HTTP 80, HTTPS 443, RDP 3389, correo (25/587, 143/993, 110/995).
7. Tipos de malware (virus/gusano/troyano/ransomware) y variantes de ingeniería social (phishing, vishing, smishing, tailgating, baiting).
8. Tríada CIA, MFA, mínimo privilegio, regla 3-2-1 y el papel del técnico en la respuesta a incidentes: contener, documentar, escalar.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1 — Servicios y periféricos:** *directory services · Active Directory · domain · group membership · GPO · shared drive · mapped drive · UNC path · `net use` · share vs. NTFS permissions · account lockout · APIPA · print spooler · print queue · driver · Bluetooth pairing · USB troubleshooting*

**Módulo 2 — Redes:** *LAN · WAN · WLAN · switch · router · access point · Ethernet · RJ-45 · 802.11 · 2.4 GHz vs. 5 GHz · SSID · WPA2/WPA3 · IPv4 · IPv6 · subnet mask · CIDR · private vs. public IP · NAT · loopback · default gateway · routing table · ARP · DHCP (DORA) · DNS · firewall · port numbers · `ipconfig` · `ping` · `tracert` · `nslookup` · `netstat`*

**Módulo 3 — Seguridad:** *CIA triad · threat actor · insider threat · white/black/gray hat · malware · virus · worm · trojan · ransomware · spyware · rootkit · social engineering · phishing · spear phishing · whaling · smishing · vishing · pretexting · baiting · tailgating · DoS/DDoS · man-in-the-middle · brute force · spoofing · MFA · least privilege · incident response · escalation · encryption at rest / in transit · backup 3-2-1 · GDPR/RGPD · data classification*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **Active Directory (AD)** | Servicio de directorio de Microsoft: gestiona de forma centralizada usuarios, equipos, grupos y políticas de un dominio. |
| **APIPA** | Dirección 169.254.x.x que se autoasigna un cliente Windows cuando no logra contactar con el servidor DHCP. |
| **ARP** | Protocolo que resuelve direcciones IP a direcciones MAC dentro de la red local. |
| **Baiting** | Ingeniería social basada en un cebo físico o digital (p. ej., un USB abandonado con malware). |
| **CIA (tríada)** | Confidencialidad, Integridad y Disponibilidad: los tres principios básicos de la seguridad de la información. |
| **Default gateway** | Interfaz del router en la red local; punto de salida del tráfico hacia otras redes. |
| **DHCP** | Protocolo que asigna automáticamente la configuración IP a los clientes (secuencia DORA). |
| **DNS** | Sistema que traduce nombres de dominio a direcciones IP. Puerto 53. |
| **DoS / DDoS** | Ataque de denegación de servicio; la variante distribuida usa muchos equipos a la vez. |
| **Firewall** | Dispositivo o software que filtra el tráfico de red según reglas de puertos, protocolos y direcciones. |
| **GPO (Group Policy Object)** | Política de grupo de Active Directory que aplica configuraciones a usuarios y equipos del dominio. |
| **Insider threat** | Amenaza interna: empleado o exempleado que causa daño por malicia o negligencia. |
| **Man-in-the-middle** | Ataque que intercepta y puede alterar la comunicación entre dos partes sin que lo sepan. |
| **MFA (autenticación multifactor)** | Verificación con dos o más factores: algo que sabes, algo que tienes, algo que eres. |
| **Mínimo privilegio** | Principio por el que cada cuenta tiene solo los permisos imprescindibles para su función. |
| **NAT** | Traducción de direcciones de red: permite que IPs privadas salgan a internet con una IP pública. |
| **Phishing** | Correo fraudulento que suplanta a una entidad legítima para robar credenciales o datos. Variantes: spear phishing (dirigido), whaling (directivos), smishing (SMS), vishing (voz). |
| **Pretexting** | Ingeniería social basada en inventar un escenario creíble para obtener información. |
| **Print Spooler** | Servicio de Windows que gestiona la cola de impresión; reiniciarlo resuelve colas atascadas. |
| **Ransomware** | Malware que cifra los datos de la víctima y exige un rescate por recuperarlos. |
| **Regla 3-2-1** | Estrategia de copias de seguridad: 3 copias, en 2 soportes distintos, 1 fuera de las instalaciones. |
| **RGPD (GDPR)** | Reglamento europeo de protección de datos personales. |
| **Rootkit** | Malware que se oculta en el sistema con privilegios elevados, muy difícil de detectar y eliminar. |
| **Spoofing** | Suplantación de una identidad de red (IP, MAC, DNS, correo) para engañar a sistemas o personas. |
| **SSID** | Nombre que identifica una red inalámbrica. |
| **Tailgating** | Acceso físico no autorizado colándose tras una persona con credenciales. |
| **Troyano** | Malware que se disfraza de software legítimo para que el usuario lo instale. |
| **UNC (ruta)** | Formato `\\servidor\recurso` para acceder a recursos compartidos de red. |
| **Virus / Gusano** | El virus se adjunta a archivos y requiere ejecución del usuario; el gusano se propaga solo por la red. |
| **VPN** | Túnel cifrado entre el equipo y la red corporativa a través de una red pública. |
| **WPA2 / WPA3** | Protocolos actuales de seguridad Wi-Fi; sustituyen al obsoleto WEP. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Security and Connectivity Support», tercer curso de la serie alineada con el CCST IT Support cursado desde Barcelona Activa. Material libre para compartir con la clase.*
