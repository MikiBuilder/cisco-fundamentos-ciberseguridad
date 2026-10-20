[← Volver a la página principal del repositorio](../../README.md)

# Manual de Estudio — Networking Devices and Initial Configuration

> **Objetivo del curso:** profundizar en los fundamentos de red: diseño jerárquico, cloud y virtualización, sistemas de numeración, conmutación Ethernet, capa de red y de transporte, y la configuración inicial de dispositivos Cisco con IOS. Segundo curso de la serie CCST Networking, continuación de [Networking Basics](networking-basics.md).

**Estado de estos apuntes:** cubren los módulos 1 a 7. El curso completo tiene 12 módulos (22 horas, 19 labs); el resto se añadirá a medida que se cursen.

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
- [Próximos módulos (pendientes de cursar)](#próximos-módulos-pendientes-de-cursar)
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

# Próximos módulos (pendientes de cursar)

Se añadirán a este manual a medida que avance el curso:

| Módulo | Título |
|---|---|
| 8 | IP Addressing Services (DNS y DHCP) |
| 9 | Transport Layer (TCP y UDP) |
| — | Checkpoint Exam: módulos 7 a 9 |
| 10 | The Cisco IOS Command Line |
| 11 | Build a Small Cisco Network |
| 12 | ICMP (ping y traceroute) |
| — | Checkpoint Exam: módulos 10 a 12 |
| — | Course Final Exam |

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

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **AND lógico** | Operación bit a bit entre IP y máscara que da la dirección de red (1 AND 1 = 1; el resto, 0). |
| **ARP** | Protocolo que asocia una IP conocida con su MAC; petición en broadcast, respuesta en unicast. |
| **ARP spoofing** | Ataque que responde a peticiones ARP con una MAC falsa para interceptar el tráfico (man in the middle). |
| **Best effort** | Entrega sin garantías: IP envía los paquetes sin confirmar que lleguen; la fiabilidad la pone TCP. |
| **Capa de acceso** | Capa del modelo jerárquico que conecta los dispositivos finales a la red (switches de planta, APs). |
| **Capa de distribución** | Capa intermedia que interconecta las redes de acceso, filtra tráfico y aísla fallos. |
| **Capa de núcleo (core)** | Backbone de alta velocidad que une las capas de distribución; prioriza el caudal máximo. |
| **CSMA/CD** | Mecanismo de detección de colisiones de las Ethernet antiguas de medio compartido; innecesario con switches full duplex. |
| **Dirección de broadcast (subred)** | Última dirección de la subred, con todos los bits de host a 1; alcanza a todos sus hosts. |
| **Dirección de red** | Primera dirección de la subred, con todos los bits de host a 0; identifica la subred. |
| **DSCP** | Campo de la cabecera IPv4 que marca la prioridad del paquete para QoS. |
| **Dúplex** | Modo de transmisión: half (por turnos, con colisiones) o full (simultáneo, sin colisiones). |
| **Escalabilidad** | Capacidad de la red para crecer en usuarios y servicios sin degradar el funcionamiento. |
| **FCS** | Campo final de la trama Ethernet para comprobar errores; si no cuadra, la trama se descarta. |
| **Flooding** | Reenvío de una trama por todos los puertos excepto el de entrada, cuando el switch no conoce la MAC de destino. |
| **Hipervisor** | Software que crea y gestiona máquinas virtuales; tipo 1 sobre el hardware, tipo 2 sobre un SO anfitrión. |
| **Hop Limit** | Campo IPv6 equivalente al TTL de IPv4. |
| **IaaS** | Infraestructura como servicio: servidores virtuales, almacenamiento y red del proveedor cloud. |
| **LLC** | Subcapa de enlace que comunica con la capa de red e identifica el protocolo transportado. |
| **Máquina virtual (VM)** | Equipo simulado por software, con su propio SO, que comparte el hardware físico con otras VMs. |
| **MTU** | Tamaño máximo de paquete que acepta un medio; 1500 bytes en Ethernet. |
| **Nibble** | Grupo de 4 bits; equivale exactamente a un dígito hexadecimal. |
| **Notación posicional** | Sistema en el que el valor de cada dígito depende de su posición (base 2, 10 o 16). |
| **Nube híbrida** | Combinación de nube pública y privada conectadas entre sí. |
| **Nube privada** | Servicios cloud reservados a una única organización, con independencia de dónde se alojen. |
| **Octeto** | Grupo de 8 bits; cada uno de los 4 bloques de una dirección IPv4, con valores de 0 a 255. |
| **OUI** | Primeros 24 bits de una MAC: el identificador del fabricante asignado por el IEEE. |
| **PaaS** | Plataforma como servicio: entorno para desarrollar y desplegar aplicaciones sin gestionar servidores. |
| **Punto único de fallo** | Componente cuya avería tumba el servicio completo; se evita con redundancia. |
| **QoS (calidad de servicio)** | Mecanismos que priorizan el tráfico sensible al retardo (voz, vídeo) en caso de congestión. |
| **Redundancia** | Duplicación de enlaces o equipos para que la red sobreviva a un fallo. |
| **Runt** | Trama menor de 64 bytes, normalmente un fragmento de colisión; el switch la descarta. |
| **SaaS** | Software como servicio: aplicaciones listas para usar a través de internet. |
| **Subnetting** | División de una red en subredes tomando prestados bits de la porción de host. |
| **Tabla ARP** | Caché local de parejas IP-MAC; presente en hosts, routers y switches multicapa. |
| **Tabla de direcciones MAC** | Tabla del switch que asocia cada MAC aprendida (por el origen de las tramas) con un puerto. |
| **Tolerancia a fallos** | Capacidad de la red para seguir operando cuando falla un componente. |
| **Topología física** | Disposición real de dispositivos y cableado de la red. |
| **Topología lógica** | Representación de cómo fluyen los datos por la red, independiente del cableado. |
| **TTL (Time to Live)** | Contador de la cabecera IPv4 que cada router decrementa; a 0, el paquete se descarta. |
| **Virtualización** | Técnica que separa el SO del hardware y permite varias VMs en un mismo servidor físico. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Networking Devices and Initial Configuration», segundo curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
