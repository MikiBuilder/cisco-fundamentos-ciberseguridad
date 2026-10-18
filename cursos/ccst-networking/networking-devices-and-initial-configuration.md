[← Volver a la página principal del repositorio](../../README.md)

# Networking Devices and Initial Configuration

> **Objetivo del curso:** profundizar en los fundamentos de red: diseño jerárquico, cloud y virtualización, sistemas de numeración, conmutación Ethernet, capa de red y de transporte, y la configuración inicial de dispositivos Cisco con IOS. Segundo curso de la serie CCST Networking, continuación de [Networking Basics](networking-basics.md).

**Estado de estos apuntes:** cubren los módulos 1 a 3. El curso completo tiene 12 módulos (22 horas, 19 labs); el resto se añadirá a medida que se cursen.

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Network Design](#módulo-1--network-design)
- [Módulo 2 — Cloud and Virtualization](#módulo-2--cloud-and-virtualization)
- [Módulo 3 — Number Systems](#módulo-3--number-systems)
- [Checkpoint Exam: módulos 1 a 3](#checkpoint-exam-módulos-1-a-3)
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

# Próximos módulos (pendientes de cursar)

Se añadirán a este manual a medida que avance el curso:

| Módulo | Título |
|---|---|
| 4 | Ethernet Switching |
| 5 | Network Layer |
| 6 | IPv4 Addressing (subnetting) |
| — | Checkpoint Exam: módulos 4 a 6 |
| 7 | Address Resolution (ARP) |
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

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **Capa de acceso** | Capa del modelo jerárquico que conecta los dispositivos finales a la red (switches de planta, APs). |
| **Capa de distribución** | Capa intermedia que interconecta las redes de acceso, filtra tráfico y aísla fallos. |
| **Capa de núcleo (core)** | Backbone de alta velocidad que une las capas de distribución; prioriza el caudal máximo. |
| **Escalabilidad** | Capacidad de la red para crecer en usuarios y servicios sin degradar el funcionamiento. |
| **Hipervisor** | Software que crea y gestiona máquinas virtuales; tipo 1 sobre el hardware, tipo 2 sobre un SO anfitrión. |
| **IaaS** | Infraestructura como servicio: servidores virtuales, almacenamiento y red del proveedor cloud. |
| **Máquina virtual (VM)** | Equipo simulado por software, con su propio SO, que comparte el hardware físico con otras VMs. |
| **Nibble** | Grupo de 4 bits; equivale exactamente a un dígito hexadecimal. |
| **Notación posicional** | Sistema en el que el valor de cada dígito depende de su posición (base 2, 10 o 16). |
| **Nube híbrida** | Combinación de nube pública y privada conectadas entre sí. |
| **Nube privada** | Servicios cloud reservados a una única organización, con independencia de dónde se alojen. |
| **Octeto** | Grupo de 8 bits; cada uno de los 4 bloques de una dirección IPv4, con valores de 0 a 255. |
| **PaaS** | Plataforma como servicio: entorno para desarrollar y desplegar aplicaciones sin gestionar servidores. |
| **Punto único de fallo** | Componente cuya avería tumba el servicio completo; se evita con redundancia. |
| **QoS (calidad de servicio)** | Mecanismos que priorizan el tráfico sensible al retardo (voz, vídeo) en caso de congestión. |
| **Redundancia** | Duplicación de enlaces o equipos para que la red sobreviva a un fallo. |
| **SaaS** | Software como servicio: aplicaciones listas para usar a través de internet. |
| **Tolerancia a fallos** | Capacidad de la red para seguir operando cuando falla un componente. |
| **Topología física** | Disposición real de dispositivos y cableado de la red. |
| **Topología lógica** | Representación de cómo fluyen los datos por la red, independiente del cableado. |
| **Virtualización** | Técnica que separa el SO del hardware y permite varias VMs en un mismo servidor físico. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Networking Devices and Initial Configuration», segundo curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
