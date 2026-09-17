# 🎓 Apuntes y Resúmenes — Cisco Networking Academy

Repositorio de resúmenes de estudio de los cursos de **Cisco NetAcad**, orientados a la preparación de las certificaciones **CCST** (Cisco Certified Support Technician) y siguientes.

> Material elaborado por y para la clase. Libre para consultar, compartir y mejorar.

---

## 📚 Cursos disponibles

| # | Curso | Certificación | Estado | Apuntes |
|---|-------|---------------|--------|---------|
| 1 | IT Customer Support Basics *(202609_Sup_G6)* | CCST IT Support | ✅ Completo | [📖 Ver resumen](cursos/it-customer-support-basics.md) |
| 2 | Security and Connectivity Support *(202609_Sup_G6)* | CCST IT Support | ⏳ Pendiente | — |

**Leyenda de estados:** ✅ Completo · ✍️ En progreso · ⏳ Pendiente

## 🧰 Recursos transversales

| Recurso | Descripción |
|---------|-------------|
| [🐧 Comandos Linux (EN-ES)](recursos/linux-commands-reference.md) | Referencia rápida: archivos, permisos, procesos, redes, SSH, seguridad y paquetes |

---

## 🗂 Estructura del repositorio

```
apuntes-ccst/
├── README.md                          ← este índice
├── cursos/
│   ├── it-customer-support-basics.md  ← un archivo .md por curso
│   └── ...
└── plantilla/
    └── plantilla-curso.md             ← plantilla para nuevos resúmenes
```

## ✍️ Cómo añadir un nuevo curso

1. Copia `plantilla/plantilla-curso.md` en la carpeta `cursos/` con un nombre descriptivo en minúsculas y con guiones (ej.: `networking-basics.md`).
2. Rellena las secciones siguiendo la misma estructura (resúmenes, 🔑 palabras clave, 💡 cajas de examen, glosario).
3. Añade la fila correspondiente en la tabla de **Cursos disponibles** de este README.
4. Haz commit con un mensaje claro: `Añade resumen de <nombre del curso>`.

## 🤝 Contribuir

¿Has visto una errata o quieres ampliar un apartado?

- **Con permisos en el repo:** edita el archivo directamente desde GitHub (botón ✏️) y haz commit.
- **Sin permisos:** haz un *fork*, edita y abre un *pull request*.

---

*Cada archivo de curso incluye su propio índice con enlaces internos a las secciones.*
