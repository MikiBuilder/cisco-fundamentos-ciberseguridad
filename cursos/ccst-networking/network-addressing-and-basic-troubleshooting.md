[← Volver a la página principal del repositorio](../../README.md)

# Network Addressing and Basic Troubleshooting

> **Objetivo del curso:** examinar a fondo la capa física, las topologías de la capa de enlace y el enrutamiento básico en la capa de red; dominar el direccionamiento IPv6 estático y dinámico y Neighbor Discovery; conocer el funcionamiento interno de switches y routers Cisco, y aprender a diagnosticar los problemas de red más comunes. Tercer curso de la serie CCST Networking, continuación de [Networking Devices and Initial Configuration](networking-devices-and-initial-configuration.md).

**Estado de estos apuntes:** curso en progreso. Cubren los módulos 1 a 5 y los 2 primeros checkpoint exams; faltan los módulos 6 y 7 (curso de 14 horas, 8 labs).

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Physical Layer](#módulo-1--physical-layer)
- [Módulo 2 — Data Link Layer](#módulo-2--data-link-layer)
- [Módulo 3 — Routing at the Network Layer](#módulo-3--routing-at-the-network-layer)
- [Checkpoint Exam: módulos 1 a 3](#checkpoint-exam-módulos-1-a-3)
- [Módulo 4 — IPv6 Addressing](#módulo-4--ipv6-addressing)
- [Módulo 5 — IPv6 Neighbor Discovery](#módulo-5--ipv6-neighbor-discovery)
- [Checkpoint Exam: módulos 4 y 5](#checkpoint-exam-módulos-4-y-5)
- [Próximos módulos (pendientes de cursar)](#próximos-módulos-pendientes-de-cursar)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del módulo correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST Networking aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Este curso profundiza en temas ya vistos (cableado, capa de red, IPv6): si algo no suena, conviene releer [Networking Basics](networking-basics.md) y el [manual del curso anterior](networking-devices-and-initial-configuration.md).

---

# MÓDULO 1 — Physical Layer

**(La capa física a fondo)**

## 1.1 Purpose of the Physical Layer (Propósito de la capa física)

- La capa física transporta los **bits** de la trama por el medio: los convierte en señales eléctricas (cobre), pulsos de luz (fibra) o ondas de radio (inalámbrico).
- Es la última capa al enviar y la primera al recibir: la NIC del destino convierte las señales de nuevo en bits y los pasa a la capa de enlace.
- Sus estándares los definen organismos como **IEEE** (Ethernet y Wi-Fi), **TIA/EIA** (cableado), ITU e ISO: gobiernan componentes, codificación y señalización.

## 1.2 Physical Layer Characteristics (Características)

- Tres áreas de función:
  - **Componentes físicos:** cables, conectores, NICs, transceptores.
  - **Codificación (encoding):** convierte los bits en patrones predecibles (Manchester, 4B/5B) que emisor y receptor reconocen.
  - **Señalización (signaling):** cómo se representa el 1 y el 0 sobre el medio (voltaje, luz, radio).
- Medidas de capacidad que conviene distinguir:

| Término | Qué mide |
|---|---|
| **Ancho de banda (bandwidth)** | Capacidad teórica del medio (kbps, Mbps, Gbps) |
| **Throughput** | Lo que de verdad se transfiere, siempre menor que el ancho de banda |
| **Goodput** | Datos útiles: throughput menos las cabeceras de los protocolos. El menor de los tres |
| **Latencia** | Tiempo que tardan los datos en llegar, incluidos los retardos de cada equipo del camino |

## 1.3 Copper Cabling (Cableado de cobre)

- Barato, fácil de instalar y el más extendido. Sus límites: la señal se degrada con la distancia (**atenuación**) y es sensible a interferencias.
- Enemigos de la señal y cómo se combaten:
  - **EMI/RFI:** interferencia electromagnética y de radio (motores, fluorescentes, microondas). Se combate con apantallamiento.
  - **Crosstalk (diafonía):** la señal de un hilo se cuela en el vecino. Se combate trenzando los pares, porque los campos opuestos se cancelan.
- Tres tipos de cable de cobre:

| Tipo | Características | Uso |
|---|---|---|
| **UTP** | Pares trenzados sin blindaje, conector RJ-45 | LANs, el estándar de facto |
| **STP** | Pares trenzados con blindaje; mejor contra EMI pero más caro | Entornos industriales con ruido |
| **Coaxial** | Conductor central con malla; conectores BNC/F | Antenas, internet por cable (módem) |

## 1.4 UTP Cabling (Cableado UTP)

- 4 pares trenzados, cada par con un ritmo de trenzado distinto para cancelar mejor la diafonía. Distancia máxima: **100 metros**.
- Categorías habituales:

| Categoría | Rendimiento |
|---|---|
| Cat 3 | Telefonía y hasta 10 Mbps |
| Cat 5 / 5e | 100 Mbps / 1 Gbps |
| Cat 6 / 6a | 10 Gbps (Cat 6 en distancias cortas) |

- Normas de pineado **T568A** y **T568B**: definen el orden de los hilos en el RJ-45. Nunca se mezclan en un mismo cable sin motivo.
- Tipos de cable según el pineado de cada extremo:

| Cable | Extremos | Conecta |
|---|---|---|
| **Directo (straight-through)** | Igual pineado en ambos (A-A o B-B) | Dispositivos distintos: PC-switch, switch-router |
| **Cruzado (crossover)** | T568A en uno, T568B en el otro | Dispositivos iguales: switch-switch, PC-PC (hoy casi innecesario por auto-MDIX) |
| **De consola (rollover)** | Pineado invertido por completo | PC al puerto de consola de un equipo Cisco |

## 1.5 Fiber-Optic Cabling (Fibra óptica)

- Transmite pulsos de luz por un hilo de vidrio: **inmune a EMI/RFI**, mucha menos atenuación y distancias de kilómetros con gran ancho de banda.
- Dos tipos:

| Tipo | Fuente de luz | Núcleo | Alcance | Coste |
|---|---|---|---|---|
| **Monomodo (single-mode)** | Láser | Muy fino (~9 µm) | Decenas de km | Mayor |
| **Multimodo (multimode)** | LED | Más grueso (50/62,5 µm) | Hasta ~550 m | Menor |

- Usos típicos: backbone de empresa entre plantas o edificios, **FTTH** (fibra hasta el hogar), redes de larga distancia y cables submarinos.
- Conectores habituales: ST, SC, LC y LC dúplex.
- Frente al cobre: más capacidad y alcance, pero más cara y exige instalación especializada. Para tiradas cortas de planta, el UTP sigue ganando.

### Para el examen
- Goodput < throughput < ancho de banda. La pregunta suele pedir ordenarlos.
- UTP: 100 m, RJ-45, el trenzado cancela la diafonía. Cat 5e = 1 Gbps, Cat 6 = 10 Gbps.
- Directo para dispositivos distintos, cruzado para iguales, rollover para consola.
- Monomodo: láser y larga distancia. Multimodo: LED y ~550 m.
- La fibra es inmune a EMI/RFI; el coaxial es el del módem de cable.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Data Link Layer

**(Topologías y acceso al medio)**

## 2.1 Topologies (Topologías)

- **Topología física:** cómo están conectados realmente equipos y cables. **Topología lógica:** cómo fluyen las tramas entre nodos. No siempre coinciden.
- Topologías WAN:

| Topología | Descripción |
|---|---|
| **Punto a punto** | Dos extremos unidos por un enlace permanente. La más simple |
| **Hub and spoke** | Un nodo central conecta con las sedes; si cae el centro, cae todo |
| **Malla (mesh)** | Todos con todos; máxima redundancia y máximo coste |

- Topologías LAN:
  - **Estrella y estrella extendida:** todos los equipos al switch central; la actual. Fácil de ampliar y de diagnosticar.
  - **Bus:** todos colgados de un mismo cable coaxial terminado en ambos extremos. Heredada.
  - **Anillo (ring):** cada nodo pasa la señal al siguiente (Token Ring, FDDI). Heredada.
- **Half duplex:** se envía o se recibe, por turnos (hubs, WLAN). **Full duplex:** ambas cosas a la vez (switches modernos).

## 2.2 Media Access Control Methods (Métodos de acceso al medio)

- En medios compartidos hace falta decidir quién transmite en cada momento:
  - **Acceso por contención (no determinista):** todos compiten.
    - **CSMA/CD** (Ethernet heredada half duplex): escuchar antes de transmitir y, si hay colisión, parar y reintentar tras un tiempo aleatorio.
    - **CSMA/CA** (WLAN): como el medio inalámbrico no puede detectar colisiones, intenta evitarlas: espera, anuncia la transmisión y exige confirmación.
  - **Acceso controlado (determinista):** cada nodo espera su turno (paso de testigo en Token Ring). Heredado.
- En una red conmutada full duplex actual no hay colisiones, así que CSMA/CD ya no interviene: cada puerto del switch es su propio dominio de colisión.

### Para el examen
- Física = cables reales; lógica = flujo de tramas.
- WAN: punto a punto, hub and spoke, malla. LAN: estrella (actual), bus y anillo (heredadas).
- CSMA/CD = Ethernet antigua (detecta colisiones). CSMA/CA = Wi-Fi (las evita). No confundirlos.
- Full duplex + switch = sin colisiones.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Routing at the Network Layer

**(Cómo deciden el camino hosts y routers)**

## 3.1 How a Host Routes (Cómo enruta un host)

- Ante cada paquete, el host decide entre tres destinos: él mismo (loopback), un host de **su propia red** (entrega directa) o un host **remoto** (entrega al default gateway).
- Para saberlo, en IPv4 aplica el AND de la máscara: si la porción de red del destino coincide con la suya, es local. En IPv6 compara el prefijo (normalmente /64).
- Si es local, obtiene la MAC del destino (ARP en IPv4, Neighbor Discovery en IPv6) y le envía directo. Si es remoto, envía la trama a la MAC del **gateway**.
- Los hosts también tienen tabla de enrutamiento: `route print` o `netstat -r` en Windows. Contiene la red local, el loopback y la ruta por defecto 0.0.0.0/0 apuntando al gateway.

## 3.2 Routing Tables (La tabla de enrutamiento del router)

- El router decide por cada paquete: entregarlo en una red conectada directamente, reenviarlo a otro router o descartarlo si no hay ruta.
- Fuentes de las rutas, con su código en `show ip route`:

| Código | Tipo de ruta | Origen |
|---|---|---|
| **C** | Red conectada directamente | Interfaz activa con IP configurada |
| **L** | Local | La IP concreta de la propia interfaz (/32) |
| **S** | Estática | Configurada a mano por el administrador |
| **S\*** | Estática por defecto | `ip route 0.0.0.0 0.0.0.0 ...`: el gateway de último recurso |
| **O / D / R** | Dinámica | Aprendida por OSPF / EIGRP / RIP |

- Cada entrada indica red de destino y prefijo, métrica y distancia administrativa, siguiente salto o interfaz de salida.
- La selección usa la **coincidencia más larga (longest match):** gana la ruta cuyo prefijo coincida en más bits con el destino. Si nada coincide y no hay ruta por defecto, el paquete se descarta.

### Para el examen
- Local o remoto se decide con el AND de la máscara. Remoto = entregar al gateway.
- `route print` y `netstat -r` muestran la tabla del host; `show ip route` la del router.
- Los códigos C, L, S, S*, O: los preguntan directamente sobre una salida de `show ip route`.
- Longest match: ante varias rutas candidatas, gana el prefijo más largo.
- Sin ruta y sin ruta por defecto, el paquete se descarta.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 1 a 3

Primer examen parcial del curso: evalúa la capa física (medios, cobre, UTP, fibra), las topologías y métodos de acceso al medio, y el enrutamiento básico de hosts y routers.

[⬆ Volver al índice](#índice)

---

# MÓDULO 4 — IPv6 Addressing

**(Direccionamiento IPv6)**

## 4.1 IPv6 Address Types (Tipos de direcciones IPv6)

- IPv6 existe porque las IPv4 se agotaron: pasa de 32 a **128 bits**, escritos como 8 **hextetos** de 16 bits en hexadecimal separados por dos puntos.
- Dos reglas para abreviar:
  1. Omitir los ceros a la izquierda de cada hexteto (`0DB8` → `DB8`).
  2. Sustituir **una sola vez** una cadena de hextetos a cero por `::`.
  - Ejemplo: `2001:0db8:0000:0000:0000:0000:0000:0001` → `2001:db8::1`
- La longitud de prefijo se escribe con barra (`/64`); no existen máscaras decimales. El prefijo típico de una LAN es **/64**: 64 bits de prefijo y 64 de identificador de interfaz.
- Tipos de dirección que hay que reconocer:

| Tipo | Rango | Uso |
|---|---|---|
| **GUA (global unicast)** | `2000::/3` | Pública y enrutable por internet |
| **LLA (link-local)** | `fe80::/10` | Obligatoria en toda interfaz IPv6; solo válida en su enlace, no enrutable |
| **ULA (unique local)** | `fc00::/7` | Privadas, el equivalente aproximado a RFC 1918 |
| **Loopback** | `::1` | El 127.0.0.1 de IPv6 |
| **Sin especificar** | `::` | Origen cuando aún no se tiene dirección |
| **Multicast** | `ff00::/8` | Entrega a grupos; **IPv6 no tiene broadcast** |

- Estructura de una GUA: 48 bits de prefijo de enrutamiento global + 16 bits de subnet ID + 64 bits de ID de interfaz. Con 16 bits de subred: 65 536 subredes sin tocar el ID de interfaz.

## 4.2 GUA and LLA Static Configuration (Configuración estática)

- En el router, dentro de la interfaz:

```
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
```

- LLA estática, para que el gateway sea fácil de identificar en todas las redes:

```
R1(config-if)# ipv6 address fe80::1 link-local
```

- En Windows se configura en las propiedades de TCP/IPv6, igual que en IPv4. Verificación en el router: `show ipv6 interface brief`.

## 4.3 Dynamic Addressing for IPv6 GUAs (GUA dinámica: SLAAC y DHCPv6)

- El host pregunta con un **RS (Router Solicitation)** y el router contesta con un **RA (Router Advertisement)**, que anuncia el prefijo de la red y cómo obtener dirección. Tres métodos según los flags del RA:

| Método | Flags | Qué hace el host |
|---|---|---|
| **Solo SLAAC** | A=1 | Construye su dirección: prefijo del RA + ID de interfaz autogenerado. Sin servidor |
| **SLAAC + DHCPv6 sin estado** | A=1, O=1 | Dirección por SLAAC; DNS y otros datos, de un servidor DHCPv6 |
| **DHCPv6 con estado** | M=1 | Todo del servidor DHCPv6, como en IPv4 |

- En los tres casos el **gateway es siempre la LLA del router** que envió el RA; nunca lo asigna el servidor DHCPv6.
- El ID de interfaz autogenerado sale de uno de estos dos métodos:
  - **EUI-64:** parte la MAC en dos, inserta `FFFE` en medio e invierte el séptimo bit.
  - **Aleatorio de 64 bits:** lo que hace Windows por defecto, por privacidad (la MAC no queda expuesta).

## 4.4 Dynamic Addressing for IPv6 LLAs (LLA dinámica)

- Si no se configura a mano, la interfaz genera su LLA automáticamente: prefijo `fe80::/10` + ID de interfaz (EUI-64 en routers Cisco, aleatorio en Windows).
- Las LLA son las direcciones con las que los routers se hablan entre sí en el enlace y la que los hosts usan como gateway.
- Verificación: `show ipv6 interface brief` en IOS (muestra LLA y GUA de cada interfaz), `ipconfig` en Windows.

## 4.5 IPv6 Multicast Addresses (Direcciones multicast)

- Multicast asignados (well-known) que hay que memorizar:
  - **`ff02::1` (all-nodes):** lo escuchan todos los dispositivos IPv6 del enlace; el efecto es similar a un broadcast. Los RA se envían aquí.
  - **`ff02::2` (all-routers):** lo escuchan los routers; los RS de los hosts se envían aquí.
- **Multicast de nodo solicitado (solicited-node):** `ff02::1:ff` + los últimos 24 bits de la dirección unicast. Cada host escucha el suyo, y así la resolución de direcciones molesta solo a quien corresponde en lugar de a toda la red.

### Para el examen
- Practicar la compresión de direcciones: `::` solo puede aparecer una vez.
- Rangos de memoria: GUA `2000::/3`, LLA `fe80::/10`, ULA `fc00::/7`, multicast `ff00::/8`, loopback `::1`.
- IPv6 no tiene broadcast; su papel lo hace el multicast (`ff02::1`).
- SLAAC solo / SLAAC + DHCPv6 sin estado / DHCPv6 con estado, y qué flag activa cada uno (A, O, M).
- El gateway siempre es la LLA del router del RA, se use el método que se use.
- EUI-64: MAC partida en dos + `FFFE` en medio + séptimo bit invertido.

[⬆ Volver al índice](#índice)

---

# MÓDULO 5 — IPv6 Neighbor Discovery

**(Neighbor Discovery: el sustituto de ARP)**

## 5.1 Neighbor Discovery Operation (Funcionamiento de ND)

- **ND (Neighbor Discovery)** forma parte de ICMPv6 y usa cinco tipos de mensaje:

| Mensaje | Función |
|---|---|
| **RS (Router Solicitation)** | El host pide a los routers que se anuncien |
| **RA (Router Advertisement)** | El router anuncia prefijo, flags y su LLA como gateway |
| **NS (Neighbor Solicitation)** | "¿Quién tiene esta IPv6?": pide la MAC de un vecino |
| **NA (Neighbor Advertisement)** | Respuesta con la MAC solicitada |
| **Redirect** | Un router indica al host un mejor siguiente salto |

- **Resolución de direcciones** (lo que en IPv4 hace ARP): el host envía un NS al multicast de nodo solicitado del destino, y el propietario responde con un NA que incluye su MAC. Al usar multicast dirigido en lugar de broadcast, solo procesa la consulta quien debe.
- **DAD (Duplicate Address Detection):** antes de usar una dirección, el host envía un NS preguntando por ella misma; si nadie responde con un NA, la dirección es única y puede usarla.
- Las parejas IPv6-MAC aprendidas se guardan en la **tabla de vecinos** (neighbor table), el equivalente de la tabla ARP: `show ipv6 neighbors` en IOS, `netsh interface ipv6 show neighbors` en Windows.

### Para el examen
- Los 5 mensajes ND y su pareja de función: RS/RA para direccionamiento, NS/NA para resolución.
- ND sustituye a ARP en IPv6 y usa multicast de nodo solicitado, no broadcast.
- DAD = NS preguntando por tu propia dirección; el silencio es buena señal.
- RS se envía a `ff02::2`; RA a `ff02::1`.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: módulos 4 y 5

Segundo examen parcial del curso: evalúa el direccionamiento IPv6 (tipos, configuración estática, SLAAC y DHCPv6, multicast) y Neighbor Discovery.

[⬆ Volver al índice](#índice)

---

# Próximos módulos (pendientes de cursar)

Se añadirán a este manual a medida que avance el curso:

| Módulo | Título |
|---|---|
| 6 | Cisco Switches and Routers (conmutación, arranque de switch y router) |
| 7 | Troubleshoot Common Network Problems (proceso de troubleshooting, capa física, Wi-Fi, internet y soporte) |
| — | Checkpoint Exam: módulos 6 y 7 |
| — | Course Final Exam |

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1:** *physical layer · encoding · signaling · bandwidth · throughput · goodput · latency · attenuation · EMI/RFI · crosstalk · UTP · STP · coaxial · RJ-45 · Cat 5e/6 · T568A/T568B · straight-through · crossover · rollover · auto-MDIX · 100 meters · fiber-optic · single-mode · multimode · laser/LED · FTTH · ST/SC/LC connectors*

**Módulo 2:** *physical topology · logical topology · point-to-point · hub and spoke · mesh · star · extended star · bus · ring · half duplex · full duplex · media access control · contention-based · CSMA/CD · CSMA/CA · token passing · collision domain*

**Módulo 3:** *host routing decision · default gateway · `route print` · `netstat -r` · routing table · directly connected (C) · local route (L) · static route (S) · default route (S*) · dynamic routing (OSPF, EIGRP, RIP) · administrative distance · metric · next hop · exit interface · longest match · gateway of last resort · `show ip route`*

**Módulo 4:** *IPv6 · 128 bits · hextet · double colon (::) · prefix length · /64 · GUA (2000::/3) · LLA (fe80::/10) · ULA (fc00::/7) · loopback (::1) · unspecified (::) · multicast (ff00::/8) · no broadcast · `ipv6 address` · `link-local` · RS/RA · SLAAC · stateless DHCPv6 · stateful DHCPv6 · A/O/M flags · EUI-64 · FFFE · random interface ID · ff02::1 all-nodes · ff02::2 all-routers · solicited-node multicast · `show ipv6 interface brief`*

**Módulo 5:** *Neighbor Discovery (ND) · ICMPv6 · Router Solicitation · Router Advertisement · Neighbor Solicitation · Neighbor Advertisement · Redirect · address resolution · DAD (Duplicate Address Detection) · neighbor table · `show ipv6 neighbors` · solicited-node multicast*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **Ancho de banda** | Capacidad teórica de un medio, en bits por segundo; el techo, no lo que se consigue. |
| **Atenuación** | Pérdida de fuerza de la señal con la distancia; la razón del límite de 100 m del UTP. |
| **Cable crossover** | Cable UTP con T568A en un extremo y T568B en el otro; conecta dispositivos iguales. |
| **Cable de consola (rollover)** | Cable con pineado invertido para conectar un PC al puerto de consola de un equipo Cisco. |
| **Cable directo (straight-through)** | Cable UTP con el mismo pineado en ambos extremos; conecta dispositivos distintos (PC-switch). |
| **Coaxial** | Cable de conductor central y malla; usado en antenas y en el módem de internet por cable. |
| **CSMA/CA** | Acceso al medio de las WLAN: evita colisiones esperando turno y exigiendo confirmación. |
| **CSMA/CD** | Acceso al medio de la Ethernet heredada half duplex: detecta colisiones y reintenta. |
| **DAD** | Duplicate Address Detection: NS a la propia dirección para comprobar que nadie más la usa. |
| **DHCPv6 con estado** | El servidor asigna dirección y configuración, como el DHCP de IPv4; flag M del RA. |
| **DHCPv6 sin estado** | El host construye su dirección por SLAAC y el servidor solo aporta DNS y opciones; flag O. |
| **Diafonía (crosstalk)** | Interferencia de un hilo sobre el vecino; se cancela trenzando los pares. |
| **Distancia administrativa** | Confianza que merece la fuente de una ruta; a menor valor, más preferida. |
| **EMI/RFI** | Interferencias electromagnéticas y de radio que degradan la señal en cobre; la fibra es inmune. |
| **EUI-64** | Método que genera el ID de interfaz IPv6 desde la MAC: la parte en dos, inserta FFFE e invierte el séptimo bit. |
| **Fibra monomodo** | Núcleo fino y láser; alcanza decenas de kilómetros. La de las largas distancias. |
| **Fibra multimodo** | Núcleo grueso y LED; hasta unos 550 m. La habitual en backbones de edificio. |
| **Gateway de último recurso** | La ruta por defecto del router: adonde va todo paquete sin ruta más específica. |
| **Goodput** | Datos útiles por segundo: el throughput descontando las cabeceras de protocolo. |
| **GUA (global unicast address)** | Dirección IPv6 pública y enrutable, del rango 2000::/3. |
| **Hexteto** | Cada uno de los 8 bloques de 16 bits de una dirección IPv6. |
| **Hub and spoke** | Topología WAN con un nodo central del que dependen las sedes. |
| **LLA (link-local address)** | Dirección IPv6 obligatoria de cada interfaz, del rango fe80::/10; solo vale dentro del enlace. |
| **Longest match** | Criterio de selección de rutas: gana la de prefijo más largo que coincida con el destino. |
| **Malla (mesh)** | Topología con enlaces entre todos los nodos; máxima redundancia, máximo coste. |
| **Multicast de nodo solicitado** | Dirección ff02::1:ff + últimos 24 bits de la unicast; la usa ND para resolver direcciones sin molestar a toda la red. |
| **Neighbor Advertisement (NA)** | Respuesta ND con la MAC solicitada; equivale al ARP reply. |
| **Neighbor Discovery (ND)** | Protocolo de ICMPv6 que sustituye a ARP y gestiona el direccionamiento dinámico en IPv6. |
| **Neighbor Solicitation (NS)** | Petición ND de la MAC de un vecino; equivale al ARP request. |
| **Punto a punto** | Topología WAN de dos extremos unidos por un enlace permanente. |
| **Router Advertisement (RA)** | Anuncio del router con el prefijo de red, los flags A/O/M y su LLA como gateway. |
| **Router Solicitation (RS)** | Petición del host para que los routers del enlace se anuncien; se envía a ff02::2. |
| **Ruta estática** | Ruta configurada a mano por el administrador; código S en la tabla. |
| **Ruta por defecto** | Ruta 0.0.0.0/0 (o ::/0) que captura el tráfico sin destino más específico. |
| **SLAAC** | Stateless Address Autoconfiguration: el host se construye su GUA con el prefijo del RA, sin servidor. |
| **STP (par trenzado blindado)** | UTP con apantallamiento extra contra EMI; más caro, para entornos ruidosos. |
| **T568A / T568B** | Normas de orden de los hilos en el conector RJ-45. |
| **Tabla de enrutamiento** | Lista de redes conocidas por un host o router con la forma de alcanzarlas. |
| **Tabla de vecinos** | Caché IPv6-MAC que mantiene ND; la tabla ARP de IPv6. |
| **Throughput** | Tasa de transferencia real conseguida, siempre por debajo del ancho de banda. |
| **Topología física** | Disposición real de equipos y cableado. |
| **Topología lógica** | Cómo fluyen las tramas entre nodos, con independencia del cableado. |
| **ULA (unique local address)** | Direcciones IPv6 privadas del rango fc00::/7, no enrutables por internet. |
| **UTP** | Par trenzado sin blindaje: el cable estándar de las LAN, con conector RJ-45. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Network Addressing and Basic Troubleshooting», tercer curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
