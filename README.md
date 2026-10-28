# Cisco — Fundamentos y Ciberseguridad

Resúmenes de estudio de los cursos de **Cisco Networking Academy** impartidos en el **Cibernàrium de Barcelona** (Barcelona Activa), orientados a la preparación de las certificaciones **CCST** (Cisco Certified Support Technician).

> Material elaborado por y para la clase. Libre para consultar, compartir y mejorar.

---

## Cursos

### CCST IT Support *(202609_Sup_G6)*

| Módulo | Curso | Estado | Apuntes |
|--------|-------|--------|---------|
| 1 | IT Customer Support Basics | Completo | [Ver resumen](cursos/ccst-it-support/it-customer-support-basics.md) |
| 2 | Operating Systems Support | Completo | [Ver resumen](cursos/ccst-it-support/operating-systems-support.md) |
| 3 | Security and Connectivity Support | Completo | [Ver resumen](cursos/ccst-it-support/security-and-connectivity-support.md) |
| 4 | Hardware and Upgrade Support | Completo | [Ver resumen](cursos/ccst-it-support/hardware-and-upgrade-support.md) |

**Test de repaso:** [abrir el simulador de examen](https://mikibuilder.github.io/cisco-fundamentos-ciberseguridad/cursos/ccst-it-support/test-ccst-it-support.html) — 266 preguntas organizadas por los 6 dominios del CCST IT Support, con corrección automática, explicaciones y desglose por dominio. Funciona desde el móvil. ([código fuente](cursos/ccst-it-support/test-ccst-it-support.html))

### CCST Networking

| Módulo | Curso | Estado | Apuntes |
|--------|-------|--------|---------|
| 1 | Networking Basics | Completo | [Ver resumen](cursos/ccst-networking/networking-basics.md) |
| 2 | Networking Devices and Initial Configuration | Completo | [Ver resumen](cursos/ccst-networking/networking-devices-and-initial-configuration.md) |
| 3 | Network Addressing and Basic Troubleshooting | En progreso | [Ver resumen](cursos/ccst-networking/network-addressing-and-basic-troubleshooting.md) |
| 4 | Network Support and Security | Pendiente | — |

## Recursos

| Recurso | Descripción |
|---------|-------------|
| [Comandos Cisco IOS y Packet Tracer](recursos/comandos-cisco-ios-packet-tracer.md) | Referencia de la CLI: modos, configuración de switch y router, VLANs, enrutamiento, DHCP, NAT, SSH, ACLs y comandos show |
| [Comandos Linux (EN-ES)](recursos/linux-commands-reference.md) | Referencia rápida: archivos, permisos, procesos, redes, SSH, seguridad y paquetes |
| [Packet Tracer y redes básicas](recursos/packet-tracer-redes-basicas.md) | Direccionamiento IP, gateway, ICMP/ARP y práctica de enrutamiento entre dos subredes (incluye .pkt) |
| [Wireshark: análisis de tráfico](recursos/wireshark-analisis-de-trafico.md) | Resumen de la cápsula bootcamp: captura, filtros BPF y de visualización, streams, latencia, extracción de ficheros, DDoS y malware |

## Estructura del repositorio

```
cisco-fundamentos-ciberseguridad/
├── README.md
├── cursos/
│   ├── ccst-it-support/               una carpeta por certificación, un .md por módulo
│   │   ├── it-customer-support-basics.md
│   │   ├── operating-systems-support.md
│   │   ├── security-and-connectivity-support.md
│   │   ├── hardware-and-upgrade-support.md
│   │   └── test-ccst-it-support.html
│   └── ccst-networking/
│       ├── networking-basics.md
│       ├── networking-devices-and-initial-configuration.md
│       └── network-addressing-and-basic-troubleshooting.md
├── recursos/                          material transversal
│   ├── comandos-cisco-ios-packet-tracer.md
│   ├── linux-commands-reference.md
│   ├── packet-tracer-redes-basicas.md
│   ├── wireshark-analisis-de-trafico.md
│   ├── img/                           imágenes de los recursos
│   └── archivos/                      archivos de práctica (.pkt, etc.)
└── plantilla/
    └── plantilla-curso.md             plantilla para nuevos resúmenes
```

## Cómo añadir un nuevo módulo o curso

1. Copia `plantilla/plantilla-curso.md` en la carpeta de la certificación correspondiente (ej.: `cursos/ccst-networking/networking-devices-and-initial-configuration.md`), con nombre en minúsculas y con guiones.
2. Rellena las secciones siguiendo la misma estructura: resúmenes, palabras clave, apartados de examen y glosario.
3. Añade o actualiza la fila correspondiente en la tabla de cursos de este README.
4. Haz commit con un mensaje claro: `Añade resumen de <nombre del módulo>`.

## Contribuir

Si ves una errata o quieres ampliar un apartado:

- Con permisos en el repo: edita el archivo directamente desde GitHub y haz commit.
- Sin permisos: haz un fork, edita y abre un pull request.

---

Cada archivo de curso incluye su propio índice con enlaces internos a las secciones.
