[← Volver a la página principal del repositorio](../../README.md)

# Networking Basics

> **Objetivo del curso:** comprender los fundamentos de las redes: dispositivos, medios y protocolos. Observar el flujo de datos en una red, configurar dispositivos para conectarse y usar aplicaciones y protocolos de red para tareas reales.

**Estado de estos apuntes:** curso completo. Cubren los 17 módulos, los 5 checkpoint exams y el examen final (22 horas, 13 labs).

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Communication in a Connected World](#módulo-1--communication-in-a-connected-world)
- [Módulo 2 — Network Components, Types, and Connections](#módulo-2--network-components-types-and-connections)
- [Módulo 3 — Wireless and Mobile Networks](#módulo-3--wireless-and-mobile-networks)
- [Módulo 4 — Build a Home Network](#módulo-4--build-a-home-network)
- [Checkpoint Exam: Build a Small Network](#checkpoint-exam-build-a-small-network)
- [Módulo 5 — Communication Principles](#módulo-5--communication-principles)
- [Módulo 6 — Network Media](#módulo-6--network-media)
- [Módulo 7 — The Access Layer](#módulo-7--the-access-layer)
- [Checkpoint Exam: Network Access](#checkpoint-exam-network-access)
- [Módulo 8 — The Internet Protocol](#módulo-8--the-internet-protocol)
- [Módulo 9 — IPv4 and Network Segmentation](#módulo-9--ipv4-and-network-segmentation)
- [Módulo 10 — IPv6 Addressing Formats and Rules](#módulo-10--ipv6-addressing-formats-and-rules)
- [Módulo 11 — Dynamic Addressing with DHCP](#módulo-11--dynamic-addressing-with-dhcp)
- [Checkpoint Exam: The Internet Protocol](#checkpoint-exam-the-internet-protocol)
- [Módulo 12 — Gateways to Other Networks](#módulo-12--gateways-to-other-networks)
- [Módulo 13 — The ARP Process](#módulo-13--the-arp-process)
- [Módulo 14 — Routing Between Networks](#módulo-14--routing-between-networks)
- [Checkpoint Exam: Communication Between Networks](#checkpoint-exam-communication-between-networks)
- [Módulo 15 — TCP and UDP](#módulo-15--tcp-and-udp)
- [Módulo 16 — Application Layer Services](#módulo-16--application-layer-services)
- [Módulo 17 — Network Testing Utilities](#módulo-17--network-testing-utilities)
- [Checkpoint Exam: Protocols for Specific Tasks](#checkpoint-exam-protocols-for-specific-tasks)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del módulo correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST Networking aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Práctica relacionada del repositorio: [Packet Tracer y redes básicas](../../recursos/packet-tracer-redes-basicas.md) (enrutamiento entre dos subredes, ligada a los módulos 8, 9, 12 y 14).

---

# MÓDULO 1 — Communication in a Connected World

**(Comunicación en un mundo conectado)**

## 1.1 Network Types (Tipos de redes)

- Todo está conectado: dispositivos personales, domótica, sensores (IoT), empresas y administraciones.
- Clasificación por alcance:

| Red | Alcance |
|---|---|
| **PAN** | Personal (Bluetooth, pocos metros) |
| **LAN** | Local: casa, oficina, edificio |
| **WLAN** | LAN inalámbrica (Wi-Fi) |
| **MAN** | Área metropolitana (ciudad) |
| **WAN** | Área amplia: interconecta LANs distantes. Internet es la WAN de WANs |

## 1.2 Data Transmission (Transmisión de datos)

- El **bit** es la unidad mínima (0 o 1); un **byte** son 8 bits.
- Los datos (texto, imagen, audio, vídeo) se digitalizan a bits antes de transmitirse.
- Tres métodos de señal según el medio: **eléctrica** (cobre), **óptica** (pulsos de luz en fibra) e **inalámbrica** (ondas de radio).

## 1.3 Bandwidth and Throughput (Ancho de banda y rendimiento)

- **Ancho de banda (bandwidth):** capacidad teórica máxima del enlace. Se mide en bps y múltiplos (Kbps, Mbps, Gbps).
- **Rendimiento (throughput):** lo que realmente se transmite, siempre igual o menor que el ancho de banda. Lo reducen la latencia, la congestión, el número de saltos y el dispositivo más lento del camino.

### Para el examen
- Bandwidth es la capacidad teórica; throughput es la velocidad real medida, y nunca supera al primero.
- El throughput de un trayecto lo limita el enlace más lento del camino.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Network Components, Types, and Connections

**(Componentes de red, tipos y conexiones)**

## 2.1 Clients and Servers (Clientes y servidores)

- **Host:** cualquier dispositivo que envía o recibe datos en la red.
- **Servidor:** proporciona servicios (web, correo, archivos). **Cliente:** los solicita y consume.
- Un mismo equipo puede ser cliente y servidor a la vez (redes **peer-to-peer, P2P**). P2P resulta simple y barato pero no escala: sin administración centralizada hay menos seguridad y peor rendimiento.

## 2.2 Network Components (Componentes de la infraestructura)

| Dispositivo | Función |
|---|---|
| **Switch** | Conecta dispositivos dentro de la LAN y conmuta tramas entre ellos |
| **Router** | Encamina paquetes entre redes distintas |
| **Punto de acceso (AP)** | Extiende la red por Wi-Fi |
| **Firewall** | Filtra el tráfico según reglas de seguridad |
| **Módem/ONT** | Conecta con la red del proveedor (ISP) |

- **Medios:** cobre (señales eléctricas), fibra óptica (luz) e inalámbrico (radio).

## 2.3 ISP Connectivity Options (Opciones de conexión al ISP)

| Tecnología | Característica |
|---|---|
| **DSL** | Por línea telefónica; velocidad según distancia a la central |
| **Cable** | Por el coaxial de la TV; ancho de banda compartido con el vecindario |
| **Fibra (FTTH)** | La opción más rápida y estable |
| **Celular (4G/5G)** | Donde no llega el cableado; depende de cobertura |
| **Satélite** | Zonas rurales; latencia alta |
| **Línea dedicada** | Empresas; caudal garantizado |

### Para el examen
- P2P es adecuado solo para redes muy pequeñas; sus desventajas (seguridad, escalabilidad, administración) son pregunta habitual.
- Saber emparejar cada tecnología de acceso con su escenario típico: satélite para zona rural aislada, fibra para máxima velocidad.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Wireless and Mobile Networks

**(Redes inalámbricas y móviles)**

## 3.1 Wireless Networks (Redes inalámbricas)

- Usan ondas de radio en bandas con y sin licencia.
- **Telefonía celular:** la zona se divide en celdas atendidas por antenas; generaciones **3G/4G/5G** (5G aporta más velocidad, menos latencia y más dispositivos por antena).
- Otras tecnologías: **Wi-Fi** (LAN inalámbrica), **Bluetooth** (PAN, corto alcance, poco consumo), **GPS** (posicionamiento).

## 3.2 Mobile Device Connectivity (Conectividad de dispositivos móviles)

- Los móviles alternan entre red celular y Wi-Fi: el Wi-Fi ahorra datos del plan y suele ser más rápido.
- Configuración habitual que gestiona el soporte: activar o desactivar Wi-Fi y datos, emparejar Bluetooth, hotspot personal (tethering), modo avión, GPS y localización.

### Para el examen
- Bluetooth funciona por emparejamiento (pairing) y corto alcance; Wi-Fi por asociación a un SSID.
- El tethering/hotspot convierte el móvil en punto de acceso para otros dispositivos.

[⬆ Volver al índice](#índice)

---

# MÓDULO 4 — Build a Home Network

**(Montar una red doméstica)**

## 4.1 Home Network Basics (Fundamentos)

- El **router doméstico** integra varios dispositivos en uno: router, switch (puertos LAN), punto de acceso Wi-Fi y, a menudo, firewall y servidor DHCP.
- Puertos: WAN/Internet (hacia el ISP) y LAN (hacia los equipos de casa).

## 4.2 Network Technologies in the Home (Tecnologías del hogar)

- Inalámbricas: Wi-Fi, Bluetooth y bandas de radiofrecuencia de **2,4 GHz y 5 GHz**.
- Cableadas: Ethernet (Cat 5e/6) y **powerline** (red por la instalación eléctrica, útil donde no llega el Wi-Fi ni el cable).

## 4.3 Wireless Standards (Estándares inalámbricos)

- Familia **IEEE 802.11** (Wi-Fi): 802.11n (Wi-Fi 4), 802.11ac (Wi-Fi 5), 802.11ax (Wi-Fi 6).
- 2,4 GHz: más alcance y penetración, más interferencias (microondas, Bluetooth, vecinos); canales 1, 6 y 11 sin solape.
- 5 GHz: más velocidad y canales, menos alcance.

## 4.4 Set Up a Home Router (Configurar el router doméstico)

Pasos y buenas prácticas:

1. Acceder a la administración vía web (IP del gateway, p. ej. 192.168.0.1).
2. **Cambiar usuario y contraseña de administración por defecto** (primera medida siempre).
3. Actualizar el firmware.
4. Configurar el **SSID** (nombre de red) y decidir si se difunde.
5. Seguridad inalámbrica: **WPA2 o WPA3** (nunca WEP ni red abierta).
6. Revisar DHCP (rango de IPs que reparte el router).
7. Canal Wi-Fi: fijo 1, 6 u 11 en 2,4 GHz si hay interferencias.

### Para el examen
- Primera acción al instalar un router: cambiar las credenciales de administración por defecto.
- Canales sin solape en 2,4 GHz: 1, 6 y 11.
- Ocultar el SSID no es una medida de seguridad real; la seguridad la da WPA2/WPA3.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: Build a Small Network

Primer examen parcial del curso: evalúa los módulos 1 a 4 (tipos de red, componentes, conexión al ISP, redes inalámbricas y configuración del router doméstico).

[⬆ Volver al índice](#índice)

---

# MÓDULO 5 — Communication Principles

**(Principios de comunicación)**

## 5.1 Communication Protocols (Protocolos)

- Toda comunicación necesita tres elementos: **emisor, receptor y canal** (medio).
- Los **protocolos** son las reglas que la gobiernan: formato y tamaño del mensaje, temporización, codificación, encapsulación y patrón (unicast, broadcast, multicast).

## 5.2 Communication Standards (Estándares)

- Los estándares garantizan que equipos de distintos fabricantes se entiendan.
- Organismos clave: **IEEE** (Ethernet 802.3, Wi-Fi 802.11), **IETF** (RFCs: TCP/IP y protocolos de internet), ITU, IANA/ICANN (direcciones y dominios).

## 5.3 Network Communication Models (Modelos de comunicación)

Los modelos en capas dividen el proceso para entenderlo y diagnosticarlo:

| OSI (7 capas) | TCP/IP (4 capas) | Qué hace |
|---|---|---|
| 7 Aplicación · 6 Presentación · 5 Sesión | Aplicación | Datos de las aplicaciones (HTTP, DNS, SMTP) |
| 4 Transporte | Transporte | TCP/UDP, puertos, segmentación |
| 3 Red | Internet | IP, direccionamiento lógico, enrutamiento |
| 2 Enlace · 1 Física | Acceso a la red | Tramas, MAC, medios físicos |

### Para el examen
- Memoriza las 7 capas OSI en orden (truco: *Please Do Not Throw Sausage Pizza Away*, de física a aplicación).
- Saber ubicar protocolos y dispositivos en su capa: switch en la 2, router e IP en la 3, TCP/UDP en la 4, HTTP en la 7.

[⬆ Volver al índice](#índice)

---

# MÓDULO 6 — Network Media

**(Medios de red)**

## 6.1 Network Media Types (Tipos de medios)

| Medio | Señal | Características |
|---|---|---|
| **Par trenzado (UTP)** | Eléctrica | El más común en LAN; Cat 5e/6/6a; hasta 100 m por tramo; sensible a interferencias (EMI) |
| **Fibra óptica** | Luz | Largas distancias y gran ancho de banda; inmune a EMI; más cara; monomodo (km) y multimodo (cientos de m) |
| **Inalámbrico** | Radio | Movilidad; sensible a obstáculos e interferencias; medio compartido |

- Criterios de elección: distancia a cubrir, entorno (interferencias), ancho de banda necesario y presupuesto.

### Para el examen
- UTP: máximo 100 metros por segmento. Dato clásico.
- Fibra: inmune a interferencias electromagnéticas; la elección para unir edificios o largas distancias.

[⬆ Volver al índice](#índice)

---

# MÓDULO 7 — The Access Layer

**(La capa de acceso)**

## 7.1 Encapsulation and the Ethernet Frame (Encapsulación y trama Ethernet)

- **Encapsulación:** cada capa envuelve los datos con su propia cabecera, como una carta dentro de un sobre. En la capa de acceso, el paquete IP se encapsula en una **trama Ethernet**.
- Campos clave de la trama: MAC de destino, MAC de origen, tipo, datos y FCS (control de errores).

## 7.2 The Access Layer (Hubs y switches)

- **Dirección MAC:** identificador físico de 48 bits grabado en la tarjeta de red, escrito en hexadecimal (p. ej. `3C:97:0E:12:AB:CD`). Única por dispositivo.
- **Hub (obsoleto):** repite todo por todos los puertos; un solo dominio de colisión; ineficiente.
- **Switch:** aprende las MACs conectadas a cada puerto y construye su **tabla de direcciones MAC**; entrega cada trama solo por el puerto del destinatario. Si la MAC de destino no está en la tabla, reenvía por todos los puertos excepto el de origen (flooding).

### Para el examen
- El switch decide por la **MAC de destino**, consultando su tabla; aprende las MACs leyendo la **MAC de origen** de las tramas que recibe.
- Hub: un dominio de colisión compartido. Switch: un dominio de colisión por puerto.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: Network Access

Segundo examen parcial: evalúa los módulos 5 a 7 (protocolos y modelos OSI/TCP-IP, medios de red, encapsulación, MAC y switches).

[⬆ Volver al índice](#índice)

---

# MÓDULO 8 — The Internet Protocol

**(El protocolo de internet)**

## 8.1 Purpose of an IPv4 Address (Propósito de la dirección IPv4)

- Cada host necesita una dirección IP **única** en su red para comunicarse.
- La IP es **lógica** (la asigna la red y cambia al cambiar de red); la MAC es **física** (fija del dispositivo). Analogía: IP como dirección postal, MAC como DNI.

## 8.2 The IPv4 Address Structure (Estructura de IPv4)

- 32 bits divididos en **4 octetos** en notación decimal con puntos: `192.168.10.2`.
- Cada octeto va de 0 a 255 (8 bits).
- La dirección tiene dos partes: **porción de red** y **porción de host**. La **máscara de subred** marca la frontera: los bits a 1 son red, los bits a 0 son host.

| Máscara | CIDR | Bits de host | Hosts útiles |
|---|---|---|---|
| 255.0.0.0 | /8 | 24 | 16.777.214 |
| 255.255.0.0 | /16 | 16 | 65.534 |
| 255.255.255.0 | /24 | 8 | 254 |

- Hosts útiles = 2^n − 2 (se restan la dirección de red y la de broadcast).

### Para el examen
- Dominar la conversión máscara ↔ CIDR y el cálculo de hosts útiles (2^n − 2).
- Dos hosts solo se comunican directamente si comparten porción de red (misma subred); si no, necesitan el router.

[⬆ Volver al índice](#índice)

---

# MÓDULO 9 — IPv4 and Network Segmentation

**(IPv4 y segmentación de redes)**

## 9.1 IPv4 Unicast, Broadcast, and Multicast (Tipos de transmisión)

| Tipo | Destino | Ejemplo |
|---|---|---|
| **Unicast** | Un único host | Navegar a un servidor web |
| **Broadcast** | Todos los hosts de la red local (todos los bits de host a 1) | Petición ARP, DHCP Discover |
| **Multicast** | Un grupo suscrito (rango 224.0.0.0 a 239.255.255.255) | Streaming a varios receptores, protocolos de routing |

- Los routers **no reenvían broadcasts**: quedan contenidos en su red local.

## 9.2 Types of IPv4 Addresses (Tipos de direcciones IPv4)

- **Públicas:** únicas y enrutables por internet; las administra IANA/ICANN.
- **Privadas (RFC 1918):** solo para redes internas, no enrutables en internet:
  - `10.0.0.0/8`
  - `172.16.0.0/12` (172.16.0.0 – 172.31.255.255)
  - `192.168.0.0/16`
- **Salida a internet:** las direcciones privadas salen mediante **NAT** (el router traduce privada ↔ pública).
- **Direcciones de uso especial:**
  - **Loopback:** `127.0.0.1` (prueba de la pila TCP/IP local).
  - **Link-local / APIPA:** `169.254.0.0/16` (autoasignada si falla DHCP).
- **Direccionamiento con clases (legacy):** clases A (1-126), B (128-191) y C (192-223), con máscaras fijas /8, /16 y /24. Hoy sustituido por **CIDR**, que permite máscaras de cualquier longitud y aprovecha mejor el espacio.
- La asignación global la gestionan IANA y los registros regionales (RIRs); los ISPs reparten a sus clientes.

## 9.3 Network Segmentation (Segmentación de redes)

- Cada broadcast lo procesan **todos** los hosts del segmento: en redes grandes, los broadcasts (ARP, DHCP) degradan el rendimiento.
- Un **dominio de broadcast** agrupa todos los dispositivos que reciben los broadcasts de los demás; lo delimitan los routers.
- **Segmentar** la red en subredes más pequeñas (subnetting):
  - Reduce el tráfico de broadcast en cada segmento.
  - Mejora el rendimiento y la seguridad (aislar departamentos, invitados, servidores).
  - Facilita la administración y la localización de problemas.
- La segmentación se hace por ubicación, grupo o tipo de dispositivo, y cada subred usa el router como salida (default gateway).

### Para el examen
- Los tres rangos privados RFC 1918, de memoria, con sus máscaras.
- 169.254.x.x significa APIPA: el cliente no contactó con DHCP. 127.0.0.1 es loopback.
- Los routers delimitan dominios de broadcast; los switches no (sin VLANs).
- Clases legacy A/B/C: reconocerlas por el primer octeto, sabiendo que hoy se usa CIDR.

[⬆ Volver al índice](#índice)

---

# MÓDULO 10 — IPv6 Addressing Formats and Rules

**(Formatos y reglas de direccionamiento IPv6)**

## 10.1 IPv4 Issues (El problema de IPv4)

- IPv4 ofrece unos 4.300 millones de direcciones; con internet, los móviles y el IoT, el espacio está **agotado**.
- NAT y las direcciones privadas han alargado la vida de IPv4, pero son un parche: rompen la conexión extremo a extremo y complican algunos servicios.
- **IPv6** es la solución definitiva: 128 bits, es decir, 340 sextillones de direcciones (3,4 × 10^38).
- IPv4 e IPv6 convivirán durante años. Técnicas de coexistencia: **dual stack** (el host tiene ambas direcciones a la vez), **tunneling** (transportar IPv6 dentro de paquetes IPv4) y **translation** (NAT64, traducir entre ambos protocolos).

## 10.2 IPv6 Addressing (Direccionamiento IPv6)

- 128 bits escritos en **hexadecimal**: 8 grupos de 16 bits (**hextetos**) separados por dos puntos.

```
2001:0db8:0000:1111:0000:0000:0000:0200
```

- **Dos reglas para acortar la escritura:**
  1. **Omitir los ceros a la izquierda** de cada hexteto: `0db8` → `db8`, `0200` → `200`.
  2. **Sustituir una única secuencia de hextetos todo-cero por `::`** (solo puede usarse una vez por dirección).

```
2001:0db8:0000:1111:0000:0000:0000:0200
→ 2001:db8:0:1111::200
```

- El prefijo (equivalente a la porción de red) se indica con /n, habitualmente **/64**: los primeros 64 bits identifican la red y los otros 64 la interfaz.

### Para el examen
- Practica la compresión y descompresión de direcciones: es pregunta segura.
- El `::` solo puede aparecer **una vez**; si hubiera dos bloques de ceros, se comprime el más largo (o el primero si empatan).
- IPv6 = 128 bits y hexadecimal; IPv4 = 32 bits y decimal.

[⬆ Volver al índice](#índice)

---

# MÓDULO 11 — Dynamic Addressing with DHCP

**(Direccionamiento dinámico con DHCP)**

## 11.1 Static and Dynamic Addressing (Asignación estática y dinámica)

| Método | Cómo | Cuándo usarlo |
|---|---|---|
| **Estática** | El administrador configura a mano IP, máscara, gateway y DNS | Servidores, impresoras de red, equipos de red: dispositivos que deben tener siempre la misma IP |
| **Dinámica (DHCP)** | El servidor DHCP asigna la configuración automáticamente, en préstamo (*lease*) por tiempo limitado | Equipos de usuario, móviles, invitados: la mayoría de los hosts |

- DHCP ahorra trabajo, evita errores de tecleo y elimina IPs duplicadas; a cambio, la IP de un host puede cambiar con el tiempo.

## 11.2 DHCPv4 Configuration (Funcionamiento y configuración)

- La asignación sigue cuatro mensajes, la secuencia **DORA**:

```
Cliente → DISCOVER  (broadcast: ¿hay algún servidor DHCP?)
Servidor → OFFER    (te ofrezco esta IP)
Cliente → REQUEST   (acepto la oferta)
Servidor → ACK      (confirmado, es tuya durante el lease)
```

- En el router doméstico se configura: rango de direcciones a repartir (ámbito o *pool*), duración del préstamo y direcciones excluidas o reservadas (para los equipos con IP fija).
- Comandos del cliente: `ipconfig /release` (liberar la IP) e `ipconfig /renew` (pedir una nueva).
- Si ningún servidor DHCP responde, el cliente Windows se autoasigna una APIPA (169.254.x.x).

### Para el examen
- DORA en orden: Discover, Offer, Request, Acknowledge. Los dos primeros y el broadcast inicial caen mucho.
- Servidores e impresoras llevan IP estática (o reserva DHCP); los puestos de usuario, DHCP.
- APIPA en un cliente = el DHCP no respondió.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: The Internet Protocol

Tercer examen parcial: evalúa los módulos 8 a 11 (estructura IPv4, tipos de direcciones y segmentación, IPv6 y DHCP).

[⬆ Volver al índice](#índice)

---

# MÓDULO 12 — Gateways to Other Networks

**(Puertas de enlace a otras redes)**

## 12.1 Network Boundaries (Fronteras de red)

- El **router** marca la frontera de la red local: separa dominios de broadcast y comunica subredes.
- El **default gateway** es la IP de la interfaz del router dentro de la red local. Todo tráfico hacia destinos fuera de la propia subred se envía al gateway.
- Cada host debe tener configurado el gateway (a mano o por DHCP); sin él, solo alcanza su propia subred.
- El router doméstico hace de gateway de todos los equipos de casa hacia internet.

## 12.2 Network Address Translation (NAT)

- Dentro de la red se usan direcciones **privadas** (RFC 1918); internet solo enruta direcciones **públicas**.
- **NAT** resuelve el salto: el router sustituye la IP privada de origen por su IP pública al salir, y deshace el cambio con las respuestas que vuelven.
- Mantiene una **tabla de traducciones** para saber a qué host interno pertenece cada conexión; al usar también los puertos (PAT, NAT con sobrecarga), muchos hosts comparten una única IP pública.
- Es el motivo por el que toda una casa sale a internet con una sola IP pública contratada al ISP.

### Para el examen
- Sin default gateway: el host se comunica en su subred pero no sale de ella. Síntoma clásico en diagnóstico.
- NAT traduce privada → pública a la salida; PAT (sobrecarga) permite compartir una IP pública entre muchos hosts gracias a los puertos.
- La práctica de [Packet Tracer](../../recursos/packet-tracer-redes-basicas.md) del repositorio monta exactamente este escenario: dos subredes y su gateway.

[⬆ Volver al índice](#índice)

---

# MÓDULO 13 — The ARP Process

**(El proceso ARP)**

## 13.1 MAC and IP (MAC e IP juntas)

- Para entregar una trama en la red local hacen falta **las dos direcciones**: la IP de destino (lógica, capa 3) y la MAC de destino (física, capa 2).
- Si el destino está **en la misma red**, la trama lleva la MAC del destinatario final.
- Si el destino está **en otra red**, la trama lleva la MAC del **default gateway** (aunque la IP de destino siga siendo la del host remoto).
- **ARP (Address Resolution Protocol)** averigua la MAC que corresponde a una IP conocida:

```
1. El host consulta su tabla ARP (caché).
2. Si la IP no está, envía una petición ARP en broadcast: "¿Quién tiene la IP x.x.x.x?"
3. El propietario responde en unicast con su MAC.
4. El solicitante guarda la pareja IP-MAC en su tabla ARP y envía la trama.
```

- Ver y gestionar la caché: `arp -a` (mostrar) y `arp -d` (vaciar). Las entradas caducan solas pasado un tiempo.

## 13.2 Broadcast Containment (Contención de broadcasts)

- Las peticiones ARP son broadcasts: todos los hosts del segmento las procesan, aunque no sean para ellos.
- En un dominio de broadcast grande, el tráfico ARP y similares (DHCP) consume recursos de todos los equipos y degrada la red.
- Los **routers no reenvían broadcasts**: segmentar la red en subredes contiene los broadcasts en segmentos pequeños, exactamente la razón de la segmentación vista en el módulo 9.

### Para el examen
- Petición ARP en **broadcast**, respuesta en **unicast**. Lo preguntan tal cual.
- Destino en otra red: ARP resuelve la MAC del **gateway**, no la del host remoto.
- ARP trabaja dentro de la red local; nunca cruza el router.

[⬆ Volver al índice](#índice)

---

# MÓDULO 14 — Routing Between Networks

**(Enrutamiento entre redes)**

## 14.1 The Need for Routing (La necesidad del enrutamiento)

- Dentro de una red, el switch basta; entre redes distintas hace falta el **router**.
- La decisión del host emisor es simple: si el destino está en su misma subred, entrega directo; si no, envía la trama al default gateway.
- El router recibe el paquete, consulta su tabla y lo reenvía hacia el destino, salto a salto, eligiendo el **mejor camino** cuando hay varios.

## 14.2 The Routing Table (La tabla de enrutamiento)

- Cada router mantiene una **tabla de enrutamiento** con las redes que conoce y por dónde alcanzarlas. Tres orígenes:

| Tipo de ruta | Cómo se aprende |
|---|---|
| **Directamente conectada** | Automática: las redes de sus propias interfaces |
| **Estática** | Configurada a mano por el administrador |
| **Dinámica** | Aprendida de otros routers mediante protocolos de enrutamiento |

- Proceso al recibir un paquete: leer la IP de destino, buscar la red en la tabla, reenviar por la interfaz indicada. Si no hay coincidencia, usa la **ruta por defecto** (0.0.0.0/0, el "gateway of last resort"); si tampoco existe, descarta el paquete.
- Al cruzar cada router, la trama de capa 2 se reconstruye (nuevas MACs), pero las IPs de origen y destino no cambian.

## 14.3 Create a LAN (Montar una LAN)

- Una **LAN** es una red bajo una misma administración: desde la red de casa hasta la de una sede con cientos de equipos.
- Montaje típico de red pequeña: router (gateway y DHCP), switch para los puestos cableados, AP para Wi-Fi, y direccionamiento privado coherente en cada subred.
- En los labs del curso se monta con Packet Tracer una LAN con dos redes y un router entre ellas: el mismo escenario de la [práctica del repositorio](../../recursos/packet-tracer-redes-basicas.md).

### Para el examen
- Los tres tipos de ruta (conectada, estática, dinámica) y cuál usa el router si no encuentra la red de destino: la ruta por defecto.
- En el viaje de un paquete las IPs no cambian; las MACs cambian en cada salto.
- Switch = dentro de la red; router = entre redes.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: Communication Between Networks

Cuarto examen parcial: evalúa los módulos 12 a 14 (default gateway, NAT, ARP y enrutamiento entre redes).

[⬆ Volver al índice](#índice)

---

# MÓDULO 15 — TCP and UDP

**(TCP y UDP)**

## 15.1 TCP and UDP (Los dos protocolos de transporte)

| | **TCP** | **UDP** |
|---|---|---|
| Tipo | Orientado a conexión | Sin conexión |
| Fiabilidad | Garantiza entrega: acuses de recibo y retransmisión | "Best effort": envía y no comprueba |
| Orden | Reordena los segmentos | No reordena |
| Sobrecarga | Mayor (control) | Mínima (rápido) |
| Usos típicos | Web (HTTP/HTTPS), correo, FTP | Streaming, voz IP, juegos, DNS, DHCP |

- TCP abre la conexión con el **saludo de tres vías** (three-way handshake): `SYN → SYN-ACK → ACK`. El destino confirma lo recibido y el emisor retransmite lo que se pierde.
- UDP sacrifica garantías por velocidad: en una llamada o un directo, reenviar un fragmento perdido llegaría tarde; mejor seguir.

## 15.2 Port Numbers (Números de puerto)

- La IP identifica al host; el **puerto** identifica a la aplicación dentro del host. Así un servidor atiende web, correo y FTP a la vez.
- El cliente usa un puerto de origen aleatorio y el puerto de destino del servicio; la combinación IP + puerto es un **socket**.
- Puertos **bien conocidos** (0-1023) que hay que saber:

| Puerto | Protocolo | Servicio |
|---|---|---|
| 20/21 | TCP | FTP (datos/control) |
| 22 | TCP | SSH |
| 23 | TCP | Telnet (inseguro) |
| 25 | TCP | SMTP (envío de correo) |
| 53 | TCP/UDP | DNS |
| 67/68 | UDP | DHCP (servidor/cliente) |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS |

### Para el examen
- La tabla de puertos, de memoria. Caen varios seguro, aquí y en el CCST.
- TCP = fiable, con conexión, three-way handshake. UDP = rápido, sin conexión, para voz/vídeo/DNS/DHCP.
- Saber clasificar una aplicación: ¿tolera pérdidas pero no retrasos? UDP. ¿Necesita todos los datos íntegros? TCP.

[⬆ Volver al índice](#índice)

---

# MÓDULO 16 — Application Layer Services

**(Servicios de la capa de aplicación)**

## 16.1 The Client-Server Relationship (Relación cliente-servidor)

- El cliente pide, el servidor responde: el modelo de casi todo internet (URI/URL para localizar los recursos).

## 16.2 Network Application Services (Servicios habituales)

- **DNS:** traduce nombres de dominio a direcciones IP. Sin él habría que memorizar IPs; es el primer paso de casi cualquier conexión. Jerárquico y distribuido.
- **Web:** el navegador pide páginas con **HTTP** (texto plano) o **HTTPS** (cifrado con TLS; siempre preferible).
- **FTP:** transferencia de archivos entre cliente y servidor; usa dos conexiones (control 21, datos 20).
- **Terminales virtuales:** administración remota por línea de comandos. **Telnet** viaja en claro (obsoleto e inseguro); **SSH** cifra la sesión y es el estándar.
- **Correo electrónico:** tres protocolos repartidos por función:

| Protocolo | Función | Detalle |
|---|---|---|
| **SMTP** | Enviar | Del cliente al servidor y entre servidores |
| **POP3** | Recibir | Descarga los mensajes al equipo (y suele borrarlos del servidor) |
| **IMAP** | Recibir | Los mensajes quedan en el servidor, sincronizados entre dispositivos |

### Para el examen
- DNS: nombre → IP. Si falla, los nombres no resuelven pero el ping a una IP funciona (síntoma clásico).
- SSH sustituye a Telnet; HTTPS sustituye a HTTP. El motivo en ambos: cifrado.
- SMTP envía; POP3 e IMAP reciben. La diferencia entre POP3 e IMAP (descargar vs sincronizar) es pregunta típica.

[⬆ Volver al índice](#índice)

---

# MÓDULO 17 — Network Testing Utilities

**(Utilidades de diagnóstico de red)**

## 17.1 Troubleshooting Commands (Comandos de diagnóstico)

| Comando | Qué hace |
|---|---|
| `ipconfig` | Muestra IP, máscara y gateway del equipo (`/all` añade MAC, DNS y DHCP; `/release` y `/renew` renuevan la IP) |
| `ping` | Comprueba conectividad con un destino (ICMP echo); mide tiempos de respuesta |
| `tracert` | Muestra los saltos (routers) del camino hasta el destino y dónde se pierde |
| `nslookup` | Consulta el DNS: comprueba qué IP devuelve un nombre |
| `netstat` | Lista las conexiones activas y los puertos abiertos del equipo |

En Linux/macOS los equivalentes son `ifconfig`/`ip addr`, `ping`, `traceroute`, `nslookup`/`dig` y `netstat`/`ss`.

- **Secuencia de diagnóstico con ping**, de dentro hacia fuera:

```
1. ping 127.0.0.1        → ¿funciona la pila TCP/IP local?
2. ping <IP propia>      → ¿funciona la tarjeta de red?
3. ping <gateway>        → ¿llego al router?
4. ping <IP externa>     → ¿salgo a internet? (ej.: 8.8.8.8)
5. ping <nombre externo> → ¿resuelve el DNS? (ej.: cisco.com)
```

- Interpretación rápida: si el paso 4 funciona y el 5 falla, el problema es DNS. Si falla el 3, el problema está en la red local o el gateway.

### Para el examen
- La secuencia de ping escalonada y qué indica cada fallo. Es de las preguntas más repetidas del CCST.
- `tracert` localiza en qué salto se pierde el tráfico; `nslookup` aísla problemas de DNS.
- `ipconfig /all` es el primer comando ante "no tengo red": revela APIPA, gateway ausente o DNS mal configurado.

[⬆ Volver al índice](#índice)

---

# Checkpoint Exam: Protocols for Specific Tasks

Quinto examen parcial: evalúa los módulos 15 a 17 (TCP/UDP y puertos, servicios de aplicación y utilidades de diagnóstico).

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El **Networking Basics Course Final Exam** cubre los 17 módulos. Recomendaciones de repaso:

1. Vuelve a los apartados "Para el examen" de cada módulo: concentran lo más preguntado.
2. Repasa de memoria: rangos RFC 1918, tabla de puertos del módulo 15, DORA, capas OSI, canales 1-6-11 y la secuencia de ping del módulo 17.
3. Rehaz mentalmente los escenarios de diagnóstico: APIPA (DHCP caído), ping a IP funciona pero el nombre no (DNS), alcanzo mi subred pero no salgo (gateway).
4. Práctica de apoyo: [Packet Tracer y redes básicas](../../recursos/packet-tracer-redes-basicas.md).

Superado este curso, el siguiente de la serie CCST Networking es **Networking Devices and Initial Configuration**.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1:** *PAN · LAN · WLAN · MAN · WAN · bit · byte · digitization · electrical/optical/wireless signals · bandwidth · throughput · latency · bps/Kbps/Mbps/Gbps*

**Módulo 2:** *host · client · server · peer-to-peer (P2P) · switch · router · access point · firewall · modem · ISP · DSL · cable · fiber (FTTH) · cellular · satellite · leased line*

**Módulo 3:** *cellular network · 3G/4G/5G · Wi-Fi · Bluetooth · pairing · GPS · hotspot · tethering · airplane mode*

**Módulo 4:** *home router · WAN/LAN ports · SSID · IEEE 802.11 (Wi-Fi 4/5/6) · 2.4 GHz vs 5 GHz · channels 1-6-11 · powerline · WPA2/WPA3 · WEP (obsoleto) · firmware · default credentials · DHCP*

**Módulo 5:** *protocol · sender/receiver/channel · encapsulation · standards · IEEE · IETF · RFC · OSI model (7 layers) · TCP/IP model · layer functions*

**Módulo 6:** *twisted pair (UTP) · Cat 5e/6 · 100 meters · EMI · fiber optic · single-mode · multi-mode · wireless media · media selection criteria*

**Módulo 7:** *encapsulation · Ethernet frame · FCS · MAC address (48 bits, hexadecimal) · hub · collision domain · switch · MAC address table · flooding*

**Módulo 8:** *IPv4 · 32 bits · octet · dotted decimal · network portion · host portion · subnet mask · CIDR (/8, /16, /24) · usable hosts (2^n − 2) · logical vs physical address*

**Módulo 9:** *unicast · broadcast · multicast (224-239) · public vs private addresses · RFC 1918 (10/8, 172.16/12, 192.168/16) · NAT · loopback (127.0.0.1) · link-local/APIPA (169.254/16) · classful (A/B/C) vs classless (CIDR) · IANA/RIR · broadcast domain · network segmentation · subnetting*

**Módulo 10:** *IPv4 exhaustion · IPv6 · 128 bits · hextet · hexadecimal · prefix /64 · omit leading zeros · double colon (::) · dual stack · tunneling · translation (NAT64)*

**Módulo 11:** *static addressing · dynamic addressing · DHCP · DORA (Discover, Offer, Request, Acknowledge) · lease · scope/pool · reservation · excluded addresses · `ipconfig /release` · `ipconfig /renew` · APIPA*

**Módulo 12:** *network boundary · default gateway · router interface · NAT · PAT (overload) · translation table · private to public · RFC 1918 · single public IP*

**Módulo 13:** *ARP · ARP request (broadcast) · ARP reply (unicast) · ARP table/cache · `arp -a` · `arp -d` · MAC and IP pairing · gateway MAC · broadcast containment*

**Módulo 14:** *routing · best path · routing table · directly connected route · static route · dynamic routing · default route (0.0.0.0/0) · gateway of last resort · hop · LAN design*

**Módulo 15:** *TCP · UDP · connection-oriented · connectionless · reliability · acknowledgment · three-way handshake (SYN, SYN-ACK, ACK) · port number · well-known ports · socket · FTP 20/21 · SSH 22 · Telnet 23 · SMTP 25 · DNS 53 · DHCP 67/68 · HTTP 80 · POP3 110 · IMAP 143 · HTTPS 443*

**Módulo 16:** *client-server · URI/URL · DNS · HTTP/HTTPS · TLS · FTP · virtual terminal · Telnet · SSH · email protocols · SMTP · POP3 · IMAP*

**Módulo 17:** *`ipconfig` (`/all`, `/release`, `/renew`) · `ping` · ICMP · `tracert`/`traceroute` · `nslookup` · `netstat` · loopback test · escalated ping sequence · DNS troubleshooting*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **Ancho de banda (bandwidth)** | Capacidad teórica máxima de un enlace, medida en bits por segundo. |
| **APIPA / link-local** | Dirección 169.254.x.x que se autoasigna un host cuando no logra obtener IP por DHCP. |
| **ARP** | Protocolo que averigua la MAC correspondiente a una IP conocida dentro de la red local; pregunta en broadcast y recibe respuesta en unicast. |
| **Broadcast** | Transmisión dirigida a todos los hosts de la red local; los routers no la reenvían. |
| **Caché ARP** | Tabla local de parejas IP-MAC aprendidas; se consulta con `arp -a` y sus entradas caducan solas. |
| **CIDR** | Direccionamiento sin clases: la máscara se expresa como /n y puede tener cualquier longitud. |
| **Default gateway** | IP de la interfaz del router en la red local; salida obligatoria del tráfico hacia otras redes. |
| **DHCP** | Protocolo que asigna automáticamente IP, máscara, gateway y DNS mediante la secuencia DORA. |
| **Dirección MAC** | Identificador físico de 48 bits de una tarjeta de red, en hexadecimal; única por dispositivo. |
| **DNS** | Servicio que traduce nombres de dominio a direcciones IP; usa el puerto 53. |
| **Dominio de broadcast** | Conjunto de dispositivos que reciben los broadcasts de los demás; lo delimitan los routers. |
| **Dominio de colisión** | Segmento donde las transmisiones pueden chocar; los switches crean uno por puerto. |
| **DORA** | Secuencia de mensajes DHCP: Discover, Offer, Request, Acknowledge. |
| **Dual stack** | Técnica de coexistencia en la que un host tiene dirección IPv4 e IPv6 a la vez. |
| **Encapsulación** | Proceso por el que cada capa añade su cabecera a los datos antes de transmitirlos. |
| **Fibra óptica** | Medio que transmite pulsos de luz; largas distancias, gran ancho de banda, inmune a EMI. |
| **FTP** | Protocolo de transferencia de archivos; usa los puertos 21 (control) y 20 (datos). |
| **Hexteto** | Cada uno de los 8 grupos de 16 bits de una dirección IPv6, escrito en hexadecimal. |
| **HTTP / HTTPS** | Protocolos de la web (puertos 80 y 443); HTTPS añade cifrado TLS. |
| **Hub** | Dispositivo obsoleto que repite las señales por todos los puertos sin inteligencia. |
| **IANA / RIR** | Organismos que administran y reparten el espacio de direcciones IP a nivel global y regional. |
| **IEEE 802.11** | Familia de estándares Wi-Fi (n = Wi-Fi 4, ac = Wi-Fi 5, ax = Wi-Fi 6). |
| **IMAP** | Protocolo de recepción de correo que mantiene los mensajes en el servidor, sincronizados entre dispositivos; puerto 143. |
| **ipconfig** | Comando de Windows que muestra la configuración IP del equipo; `/all` amplía la información. |
| **IPv6** | Versión del protocolo IP con direcciones de 128 bits en hexadecimal; sucesora de IPv4. |
| **Lease (préstamo DHCP)** | Tiempo durante el cual el cliente puede usar la IP asignada antes de renovarla. |
| **Loopback** | Dirección 127.0.0.1, prueba interna de la pila TCP/IP del propio equipo. |
| **Máscara de subred** | Patrón de bits que separa la porción de red de la porción de host en una dirección IP. |
| **Modelo OSI** | Modelo de referencia de 7 capas: física, enlace, red, transporte, sesión, presentación, aplicación. |
| **Modelo TCP/IP** | Modelo práctico de 4 capas: acceso a la red, internet, transporte, aplicación. |
| **Multicast** | Transmisión a un grupo de hosts suscritos; rango IPv4 224.0.0.0-239.255.255.255. |
| **NAT** | Traducción de direcciones: permite que IPs privadas salgan a internet con una IP pública. |
| **netstat** | Comando que lista las conexiones activas y los puertos abiertos del equipo. |
| **nslookup** | Comando que consulta el DNS para comprobar qué IP devuelve un nombre de dominio. |
| **P2P (peer-to-peer)** | Red sin servidor dedicado donde cada equipo puede ser cliente y servidor; no escala bien. |
| **PAT (NAT con sobrecarga)** | Variante de NAT que usa los puertos para que muchos hosts compartan una sola IP pública. |
| **ping** | Comando que comprueba la conectividad con un destino mediante mensajes ICMP y mide el tiempo de respuesta. |
| **POP3** | Protocolo de recepción de correo que descarga los mensajes al equipo; puerto 110. |
| **Powerline** | Tecnología que transmite la red por la instalación eléctrica de la vivienda. |
| **Puerto** | Número que identifica a una aplicación dentro de un host; los bien conocidos van del 0 al 1023. |
| **RFC 1918** | Documento que define los tres rangos de direcciones IPv4 privadas. |
| **Ruta por defecto** | Entrada 0.0.0.0/0 de la tabla de enrutamiento: destino de los paquetes cuya red no figura en la tabla. |
| **Saludo de tres vías** | Apertura de una conexión TCP: SYN, SYN-ACK, ACK. |
| **SMTP** | Protocolo de envío de correo entre cliente y servidor y entre servidores; puerto 25. |
| **Socket** | Combinación de dirección IP y puerto que identifica un extremo de una conexión. |
| **SSH** | Acceso remoto cifrado por línea de comandos; puerto 22. Sustituye a Telnet. |
| **SSID** | Nombre que identifica una red inalámbrica. |
| **Switch** | Dispositivo de capa 2 que aprende MACs y entrega cada trama solo por el puerto del destinatario. |
| **Tabla de direcciones MAC** | Tabla del switch que asocia cada MAC aprendida con el puerto donde se encuentra. |
| **Tabla de enrutamiento** | Tabla del router con las redes que conoce (conectadas, estáticas y dinámicas) y por dónde alcanzarlas. |
| **TCP** | Protocolo de transporte fiable y orientado a conexión; garantiza entrega y orden. |
| **Telnet** | Acceso remoto por línea de comandos sin cifrar; obsoleto, puerto 23. |
| **Throughput** | Caudal real de datos transmitidos; siempre menor o igual que el ancho de banda. |
| **tracert / traceroute** | Comando que muestra los routers del camino hasta un destino y dónde se pierde el tráfico. |
| **Trama (frame)** | Unidad de datos de capa 2; en Ethernet incluye MACs de origen y destino y FCS. |
| **Tunneling** | Técnica de coexistencia que transporta paquetes IPv6 dentro de paquetes IPv4. |
| **UDP** | Protocolo de transporte sin conexión, rápido y sin garantías; para voz, vídeo, DNS y DHCP. |
| **Unicast** | Transmisión de un emisor a un único destinatario. |
| **UTP (par trenzado)** | Cable de cobre más común en LANs; categorías 5e/6/6a, máximo 100 m por tramo. |
| **WPA2 / WPA3** | Protocolos actuales de seguridad Wi-Fi; WEP y las redes abiertas son inseguras. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Networking Basics», primer curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
