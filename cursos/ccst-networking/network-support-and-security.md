[← Volver a la página principal del repositorio](../../README.md)

# Manual de Estudio — Network Support and Security

> **Objetivo del curso:** aprender el día a día del soporte de red: diagnóstico y documentación, trabajo en un help desk, resolución de problemas de endpoints y de red (también en remoto), amenazas y ataques de ciberseguridad, y la configuración de un acceso seguro. Cuarto y último curso de la serie CCST Networking, continuación de [Network Addressing and Basic Troubleshooting](network-addressing-and-basic-troubleshooting.md).

**Estado de estos apuntes:** curso completo. Cubren los 3 módulos y el examen final (12 horas, 10 labs).

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Network Support](#módulo-1--network-support)
- [Módulo 2 — Cybersecurity Threats, Vulnerabilities, and Attacks](#módulo-2--cybersecurity-threats-vulnerabilities-and-attacks)
- [Módulo 3 — Network Security](#módulo-3--network-security)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del módulo correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En el examen CCST Networking aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Este curso enlaza con los manuales de IT Support (help desk, tickets, seguridad) y con los tres cursos anteriores de networking: los enlaces cruzados apuntan a los apartados relacionados.

---

# MÓDULO 1 — Network Support

**(Soporte de red: diagnóstico, documentación y help desk)**

## 1.1 Diagnostics and Troubleshooting Methodologies (Diagnóstico y metodologías)

- Este curso formaliza el proceso de troubleshooting en **7 pasos**:

| Paso | Acción |
|---|---|
| 1 | Definir el problema |
| 2 | Recopilar información |
| 3 | Analizar la información |
| 4 | Eliminar causas posibles |
| 5 | Proponer una hipótesis |
| 6 | Probar la hipótesis |
| 7 | Resolver el problema y documentarlo |

- Nota de repaso: en IT Support trabajamos la versión de **8 pasos** (añade "repetir el proceso si no se resuelve" como paso propio). La lógica es la misma; conviene saber responder con la numeración que pida cada examen.
- **Troubleshooting con modelos de capas:** usar OSI o TCP/IP como guion para acotar: ¿el fallo está en la física, en la red, en la aplicación?
- Métodos estructurados (vistos en el [curso anterior](network-addressing-and-basic-troubleshooting.md#módulo-7--troubleshoot-common-network-problems)): **top-down, bottom-up, divide and conquer, follow-the-path, sustitución**, más dos nuevos: **comparación** (contrastar con un equipo que funciona) y **conjetura fundamentada** (la intuición del técnico con experiencia).
- Elegir método según el síntoma; registrar siempre hallazgos, acciones y resultados.

## 1.2 Network Documentation (Documentación de red)

- La documentación es la memoria de la red. Debe existir antes del problema, no después:
  - **Diagramas de topología física** (dónde está cada equipo y cable) **y lógica** (direccionamiento, VLANs, enlaces).
  - Documentación de dispositivos: modelo, IOS, IPs, puertos usados, contraseñas en gestor seguro.
  - **Baseline de rendimiento:** mediciones de la red funcionando bien (uso de CPU, tráfico, tiempos de ping) para comparar cuando algo va mal. Se obtiene con capturas periódicas y comandos show.
- Sin baseline no hay forma objetiva de afirmar que "la red va lenta".

## 1.3 Help Desks (El help desk)

- La **política de seguridad** marca el terreno de juego: autenticación, requisitos de contraseñas, comportamiento aceptable (AUP), acceso remoto. De ella cuelgan:
  - **SOPs:** procedimientos paso a paso para tareas concretas (altas, bajas, sustitución de equipos).
  - **Guidelines:** pautas para lo que no tiene SOP.
- El help desk es el punto de contacto único; gestiona el ciclo de vida del problema con un **sistema de tickets**: el usuario abre (o el técnico abre por él), el técnico valida, investiga, y **resuelve y documenta** o **escala** al siguiente nivel.
- Con el usuario: preguntas **abiertas** para entender y **cerradas** para concretar; escucha activa (dejar hablar, confirmar resumiendo, no interrumpir); nunca culpar ni usar jerga.
- Información útil para tickets de host: fabricante y modelo, versión del SO, entorno de red, resultados de ping/tracert, códigos de pitidos, Visor de eventos, Administrador de dispositivos, Administrador de tareas.
- Para tickets de equipos Cisco: comandos show, logs del dispositivo y capturas de paquetes.

## 1.4 Troubleshoot Endpoint Connectivity (Conectividad de endpoints)

- Verificar la configuración de red en cada sistema:

| Sistema | Dónde mirar |
|---|---|
| Windows | `ipconfig /all`, ping, tracert, nslookup |
| Linux | `ip addr` (o `ifconfig`), ping, traceroute, dig |
| macOS | Preferencias del Sistema > Red, `ifconfig`, `networksetup` |
| Android / iOS | Ajustes > Wi-Fi: IP, gateway y DNS de la conexión activa |

- Comprobaciones de siempre: ¿tiene IP válida o APIPA?, ¿gateway y DNS correctos?, ¿funciona la escalera de pings?, ¿el Wi-Fi está conectado al SSID correcto?
- En inalámbrico, revisar también señal, banda y que el adaptador no esté en modo avión o ahorro de energía.

## 1.5 Troubleshoot a Network (Diagnóstico de la red)

- Cuando el problema no es de un solo endpoint, se diagnostica desde los equipos de red:
  - `show ip interface brief`: el primer vistazo; interfaces, IPs y estado.
  - `show ip route`: ¿existe ruta hacia el destino?
  - `show interfaces`: errores, descartes y duplex de cada interfaz.
  - ping y traceroute desde el propio router o switch para acotar el tramo que falla.
- Correlacionar con los avisos de los usuarios: si cae un switch de planta, fallan muchos a la vez; si falla un host, el problema es local.

## 1.6 Troubleshoot Connectivity Remotely (Soporte en remoto)

- Gran parte del soporte se hace sin estar delante del equipo:

| Herramienta | Uso | Seguridad |
|---|---|---|
| **SSH** | CLI remota de equipos de red y servidores | Cifrado; el estándar |
| **Telnet** | CLI remota heredada | Texto plano: no usar |
| **RDP** | Escritorio remoto de Windows | Cifrado; exponerlo a internet es peligroso |
| **Software de escritorio remoto** | Ver y controlar el equipo del usuario | Siempre con consentimiento del usuario |
| **VPN** | Túnel cifrado hacia la red corporativa | Base del teletrabajo seguro |

- Buenas prácticas: pedir permiso antes de tomar el control, explicar lo que se hace, cerrar la sesión al terminar y dejar constancia en el ticket.

### Para el examen
- Los 7 pasos del proceso en orden; y saber que la variante de 8 pasos añade "repetir si no se resuelve".
- Baseline = referencia de la red sana; sin ella no se puede medir la degradación.
- Política de seguridad → SOPs (paso a paso) y guidelines (lo demás). AUP = comportamiento aceptable.
- Pregunta abierta para explorar, cerrada para confirmar. Escalar cuando faltan conocimientos o permisos.
- SSH sí, Telnet no: la pareja favorita del examen.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Cybersecurity Threats, Vulnerabilities, and Attacks

**(Amenazas, vulnerabilidades y ataques)**

## 2.1 Common Threats (Amenazas comunes)

- Conceptos base: una **amenaza** explota una **vulnerabilidad** mediante un **ataque**. Las amenazas pueden ser internas (empleados, por malicia o error) o externas.
- Actores de amenaza:

| Actor | Perfil |
|---|---|
| **Script kiddie** | Sin conocimientos profundos; usa herramientas de otros |
| **Hacktivista** | Ataca por motivos ideológicos |
| **Cibercriminal** | Busca dinero; el más común |
| **Patrocinado por estados** | Espionaje y sabotaje con muchos recursos |
| **Sombrero blanco / gris / negro** | Hackea legalmente con permiso / sin permiso pero sin ánimo de daño / con fines maliciosos |

- Tipos de **malware** que hay que distinguir:

| Malware | Comportamiento |
|---|---|
| **Virus** | Se adjunta a archivos legítimos; necesita ejecución del usuario para propagarse |
| **Gusano (worm)** | Se propaga solo por la red, sin intervención del usuario |
| **Troyano** | Se disfraza de software legítimo; no se replica |
| **Ransomware** | Cifra los datos y pide rescate |
| **Spyware** | Espía la actividad (incluye keyloggers) |
| **Adware** | Publicidad no deseada; a menudo acompaña a otros |
| **Rootkit** | Se esconde en el sistema con privilegios; muy difícil de detectar |
| **Backdoor / RAT** | Acceso remoto persistente saltándose la autenticación |
| **Bomba lógica** | Se activa ante una condición (fecha, evento) |

## 2.2 Deception (Engaño e ingeniería social)

- La **ingeniería social** ataca a las personas, no a las máquinas. Técnicas que caen en el examen:

| Técnica | Descripción |
|---|---|
| **Pretexting** | Inventar un escenario creíble para sacar información |
| **Phishing** | Correo masivo que suplanta a una entidad legítima |
| **Spear phishing** | Phishing dirigido a una persona concreta, con datos personalizados |
| **Vishing / Smishing** | Phishing por llamada de voz / por SMS |
| **Baiting** | Cebo físico o digital (un USB "olvidado") |
| **Quid pro quo** | Algo a cambio: "soporte técnico" a cambio de credenciales |
| **Tailgating** | Colarse detrás de alguien autorizado por una puerta |
| **Shoulder surfing** | Mirar por encima del hombro al teclear |
| **Dumpster diving** | Buscar información en la basura |
| **Typosquatting** | Dominios casi idénticos al legítimo (gooogle.com) |

- La defensa es formación y procedimiento: verificar identidades, no compartir credenciales nunca, desconfiar de la urgencia y reportar los intentos.

## 2.3 Cyber Attacks (Ciberataques)

- **DoS:** inundar un servicio para dejarlo inservible. **DDoS:** lo mismo desde miles de equipos infectados (**botnet** de **zombis**) a la vez.
- **Man in the middle (MitM):** el atacante se interpone en la comunicación y lee o modifica el tráfico; en el móvil, man in the mobile (MitMo). El ARP spoofing visto en cursos anteriores es un ejemplo.
- Ataques a contraseñas: **fuerza bruta** (probar todo), **diccionario** (palabras comunes) y **password spraying** (una contraseña típica contra muchas cuentas).
- **SEO poisoning:** posicionar webs maliciosas arriba en los buscadores.
- **Zero-day:** explota una vulnerabilidad aún sin parche; no hay defensa por firma posible.

## 2.4 Wireless and Mobile Device Attacks (Ataques inalámbricos y a móviles)

- **Rogue AP:** punto de acceso no autorizado conectado a la red.
- **Evil twin:** AP falso que clona el SSID legítimo para que las víctimas se conecten a él.
- **Interferencia / jamming de RF:** saturar las frecuencias para tumbar el servicio inalámbrico.
- Bluetooth: **bluejacking** (mensajes no solicitados) y **bluesnarfing** (robo de información).
- Protocolos débiles: **WEP** y **WPA** están rotos; el mínimo aceptable es WPA2 y lo recomendado WPA3.
- En móviles: apps de fuentes no oficiales, grayware y smishing.

## 2.5 Application Attacks (Ataques a aplicaciones)

- **XSS (cross-site scripting):** inyectar scripts en una web que se ejecutan en el navegador de otros usuarios.
- **Inyección de código:** colar comandos en campos de entrada; la clásica es la **inyección SQL** contra bases de datos.
- **Buffer overflow:** desbordar la memoria asignada para ejecutar código o tumbar la aplicación.
- **Ejecución remota de código (RCE):** el atacante ejecuta lo que quiere en el servidor.
- Correo: **spam** como vehículo de phishing y malware.
- Defensas: **validar todas las entradas** del usuario, mantener el software actualizado y aplicar los parches de seguridad en cuanto salen.

### Para el examen
- Virus necesita al usuario; el gusano se propaga solo; el troyano no se replica. Trío clásico.
- Phishing masivo, spear phishing dirigido, vishing por voz, smishing por SMS.
- DoS un origen, DDoS muchos (botnet). Zero-day = sin parche disponible.
- Evil twin clona el SSID; rogue AP es cualquier AP no autorizado.
- SQL injection y XSS se mitigan validando las entradas.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Network Security

**(Asegurar el acceso a la red)**

## 3.1 Security Foundations (Fundamentos de seguridad)

- La tríada **CIA**: confidencialidad (solo accede quien debe), integridad (los datos no se alteran), disponibilidad (el servicio funciona cuando se necesita).
- **Defensa en profundidad:** capas de protección superpuestas, de modo que si una falla, las demás aguantan. Principios asociados: capas, limitación (mínimo acceso necesario), diversidad (protecciones distintas entre capas), oscuridad (no regalar información) y simplicidad (lo complejo acaba mal configurado).
- **AAA:**

| A | Pregunta que responde |
|---|---|
| **Authentication** | ¿Quién eres? (credenciales) |
| **Authorization** | ¿Qué puedes hacer? (permisos) |
| **Accounting** | ¿Qué has hecho? (registro) |

- **MFA (autenticación multifactor):** combinar algo que sabes (contraseña), algo que tienes (token, móvil) y algo que eres (biometría).

## 3.2 Access Control (Control de acceso)

- Tipos de control: **físico** (cerraduras, tarjetas), **lógico** (contraseñas, firewalls, cifrado) y **administrativo** (políticas y procedimientos).
- Modelos de control de acceso:

| Modelo | Quién decide |
|---|---|
| **DAC (discrecional)** | El propietario del recurso reparte permisos |
| **MAC (obligatorio)** | El sistema, por niveles de clasificación; el más estricto |
| **RBAC (por roles)** | Los permisos van con el puesto, no con la persona |
| **Basado en reglas** | Condiciones definidas por el administrador (horarios, ubicaciones) |

- Principio de **mínimo privilegio**: cada usuario, solo los permisos imprescindibles para su trabajo.

## 3.3 Defending Systems and Devices (Defender sistemas y dispositivos)

- Endurecimiento (hardening) del host, la lista de tareas básica:
  - Sistema operativo y aplicaciones **actualizados y parcheados**; activar las actualizaciones automáticas.
  - **Firewall del host activado** y servicios innecesarios desactivados.
  - Contraseñas fuertes y distintas por servicio; **gestor de contraseñas** para no reutilizar.
  - **Cifrado** del disco (BitLocker, FileVault) y de las comunicaciones.
  - Bloqueo de sesión, protección física del equipo y copias de seguridad (regla 3-2-1).

## 3.4 Antimalware Protection (Protección antimalware)

- El antivirus/antimalware detecta por tres vías: **firmas** (patrones de malware conocido), **heurística** (características sospechosas) y **comportamiento** (acciones anómalas al ejecutar).
- Solo protege si se mantiene actualizado; contra un zero-day la firma no existe todavía.
- Cuidado con el **rogue antivirus**: ventanas emergentes que fingen detectar infecciones para colarte el malware real.
- En empresa, la protección del endpoint se gestiona de forma centralizada.

## 3.5 Firewalls and Host-Based Intrusion Prevention (Firewalls y prevención de intrusiones)

- El firewall aplica una política de control de acceso entre redes: todo el tráfico pasa por él.
- Tipos que hay que distinguir:

| Tipo | Cómo filtra |
|---|---|
| **Filtrado de paquetes** | Por IP y puerto, paquete a paquete, sin contexto |
| **Con estado (stateful)** | Recuerda las conexiones: entra solo lo que responde a algo que salió |
| **De aplicación (proxy)** | Entiende el protocolo (HTTP, FTP) y filtra por contenido |
| **De nueva generación (NGFW)** | Añade inspección profunda, IPS y conciencia de aplicación |

- En el host: firewall por software (Firewall de Windows, iptables en Linux) y **HIPS/HIDS**, que detectan y bloquean comportamiento intrusivo en el propio equipo.

## 3.6 Secure Wireless Access (Asegurar la red Wi-Fi)

- Lista de configuración segura de un router doméstico, en orden de importancia:
  1. Cambiar la **contraseña de administración** por defecto del router.
  2. Actualizar el **firmware**.
  3. Cifrado **WPA3** (o WPA2 como mínimo); nunca WEP ni abierto.
  4. Cambiar el **SSID** por defecto (delata el modelo del router) y la clave Wi-Fi.
  5. Desactivar **WPS** (vulnerable a fuerza bruta del PIN).
  6. **Red de invitados** separada para visitas y dispositivos IoT.
- **SSID cloaking** (ocultar el nombre de la red) y **filtrado MAC** existen y los pregunta el examen, pero son medidas débiles: el SSID se captura con un sniffer y las MAC se falsifican. Nunca sustituyen al cifrado fuerte.

### Para el examen
- CIA: confidencialidad, integridad, disponibilidad. AAA: autenticación, autorización, accounting.
- MFA = combinar factores distintos (saber, tener, ser); dos contraseñas no son MFA.
- Los 4 modelos de acceso: DAC propietario, MAC sistema, RBAC rol, reglas condiciones.
- Firewall stateful recuerda conexiones; el de paquetes no. NGFW = stateful + inspección profunda + IPS.
- Wi-Fi: WPA3 > WPA2 > (nunca) WEP. WPS desactivado. SSID cloaking y filtrado MAC no protegen por sí solos.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El examen final cubre los 3 módulos. Recomendaciones de repaso:

1. Vuelve a los apartados "Para el examen" de cada módulo.
2. De memoria: los 7 pasos del proceso de troubleshooting, la tabla de tipos de malware, las técnicas de ingeniería social, CIA y AAA, los 4 modelos de control de acceso y los tipos de firewall.
3. Repasa los escenarios: el examen plantea casos ("un usuario recibe un SMS de su banco...", "¿qué tipo de firewall...?") y pide clasificar el ataque o elegir la medida correcta.
4. Este curso cierra la serie: para el examen de certificación CCST Networking, repasa los cuatro manuales empezando por los anexos de palabras clave.

Con este curso termina el itinerario Network Technician de NetAcad. El siguiente paso recomendado por Cisco es **CCNA: Introduction to Networks**.

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1:** *seven-step troubleshooting process · define the problem · gather information · analyze · eliminate · hypothesis · test · solve and document · layered models · top-down · bottom-up · divide and conquer · follow-the-path · substitution · comparison · educated guess · network documentation · physical/logical topology diagram · baseline · security policy · SOP · guidelines · AUP · help desk · ticketing system · trouble ticket · escalation · open-ended/closed-ended questions · active listening · Event Viewer · Device Manager · Task Manager · `ipconfig /all` · `ip addr` · `networksetup` · `show ip interface brief` · `show ip route` · SSH · Telnet · RDP · remote desktop · VPN*

**Módulo 2:** *threat · vulnerability · attack · threat actor · script kiddie · hacktivist · cybercriminal · state-sponsored · white/grey/black hat · malware · virus · worm · trojan · ransomware · spyware · keylogger · adware · rootkit · backdoor · RAT · logic bomb · social engineering · pretexting · phishing · spear phishing · vishing · smishing · baiting · quid pro quo · tailgating · shoulder surfing · dumpster diving · typosquatting · DoS · DDoS · botnet · zombie · man in the middle (MitM) · brute force · dictionary attack · password spraying · SEO poisoning · zero-day · rogue AP · evil twin · RF jamming · bluejacking · bluesnarfing · WEP/WPA weakness · XSS · SQL injection · buffer overflow · remote code execution · spam · input validation*

**Módulo 3:** *CIA triad · confidentiality · integrity · availability · defense-in-depth · layering · limiting · diversity · obscurity · simplicity · AAA · authentication · authorization · accounting · MFA · physical/logical/administrative controls · DAC · MAC (mandatory) · RBAC · rule-based · least privilege · hardening · patching · host firewall · password manager · encryption · BitLocker/FileVault · antimalware · signature/heuristic/behavior-based · rogue antivirus · packet filtering firewall · stateful firewall · proxy firewall · NGFW · HIPS/HIDS · iptables · WPA2/WPA3 · WPS · guest network · SSID cloaking · MAC filtering*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **AAA** | Autenticación (quién eres), autorización (qué puedes hacer) y accounting (qué has hecho). |
| **Adware** | Malware que muestra publicidad no deseada; suele venir acompañando a otro software. |
| **AUP (política de uso aceptable)** | Documento que define qué comportamiento se permite en la red corporativa. |
| **Backdoor (puerta trasera)** | Acceso oculto a un sistema que se salta la autenticación normal. |
| **Baseline** | Medición de la red funcionando con normalidad; la referencia para detectar degradaciones. |
| **Botnet** | Red de equipos infectados (zombis) controlados por un atacante; el motor de los DDoS. |
| **Cifrado** | Transformación de los datos para que solo quien tiene la clave pueda leerlos; en disco y en tránsito. |
| **Control de acceso basado en roles (RBAC)** | Los permisos se asignan al puesto de trabajo, no a la persona. |
| **DDoS** | Denegación de servicio distribuida: el ataque DoS lanzado desde una botnet. |
| **Defensa en profundidad** | Estrategia de capas de seguridad superpuestas; si cae una, quedan las demás. |
| **DoS** | Ataque que satura un servicio para dejarlo inaccesible a los usuarios legítimos. |
| **Escalado (escalation)** | Pasar el ticket a un nivel superior cuando faltan conocimientos o permisos. |
| **Evil twin** | Punto de acceso falso que clona el SSID legítimo para capturar a las víctimas. |
| **Filtrado MAC** | Lista de MACs admitidas en el AP; medida débil, las MAC se falsifican. |
| **Firewall con estado (stateful)** | Firewall que recuerda las conexiones y solo deja entrar el tráfico de respuesta. |
| **Gusano (worm)** | Malware que se propaga solo por la red, sin intervención del usuario. |
| **HIPS** | Sistema de prevención de intrusiones del host: detecta y bloquea comportamiento malicioso en el equipo. |
| **Ingeniería social** | Manipular a las personas para obtener información o acceso; ataca al humano, no a la máquina. |
| **Inyección SQL** | Colar sentencias SQL en campos de entrada para manipular la base de datos. |
| **Malware** | Software malicioso en general: virus, gusanos, troyanos, ransomware y compañía. |
| **MFA (autenticación multifactor)** | Combinar factores distintos: algo que sabes, algo que tienes, algo que eres. |
| **Mínimo privilegio** | Dar a cada usuario solo los permisos imprescindibles para su trabajo. |
| **MitM (man in the middle)** | El atacante se interpone en la comunicación y lee o altera el tráfico. |
| **Phishing** | Suplantación por correo masivo para robar credenciales o colar malware. |
| **Pretexting** | Escenario inventado y creíble para sacar información a la víctima. |
| **Ransomware** | Malware que cifra los datos y exige un rescate por recuperarlos. |
| **RAT** | Troyano de acceso remoto: control persistente del equipo infectado. |
| **Rogue AP** | Punto de acceso no autorizado conectado a la red. |
| **Rootkit** | Malware que se oculta en el sistema con privilegios elevados; de los más difíciles de eliminar. |
| **Script kiddie** | Atacante sin conocimientos profundos que usa herramientas creadas por otros. |
| **Smishing** | Phishing por SMS. |
| **SOP** | Procedimiento operativo estándar: pasos definidos para cumplir una política en una tarea concreta. |
| **Spear phishing** | Phishing dirigido a una persona concreta con información personalizada. |
| **Spyware** | Malware que espía la actividad del usuario; incluye los keyloggers. |
| **SSID cloaking** | Ocultar el nombre de la red Wi-Fi; medida débil, un sniffer lo captura igual. |
| **Tailgating** | Colarse en una zona restringida siguiendo a alguien autorizado. |
| **Ticket (trouble ticket)** | Registro de un problema en el sistema del help desk: síntomas, pasos, solución. |
| **Troyano** | Malware disfrazado de software legítimo; no se replica, lo instala el propio usuario. |
| **Virus** | Malware que se adjunta a archivos legítimos y necesita que el usuario lo ejecute. |
| **Vishing** | Phishing por llamada de voz. |
| **VPN** | Túnel cifrado entre el equipo remoto y la red corporativa. |
| **WPA3** | Estándar actual de cifrado Wi-Fi; WPA2 es el mínimo aceptable y WEP está roto. |
| **XSS (cross-site scripting)** | Inyección de scripts en una web que se ejecutan en el navegador de otros usuarios. |
| **Zero-day** | Ataque que explota una vulnerabilidad sin parche disponible; las firmas no lo detectan. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Network Support and Security», cuarto y último curso de la serie alineada con el CCST Networking cursado desde Barcelona Activa. Material libre para compartir con la clase.*
