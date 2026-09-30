[← Volver a la página principal del repositorio](../../README.md)

# Hardware and Upgrade Support

> **Objetivo del curso:** diagnosticar y reparar problemas comunes de hardware (desde una fuente de alimentación defectuosa hasta un disco que falla), aplicar los procedimientos de seguridad, identificar puertos y cables, e instalar y ampliar componentes clave como memoria RAM y unidades de almacenamiento.

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [0. Introducción al curso](#0-introducción-al-curso)
- [Módulo 1 — Troubleshooting Common Hardware Issues](#módulo-1--troubleshooting-common-hardware-issues)
  - [1.1 Basic Safety Procedures](#11-basic-safety-procedures-procedimientos-básicos-de-seguridad)
  - [1.2 Device Information Tools](#12-device-information-tools-herramientas-de-información-del-equipo)
  - [1.3 Ports and Cables](#13-ports-and-cables-puertos-y-cables)
  - [1.4 Hardware Issues](#14-hardware-issues-problemas-de-hardware)
  - [1.5 Resumen del Módulo 1](#15-resumen-del-módulo-1)
- [Módulo 2 — Common Hardware Upgrades](#módulo-2--common-hardware-upgrades)
  - [2.1 System Architecture and Compatibility](#21-system-architecture-and-compatibility-arquitectura-y-compatibilidad)
  - [2.2 Core Hardware Components](#22-core-hardware-components-componentes-principales)
  - [2.3 Interfaces and Expansion Technologies](#23-interfaces-and-expansion-technologies-interfaces-y-expansión)
  - [2.4 Driver Management and Device Manager](#24-driver-management-and-device-manager-gestión-de-drivers)
  - [2.5 E-Waste and Responsible Component Disposal](#25-e-waste-and-responsible-component-disposal-residuos-electrónicos)
  - [2.6 Resumen del Módulo 2](#26-resumen-del-módulo-2)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del apartado correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Es el curso más práctico de la serie: si puedes, acompaña la lectura abriendo un equipo real o usando los simuladores del curso.

---

# 0. Introducción al curso

Cuarto y último curso del *IT Support Specialist Career Path*, orientado al CCST IT Support. Cuando el hardware falla (el equipo va lento, no arranca, un componente muere), el técnico de soporte es quien diagnostica y resuelve.

Dos módulos: diagnóstico y reparación de problemas de hardware (Módulo 1) y ampliaciones de componentes (Módulo 2). Al terminar, el alumno sabe realizar reparaciones básicas, mantenimiento y upgrades de RAM y almacenamiento.

[⬆ Volver al índice](#índice)

---

# MÓDULO 1 — Troubleshooting Common Hardware Issues

**(Resolución de problemas comunes de hardware)**

Antes de tocar un componente hay que saber trabajar con seguridad, identificar qué hardware tiene el equipo y reconocer cada puerto y cable.

---

## 1.1 Basic Safety Procedures (Procedimientos básicos de seguridad)

Protegen tanto al técnico como al equipo:

- **Descarga electrostática (ESD):** el enemigo silencioso de los componentes. Prevención: **pulsera antiestática** conectada al chasis, alfombrilla antiestática, tocar el chasis metálico antes de manipular, guardar componentes en **bolsas antiestáticas**, evitar alfombras y ambientes muy secos.
- **Seguridad eléctrica:** desconectar el equipo de la corriente antes de abrirlo; no abrir nunca **fuentes de alimentación ni monitores CRT** (retienen carga letal incluso desconectados).
- **Entorno de trabajo:** superficie limpia y ordenada, organizadores para tornillos, herramientas adecuadas (destornilladores imantados con precaución), buena iluminación.
- **Seguridad personal:** quitarse anillos y pulseras, cuidado con bordes cortantes del chasis, levantar peso con la espalda recta.
- Limpieza: aire comprimido para el polvo (ventiladores bloqueados al aplicarlo), alcohol isopropílico para contactos.

### Para el examen
- ESD: pueden bastar menos de 30 voltios para dañar un componente, y el técnico ni lo nota (se sienten a partir de ~3.000 V).
- Nunca abrir una fuente de alimentación: se sustituye entera.
- La pulsera antiestática NO se usa al trabajar con fuentes o CRT (riesgo de descarga hacia el técnico).

## 1.2 Device Information Tools (Herramientas de información del equipo)

Antes de diagnosticar hay que saber qué hardware hay dentro sin abrir el equipo:

| Herramienta (Windows) | Qué muestra |
|---|---|
| **System Information (`msinfo32`)** | Resumen completo: CPU, RAM, placa, BIOS/UEFI, drivers |
| **Device Manager (`devmgmt.msc`)** | Todos los dispositivos y el estado de sus drivers |
| **Task Manager → Rendimiento** | Uso en tiempo real de CPU, RAM, disco, red y GPU |
| **DirectX Diagnostic (`dxdiag`)** | Detalles de gráficos y sonido |
| **BIOS/UEFI** | Inventario a más bajo nivel, temperaturas, orden de arranque |

- Equivalentes: **Información del Sistema** en macOS; `lscpu`, `lsblk`, `lspci`, `lsusb`, `dmidecode` en Linux (ver [referencia de comandos Linux](../../recursos/linux-commands-reference.md)).
- Utilidad en soporte: verificar specs antes de una ampliación, detectar componentes no reconocidos y documentar la configuración en el ticket.

### Para el examen
- `msinfo32` = visión general del sistema; Device Manager = estado de dispositivos y drivers.
- Un dispositivo con triángulo amarillo en Device Manager tiene un problema de driver.

## 1.3 Ports and Cables (Puertos y cables)

Identificar cada puerto de un vistazo es competencia básica del técnico:

**Vídeo:**

| Puerto | Característica |
|---|---|
| **VGA** | Analógico, 15 pines, azul; obsoleto pero aún presente |
| **DVI** | Digital (y/o analógico según variante) |
| **HDMI** | Digital, vídeo + audio; el más común en monitores y TVs |
| **DisplayPort** | Digital, vídeo + audio; habitual en monitores profesionales |
| **USB-C (DP Alt Mode)** | Vídeo por USB-C en equipos modernos |

**Datos y periféricos:**

- **USB:** USB-A (clásico), USB-B (impresoras), Mini/Micro-USB, **USB-C** (reversible, actual). Versiones: USB 2.0 (480 Mbps), 3.x (5-20 Gbps, conectores azules), USB4.
- **Thunderbolt:** sobre conector USB-C, hasta 40 Gbps; permite datos, vídeo y alimentación.
- **Ethernet RJ-45:** red cableada.
- Audio jack 3,5 mm (verde salida, rosa micrófono).

**Almacenamiento y alimentación (internos):** SATA (datos + alimentación), conectores de la fuente (24 pines placa, 8 pines CPU, PCIe para gráficas).

### Para el examen
- Saber emparejar imagen/descripción de puerto con su nombre: VGA azul analógico, HDMI audio+vídeo, USB-C reversible.
- USB 3.x se identifica por el conector azul o el logo SS (SuperSpeed).

## 1.4 Hardware Issues (Problemas de hardware)

Síntomas y componente sospechoso:

| Síntoma | Sospechoso principal | Comprobaciones |
|---|---|---|
| No enciende nada (ni luces ni ventiladores) | **Fuente de alimentación (PSU)** | Cable y enchufe, interruptor trasero, tester de fuente |
| Enciende pero no da imagen | RAM, GPU, monitor | Reasentar RAM/GPU, monitor y cable alternativos, pitidos POST |
| Pitidos al arrancar (beep codes) | Según el patrón: RAM, GPU, placa | Consultar el manual de la placa base |
| Apagados aleatorios / reinicios | Sobrecalentamiento, PSU | Temperaturas, ventiladores, polvo, pasta térmica |
| Lentitud extrema + ruidos de clic | **Disco duro (HDD) fallando** | S.M.A.R.T., copia de seguridad urgente, sustituir por SSD |
| Pantallazos azules (BSOD) recurrentes | RAM, drivers, disco | Test de memoria (Windows Memory Diagnostic, MemTest86) |
| Fecha/hora se pierden al apagar | **Pila CMOS** agotada | Sustituir la pila (CR2032) |
| Ruido excesivo de ventiladores | Polvo, refrigeración insuficiente | Limpieza, curvas de ventilador, pasta térmica |

- El **POST** (Power-On Self-Test) diagnostica el hardware básico al encender; sus pitidos o códigos indican el componente que falla.
- Metodología: aplicar los 8 pasos del [primer curso](it-customer-support-basics.md), cambiando un componente cada vez y probando tras cada cambio.

### Para el examen
- Clics rítmicos en un HDD = fallo inminente: copia de seguridad inmediata.
- Fecha y hora que se resetean = pila CMOS (CR2032).
- Beep codes del POST: su significado depende del fabricante de la BIOS; se consulta el manual.

## 1.5 Resumen del Módulo 1

El módulo prepara al técnico para intervenir hardware con seguridad (ESD, electricidad), inventariar el equipo con herramientas del sistema, identificar cualquier puerto o cable y asociar síntomas típicos a componentes concretos usando el POST y las herramientas de diagnóstico. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Common Hardware Upgrades

**(Ampliaciones comunes de hardware)**

Ampliar RAM o cambiar un disco por un SSD son las intervenciones con mejor relación coste/beneficio en un equipo lento. La clave está en la compatibilidad.

---

## 2.1 System Architecture and Compatibility (Arquitectura y compatibilidad)

- **Placa base (motherboard):** el nexo de todo. Factores de forma (ATX, micro-ATX, mini-ITX), chipset, socket de CPU.
- **Compatibilidad antes de comprar nada:**
  - CPU ↔ socket y chipset de la placa.
  - RAM ↔ tipo (DDR4/DDR5), velocidad y máximo soportado por placa y CPU.
  - Fuente ↔ potencia suficiente para los componentes (especialmente GPU).
  - Caja ↔ tamaño de placa y GPU.
- **BIOS/UEFI:** reconoce el hardware; a veces una ampliación requiere actualizarla. UEFI aporta arranque seguro (Secure Boot) y discos grandes (GPT).
- Consultar el manual de la placa o la web del fabricante (QVL, lista de compatibilidad cualificada) antes de una ampliación.

### Para el examen
- No se puede montar RAM DDR5 en una placa DDR4: las muescas del zócalo son distintas físicamente.
- UEFI + GPT sustituyen a BIOS + MBR en equipos modernos.

## 2.2 Core Hardware Components (Componentes principales)

| Componente | Función | Claves de ampliación |
|---|---|---|
| **CPU** | Ejecuta las instrucciones | Socket compatible, pasta térmica nueva al montar el disipador |
| **RAM** | Memoria de trabajo volátil | DDR4/DDR5, instalar en pares para dual channel, muesca de alineación |
| **Almacenamiento** | Datos persistentes | HDD (mecánico, barato) frente a **SSD SATA** y **SSD NVMe M.2** (mucho más rápidos) |
| **GPU** | Gráficos | Ranura PCIe x16, potencia de fuente y conectores requeridos |
| **PSU (fuente)** | Alimenta el sistema | Vatios suficientes, certificación 80 Plus |
| **Refrigeración** | Mantiene temperaturas | Disipador de stock o mejor, flujo de aire de la caja |

- **La ampliación estrella:** sustituir HDD por SSD. Es el upgrade que más rendimiento percibido aporta a un equipo lento.
- Instalación de RAM: apertura de pestañas, alinear muesca, presión firme hasta el clic. Comprobar en BIOS/`msinfo32` que se reconoce la nueva capacidad.
- Clonación de disco o instalación limpia al migrar de HDD a SSD.

### Para el examen
- ¿Equipo lento con HDD? La respuesta esperada suele ser: migrar a SSD y/o ampliar RAM.
- Jerarquía de velocidad de almacenamiento: NVMe M.2 > SSD SATA > HDD.
- RAM en dual channel: módulos por pares en las ranuras del mismo color (según manual de placa).

## 2.3 Interfaces and Expansion Technologies (Interfaces y expansión)

- **PCIe (PCI Express):** la interfaz de expansión moderna. Tamaños x1, x4, x8, **x16** (gráficas); generaciones 3.0/4.0/5.0 que duplican ancho de banda.
- **M.2:** formato compacto para SSDs; puede usar bus SATA o **NVMe** (PCIe), mucho más rápido. Atención a la longitud (2280 es la común) y a la llave del conector.
- **SATA III:** discos y SSDs de 2,5"/3,5", hasta 6 Gbps.
- Expansión externa: USB, Thunderbolt, lectores de tarjetas, docks y replicadores de puertos.

### Para el examen
- Un SSD M.2 puede ser SATA o NVMe: no son intercambiables si la placa no soporta ambos; verificar en el manual.
- La GPU va siempre en la ranura PCIe x16.

## 2.4 Driver Management and Device Manager (Gestión de drivers)

- El **driver** hace de puente entre el sistema operativo y el hardware. Tras instalar un componente, puede necesitar driver del fabricante.
- **Device Manager (Administrador de dispositivos):** ver estado de cada dispositivo, actualizar driver, **revertir driver (Roll Back)** si una actualización causa problemas, deshabilitar o desinstalar dispositivos.
- Símbolos de estado: triángulo amarillo (problema de driver), flecha hacia abajo (deshabilitado), dispositivo desconocido (sin driver).
- Buenas prácticas: descargar drivers solo de la web del fabricante, crear punto de restauración antes de cambios importantes, mantener drivers críticos actualizados (GPU, chipset, red).

### Para el examen
- Driver recién actualizado que causa fallos → **Roll Back Driver** en Device Manager.
- Dispositivo desconocido tras instalar hardware nuevo = falta el driver.

## 2.5 E-Waste and Responsible Component Disposal (Residuos electrónicos)

- Los componentes electrónicos contienen materiales contaminantes (plomo, mercurio, litio) y valiosos (oro, cobre): nunca a la basura común.
- **Baterías y pilas:** puntos de recogida específicos; riesgo de incendio en las de litio dañadas.
- **Discos y soportes de datos:** antes de desechar o donar, **borrado seguro** (varias pasadas o herramientas de wipe) o **destrucción física** si la política lo exige; formatear no basta.
- Vías responsables: puntos limpios, programas de reciclaje del fabricante, donación de equipos funcionales.
- Normativa: en Europa, la directiva **WEEE/RAEE** regula la gestión de residuos electrónicos.

### Para el examen
- Formatear un disco NO elimina los datos de forma segura: se requiere borrado seguro o destrucción física.
- Tóner, baterías y CRT tienen procedimientos de desecho específicos regulados.

## 2.6 Resumen del Módulo 2

El módulo cubre la lógica completa de una ampliación: verificar compatibilidad (placa, socket, RAM, potencia), conocer cada componente y su upgrade típico (SSD y RAM como estrellas), dominar las interfaces (PCIe, M.2, SATA), gestionar drivers desde Device Manager y desechar los componentes retirados de forma segura y responsable. Cierra con quiz.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El curso cierra con el **Hardware and Upgrade Support Course Final Exam** (y una encuesta de satisfacción que no puntúa). Repasa especialmente:

1. ESD y procedimientos de seguridad: pulsera antiestática, cuándo NO usarla, fuentes y CRT que no se abren.
2. Identificación de puertos: VGA, HDMI, DisplayPort, USB-A/C, Thunderbolt, RJ-45.
3. Tabla síntoma → componente: no enciende (PSU), clics (HDD), fecha perdida (pila CMOS), pitidos POST.
4. Compatibilidad de ampliaciones: DDR4 vs DDR5, socket de CPU, potencia de fuente.
5. Jerarquía de almacenamiento: NVMe > SSD SATA > HDD; el upgrade HDD → SSD.
6. Device Manager: triángulo amarillo, Roll Back Driver, dispositivo desconocido.
7. Borrado seguro de datos antes de desechar discos; formatear no basta.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1 — Diagnóstico de hardware:** *ESD · antistatic wrist strap · antistatic bag · power supply (PSU) · CRT · `msinfo32` · Device Manager · `dxdiag` · Task Manager · BIOS/UEFI · POST · beep codes · VGA · DVI · HDMI · DisplayPort · USB-A/B/C · Thunderbolt · RJ-45 · SATA · S.M.A.R.T. · CMOS battery (CR2032) · BSOD · Windows Memory Diagnostic · thermal paste · overheating*

**Módulo 2 — Ampliaciones:** *motherboard · form factor (ATX, micro-ATX, mini-ITX) · socket · chipset · DDR4/DDR5 · dual channel · HDD · SSD · NVMe · M.2 (2280) · SATA III · PCIe x16 · GPU · PSU wattage · 80 Plus · UEFI/GPT vs. BIOS/MBR · Secure Boot · QVL · driver · Roll Back Driver · unknown device · disk cloning · secure wipe · e-waste · WEEE/RAEE*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **80 Plus** | Certificación de eficiencia energética de fuentes de alimentación (Bronze, Gold, Platinum…). |
| **Beep codes** | Pitidos del POST que codifican el componente que falla; su significado depende del fabricante de la BIOS. |
| **BIOS/UEFI** | Firmware de la placa base que inicializa el hardware. UEFI es el sucesor moderno: Secure Boot, discos GPT, interfaz gráfica. |
| **BSOD** | Pantalla azul de error crítico de Windows; recurrente suele apuntar a RAM, driver o disco. |
| **Chipset** | Conjunto de chips de la placa base que gestiona la comunicación entre CPU, memoria y periféricos. |
| **CMOS (pila)** | Pila de botón (CR2032) que mantiene la configuración de la BIOS y el reloj; agotada, el equipo pierde fecha y hora. |
| **DDR4 / DDR5** | Generaciones de memoria RAM, físicamente incompatibles entre sí. |
| **Device Manager** | Consola de Windows para ver el estado de los dispositivos y gestionar sus drivers. |
| **Driver (controlador)** | Software que permite al sistema operativo comunicarse con un componente de hardware. |
| **Dual channel** | Modo que duplica el ancho de banda de la RAM instalando los módulos por pares. |
| **ESD (descarga electrostática)** | Descarga de electricidad estática capaz de dañar componentes con voltajes imperceptibles para el técnico. |
| **Factor de forma** | Tamaño estandarizado de placa base o caja: ATX, micro-ATX, mini-ITX. |
| **GPT / MBR** | Esquemas de particionado de disco. GPT (con UEFI) soporta discos grandes y más particiones que el antiguo MBR. |
| **HDD** | Disco duro mecánico; mayor capacidad por precio, más lento y frágil que un SSD. |
| **M.2** | Formato compacto de SSD que se inserta directamente en la placa; puede usar bus SATA o NVMe. |
| **NVMe** | Protocolo de almacenamiento sobre PCIe; los SSD más rápidos del mercado. |
| **PCIe (PCI Express)** | Interfaz de expansión moderna en tamaños x1 a x16; las gráficas usan x16. |
| **POST (Power-On Self-Test)** | Autodiagnóstico del hardware básico que ejecuta el firmware al encender el equipo. |
| **PSU (fuente de alimentación)** | Convierte la corriente alterna en los voltajes que usa el equipo. No se abre nunca: se sustituye. |
| **Pulsera antiestática** | Brazalete conectado al chasis que iguala el potencial eléctrico del técnico y evita ESD. |
| **QVL (Qualified Vendor List)** | Lista de componentes verificados como compatibles por el fabricante de la placa base. |
| **Roll Back Driver** | Función de Device Manager que restaura la versión anterior de un driver problemático. |
| **S.M.A.R.T.** | Sistema de automonitorización de discos que anticipa fallos; se consulta con herramientas de diagnóstico. |
| **Secure Boot** | Función de UEFI que impide cargar software de arranque no firmado. |
| **Socket** | Zócalo de la placa base donde encaja la CPU; determina qué procesadores son compatibles. |
| **SSD** | Unidad de estado sólido, sin partes móviles; el upgrade de mayor impacto sobre un equipo con HDD. |
| **Thunderbolt** | Interfaz de alta velocidad (hasta 40 Gbps) sobre conector USB-C: datos, vídeo y alimentación. |
| **WEEE / RAEE** | Directiva europea que regula la recogida y reciclaje de residuos de aparatos eléctricos y electrónicos. |
| **Wipe (borrado seguro)** | Eliminación irrecuperable de los datos de un soporte antes de desecharlo o donarlo; formatear no es suficiente. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Hardware and Upgrade Support», cuarto y último curso de la serie alineada con el CCST IT Support cursado desde Barcelona Activa. Material libre para compartir con la clase.*
