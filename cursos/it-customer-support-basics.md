# 📘 Manual de Estudio — IT Customer Support Basics


> **Objetivo del curso:** desarrollar las competencias de help desk y atención al cliente necesarias para trabajar en puestos de soporte TI de nivel inicial, aprendiendo a gestionar y resolver incidencias en entornos de TI.

---

## 📑 Índice

- [Cómo usar este manual](#-cómo-usar-este-manual)
- [0. Introducción al curso](#0-introducción-al-curso)
- [Módulo 1 — Customer Service in IT Support](#módulo-1--customer-service-in-it-support)
  - [1.1 Help Desk Concepts](#11-help-desk-concepts-conceptos-de-help-desk)
  - [1.2 Professional Communication Skills](#12-professional-communication-skills-habilidades-de-comunicación-profesional)
  - [1.3 Customer Interaction and Documentation](#13-customer-interaction-and-documentation-interacción-con-el-cliente-y-documentación)
  - [1.4 Resumen del Módulo 1](#14-resumen-del-módulo-1)
- [Módulo 2 — Processes and Tools for Troubleshooting](#módulo-2--processes-and-tools-for-troubleshooting)
  - [2.1 El proceso de troubleshooting: los 8 pasos](#21-the-troubleshooting-process-el-proceso-de-troubleshooting-los-8-pasos)
  - [2.2 Remote Access Support](#22-remote-access-support-soporte-mediante-acceso-remoto)
  - [2.3 Researching with AI and Troubleshooting Tools](#23-researching-with-ai-and-troubleshooting-tools-investigación-con-ia)
  - [2.4 Common Application Issues](#24-common-application-issues-problemas-comunes-de-aplicaciones)
  - [2.5 Resumen del Módulo 2](#25-resumen-del-módulo-2)
- [Examen final del curso](#-examen-final-del-curso)
- [Mapeo con la certificación CCST IT Support](#-mapeo-con-la-certificación-ccst-it-support)
- [Glosario de términos](#-glosario-de-términos)

---

## 🧭 Cómo usar este manual

1. Antes de cada sesión, lee el resumen del apartado correspondiente.
2. Después de cada sesión, repasa las palabras clave. En el examen CCST aparecen normalmente en inglés.
3. Las cajas 💡 "Para el examen" recogen los datos que más se preguntan.
4. La semana previa al examen, repasa el [glosario](#-glosario-de-términos) completo y recita de memoria los 8 pasos del troubleshooting.

---

# 0. Introducción al curso

Presentación general: título del curso, recursos del estudiante y las empresas ficticias que sirven de contexto en los escenarios prácticos.

El técnico de help desk es el primer punto de contacto entre el usuario y el departamento de TI. En ese puesto se trabaja con muchas tecnologías y sistemas distintos, experiencia que después facilita pasar a administración de sistemas, redes o ciberseguridad.

El curso se organiza en dos módulos: atención al cliente (Módulo 1) y resolución técnica de problemas, incluido el soporte remoto (Módulo 2).

**🔑 Palabras clave:** *entry-level IT support · help desk · career path · soft skills · technical skills*

[⬆ Volver al índice](#-índice)

---

# MÓDULO 1 — Customer Service in IT Support

**(Servicio al cliente en soporte TI)**

En soporte TI, la experiencia del cliente pesa tanto como la solución técnica: un técnico que resuelve bien pero comunica mal deja usuarios insatisfechos. El módulo cubre el funcionamiento del help desk, la comunicación profesional y la documentación.

---

## 1.1 Help Desk Concepts (Conceptos de Help Desk)

### 1.1.1 El ticket y su flujo de trabajo

Todo incidente o solicitud se registra en un **ticket**, la unidad de trabajo del help desk. El ticket sigue un flujo estandarizado:

```
Creación → Asignación → Diagnóstico → Resolución → Cierre
```

El ticket documenta quién reporta, qué ocurre, cuándo y qué se ha hecho en cada momento.

### 1.1.2 Gestión de colas (queue management)

Los tickets se organizan en colas por prioridad, categoría o equipo asignado. La prioridad se calcula combinando dos factores:

| Factor | Pregunta que responde |
|---|---|
| **Impacto (impact)** | ¿A cuántos usuarios o procesos de negocio afecta? |
| **Urgencia (urgency)** | ¿Cómo de crítico es en el tiempo? |

> Prioridad = Impacto × Urgencia. Es la fórmula habitual en gestión de servicios (ITSM).

### 1.1.3 Sistemas de ticketing

Software que centraliza el registro y seguimiento de los tickets, además de sus métricas. Ejemplos habituales: ServiceNow, Zendesk, Jira Service Management, osTicket.

### 1.1.4 SLA y métricas

Los **SLA (Service Level Agreements)** definen tiempos máximos comprometidos de respuesta y resolución según la prioridad del ticket. Se controlan mediante KPIs:

- *First response time* (tiempo de primera respuesta)
- *Resolution time* (tiempo de resolución)
- *FCR, First Contact Resolution* (resolución en el primer contacto)
- *CSAT* (satisfacción del cliente)

### 1.1.5 Niveles de soporte (tiers) y escalado

| Nivel | Rol | Ejemplos |
|---|---|---|
| **Tier 1** | Primer contacto; incidencias comunes y conocidas | Reset de contraseñas, problemas básicos de conectividad |
| **Tier 2** | Técnicos especializados; problemas complejos | Fallos de configuración avanzada, incidencias recurrentes |
| **Tier 3** | Expertos, ingeniería o fabricante | Bugs de producto, problemas de arquitectura |

El paso de un nivel a otro se denomina **escalado (escalation)**. Regla de oro: antes de escalar, documentar todo lo probado.

### 1.1.6 Gestión simultánea de tickets

Para manejar varios tickets a la vez sin perder calidad hace falta priorizar de forma continua, mantener los estados actualizados en el sistema y comunicarse proactivamente con el usuario, informándole incluso cuando no hay avances.

### 1.1.7 Herramientas de IA en el ticketing

La IA asiste al help desk en tareas concretas: clasificación automática de tickets (triage), sugerencia de artículos de la base de conocimiento, redacción asistida de respuestas y detección de patrones de incidencias repetidas.

### 💡 Para el examen
- Distingue **incidente** (algo que funcionaba deja de funcionar) de **solicitud de servicio** (petición de algo nuevo: acceso, instalación, información).
- Memoriza el ciclo de vida del ticket y los criterios de escalado.
- Prioridad = impacto × urgencia.

**🔑 Palabras clave:** *ticket · ticketing system · workflow · queue · SLA · escalation · tier 1/2/3 · incident · service request · prioritization · impact · urgency · knowledge base · AI triage · CSAT · FCR*

[⬆ Volver al índice](#-índice)

---

## 1.2 Professional Communication Skills (Habilidades de comunicación profesional)

Apartado con mucho peso en el examen CCST.

### 1.2.1 Compromiso con el cliente (customer engagement)

Saludo profesional, identificarse con nombre y departamento, mostrar disposición a ayudar y generar confianza (*rapport*) desde el primer segundo.

### 1.2.2 Conocer, relacionar y comprender (Know, Relate, Understand)

Método de tres fases: conocer el problema, empatizar con la situación del usuario y confirmar la comprensión antes de actuar.

### 1.2.3 Preguntas abiertas y cerradas

| Tipo | Cuándo usarla | Ejemplo |
|---|---|---|
| **Abierta (open-ended)** | Al inicio, para explorar y obtener información amplia | «¿Qué apareció en pantalla cuando falló?» |
| **Cerrada (closed-ended)** | Para confirmar datos concretos | «¿El equipo está encendido?» |

### 1.2.4 Escucha activa (active listening)

- No interrumpir; tomar notas mientras el usuario habla.
- Parafrasear y resumir para confirmar comprensión: «Entonces, si le he entendido bien…». Es la técnica que el examen asocia directamente con la escucha activa.

### 1.2.5 Poner en espera y transferir (hold & transfer)

- **Hold:** pedir permiso antes de poner en espera, explicar el motivo y agradecer la espera al volver.
- **Transfer:** hacer una transferencia atendida (**warm transfer**): presentar al usuario y el contexto al nuevo técnico para que el usuario no tenga que repetir toda la información.

### 1.2.6 Mantener el foco de la llamada (call focus)

Redirigir con cortesía las conversaciones que se desvían del problema, sin resultar brusco.

### 1.2.7 Tipos de clientes difíciles y estrategia de manejo

| Tipo de cliente | Estrategia correcta |
|---|---|
| **Hablador (talkative)** | Preguntas cerradas; redirigir amablemente al problema |
| **Grosero (rude)** | Mantener calma y profesionalismo; no tomarlo como algo personal |
| **Enfadado (angry)** | Dejar que se desahogue → empatizar → disculparse por la molestia → centrarse en la solución |
| **Experto / sabelotodo (knowledgeable)** | Respetar sus conocimientos; no ser condescendiente; nivel técnico de tú a tú |
| **Inexperto (inexperienced)** | Lenguaje sencillo sin jerga; instrucciones paso a paso; paciencia |

### 💡 Para el examen
- Nunca discutir, culpar al usuario ni usar jerga técnica con usuarios inexpertos.
- Secuencia ante cliente enfadado: escuchar → empatizar → disculparse → resolver.
- En preguntas sobre escucha activa, la respuesta correcta suele ser parafrasear o resumir.

**🔑 Palabras clave:** *active listening · paraphrasing · summarizing · open-ended questions · closed-ended questions · empathy · rapport · hold · warm transfer · call focus · difficult customers · professionalism · netiquette*

[⬆ Volver al índice](#-índice)

---

## 1.3 Customer Interaction and Documentation (Interacción con el cliente y documentación)

Cada interacción debe quedar registrada en el ticket con lenguaje claro y objetivo.

**Qué documentar:**

1. Síntomas descritos por el usuario (con sus palabras y el mensaje de error literal).
2. Pasos de diagnóstico realizados y su resultado.
3. Cambios aplicados en el sistema.
4. Resolución final y estado del ticket.

**Por qué documentar:**

- **Continuidad:** cualquier técnico puede retomar el caso sin repetir preguntas al usuario.
- **Conocimiento:** las soluciones se convierten en artículos de la base de conocimiento (KB).
- **Trazabilidad:** auditoría y protección ante reclamaciones.

**Buenas prácticas:** escribir durante la atención o inmediatamente después · hechos, no opiniones · sin abreviaturas ambiguas · respetar la privacidad de los datos del usuario.

### 💡 Para el examen
- Se documenta en cada fase del proceso. Las preguntas suelen dar por incorrecta la opción de documentar únicamente al cerrar el ticket.

**🔑 Palabras clave:** *documentation · ticket notes · knowledge base article · case history · follow-up · closure · data privacy*

[⬆ Volver al índice](#-índice)

---

## 1.4 Resumen del Módulo 1

El módulo trabaja tres competencias:

1. **Gestión de tickets:** colas, prioridades, SLA, escalado entre niveles.
2. **Comunicación profesional:** escucha activa, empatía, manejo de los 5 tipos de clientes difíciles.
3. **Documentación:** registro completo de cada interacción y resolución.

[⬆ Volver al índice](#-índice)

---

# MÓDULO 2 — Processes and Tools for Troubleshooting

**(Procesos y herramientas para la resolución de problemas)**

El troubleshooting sigue un método fijo y repetible. Trabajar con método reduce el tiempo de resolución, evita errores y deja constancia documental de lo hecho; improvisar suele producir lo contrario.

---

## 2.1 The Troubleshooting Process (El proceso de troubleshooting: los 8 pasos)

Memoriza los 8 pasos en orden. Es de lo más preguntado en el examen.

| Paso | Nombre (EN) | Qué se hace |
|---|---|---|
| **1** | **Define the Problem** | Definir el problema: recoger síntomas, preguntar al usuario, reproducir el fallo si es posible. Distinguir síntoma de causa. |
| **2** | **Gather Detailed Information** | Recopilar información detallada: logs, mensajes de error literales, cambios recientes, alcance (¿un usuario o muchos?). |
| **3** | **Identify the Probable Cause of the Failure** | Identificar la causa probable: formular hipótesis a partir de la evidencia, empezando por lo más simple y probable. |
| **4** | **Devise a Plan to Resolve the Problem** | Diseñar un plan de resolución: elegir la solución, valorar riesgos e impacto, preparar plan de reversión (rollback). |
| **5** | **Make the Necessary Changes to Implement the Plan** | Implementar los cambios del plan de forma controlada, un solo cambio cada vez. |
| **6** | **Observe the Results of the Changes** | Observar los resultados: comprobar que el problema está resuelto y que no han aparecido problemas nuevos; verificar con el usuario. |
| **7** | **If the Problem Is Not Resolved, Repeat the Process** | Si el problema sigue sin resolverse, repetir el proceso: deshacer el cambio si procede y probar la siguiente hipótesis, o escalar con toda la información recopilada. |
| **8** | **Document the Changes Made to Resolve the Problem** | Documentar los cambios realizados y la resolución en el ticket y, si aporta valor, en la base de conocimiento. |

**Escenario práctico del curso:** aplicación del método completo a un problema de conexión Wi-Fi.

### 💡 Para el examen
- Pregunta típica: «El técnico acaba de aplicar la solución, ¿cuál es el siguiente paso?» → Observar los resultados (paso 6).
- El paso 7 convierte el método en un ciclo: si la solución falla, se repite el proceso desde la siguiente hipótesis.
- Cambiar una sola variable a la vez al probar soluciones.
- La documentación (paso 8) es un paso formal del proceso, con el mismo rango que los demás.

**🔑 Palabras clave:** *troubleshooting process · define the problem · gather information · probable cause · hypothesis · plan of action · implement · observe results · repeat the process · document · rollback · escalate · one change at a time · root cause*

[⬆ Volver al índice](#-índice)

---

## 2.2 Remote Access Support (Soporte mediante acceso remoto)

### 2.2.1 Software de acceso remoto

Permite al técnico ver y controlar el equipo del usuario a distancia. Ejemplos: Remote Desktop (RDP) y Remote Assistance / Quick Assist de Windows, VNC, TeamViewer, AnyDesk.

### 2.2.2 Remote Desktop frente a Remote Assistance

| | **Remote Desktop (RDP)** | **Remote Assistance / Quick Assist** |
|---|---|---|
| Control | El técnico toma el control total | Sesión colaborativa: el usuario ve y participa |
| Sesión del usuario | Se bloquea la sesión local | El usuario sigue viendo su pantalla |
| Inicio | El técnico se conecta (puede ser desatendido) | Requiere invitación y consentimiento del usuario |
| Uso típico | Administrar servidores y equipos desatendidos | Soporte guiado con el usuario delante |
| Puerto | TCP 3389 | — |

### 2.2.3 Preparación de la sesión remota

Antes de conectar: obtener el consentimiento explícito del usuario → verificar su identidad → explicar qué se va a hacer → comprobar conectividad y credenciales.

### 2.2.4 Seguridad y buenas prácticas

- Conexión cifrada siempre.
- No dejar sesiones abiertas; cerrar sesión correctamente al terminar.
- Respetar la privacidad: no abrir archivos personales del usuario.
- Documentar todo lo realizado durante la sesión.

### 💡 Para el examen
- RDP = puerto TCP 3389. Dato que cae con frecuencia.
- El consentimiento del usuario va siempre antes de tomar el control remoto.
- Elegir herramienta según escenario: servidor desatendido → RDP; usuario que necesita ver lo que haces → Remote Assistance.

**🔑 Palabras clave:** *remote access · RDP (port 3389) · Remote Assistance · Quick Assist · VNC · screen sharing · unattended access · user consent · session security · encryption*

[⬆ Volver al índice](#-índice)

---

## 2.3 Researching with AI and Troubleshooting Tools (Investigación con IA)

### 2.3.1 Fuentes de investigación técnica (en orden de consulta)

1. Base de conocimiento interna (KB): primera parada siempre.
2. Documentación oficial del fabricante (vendor documentation).
3. Motores de búsqueda, foros técnicos y herramientas de IA.

### 2.3.2 IA para el diagnóstico (AI prompting)

Para redactar prompts eficaces:

- Dar contexto completo: sistema operativo, versión, mensaje de error exacto, qué se ha probado ya.
- Pedir pasos concretos y ordenados.
- Verificar la respuesta antes de aplicarla, porque la IA puede inventar información (*hallucinations*).

### 2.3.3 Motores de búsqueda con criterio

- Buscar el mensaje de error literal entre comillas.
- Priorizar fuentes fiables: fabricante y documentación oficial.
- Desconfiar de soluciones sin fundamento o de foros sin respuestas verificadas.

### 2.3.4 Foros técnicos: etiqueta de comunidad

Buscar antes de preguntar · describir bien el problema con contexto · compartir la solución encontrada para ayudar a otros.

### 💡 Para el examen
- Orden de investigación: KB interna → documentación oficial → búsqueda/foros/IA.
- Las soluciones nuevas y útiles deberían acabar como artículo de la KB.

**🔑 Palabras clave:** *AI prompting · generative AI · hallucination · knowledge base · search engine · technical forums · vendor documentation · verify sources*

[⬆ Volver al índice](#-índice)

---

## 2.4 Common Application Issues (Problemas comunes de aplicaciones)

### 2.4.1 Problemas de instalación de aplicaciones

Causas más frecuentes, en el orden en que deben comprobarse:

1. Requisitos del sistema no cumplidos (SO, RAM, espacio en disco).
2. Falta de permisos de administrador.
3. Instalador corrupto o descarga incompleta.
4. Conflictos con el antivirus o software de seguridad.
5. Dependencias que faltan; incompatibilidad de arquitectura (32/64 bits).

### 2.4.2 Problemas de email y aplicaciones de colaboración

- **Email:** configuración incorrecta de cuenta (servidores/puertos/autenticación), contraseñas caducadas, buzón lleno, problemas de sincronización.
- **Colaboración (Teams, Zoom, Webex…):** audio/vídeo, permisos de micrófono y cámara, versiones desactualizadas.

**Protocolos de correo a memorizar:**

| Protocolo | Función | Puertos (estándar / seguro) |
|---|---|---|
| **SMTP** | Envío | 25 / 587 (465) |
| **IMAP** | Recepción; sincroniza con el servidor | 143 / 993 |
| **POP3** | Recepción; descarga local | 110 / 995 |

**Escenario práctico del curso:** resolver un problema en una app de mensajería aplicando los 8 pasos del apartado [2.1](#21-the-troubleshooting-process-el-proceso-de-troubleshooting-los-8-pasos).

### 💡 Para el examen
- Ante un fallo de instalación, lo primero: requisitos del sistema y permisos.
- IMAP mantiene el correo en el servidor; POP3 lo descarga. Distinción clásica de examen.

**🔑 Palabras clave:** *system requirements · administrator privileges · installation error · compatibility · dependencies · email client · SMTP · IMAP · POP3 · synchronization · collaboration apps*

[⬆ Volver al índice](#-índice)

---

## 2.5 Resumen del Módulo 2

El módulo cubre cuatro bloques:

1. El proceso de troubleshooting de 8 pasos, con el paso 7 como mecanismo de iteración cuando la primera solución falla.
2. Herramientas de acceso remoto, usadas de forma segura y con consentimiento del usuario.
3. Investigación con criterio: KB → documentación oficial → búsqueda/IA, verificando las fuentes.
4. Fallos de aplicación habituales: instalación, email y apps de colaboración.

[⬆ Volver al índice](#-índice)

---

# 🏁 Examen final del curso

El curso cierra con el **IT Customer Support Basics Final Exam** (y una encuesta de satisfacción que no puntúa). Repasa especialmente:

1. Ciclo de vida del ticket, niveles de soporte (tiers) y criterios de escalado.
2. Técnicas de comunicación y manejo de los 5 tipos de clientes difíciles.
3. Los 8 pasos del proceso de troubleshooting, en orden.
4. Remote Desktop frente a Remote Assistance, y el consentimiento del usuario.
5. Buenas prácticas de documentación e investigación con IA.
6. Puertos: RDP 3389 · SMTP 25/587 · IMAP 143/993 · POP3 110/995.

[⬆ Volver al índice](#-índice)

---

# 🎯 Mapeo con la certificación CCST IT Support

| Dominio CCST IT Support | Contenido del curso relacionado |
|---|---|
| Essential Diagnostic & Troubleshooting | [2.1](#21-the-troubleshooting-process-el-proceso-de-troubleshooting-los-8-pasos) (los 8 pasos), [2.4](#24-common-application-issues-problemas-comunes-de-aplicaciones) |
| Job Tasks & Help Desk Responsibilities | [1.1](#11-help-desk-concepts-conceptos-de-help-desk) (tickets, SLA, escalado, tiers) |
| Communication & Customer Service | [1.2](#12-professional-communication-skills-habilidades-de-comunicación-profesional), [1.3](#13-customer-interaction-and-documentation-interacción-con-el-cliente-y-documentación) |
| Remote Support Tools | [2.2](#22-remote-access-support-soporte-mediante-acceso-remoto) |
| Research & Documentation | [1.3](#13-customer-interaction-and-documentation-interacción-con-el-cliente-y-documentación), [2.3](#23-researching-with-ai-and-troubleshooting-tools-investigación-con-ia) |

[⬆ Volver al índice](#-índice)

---

# 📖 Glosario de términos

| Término | Definición |
|---|---|
| **Active listening (escucha activa)** | Técnica de comunicación que consiste en atender plenamente al interlocutor, sin interrumpir, confirmando la comprensión mediante paráfrasis y resúmenes. |
| **AI prompting** | Redacción de instrucciones (prompts) claras y con contexto para obtener respuestas útiles de una herramienta de IA generativa. |
| **CSAT (Customer Satisfaction)** | Métrica que mide la satisfacción del cliente tras una interacción de soporte, normalmente mediante encuesta. |
| **Escalation (escalado)** | Transferencia de un ticket a un nivel de soporte superior cuando excede la capacidad o autoridad del nivel actual. |
| **FCR (First Contact Resolution)** | Porcentaje de incidencias resueltas en el primer contacto, sin escalados ni llamadas posteriores. |
| **Help desk** | Punto único de contacto entre los usuarios y el departamento de TI para incidencias y solicitudes. |
| **IMAP / POP3** | Protocolos de recepción de correo. IMAP (143/993) sincroniza con el servidor; POP3 (110/995) descarga los mensajes localmente. |
| **Impact (impacto)** | Alcance de un incidente: número de usuarios o procesos de negocio afectados. Junto con la urgencia determina la prioridad. |
| **Incident (incidente)** | Interrupción no planificada o degradación de un servicio de TI. |
| **KB / Knowledge base (base de conocimiento)** | Repositorio de artículos con soluciones documentadas a problemas conocidos, reutilizables por técnicos y usuarios. |
| **KPI** | Indicador clave de rendimiento; en help desk: tiempo de primera respuesta, tiempo de resolución, FCR, CSAT. |
| **Open-ended / Closed-ended questions** | Preguntas abiertas (respuesta libre, para explorar) frente a cerradas (sí/no o dato concreto, para confirmar). |
| **Queue (cola)** | Lista ordenada de tickets pendientes, organizada por prioridad, categoría o equipo asignado. |
| **RDP (Remote Desktop Protocol)** | Protocolo de Microsoft para control remoto total de un equipo. Puerto TCP 3389. Bloquea la sesión local del usuario. |
| **Remote Assistance / Quick Assist** | Herramientas de Windows para soporte remoto colaborativo: el usuario ve la sesión y debe dar su consentimiento. |
| **Rollback (plan de reversión)** | Procedimiento para deshacer un cambio si la solución aplicada causa nuevos problemas. |
| **Root cause (causa raíz)** | Origen real de un problema, distinto de sus síntomas visibles. |
| **Service request (solicitud de servicio)** | Petición formal de un usuario (acceso, instalación, información) que no implica una avería. |
| **SLA (Service Level Agreement)** | Acuerdo que define los niveles de servicio comprometidos: tiempos máximos de respuesta y resolución según prioridad. |
| **SMTP** | Protocolo de envío de correo electrónico (puertos 25/587/465). |
| **Soft skills (habilidades blandas)** | Competencias interpersonales: comunicación, empatía, paciencia, gestión de conflictos. |
| **Ticket** | Registro digital de un incidente o solicitud que documenta todo su ciclo de vida hasta el cierre. |
| **Ticketing system** | Software de gestión de tickets (ServiceNow, Zendesk, Jira SM, osTicket…): registro, asignación, seguimiento y métricas. |
| **Tier / Level 1, 2, 3** | Niveles de soporte escalonados: L1 primer contacto, L2 especialistas, L3 expertos/fabricante. |
| **Triage** | Clasificación inicial de tickets para asignarles prioridad y equipo; a menudo asistida por IA. |
| **Troubleshooting** | Proceso sistemático de diagnóstico y resolución de problemas técnicos; en este curso, el método de 8 pasos. |
| **Urgency (urgencia)** | Rapidez con la que un incidente debe resolverse por su criticidad temporal. |
| **VNC (Virtual Network Computing)** | Sistema multiplataforma de compartición de escritorio remoto. |
| **Warm transfer (transferencia atendida)** | Transferencia de llamada en la que el técnico presenta el caso al nuevo agente antes de retirarse, evitando que el usuario repita la información. |
| **Workflow (flujo de trabajo)** | Secuencia estandarizada de estados por los que pasa un ticket: nuevo → asignado → en curso → resuelto → cerrado. |

[⬆ Volver al índice](#-índice)

---

*Manual de repaso del curso Cisco NetAcad «IT Customer Support Basics» y preparación del examen CCST IT Support. Material libre para compartir con la clase.*
