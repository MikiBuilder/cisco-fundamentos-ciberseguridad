# 🎓  Cisco — Fundamentos y Ciberseguridad

Resúmenes de estudio de los cursos de **Cisco Networking Academy** impartidos en el **Cibernàrium de Barcelona** (Barcelona Activa), orientados a la preparación de las certificaciones **CCST** (Cisco Certified Support Technician).

> Material elaborado por y para la clase. Libre para consultar, compartir y mejorar.

---

## Cursos

| # | Curso | Certificación | Estado | Apuntes |
|---|-------|---------------|--------|---------|
| 1 | IT Customer Support Basics *(202609_Sup_G6)* | CCST IT Support | Completo | [Ver resumen](cursos/it-customer-support-basics.md) |
| 2 | Security and Connectivity Support *(202609_Sup_G6)* | CCST IT Support | Pendiente | — |

## Recursos

| Recurso | Descripción |
|---------|-------------|
| [Comandos Linux (EN-ES)](recursos/linux-commands-reference.md) | Referencia rápida: archivos, permisos, procesos, redes, SSH, seguridad y paquetes |
| [Packet Tracer y redes básicas](recursos/packet-tracer-redes-basicas.md) | Direccionamiento IP, gateway, ICMP/ARP y práctica de enrutamiento entre dos subredes (incluye .pkt) |

## Estructura del repositorio

```
cisco-fundamentos-ciberseguridad/
├── README.md
├── cursos/                            un archivo .md por curso
│   └── it-customer-support-basics.md
├── recursos/                          material transversal
│   ├── linux-commands-reference.md
│   ├── packet-tracer-redes-basicas.md
│   ├── img/                           imágenes de los recursos
│   └── archivos/                      archivos de práctica (.pkt, etc.)
└── plantilla/
    └── plantilla-curso.md             plantilla para nuevos resúmenes
```

## Cómo añadir un nuevo curso

1. Copia `plantilla/plantilla-curso.md` en la carpeta `cursos/` con un nombre en minúsculas y con guiones (ej.: `security-and-connectivity-support.md`).
2. Rellena las secciones siguiendo la misma estructura: resúmenes, palabras clave, apartados de examen y glosario.
3. Añade la fila correspondiente en la tabla de cursos de este README.
4. Haz commit con un mensaje claro: `Añade resumen de <nombre del curso>`.

## Contribuir

Si ves una errata o quieres ampliar un apartado:

- Con permisos en el repo: edita el archivo directamente desde GitHub y haz commit.
- Sin permisos: haz un fork, edita y abre un pull request.

---

Cada archivo de curso incluye su propio índice con enlaces internos a las secciones.