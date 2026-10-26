[← Volver a la página principal del repositorio](../README.md)

# Guía de comandos Cisco IOS y Packet Tracer

Referencia de comandos Cisco IOS para los labs de Packet Tracer de la serie CCST Networking. Cubre también material de nivel CCNA (VLANs, enrutamiento dinámico, NAT, ACLs) para que siga sirviendo en cursos posteriores. Elaborada durante la formación en Cisco Networking Academy, impartida en el Cibernàrium de Barcelona (Barcelona Activa).

---

## Índice

- [Referencia rápida de modos CLI](#referencia-rápida-de-modos-cli)
- [1. Navegación, modos CLI y ayuda del sistema](#1-navegación-modos-cli-y-ayuda-del-sistema)
- [2. Configuración básica del dispositivo y seguridad inicial](#2-configuración-básica-del-dispositivo-y-seguridad-inicial)
- [3. Gestión de memoria y archivos de configuración](#3-gestión-de-memoria-y-archivos-de-configuración)
- [4. Configuración de interfaces y capa de red](#4-configuración-de-interfaces-y-capa-de-red)
- [5. Conmutación y seguridad de puertos](#5-conmutación-y-seguridad-de-puertos)
- [6. Enrutamiento IP estático y dinámico](#6-enrutamiento-ip-estático-y-dinámico)
- [7. Servicios de red: DHCP, NAT y SSH](#7-servicios-de-red-dhcp-nat-y-ssh)
- [8. Listas de control de acceso (ACLs)](#8-listas-de-control-de-acceso-acls)
- [9. Diagnóstico, verificación y mantenimiento](#9-diagnóstico-verificación-y-mantenimiento)
- [10. Comandos de los PCs en Packet Tracer](#10-comandos-de-los-pcs-en-packet-tracer)

---

## Referencia rápida de modos CLI

| Modo | Prompt | Acceso y uso |
| :--- | :--- | :--- |
| **User EXEC** | `Router>` | Modo inicial. Solo comandos básicos de consulta. |
| **Privileged EXEC** | `Router#` | Se entra con `enable`. Acceso completo a diagnósticos, verificaciones y archivos. |
| **Global Configuration** | `Router(config)#` | Se entra con `configure terminal`. Cambios que afectan a todo el equipo. |
| **Interface Configuration** | `Router(config-if)#` | Ajustes de una interfaz física o lógica concreta. |
| **Line Configuration** | `Router(config-line)#` | Líneas de acceso local y remoto (consola, VTY). |
| **Router Configuration** | `Router(config-router)#` | Protocolos de enrutamiento dinámico (OSPF, RIP, EIGRP). |
| **VLAN Configuration** | `Switch(config-vlan)#` | Creación y edición de VLANs. |
| **DHCP Pool Configuration** | `Router(dhcp-config)#` | Parámetros de un pool DHCP. |

[⬆ Volver al índice](#índice)

---

## 1. Navegación, modos CLI y ayuda del sistema

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `enable` | User EXEC | Accede al modo EXEC privilegiado. |
| `disable` | Privileged | Vuelve del modo privilegiado al modo usuario. |
| `configure terminal` | Privileged | Entra al modo de configuración global. |
| `exit` | Cualquiera | Retrocede un nivel en la jerarquía de modos. |
| `end` / `Ctrl+Z` | Sub-config | Sale de cualquier submodo y vuelve directo al EXEC privilegiado. |
| `?` | Cualquiera | Ayuda contextual: lista los comandos u opciones disponibles en ese punto. |
| `Tab` *(tecla)* | Cualquiera | Autocompleta el comando si lo escrito ya lo identifica sin ambigüedad. |
| `Ctrl+Mayús+6` | EXEC | Interrumpe un proceso en curso (un ping o traceroute largos). |
| `show history` | EXEC | Muestra los últimos comandos ejecutados en la sesión. |
| `terminal history size [n]` | Privileged | Ajusta cuántos comandos guarda el historial de la sesión. |
| `reload` | Privileged | Reinicia el dispositivo. Los cambios no guardados se pierden. |
| `clock set [hh:mm:ss] [día mes año]` | Privileged | Ajusta la fecha y hora del sistema para que los registros sean fiables. |

[⬆ Volver al índice](#índice)

---

## 2. Configuración básica del dispositivo y seguridad inicial

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `hostname [nombre]` | Global | Asigna el nombre del dispositivo, visible en el prompt. |
| `enable secret [clave]` | Global | Clave de acceso al modo privilegiado, guardada como hash no reversible (type 5 en Packet Tracer; type 8/9 en IOS recientes). Es la que hay que usar. |
| `enable password [clave]` | Global | Versión heredada en texto plano (type 0). Insegura; `secret` tiene prioridad si coexisten. |
| `service password-encryption` | Global | Cifra (type 7, débil pero mejor que texto plano) las contraseñas legibles del archivo de configuración. |
| `banner motd #[mensaje]#` | Global | Mensaje de advertencia legal que se muestra antes de pedir credenciales. |
| `no ip domain-lookup` | Global | Evita que el equipo intente resolver por DNS los comandos mal escritos (y el molesto bloqueo que provoca). |
| `line console 0` | Global | Entra a la configuración del puerto de consola (gestión local). |
| `line vty 0 15` | Global | Entra a la configuración de las 16 líneas virtuales (gestión remota Telnet/SSH). |
| `password [clave]` + `login` | Line | Define la contraseña de la línea y activa su comprobación al conectar. |
| `exec-timeout [min] [seg]` | Line | Cierra la sesión tras ese tiempo de inactividad. |
| `logging synchronous` | Line | Evita que los mensajes del sistema corten la línea que estás escribiendo. |

[⬆ Volver al índice](#índice)

---

## 3. Gestión de memoria y archivos de configuración

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `copy running-config startup-config` | Privileged | Guarda la configuración activa (RAM) en la NVRAM. El comando que no hay que olvidar. |
| `write memory` / `wr` | Privileged | Equivalente heredado del anterior. |
| `show running-config` | Privileged | Muestra la configuración en ejecución (RAM; se pierde al reiniciar). |
| `show startup-config` | Privileged | Muestra la configuración guardada en NVRAM que se cargará al arrancar. |
| `erase startup-config` | Privileged | Borra la configuración de inicio de la NVRAM. |
| `delete [dispositivo:]archivo` | Privileged | Borra un archivo de la Flash (p. ej. `vlan.dat` en switches, donde vive la base de datos de VLANs). |
| `show flash:` | Privileged | Lista el contenido de la memoria Flash (imagen del IOS y otros archivos). |
| `copy running-config tftp:` | Privileged | Exporta una copia de seguridad de la configuración a un servidor TFTP. |

[⬆ Volver al índice](#índice)

---

## 4. Configuración de interfaces y capa de red

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `interface [tipo/núm]` | Global | Entra a la configuración de una interfaz (p. ej. `GigabitEthernet0/0/0`, abreviable `g0/0/0`). |
| `ip address [ip] [máscara]` | Interface | Asigna dirección IPv4 y máscara a la interfaz. |
| `ipv6 address [ipv6/prefijo]` | Interface | Asigna una dirección IPv6 (global unicast o link-local) a la interfaz. |
| `description [texto]` | Interface | Etiqueta descriptiva de la interfaz, para documentar a qué conecta. |
| `no shutdown` | Interface | Activa la interfaz. En routers vienen apagadas de fábrica: olvidarlo es el fallo clásico. |
| `shutdown` | Interface | Desactiva administrativamente la interfaz. |
| `clock rate [velocidad]` | Interface | Velocidad de sincronización del extremo DCE en un enlace serial punto a punto. |
| `duplex [auto / full / half]` | Interface | Modo de transmisión del puerto Ethernet. |
| `speed [auto / 10 / 100 / 1000]` | Interface | Velocidad del puerto Ethernet, fija o autonegociada. |
| `ip default-gateway [ip]` | Global | Puerta de enlace de un switch de capa 2, para administrarlo desde otras redes. |
| `interface loopback [id]` | Global | Crea una interfaz lógica siempre activa (útil como Router-ID y para pruebas). |
| `interface range [rango]` | Global | Selecciona varios puertos a la vez para aplicarles la misma configuración. |

[⬆ Volver al índice](#índice)

---

## 5. Conmutación y seguridad de puertos

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `vlan [id]` | Global | Crea o edita una VLAN y entra a su submodo de configuración. |
| `name [nombre]` | VLAN | Asigna un nombre descriptivo a la VLAN. |
| `switchport mode access` | Interface | Configura el puerto como acceso: pertenece a una sola VLAN. |
| `switchport access vlan [id]` | Interface | Asigna el puerto de acceso a esa VLAN. |
| `switchport mode trunk` | Interface | Configura el puerto como troncal: transporta varias VLANs etiquetadas con IEEE 802.1Q. |
| `switchport trunk native vlan [id]` | Interface | Define la VLAN nativa, la que viaja sin etiqueta por el troncal. |
| `switchport trunk allowed vlan [lista]` | Interface | Limita qué VLANs pueden cruzar el troncal. |
| `switchport port-security` | Interface | Activa la seguridad de puerto basada en direcciones MAC. |
| `switchport port-security maximum [n]` | Interface | Número máximo de MACs permitidas a la vez en el puerto. |
| `switchport port-security mac-address sticky` | Interface | Aprende las MACs conectadas y las fija automáticamente en la running-config. |

[⬆ Volver al índice](#índice)

---

## 6. Enrutamiento IP estático y dinámico

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `ip route [red] [máscara] [salto o interfaz]` | Global | Ruta estática hacia una red remota, por next-hop o por interfaz de salida. |
| `ip route 0.0.0.0 0.0.0.0 [salto]` | Global | Ruta por defecto (último recurso): todo el tráfico sin destino conocido sale por ahí. |
| `router ospf [process-id]` | Global | Activa OSPF (estado de enlace) y entra a su submodo. |
| `network [red] [wildcard] area [id]` | Router (OSPF) | Define qué interfaces participan en OSPF, por máscara wildcard y área. |
| `router-id [x.x.x.x]` | Router | Fija manualmente el identificador del router en OSPF o EIGRP. |
| `passive-interface [interfaz]` | Router | La red se sigue anunciando, pero por esa interfaz no se envían actualizaciones del protocolo. |
| `router rip` | Global | Activa RIP (vector de distancias). |
| `version 2` | Router (RIP) | Pasa a RIPv2, con soporte de VLSM y redes sin clase. |
| `no auto-summary` | Router | Desactiva la sumarización automática en los límites de red con clase (RIP/EIGRP). |

[⬆ Volver al índice](#índice)

---

## 7. Servicios de red: DHCP, NAT y SSH

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `ip dhcp excluded-address [inicio] [fin]` | Global | Excluye un rango de IPs del reparto automático (gateway, servidores, impresoras). |
| `ip dhcp pool [nombre]` | Global | Crea el pool DHCP y entra a su submodo. |
| `network [red] [máscara]` | DHCP | Bloque de direcciones que el servidor ofrecerá. |
| `default-router [ip]` | DHCP | Gateway que recibirán los clientes. |
| `dns-server [ip]` | DHCP | Servidor DNS que recibirán los clientes. |
| `ip helper-address [ip-servidor]` | Interface | DHCP Relay: reenvía como unicast las peticiones broadcast de los clientes hacia un servidor DHCP remoto. |
| `ip nat inside` / `ip nat outside` | Interface | Marca la interfaz como lado interno (privado) o externo (público) para NAT. |
| `ip nat inside source static [privada] [pública]` | Global | NAT estático uno a uno, para servidores internos que deben ser accesibles desde fuera. |
| `ip nat inside source list [acl] interface [int] overload` | Global | PAT: muchas IPs privadas salen por una pública, diferenciadas por puerto. |
| `ip domain-name [dominio]` | Global | Nombre de dominio del equipo; requisito previo para generar las claves RSA de SSH. |
| `crypto key generate rsa general-keys modulus [bits]` | Global | Genera el par de claves RSA que cifra las sesiones SSH (1024 bits o más). |
| `username [usuario] secret [clave]` | Global | Crea un usuario local con contraseña cifrada. |
| `transport input [ssh / telnet / all]` | Line VTY | Protocolos de entrada admitidos en las VTY; lo correcto es dejar solo `ssh`. |
| `login local` | Line | La línea valida el acceso contra los usuarios locales del equipo. |
| `ip ssh version 2` | Global | Fuerza SSHv2 y descarta la versión 1, vulnerable. |

Secuencia completa de SSH, en orden: `ip domain-name` → `crypto key generate rsa` → `username ... secret` → `line vty 0 15` → `transport input ssh` → `login local`.

[⬆ Volver al índice](#índice)

---

## 8. Listas de control de acceso (ACLs)

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `access-list [1-99] [permit/deny] [ip] [wildcard]` | Global | Regla de ACL estándar numerada: filtra solo por IP de origen. |
| `access-list [100-199] [permit/deny] [protocolo] [origen] [destino]` | Global | Regla de ACL extendida: evalúa origen, destino, protocolo (TCP/UDP/ICMP) y puertos. |
| `ip access-list standard [nombre]` | Global | ACL estándar nombrada; permite editar reglas sueltas. |
| `ip access-list extended [nombre]` | Global | ACL extendida nombrada. |
| `ip access-group [núm o nombre] [in/out]` | Interface | Aplica la ACL a la interfaz, sobre tráfico entrante o saliente. |
| `access-class [núm o nombre] in` | Line VTY | Restringe por ACL qué IPs pueden abrir sesión remota. |
| `remark [texto]` | ACL | Comentario que documenta el propósito de las reglas. |
| `show access-lists` | Privileged | Muestra todas las ACLs y las coincidencias acumuladas por regla. |
| `clear ip access-list counters` | Privileged | Pone a cero los contadores de coincidencias. |

Regla implícita: toda ACL termina con un `deny any` invisible. Si una ACL solo tiene denegaciones, bloquea todo el tráfico.

[⬆ Volver al índice](#índice)

---

## 9. Diagnóstico, verificación y mantenimiento

| Comando | Modo | Descripción |
| :--- | :--- | :--- |
| `ping [destino]` | EXEC | Envía ICMP Echo Request: prueba la conectividad de capa 3 y mide la latencia. |
| `ping` *(sin argumentos)* | Privileged | Ping extendido: permite elegir origen, repeticiones y tamaño. |
| `traceroute [destino]` | EXEC | Descubre la ruta salto a salto incrementando el TTL. |
| `show version` | Privileged | Modelo, versión de IOS, memoria, tiempo encendido y registro de configuración. |
| `show ip interface brief` | Privileged | Resumen de interfaces: IP, estado y protocolo. El primer comando ante cualquier problema. |
| `show interfaces [tipo/núm]` | Privileged | Estadísticas completas de la interfaz: duplex, velocidad, errores, contadores. |
| `show ip route` | Privileged | Tabla de enrutamiento: rutas conectadas, estáticas y dinámicas. |
| `show arp` / `show ip arp` | Privileged | Tabla ARP del dispositivo (parejas IP-MAC). |
| `show vlan brief` | Privileged | VLANs del switch y puertos asignados a cada una. |
| `show mac address-table` | Privileged | Tabla CAM del switch: MACs aprendidas, puerto y VLAN. |
| `show cdp neighbors` | Privileged | Dispositivos Cisco directamente conectados, descubiertos por CDP (capa 2). |
| `show cdp neighbors detail` | Privileged | Lo mismo con detalle: IPs, plataforma y versión de IOS de los vecinos. |
| `show port-security interface [int]` | Privileged | Estado de la seguridad de puerto y violaciones registradas. |
| `show ip protocols` | Privileged | Protocolos de enrutamiento activos, métricas y redes anunciadas. |
| `show ip dhcp binding` | Privileged | Asignaciones activas del servidor DHCP (IP, MAC, caducidad). |
| `show ip nat translations` | Privileged | Tabla de traducciones NAT/PAT en curso. |

[⬆ Volver al índice](#índice)

---

## 10. Comandos de los PCs en Packet Tracer

En el escritorio de los PCs y portátiles de Packet Tracer (pestaña Desktop → Command Prompt) funcionan los comandos habituales de Windows:

| Comando | Descripción |
| :--- | :--- |
| `ipconfig` | IP, máscara y gateway del PC. |
| `ipconfig /all` | Añade MAC, servidor DHCP y DNS. |
| `ipconfig /renew` | Vuelve a pedir dirección al servidor DHCP. |
| `ping [destino]` | Prueba de conectividad desde el PC. |
| `tracert [destino]` | Traceroute en su versión Windows. |
| `arp -a` | Tabla ARP del PC. |
| `nslookup [nombre]` | Comprueba qué IP devuelve el DNS configurado. |
| `netstat` | Conexiones TCP/UDP activas del PC. |
| `ssh -l [usuario] [ip]` | Abre sesión SSH contra un equipo de red configurado. |
| `telnet [ip]` | Sesión Telnet (solo para comprobar que lo has deshabilitado). |

[⬆ Volver al índice](#índice)

---

*Referencia de comandos Cisco IOS, parte del repositorio [cisco-fundamentos-ciberseguridad](../README.md). Material libre para compartir con la clase.*
