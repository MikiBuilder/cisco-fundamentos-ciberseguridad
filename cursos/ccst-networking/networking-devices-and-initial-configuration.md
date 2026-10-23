[← Volver a la página principal del repositorio](../../README.md)

# Manual de Estudio — Networking Devices and Initial Configuration

> **Objetivo del curso:** profundizar en los fundamentos de red: diseño jerárquico, cloud y virtualización, sistemas de numeración, conmutación Ethernet, capa de red y de transporte, y la configuración inicial de dispositivos Cisco con IOS. Segundo curso de la serie CCST Networking, continuación de [Networking Basics](networking-basics.md).

**Estado de estos apuntes:** curso completo. Cubren los 12 módulos, los 4 checkpoint exams y el examen final (22 horas, 19 labs).

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Network Design](#módulo-1--network-design)
- [Módulo 2 — Cloud and Virtualization](#módulo-2--cloud-and-virtualization)
- [Módulo 3 — Number Systems](#módulo-3--number-systems)
- [Checkpoint Exam: módulos 1 a 3](#checkpoint-exam-módulos-1-a-3)
- [Módulo 4 — Ethernet Switching](#módulo-4--ethernet-switching)
- [Módulo 5 — Network Layer](#módulo-5--network-layer)
- [Módulo 6 — IPv4 Addressing](#módulo-6--ipv4-addressing)
- [Checkpoint Exam: módulos 4 a 6](#checkpoint-exam-módulos-4-a-6)
- [Módulo 7 — Address Resolution](#módulo-7--address-resolution)
- [Módulo 8 — IP Addressing Services](#módulo-8--ip-addressing-services)
- [Módulo 9 — Transport Layer](#módulo-9--transport-layer)
- [Checkpoint Exam: módulos 7 a 9](#checkpoint-exam-módulos-7-a-9)
- [Módulo 10 — The Cisco IOS Command Line](#módulo-10--the-cisco-ios-command-line)
- [Módulo 11 — Build a Small Cisco Network](#módulo-11--build-a-small-cisco-network)
- [Módulo 12 — ICMP](#módulo-12--icmp)
- [Checkpoint Exam: módulos 10 a 12](#checkpoint-exam-módulos-10-a-12)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del módulo correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST Networking aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Este curso repite y amplía temas de Networking Basics (Ethernet, IPv4, ARP, DNS/DHCP, TCP/UDP): si algo no suena, conviene releer el [manual anterior](networking-basics.md).

---

# MÓDULO 1 — Network Design

**(Diseño de redes)**

## 1.1 Reliable Networks (Redes fiables)

Una red bien diseñada cumple **cuatro requisitos básicos**:

| Requisito | Qué significa | Ejemplo |
|---|---|---|
| **Tolerancia a fallos (fault tolerance)** | La red sigue funcionando aunque falle un componente: rutas y enlaces redundantes | Se corta una fibra y el tráfico se desvía por otro camino sin que los usuarios lo noten |
| **Escalabilidad (scalability)** | Crece para admitir nuevos usuarios y servicios sin degradar lo existente | Añadir voz y vídeo a una red de datos |
| **Calidad de servicio (QoS)** | Prioriza el tráfico sensible al retardo cuando hay congestión | La voz y el vídeo pasan antes que una descarga |
| **Seguridad (security)** | Protege la infraestructura y la información: confidencialidad, integridad y disponibilidad | Credenciales de acceso, cifrado, control físico de los equipos |

- La redundancia se implementa con múltiples caminos: si un enlace o dispositivo cae, hay alternativa. Internet mismo funciona así (conmutación de paquetes: cada paquete puede tomar rutas distintas).

## 1.2 Hierarchical Network Design (Diseño jerárquico)

- **Topología física:** cómo están conectados realmente los dispositivos y los cables. **Topología lógica:** cómo fluyen los datos por la red. No tienen por qué coincidir.
- Las redes grandes se organizan en un **modelo de tres capas**; cada una tiene una función concreta:

| Capa | Función | Dispositivos típicos |
|---|---|---|
| **Acceso (access)** | Conecta los dispositivos finales (hosts) a la red | Switches de planta, puntos de acceso |
| **Distribución (distribution)** | Interconecta las redes de acceso; filtra tráfico y aísla los fallos para que no lleguen al core | Switches multicapa, routers |
| **Núcleo (core)** | Backbone de alta velocidad que une las capas de distribución; su objetivo es el máximo caudal | Switches y routers de alto rendimiento, enlaces redundantes |

- Ventajas del diseño jerárquico: facilita el crecimiento (escalabilidad), limita el alcance de los fallos, simplifica la administración y permite dimensionar cada capa según su trabajo.

### Para el examen
- Los cuatro requisitos con su escenario: cable cortado sin interrupción = fault tolerance; añadir voz y vídeo = scalability; priorizar videoconferencia = QoS; credenciales y cifrado = security. Caen como caso práctico.
- Las tres capas y su frase: access conecta hosts, distribution interconecta redes de acceso y filtra, core es el backbone de alta velocidad.
- El filtrado de tráfico se hace en distribución, no en el core: el core solo conmuta rápido.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Cloud and Virtualization

**(Nube y virtualización)**

## 2.1 Cloud and Cloud Services (La nube y sus servicios)

- La **nube** es el uso de servidores remotos, accesibles por internet, para almacenar datos y ejecutar aplicaciones en lugar de hacerlo en equipos propios.
- **Modelos de servicio** (los "aaS"):

| Modelo | Qué ofrece | Ejemplo |
|---|---|---|
| **SaaS** (Software as a Service) | Aplicaciones listas para usar vía navegador | Gmail, Office 365 |
| **PaaS** (Platform as a Service) | Entorno para desarrollar y desplegar aplicaciones | Herramientas de desarrollo en la nube |
| **IaaS** (Infrastructure as a Service) | Infraestructura: servidores virtuales, almacenamiento, red | Máquinas virtuales de AWS o Azure |
| **ITaaS** (IT as a Service) | Soporte TI completo contratado como servicio | Externalización de los servicios TI |

- **Tipos de nube:**

| Tipo | Característica |
|---|---|
| **Pública** | Servicios abiertos a cualquiera, por suscripción o gratuitos |
| **Privada** | Para una única organización (p. ej. una administración pública); puede estar en sus propias instalaciones |
| **Híbrida** | Combina pública y privada conectadas entre sí |
| **Comunitaria** | Para un sector con necesidades comunes (sanidad, banca) y requisitos propios de cumplimiento |

- Ventajas: pagar por lo que se usa, acceso desde cualquier lugar y dispositivo, menos inversión en equipos propios, copias y recuperación gestionadas por el proveedor.

## 2.2 Virtualization (Virtualización)

- Problema del modelo tradicional de **un servidor físico por servicio**: infrautilización (la máquina rinde muy por debajo de su capacidad), punto único de fallo, consumo de espacio, energía y refrigeración.
- La **virtualización** separa el sistema operativo del hardware: varias **máquinas virtuales (VMs)** independientes conviven en un mismo servidor físico.
- El **hipervisor** es el software que crea y gestiona las VMs repartiendo el hardware entre ellas:

| Tipo | Dónde corre | Uso |
|---|---|---|
| **Tipo 1 ("bare metal")** | Directamente sobre el hardware | Servidores de empresa y centros de datos |
| **Tipo 2 ("hosted")** | Como aplicación sobre un SO anfitrión | Equipos personales: VirtualBox, VMware Workstation |

- Beneficios: menos equipos físicos (consolidación), menor consumo y espacio, aprovisionamiento rápido de servidores nuevos, pruebas y prototipos sin hardware adicional, recuperación ante desastres más sencilla.
- La virtualización es la base técnica de la nube: los proveedores reparten sus servidores físicos entre miles de clientes mediante VMs.

### Para el examen
- Emparejar servicio con modelo: correo web = SaaS, entorno de desarrollo = PaaS, servidor virtual = IaaS.
- Nube privada no significa "en mi edificio": significa para una sola organización, esté donde esté.
- Hipervisor tipo 1 sobre el hardware (empresa); tipo 2 sobre un SO (uso personal).
- El problema que resuelve la virtualización: servidores dedicados infrautilizados y punto único de fallo.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Number Systems

**(Sistemas de numeración)**

## 3.1 Binary Number System (Sistema binario)

- Las direcciones IPv4 son 32 bits: lo que escribimos como `192.168.10.1` son 4 octetos binarios. Hay que saber convertir en ambos sentidos.
- **Notación posicional en base 2:** cada bit de un octeto vale una potencia de 2:

```
Posición:   128   64   32   16    8    4    2    1
Bit:          1    1    0    0    0    0    0    0   →  128 + 64 = 192
```

- **Binario → decimal:** sumar los valores de las posiciones con bit a 1.
  - `10101100` → 128 + 32 + 8 + 4 = **172**
- **Decimal → binario:** ir restando las potencias de mayor a menor; si cabe, bit a 1; si no, bit a 0.
  - 168 → 128 cabe (resta 40), 64 no, 32 cabe (resta 8), 16 no, 8 cabe (resta 0) → `10101000`
- Rango de un octeto: 8 bits, de 0 (`00000000`) a 255 (`11111111`).

## 3.2 Hexadecimal Number System (Sistema hexadecimal)

- Base 16: dígitos `0-9` y letras `A-F` (A=10, B=11, C=12, D=13, E=14, F=15).
- Se usa porque compacta el binario: **1 dígito hexadecimal = 4 bits exactos**. Un octeto son 2 dígitos hex.
- Dónde aparece: direcciones **IPv6** (hextetos) y direcciones **MAC**.
- Conversión práctica pasando por binario:

```
Decimal 168 → binario 1010 1000 → hex A8
Hex 3F      → binario 0011 1111 → decimal 63
```

- Tabla de apoyo para los 16 valores:

| Hex | Binario | Dec | | Hex | Binario | Dec |
|---|---|---|---|---|---|---|
| 0 | 0000 | 0 | | 8 | 1000 | 8 |
| 1 | 0001 | 1 | | 9 | 1001 | 9 |
| 2 | 0010 | 2 | | A | 1010 | 10 |
| 3 | 0011 | 3 | | B | 1011 | 11 |
| 4 | 0100 | 4 | | C | 1100 | 12 |
| 5 | 0101 | 5 | | D | 1101 | 13 |
| 6 | 0110 | 6 | | E | 1110 | 14 |
| 7 | 0111 | 7 | | F | 1111 | 15 |

### Para el examen
- Memoriza la fila de potencias: 128, 64, 32, 16, 8, 4, 2, 1. Con ella sale todo.
- Practica conversiones hasta hacerlas sin pensar: son la base del subnetting del módulo 6.
- 1 dígito hex = 4 bits; 2 dígitos hex = 1 octeto. A=10 ... F=15.
- Truco de verificación: un octeto que empieza por 1 en binario vale 128 o más; si el primer dígito hex es 8 o superior, también.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 1 a 3

Primer examen parcial del curso: evalúa diseño jerárquico y redes fiables, nube y virtualización, y conversiones entre decimal, binario y hexadecimal.

[⬆ Volver al índice](#índice)

---

# MÓDULO 4 — Ethernet Switching

**(Conmutación Ethernet)**

## 4.1 Ethernet

- Ethernet es la tecnología LAN dominante, definida en el estándar **IEEE 802.3**. Opera en las capas 1 y 2 del modelo OSI.
- La capa de enlace se divide en dos subcapas:
  - **LLC (Logical Link Control):** comunica con la capa de red; identifica qué protocolo viaja en la trama.
  - **MAC:** encapsula los datos en tramas y gestiona el acceso al medio.
- En las redes antiguas de medio compartido (hubs, bus) se usaba **CSMA/CD** para detectar colisiones y funcionaban en **half duplex**. Con switches modernos cada puerto es un enlace dedicado en **full duplex**: sin colisiones.

## 4.2 Ethernet Frames (Tramas Ethernet)

- Campos de la trama, en orden:

| Campo | Función |
|---|---|
| Preámbulo | Sincronización; avisa de que llega una trama |
| **MAC de destino** | A quién va dirigida |
| **MAC de origen** | Quién la envía |
| Tipo/Longitud | Qué protocolo transporta (p. ej. IPv4, IPv6, ARP) |
| Datos | El paquete encapsulado |
| **FCS** | Comprobación de errores (CRC); si no cuadra, la trama se descarta |

- Tamaños: **mínimo 64 bytes, máximo 1518 bytes**. Una trama menor de 64 es un **runt** (normalmente fragmento de colisión) y se descarta; algunos equipos soportan **jumbo frames** de hasta 9000 bytes.

## 4.3 Ethernet MAC Address (La dirección MAC)

- 48 bits en hexadecimal. Los primeros 24 bits son el **OUI** (identificador del fabricante, asignado por el IEEE); los otros 24, el número de serie del dispositivo.
- Va grabada en la ROM de la tarjeta ("burned-in address"), aunque puede suplantarse por software.
- Tres tipos:

| Tipo | MAC de destino |
|---|---|
| **Unicast** | La MAC de un dispositivo concreto |
| **Broadcast** | `FF-FF-FF-FF-FF-FF` (todos los dispositivos de la LAN) |
| **Multicast** | Prefijo `01-00-5E` (IPv4) o `33-33` (IPv6) |

## 4.4 The MAC Address Table (La tabla de direcciones MAC)

- El switch construye su tabla **examinando la MAC de origen** de cada trama que entra: la asocia al puerto por el que llegó (con un temporizador de caducidad, unos 5 minutos).
- Para reenviar, **busca la MAC de destino** en la tabla:
  - Está → envía solo por ese puerto (*filtering*).
  - No está, o es broadcast → reenvía por todos los puertos excepto el de entrada (*flooding*).
- Comando para consultarla en un switch Cisco: `show mac address-table`.

### Para el examen
- Trama Ethernet: 64 bytes mínimo, 1518 máximo. Menos de 64 = runt.
- `FF-FF-FF-FF-FF-FF` = broadcast de capa 2 (lo usa, por ejemplo, la petición ARP).
- El switch aprende del **origen** y reenvía por el **destino**. La pregunta trampa habitual invierte los dos.
- OUI = primeros 24 bits = fabricante.

[⬆ Volver al índice](#índice)

---

# MÓDULO 5 — Network Layer

**(La capa de red)**

## 5.1 Network Layer Characteristics (Características)

- La capa de red (capa 3 OSI) permite la comunicación extremo a extremo con cuatro operaciones: **direccionar** los dispositivos, **encapsular** los segmentos en paquetes, **enrutar** entre redes y **desencapsular** en el destino.
- Tres características de IP que caen en examen:

| Característica | Qué significa |
|---|---|
| **Sin conexión (connectionless)** | No se establece contacto previo con el destino antes de enviar |
| **Best effort** | IP no garantiza la entrega; la fiabilidad, si hace falta, la aporta TCP en capa 4 |
| **Independiente del medio** | Viaja igual por cobre, fibra o aire; el único límite es la **MTU** (tamaño máximo que acepta el medio, 1500 bytes en Ethernet) |

## 5.2 IPv4 Packet (El paquete IPv4)

Campos relevantes de la cabecera:

| Campo | Función |
|---|---|
| Versión | 4 |
| **DSCP** | Prioridad del paquete (QoS) |
| **TTL (Time to Live)** | Cada router lo resta en 1; al llegar a 0, el paquete se descarta y el router avisa con un ICMP "Time Exceeded". Evita bucles infinitos |
| **Protocolo** | Qué transporta: 1 = ICMP, 6 = TCP, 17 = UDP |
| Checksum | Comprobación de errores de la cabecera |
| **IP de origen / destino** | No cambian en todo el trayecto (salvo NAT) |

## 5.3 IPv6 Packet (El paquete IPv6)

- IPv6 responde a tres problemas de IPv4: agotamiento de direcciones, pérdida de conectividad extremo a extremo por culpa del NAT, y complejidad añadida.
- Cabecera **simplificada** de 40 bytes fijos, más eficiente de procesar:

| Campo IPv6 | Equivalente IPv4 |
|---|---|
| Traffic Class | DSCP |
| Flow Label | (nuevo: identifica flujos para tratarlos igual) |
| Payload Length | Longitud |
| Next Header | Protocolo |
| **Hop Limit** | TTL |

### Para el examen
- TTL a 0 = el router descarta el paquete y envía ICMP Time Exceeded: es el mecanismo que aprovecha `tracert` para descubrir los saltos.
- Números de protocolo: 1 ICMP, 6 TCP, 17 UDP.
- IP es sin conexión y best effort: la fiabilidad es trabajo de TCP, no de IP.
- Hop Limit es el TTL de IPv6.

[⬆ Volver al índice](#índice)

---

# MÓDULO 6 — IPv4 Addressing

**(Direccionamiento IPv4 y subnetting)**

## 6.1 IPv4 Address Structure (Estructura y subnetting)

- Repaso: 32 bits, porción de red + porción de host, separadas por la **máscara** (o el prefijo /n).
- El host obtiene su dirección de red aplicando un **AND lógico** bit a bit entre su IP y la máscara (1 AND 1 = 1; el resto, 0).
- En toda subred hay tres tipos de dirección:

| Tipo | Bits de host | Ejemplo en 192.168.10.0/24 |
|---|---|---|
| **Dirección de red** | Todos a 0 | 192.168.10.0 |
| **Direcciones de host** | Mezcla | 192.168.10.1 – 192.168.10.254 |
| **Dirección de broadcast** | Todos a 1 | 192.168.10.255 |

- **Subnetting:** tomar prestados bits de la porción de host para crear subredes.
  - Con **s** bits prestados se crean **2^s subredes**.
  - Con **h** bits de host restantes quedan **2^h − 2 hosts** por subred.
- Ejemplo trabajado: dividir `192.168.1.0/24` en 4 subredes → se piden prestados 2 bits → /26 (máscara 255.255.255.192), 62 hosts cada una:

```
192.168.1.0/26    hosts .1 – .62     broadcast .63
192.168.1.64/26   hosts .65 – .126   broadcast .127
192.168.1.128/26  hosts .129 – .190  broadcast .191
192.168.1.192/26  hosts .193 – .254  broadcast .255
```

- Tabla de referencia para subredes de un /24:

| Prefijo | Máscara | Subredes | Hosts por subred |
|---|---|---|---|
| /25 | 255.255.255.128 | 2 | 126 |
| /26 | 255.255.255.192 | 4 | 62 |
| /27 | 255.255.255.224 | 8 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 32 | 6 |
| /30 | 255.255.255.252 | 64 | 2 |

### Para el examen
- El escenario típico: "necesito N hosts por subred, ¿qué prefijo uso?" Se resuelve con 2^h − 2 ≥ N. Para 30 hosts → /27; para 2 (enlace entre routers) → /30.
- Saber identificar si una IP es de red, de host o de broadcast dentro de un prefijo dado.
- La dirección de red sale del AND entre IP y máscara: repásalo con binario del módulo 3.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 4 a 6

Segundo examen parcial del curso: evalúa conmutación Ethernet (tramas, MAC, tabla del switch), capa de red (cabeceras IPv4/IPv6, TTL) y subnetting IPv4.

[⬆ Volver al índice](#índice)

---

# MÓDULO 7 — Address Resolution

**(Resolución de direcciones: ARP)**

## 7.1 ARP

Amplía lo visto en [Networking Basics, módulo 13](networking-basics.md#módulo-13--the-arp-process): mismo protocolo, ahora con más detalle de las tablas y la parte de seguridad.

- Para entregar una trama hacen falta la IP (capa 3) y la MAC (capa 2) del siguiente salto. **ARP** asocia ambas: pregunta en **broadcast** "¿quién tiene esta IP?" y el propietario responde en **unicast** con su MAC.
- Si el destino está en otra red, se resuelve la MAC del **default gateway**, no la del host remoto.
- Todos los dispositivos mantienen **tabla ARP** (también llamada caché): hosts, routers y switches multicapa. Las entradas caducan solas (en Windows en segundos o minutos; en routers Cisco, horas) y pueden añadirse estáticamente.
- Comandos:

| Dispositivo | Comando |
|---|---|
| Windows | `arp -a` (ver), `arp -d` (vaciar) |
| Router/switch Cisco | `show ip arp` / `show arp` |

- **Riesgo de seguridad, el ARP spoofing (envenenamiento ARP):** un atacante responde a las peticiones ARP con su propia MAC haciéndose pasar por otro equipo (típicamente el gateway) y consigue interceptar el tráfico (man in the middle). En redes gestionadas se mitiga con funciones del switch como la inspección dinámica de ARP.

### Para el examen
- Petición en broadcast, respuesta en unicast; destino remoto = MAC del gateway. Igual que en Networking Basics, lo repreguntan aquí.
- ARP no cruza routers: trabaja solo dentro del dominio de broadcast.
- ARP spoofing = responder con una MAC falsa para interceptar tráfico; es la amenaza asociada a ARP que menciona el curso.

[⬆ Volver al índice](#índice)

---

# MÓDULO 8 — IP Addressing Services

**(Servicios de direccionamiento IP: DNS y DHCP)**

## 8.1 DNS Services (El servicio DNS)

- **DNS** traduce nombres de dominio a direcciones IP: es el primer paso de casi cualquier conexión. Sin él habría que memorizar las IPs de cada servicio.
- Es un sistema **jerárquico y distribuido**: ningún servidor lo sabe todo; las consultas se resuelven por niveles (raíz, dominios de primer nivel, dominios concretos).
- El cliente envía la consulta al servidor DNS que tiene configurado (a mano o por DHCP) y este resuelve por él.
- Tipos de registro habituales:

| Registro | Contenido |
|---|---|
| **A** | Nombre → dirección IPv4 |
| **AAAA** | Nombre → dirección IPv6 |
| **NS** | Servidor de nombres autoritativo del dominio |
| **MX** | Servidor de correo del dominio |

- Para probarlo: `nslookup nombre` muestra qué IP devuelve el DNS configurado.

## 8.2 DHCP Services (El servicio DHCP)

- **DHCP** entrega automáticamente la configuración de red: IP, máscara, gateway y DNS, en préstamo (*lease*) temporal.
- La asignación sigue los cuatro mensajes **DORA**: Discover (broadcast del cliente), Offer, Request, Acknowledge.
- El servidor puede ser el router doméstico o un servidor dedicado en empresas. Se configura: el **pool** (rango a repartir), la duración del lease, y las **reservas y exclusiones** para los equipos que necesitan IP fija.
- Si ningún servidor responde, el cliente Windows acaba en APIPA (169.254.x.x).

### Para el examen
- Registro A = IPv4, AAAA = IPv6. La pareja cae seguro.
- Puertos: DNS 53; DHCP 67 (servidor) y 68 (cliente), ambos UDP.
- DORA en orden y quién envía cada mensaje.
- `nslookup` aísla problemas de DNS; APIPA delata DHCP inaccesible.

[⬆ Volver al índice](#índice)

---

# MÓDULO 9 — Transport Layer

**(La capa de transporte)**

## 9.1 Transportation of Data (El papel de la capa de transporte)

- La capa de transporte conecta aplicaciones extremo a extremo: **segmenta** los datos, **multiplexa** varias conversaciones a la vez y identifica cada aplicación por su **número de puerto**.
- Dos protocolos con filosofías opuestas: TCP (fiable) y UDP (ligero).

## 9.2 TCP Overview (TCP)

- **Orientado a conexión:** establece la sesión antes de enviar datos.
- **Fiable:** numera los segmentos, confirma la recepción y **retransmite** lo que se pierde; entrega los datos **en orden**.
- A cambio, más sobrecarga. Usos: web, correo, transferencia de archivos.

## 9.3 UDP Overview (UDP)

- **Sin conexión** y sin garantías (*best effort*): envía y no comprueba.
- Cabecera mínima, máxima velocidad. Usos: VoIP, vídeo en directo, DNS, DHCP.
- Si la aplicación necesita fiabilidad sobre UDP, la implementa ella misma.

## 9.4 Port Numbers (Números de puerto)

| Rango | Nombre | Uso |
|---|---|---|
| 0 – 1023 | **Bien conocidos (well-known)** | Servicios estándar: HTTP 80, HTTPS 443, DNS 53... |
| 1024 – 49151 | **Registrados** | Aplicaciones concretas registradas por fabricantes |
| 49152 – 65535 | **Dinámicos o privados** | Puertos de origen que eligen los clientes al conectar |

- **Socket:** la combinación IP + puerto (p. ej. `192.168.1.5:49152`). La **pareja de sockets** origen-destino identifica de forma única cada conversación.
- `netstat` muestra las conversaciones TCP/UDP activas del equipo y sus puertos.

## 9.5 TCP Communication Process (Establecimiento y cierre de sesión)

- **Apertura, saludo de tres vías:**

```
Cliente → SYN        (quiero hablar contigo)
Servidor → SYN-ACK   (de acuerdo, confírmame)
Cliente → ACK        (confirmado, empezamos)
```

- **Cierre ordenado:** cada extremo termina su mitad de la conversación con un intercambio **FIN / ACK** (cuatro mensajes en total).

## 9.6 Reliability and Flow Control (Fiabilidad y control de flujo)

- **Fiabilidad:** los números de secuencia permiten al receptor detectar huecos y reordenar; los **ACK** confirman lo recibido y el emisor retransmite lo no confirmado.
- **Control de flujo:** el campo **window size** (tamaño de ventana) indica cuántos bytes acepta el receptor antes del siguiente ACK. Si el receptor se satura, reduce la ventana y el emisor baja el ritmo.

## 9.7 UDP Communication (Comunicación UDP)

- El servidor escucha en su puerto conocido; el cliente envía desde un puerto dinámico elegido al azar.
- No hay establecimiento ni cierre: los datagramas se procesan según llegan, y si alguno se pierde, no se reenvía.

### Para el examen
- Los tres rangos de puertos con sus números exactos: 0-1023, 1024-49151, 49152-65535.
- Socket = IP + puerto; pareja de sockets = conversación única.
- Apertura TCP: SYN, SYN-ACK, ACK. Cierre: FIN/ACK.
- Window size = control de flujo. Retransmisión = fiabilidad. No confundirlos.
- UDP no tiene handshake: pregunta trampa habitual.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 7 a 9

Tercer examen parcial del curso: evalúa ARP, los servicios DNS y DHCP, y la capa de transporte (TCP, UDP y puertos).

[⬆ Volver al índice](#índice)

---

# MÓDULO 10 — The Cisco IOS Command Line

**(La línea de comandos de Cisco IOS)**

## 10.1 IOS Navigation (Modos de la CLI)

| Modo | Prompt | Cómo se entra | Qué permite |
|---|---|---|---|
| **EXEC usuario** | `Switch>` | Al conectar | Comandos básicos de consulta |
| **EXEC privilegiado** | `Switch#` | `enable` | Todos los show, reinicios, copias |
| **Configuración global** | `Switch(config)#` | `configure terminal` | Cambiar la configuración |
| **Config. de línea** | `Switch(config-line)#` | `line console 0` / `line vty 0 15` | Contraseñas de acceso |
| **Config. de interfaz** | `Switch(config-if)#` | `interface vlan 1` / `interface g0/0` | IPs, descripciones, encender puertos |

- Para retroceder: `exit` sube un nivel; `end` (o Ctrl+Z) vuelve directo al modo privilegiado.

## 10.2 The Command Structure (Estructura de los comandos)

- Un comando se compone de la orden más palabras clave y argumentos: `ip address 192.168.1.2 255.255.255.0`.
- Ayudas de la CLI:

| Recurso | Qué hace |
|---|---|
| `?` | Ayuda contextual: lista comandos u opciones disponibles en ese punto |
| Tabulador | Completa el comando empezado |
| Flecha arriba | Recupera comandos anteriores (historial) |
| Ctrl+C | Cancela el comando en edición y sale de configuración |
| Ctrl+Mayús+6 | Interrumpe procesos como un ping o un traceroute largos |

- Los comandos pueden abreviarse si no hay ambigüedad: `conf t`, `sh ip int br`.

## 10.3 View Device Information (Comandos show)

| Comando | Muestra |
|---|---|
| `show version` | Modelo, versión de IOS, memoria, tiempo encendido |
| `show running-config` | Configuración activa (en RAM) |
| `show startup-config` | Configuración guardada (en NVRAM) |
| `show ip interface brief` | Resumen de interfaces: IP y estado. El más usado |
| `show interfaces` | Detalle y estadísticas de cada interfaz |
| `show arp` | La tabla ARP del dispositivo |
| `show mac address-table` | La tabla MAC (en switches) |

### Para el examen
- Asociar cada prompt con su modo y saber el comando que lleva a cada uno.
- `running-config` está en RAM y se pierde al reiniciar; `startup-config` está en NVRAM y sobrevive.
- `?` es la ayuda contextual; Tab completa; `end` y Ctrl+Z vuelven al modo privilegiado.

[⬆ Volver al índice](#índice)

---

# MÓDULO 11 — Build a Small Cisco Network

**(Montar una red Cisco pequeña)**

## 11.1 Basic Switch Configuration (Configuración inicial del switch)

Secuencia típica completa:

```
Switch> enable
Switch# configure terminal
Switch(config)# hostname S1
S1(config)# enable secret MiClaveSegura
S1(config)# line console 0
S1(config-line)# password ClaveConsola
S1(config-line)# login
S1(config-line)# exit
S1(config)# line vty 0 15
S1(config-line)# password ClaveRemota
S1(config-line)# login
S1(config-line)# exit
S1(config)# service password-encryption
S1(config)# banner motd #Acceso autorizado unicamente#
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.2 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# end
S1# copy running-config startup-config
```

- La IP del switch se configura en la **SVI** (interfaz virtual, `interface vlan 1`): sirve solo para administrarlo en remoto, no para conmutar.
- `enable secret` protege el acceso al modo privilegiado con la clave cifrada; `service password-encryption` cifra el resto de contraseñas del archivo de configuración.

## 11.2 Configure Initial Router Settings (Configuración inicial del router)

- Los mismos pasos básicos (hostname, secret, líneas, banner) más la configuración de cada **interfaz física**:

```
R1(config)# interface g0/0
R1(config-if)# description LAN de oficina
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
```

- `no shutdown` es obligatorio: las interfaces de router vienen administrativamente apagadas de fábrica.

## 11.3 Secure the Devices (Asegurar los dispositivos)

- Contraseñas fuertes y cifradas; banner que advierta de acceso restringido.
- **Habilitar SSH y desterrar Telnet:**

```
R1(config)# ip domain-name ejemplo.local
R1(config)# crypto key generate rsa      (claves de 1024 bits o más)
R1(config)# username admin secret ClaveDeAdmin
R1(config)# line vty 0 15
R1(config-line)# transport input ssh
R1(config-line)# login local
```

- `transport input ssh` bloquea Telnet en las líneas remotas; `login local` valida contra los usuarios creados en el equipo.

## 11.4 Configure the Default Gateway (La puerta de enlace)

- En el **switch**: `ip default-gateway 192.168.1.1` (en configuración global) para poder administrarlo desde otras redes.
- En los **hosts**: el gateway llega por DHCP o se configura a mano; sin él, no salen de su subred.

### Para el examen
- `enable secret` manda sobre `enable password` y va cifrado: es el que hay que usar.
- `no shutdown`: el olvido clásico que deja la interfaz apagada.
- El switch se administra por la SVI (vlan 1) y necesita `ip default-gateway`; el router no, porque enruta.
- Pasos de SSH en orden: dominio, claves RSA, usuario, transport input ssh, login local.
- `copy running-config startup-config` o los cambios mueren con el primer reinicio.

[⬆ Volver al índice](#índice)

---

# MÓDULO 12 — ICMP

**(Mensajes de control y pruebas de conectividad)**

## 12.1 ICMP Messages (Mensajes ICMP)

- **ICMP** es el protocolo de mensajes de control y error de IP. No transporta datos de usuario: informa.
- Mensajes que hay que conocer:

| Mensaje | Qué indica |
|---|---|
| **Echo Request / Echo Reply** | La pareja que usa el ping: pregunta y respuesta |
| **Destination Unreachable** | El destino no es alcanzable (red, host, protocolo o puerto, según el código) |
| **Time Exceeded** | El TTL del paquete llegó a 0 y un router lo descartó |

- **ICMPv6** cumple la misma función en IPv6 y añade los mensajes de descubrimiento de vecinos (Neighbor Discovery), que sustituyen a ARP.

## 12.2 Ping and Traceroute Testing (Pruebas con ping y traceroute)

- **ping** envía Echo Requests y mide el **RTT** (tiempo de ida y vuelta) y las pérdidas. La secuencia escalonada de siempre: loopback, IP propia, gateway, IP externa, nombre de dominio.
- **traceroute** (`tracert` en Windows, `traceroute` en Linux e IOS) descubre los saltos del camino enviando paquetes con TTL creciente: cada router que descarta responde con Time Exceeded y se delata.
- En IOS, el **ping extendido** (escribir `ping` sin argumentos en modo privilegiado) permite elegir origen, número de paquetes y tamaño: útil para probar desde una interfaz concreta del router.

### Para el examen
- Ping = Echo Request + Echo Reply. Traceroute se apoya en Time Exceeded.
- Respuesta Destination Unreachable: el paquete llegó a un router que no sabe continuar (o a un host sin ese puerto).
- ICMPv6 incluye Neighbor Discovery, el sustituto de ARP en IPv6.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 10 a 12

Cuarto examen parcial del curso: evalúa la navegación y comandos de Cisco IOS, la configuración inicial de switches y routers, la securización con SSH e ICMP con sus herramientas de prueba.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El examen final cubre los 12 módulos. Recomendaciones de repaso:

1. Vuelve a los apartados "Para el examen" de cada módulo.
2. De memoria: las 3 capas del diseño jerárquico, la fila de potencias (128-64-32-16-8-4-2-1), la trama Ethernet (64-1518), los campos TTL y protocolo (1/6/17), los rangos de puertos (0-1023, 1024-49151, 49152-65535) y la secuencia de configuración del switch.
3. Practica subnetting hasta que el escenario "necesito N hosts" salga solo (tabla /25 a /30 del módulo 6).
4. Repasa los comandos IOS tecleándolos en Packet Tracer: los labs del curso (conectividad básica, configuración de router, SSH) son el mejor simulacro.

Superado este curso, el siguiente de la serie CCST Networking es **Network Addressing and Basic Troubleshooting**.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1:** *fault tolerance · redundancy · packet switching · scalability · QoS (Quality of Service) · security · confidentiality/integrity/availability · physical vs logical topology · hierarchical design · access layer · distribution layer · core layer · backbone · traffic filtering*

**Módulo 2:** *cloud computing · SaaS · PaaS · IaaS · ITaaS · public/private/hybrid/community cloud · virtualization · dedicated server · server consolidation · virtual machine (VM) · hypervisor type 1 (bare metal) · hypervisor type 2 (hosted) · single point of failure · disaster recovery*

**Módulo 3:** *binary · decimal · hexadecimal · base 2/10/16 · positional notation · bit · octet · powers of 2 (128-64-32-16-8-4-2-1) · 0-255 range · nibble (4 bits) · A-F values · binary-to-decimal conversion · hex-to-binary conversion*

**Módulo 4:** *IEEE 802.3 · LLC · MAC sublayer · CSMA/CD · half/full duplex · preamble · frame check sequence (FCS) · 64-1518 bytes · runt · jumbo frame · OUI · burned-in address · unicast/broadcast/multicast MAC · FF-FF-FF-FF-FF-FF · MAC address table · learning · filtering · flooding · aging · `show mac address-table`*

**Módulo 5:** *network layer · addressing/encapsulation/routing/de-encapsulation · connectionless · best effort · media independent · MTU · IPv4 header · DSCP · TTL · protocol field (1 ICMP, 6 TCP, 17 UDP) · header checksum · IPv6 header · traffic class · flow label · next header · hop limit*

**Módulo 6:** *network portion · host portion · subnet mask · prefix length · logical AND · network address · broadcast address · host addresses · subnetting · borrowed bits · 2^s subnets · 2^h − 2 hosts · /25 to /30 · 255.255.255.192*

**Módulo 7:** *ARP · ARP table/cache · ARP request (broadcast) · ARP reply (unicast) · gateway MAC · static/dynamic entries · aging · `arp -a` · `show ip arp` · ARP spoofing · ARP poisoning · man in the middle · dynamic ARP inspection*

**Módulo 8:** *DNS · domain name · A record · AAAA record · NS record · MX record · `nslookup` · DHCP · lease · pool · reservation · exclusion · DORA (Discover, Offer, Request, Acknowledge) · UDP 67/68 · APIPA*

**Módulo 9:** *transport layer · segmentation · multiplexing · TCP · connection-oriented · reliability · sequence numbers · acknowledgment · retransmission · UDP · connectionless · best effort · well-known ports (0-1023) · registered ports (1024-49151) · dynamic ports (49152-65535) · socket · socket pair · `netstat` · three-way handshake · SYN · SYN-ACK · ACK · FIN · window size · flow control*

**Módulo 10:** *CLI · user EXEC mode · privileged EXEC mode · global configuration mode · line configuration mode · interface configuration mode · `enable` · `configure terminal` · `exit` · `end` · context-sensitive help (`?`) · Tab completion · command history · `show version` · `show running-config` · `show startup-config` · `show ip interface brief` · `show interfaces` · `show arp` · `show mac address-table` · RAM · NVRAM*

**Módulo 11:** *`hostname` · `enable secret` · `line console 0` · `line vty 0 15` · `password` · `login` · `service password-encryption` · `banner motd` · SVI · `interface vlan 1` · `ip address` · `no shutdown` · `description` · `copy running-config startup-config` · SSH · Telnet · `ip domain-name` · `crypto key generate rsa` · `username secret` · `transport input ssh` · `login local` · `ip default-gateway`*

**Módulo 12:** *ICMP · echo request · echo reply · destination unreachable · time exceeded · ICMPv6 · Neighbor Discovery · ping · RTT (round-trip time) · extended ping · traceroute · `tracert` · TTL incremental · hop*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **AND lógico** | Operación bit a bit entre IP y máscara que da la dirección de red (1 AND 1 = 1; el resto, 0). |
| **ARP** | Protocolo que asocia una IP conocida con su MAC; petición en broadcast, respuesta en unicast. |
| **ARP spoofing** | Ataque que responde a peticiones ARP con una MAC falsa para interceptar el tráfico (man in the middle). |
| **Banner MOTD** | Mensaje que muestra el dispositivo al conectarse; se usa para advertir de que el acceso no autorizado está prohibido. |
| **Best effort** | Entrega sin garantías: IP envía los paquetes sin confirmar que lleguen; la fiabilidad la pone TCP. |
| **Capa de acceso** | Capa del modelo jerárquico que conecta los dispositivos finales a la red (switches de planta, APs). |
| **Capa de distribución** | Capa intermedia que interconecta las redes de acceso, filtra tráfico y aísla fallos. |
| **Capa de núcleo (core)** | Backbone de alta velocidad que une las capas de distribución; prioriza el caudal máximo. |
| **Control de flujo** | Mecanismo TCP por el que el receptor ajusta la ventana (window size) para regular cuántos datos acepta antes de confirmar. |
| **CSMA/CD** | Mecanismo de detección de colisiones de las Ethernet antiguas de medio compartido; innecesario con switches full duplex. |
| **DHCP** | Protocolo que asigna automáticamente IP, máscara, gateway y DNS en préstamo temporal (lease); usa UDP 67/68. |
| **Dirección de broadcast (subred)** | Última dirección de la subred, con todos los bits de host a 1; alcanza a todos sus hosts. |
| **Dirección de red** | Primera dirección de la subred, con todos los bits de host a 0; identifica la subred. |
| **DNS** | Sistema jerárquico que traduce nombres de dominio a direcciones IP; usa el puerto 53. |
| **DSCP** | Campo de la cabecera IPv4 que marca la prioridad del paquete para QoS. |
| **Dúplex** | Modo de transmisión: half (por turnos, con colisiones) o full (simultáneo, sin colisiones). |
| **Enable secret** | Contraseña cifrada que protege el acceso al modo EXEC privilegiado; tiene prioridad sobre enable password. |
| **Escalabilidad** | Capacidad de la red para crecer en usuarios y servicios sin degradar el funcionamiento. |
| **FCS** | Campo final de la trama Ethernet para comprobar errores; si no cuadra, la trama se descarta. |
| **Flooding** | Reenvío de una trama por todos los puertos excepto el de entrada, cuando el switch no conoce la MAC de destino. |
| **Hipervisor** | Software que crea y gestiona máquinas virtuales; tipo 1 sobre el hardware, tipo 2 sobre un SO anfitrión. |
| **Hop Limit** | Campo IPv6 equivalente al TTL de IPv4. |
| **IaaS** | Infraestructura como servicio: servidores virtuales, almacenamiento y red del proveedor cloud. |
| **ICMP** | Protocolo de mensajes de control y error de IP; en él se apoyan ping (echo request/reply) y traceroute (time exceeded). |
| **LLC** | Subcapa de enlace que comunica con la capa de red e identifica el protocolo transportado. |
| **Máquina virtual (VM)** | Equipo simulado por software, con su propio SO, que comparte el hardware físico con otras VMs. |
| **Modo EXEC privilegiado** | Modo de IOS con prompt `#`; se entra con `enable` y da acceso a todos los comandos show y de gestión. |
| **Modo EXEC usuario** | Modo inicial de IOS con prompt `>`; solo permite comandos básicos de consulta. |
| **MTU** | Tamaño máximo de paquete que acepta un medio; 1500 bytes en Ethernet. |
| **Nibble** | Grupo de 4 bits; equivale exactamente a un dígito hexadecimal. |
| **Notación posicional** | Sistema en el que el valor de cada dígito depende de su posición (base 2, 10 o 16). |
| **Nube híbrida** | Combinación de nube pública y privada conectadas entre sí. |
| **Nube privada** | Servicios cloud reservados a una única organización, con independencia de dónde se alojen. |
| **Número de puerto** | Identificador de 16 bits que señala a qué aplicación van los datos; rangos: bien conocidos (0-1023), registrados (1024-49151) y dinámicos (49152-65535). |
| **NVRAM** | Memoria no volátil del dispositivo donde se guarda la startup-config; sobrevive a los reinicios. |
| **Octeto** | Grupo de 8 bits; cada uno de los 4 bloques de una dirección IPv4, con valores de 0 a 255. |
| **OUI** | Primeros 24 bits de una MAC: el identificador del fabricante asignado por el IEEE. |
| **PaaS** | Plataforma como servicio: entorno para desarrollar y desplegar aplicaciones sin gestionar servidores. |
| **Punto único de fallo** | Componente cuya avería tumba el servicio completo; se evita con redundancia. |
| **QoS (calidad de servicio)** | Mecanismos que priorizan el tráfico sensible al retardo (voz, vídeo) en caso de congestión. |
| **Redundancia** | Duplicación de enlaces o equipos para que la red sobreviva a un fallo. |
| **Running-config** | Configuración activa del dispositivo, almacenada en RAM; se pierde al reiniciar si no se copia a la startup-config. |
| **Runt** | Trama menor de 64 bytes, normalmente un fragmento de colisión; el switch la descarta. |
| **SaaS** | Software como servicio: aplicaciones listas para usar a través de internet. |
| **Saludo de tres vías** | Apertura de sesión TCP en tres mensajes: SYN, SYN-ACK y ACK. |
| **Socket** | Combinación de dirección IP y puerto; la pareja de sockets origen-destino identifica cada conversación. |
| **SSH** | Protocolo de administración remota cifrado que sustituye a Telnet; en IOS requiere nombre de dominio, claves RSA y usuario local. |
| **Startup-config** | Configuración guardada en NVRAM que se carga al arrancar; se actualiza con `copy running-config startup-config`. |
| **Subnetting** | División de una red en subredes tomando prestados bits de la porción de host. |
| **SVI** | Interfaz virtual del switch (interface vlan 1) donde se configura su IP de administración. |
| **Tabla ARP** | Caché local de parejas IP-MAC; presente en hosts, routers y switches multicapa. |
| **Tabla de direcciones MAC** | Tabla del switch que asocia cada MAC aprendida (por el origen de las tramas) con un puerto. |
| **TCP** | Protocolo de transporte orientado a conexión y fiable: numera, confirma, retransmite y entrega en orden. |
| **Tolerancia a fallos** | Capacidad de la red para seguir operando cuando falla un componente. |
| **Topología física** | Disposición real de dispositivos y cableado de la red. |
| **Topología lógica** | Representación de cómo fluyen los datos por la red, independiente del cableado. |
| **Traceroute** | Herramienta que descubre los routers del camino enviando paquetes con TTL creciente (tracert en Windows). |
| **TTL (Time to Live)** | Contador de la cabecera IPv4 que cada router decrementa; a 0, el paquete se descarta. |
| **UDP** | Protocolo de transporte sin conexión y sin garantías; mínima sobrecarga, usado en VoIP, vídeo, DNS y DHCP. |
| **Ventana (window size)** | Campo TCP con el que el receptor indica cuántos bytes acepta antes del siguiente ACK; base del control de flujo. |
| **Virtualización** | Técnica que separa el SO del hardware y permite varias VMs en un mismo servidor físico. |
| **VTY** | Líneas virtuales del dispositivo (line vty 0 15) por las que entran las sesiones remotas Telnet o SSH. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Networking Devices and Initial Configuration», segundo curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
