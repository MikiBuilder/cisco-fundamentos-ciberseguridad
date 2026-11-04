[← Volver a la página principal del repositorio](../../README.md)

# Introduction to Cybersecurity

> **Objetivo del curso:** entender qué es la ciberseguridad y por qué importa: el valor de los datos personales y corporativos, cómo operan los atacantes y sus técnicas, cómo proteger tus dispositivos y tu privacidad, cómo se defienden las organizaciones y qué salidas profesionales ofrece el sector. Primer curso del itinerario CCST Cybersecurity.

**Estado de estos apuntes:** curso completo. Cubren los 5 módulos y el examen final (6 horas, 7 labs).

---

## Índice

- [Cómo usar este manual](#cómo-usar-este-manual)
- [Módulo 1 — Introduction to Cybersecurity](#módulo-1--introduction-to-cybersecurity)
- [Módulo 2 — Attacks, Concepts and Techniques](#módulo-2--attacks-concepts-and-techniques)
- [Módulo 3 — Protecting Your Data and Privacy](#módulo-3--protecting-your-data-and-privacy)
- [Módulo 4 — Protecting the Organization](#módulo-4--protecting-the-organization)
- [Módulo 5 — Will Your Future Be in Cybersecurity?](#módulo-5--will-your-future-be-in-cybersecurity)
- [Examen final del curso](#examen-final-del-curso)
- [Anexo: palabras clave por módulo](#anexo-palabras-clave-por-módulo)
- [Glosario de términos](#glosario-de-términos)

---

## Cómo usar este manual

1. Antes de cada sesión, lee el resumen del módulo correspondiente.
2. Después de cada sesión, repasa las palabras clave del [anexo](#anexo-palabras-clave-por-módulo). En los exámenes aparecen normalmente en inglés.
3. Los apartados "Para el examen" recogen los datos que más se preguntan.
4. Varios temas (malware, ingeniería social, firewalls) se tratan con más profundidad en el [manual de Network Support and Security](../ccst-networking/network-support-and-security.md): los dos manuales se complementan.

---

# MÓDULO 1 — Introduction to Cybersecurity

**(El mundo de la ciberseguridad y el valor de los datos)**

## 1.1 The World of Cybersecurity (Qué es la ciberseguridad)

- La ciberseguridad es el esfuerzo continuo por proteger sistemas, redes y datos del uso no autorizado o malicioso.
- Tu **identidad en línea** (quién eres en internet: usuarios, perfiles, hábitos) vale dinero, y tus datos existen en muchos sitios que no controlas: historiales médicos, registros académicos, datos bancarios y laborales.
- Los dispositivos inteligentes y wearables añaden más fuentes: ubicación, salud, rutinas.

## 1.2 Organizational Data (Los datos de la organización)

- Tipos de datos corporativos:
  - **Tradicionales:** de personal (nóminas, contratos), **propiedad intelectual** (patentes, secretos comerciales, planes de producto) y financieros (balances, cuentas de resultados).
  - **IoT y Big Data:** la red de sensores y objetos conectados genera volúmenes enormes de datos que también hay que proteger.
- La tríada **CIA** resume lo que se protege: **confidencialidad** (privacidad), **integridad** (exactitud y confianza en los datos) y **disponibilidad** (acceso cuando se necesita).
- Una brecha de seguridad cuesta dinero, reputación, clientes y propiedad intelectual; y una vez robados los datos, no hay vuelta atrás.

## 1.3 Cyber Attackers (Los atacantes)

| Atacante | Perfil |
|---|---|
| **Aficionados (script kiddies)** | Poca habilidad; usan herramientas de otros |
| **Sombrero blanco** | Hackea con permiso para encontrar fallos y reportarlos |
| **Sombrero gris** | Sin permiso, pero sin ánimo de daño; a veces publica el fallo |
| **Sombrero negro** | Explota los fallos en beneficio propio |
| **Cibercriminales organizados** | Grupos profesionales motivados por dinero |
| **Hacktivistas** | Atacan por motivos políticos o ideológicos |
| **Patrocinados por estados** | Espionaje y sabotaje con grandes recursos |

- **Amenaza interna vs externa:** los empleados (por error o malicia) causan gran parte de los incidentes y tienen acceso privilegiado al edificio, los equipos y la red.

## 1.4 Cyberwarfare (Ciberguerra)

- La ciberguerra es el uso de ataques informáticos por estados para dañar o espiar a otros países: puede sabotear infraestructuras (red eléctrica, agua, transporte) sin un solo disparo.
- El ejemplo clásico es **Stuxnet**: malware diseñado para dañar físicamente las centrifugadoras del programa nuclear iraní, propagado incluso por USB.
- Objetivos típicos: robar secretos de defensa e industria, presionar a gobiernos y desestabilizar servicios esenciales.

### Para el examen
- CIA: confidencialidad, integridad, disponibilidad, y qué protege cada una.
- Sombrero blanco con permiso, gris sin permiso y sin daño, negro malicioso.
- La amenaza interna es tan peligrosa como la externa: acceso y confianza ya concedidos.
- Stuxnet = ciberguerra con daño físico.

[⬆ Volver al índice](#índice)

---

# MÓDULO 2 — Attacks, Concepts and Techniques

**(Cómo operan los ataques)**

## 2.1 Analyzing a Cyber Attack (Tipos de malware)

- Repaso de los tipos de malware y su comportamiento:

| Malware | Comportamiento |
|---|---|
| **Virus** | Se adjunta a archivos y necesita ejecución del usuario |
| **Gusano** | Se replica solo a través de la red |
| **Troyano** | Se disfraza de software legítimo |
| **Ransomware** | Cifra los datos y exige rescate |
| **Spyware** | Espía actividad, teclas y credenciales |
| **Adware** | Publicidad no deseada |
| **Scareware** | Asusta con falsas alertas para que instales o pagues |
| **Rootkit** | Se oculta con privilegios y modifica el sistema |
| **Backdoor** | Acceso que se salta la autenticación |

- Síntomas de infección: lentitud repentina, ventanas emergentes, archivos modificados o desaparecidos, programas desconocidos, tráfico de red inexplicable.

## 2.2 Methods of Infiltration (Métodos de infiltración)

- **Ingeniería social:** pretexting (escenario inventado), **tailgating** (colarse detrás de alguien) y **quid pro quo** (algo a cambio de algo).
- **DoS y DDoS:** saturar un servicio hasta tumbarlo; el DDoS usa una **botnet** de equipos zombi.
- **Ataque on-path (man in the middle):** interceptar la comunicación entre dos partes; en móviles, man in the mobile.
- **SEO poisoning:** posicionar páginas maliciosas en los primeros resultados del buscador.
- **Descifrado de contraseñas Wi-Fi** y ataques a contraseñas: fuerza bruta, diccionario y **password spraying** (una clave común contra muchas cuentas).
- **APT (amenaza persistente avanzada):** campaña sigilosa, prolongada y con recursos, dirigida a un objetivo concreto; típica de grupos patrocinados por estados.

## 2.3 Security Vulnerability and Exploits (Vulnerabilidades y exploits)

- Una **vulnerabilidad** es un defecto que puede aprovecharse; un **exploit** es el programa que la aprovecha; un **ataque** es el uso del exploit.
- Vulnerabilidades de **hardware** (fallos de diseño, como los de CPU) y de **software**. Las categorías de software que hay que reconocer:

| Categoría | Descripción |
|---|---|
| **Buffer overflow** | Escribir fuera de la memoria asignada para colar código |
| **Entrada no validada** | Datos del usuario que el programa se traga sin comprobar |
| **Condiciones de carrera** | Resultados que dependen del orden de eventos manipulable |
| **Debilidades en prácticas de seguridad** | Cifrados caseros, credenciales en el código |
| **Problemas de control de acceso** | Permisos mal puestos, recursos sin proteger |

- **Zero-day:** vulnerabilidad explotada antes de que exista parche.
- La defensa número uno: **mantener el software actualizado**.

## 2.4 The Cybersecurity Landscape (El panorama de amenazas)

- **Ataque combinado (blended attack):** mezcla varias técnicas a la vez (gusano + troyano + spam + phishing) para maximizar el daño; ejemplos históricos: Nimda, CodeRed, Klez.
- **Reducción del impacto** tras una brecha: comunicar el problema con honestidad, entender la causa, limpiar todos los sistemas, tomar medidas para que no se repita y formar a empleados, socios y clientes.

### Para el examen
- Vulnerabilidad (el fallo) ≠ exploit (el programa que lo aprovecha) ≠ ataque (su uso).
- Las 5 categorías de vulnerabilidad de software, especialmente buffer overflow y entrada no validada.
- Scareware = miedo con falsas alertas. APT = ataque sigiloso y prolongado.
- Blended attack = varias técnicas combinadas.
- En la reducción de impacto: transparencia, causa raíz, sistemas limpios y formación.

[⬆ Volver al índice](#índice)

---

# MÓDULO 3 — Protecting Your Data and Privacy

**(Protege tus dispositivos y tu privacidad)**

## 3.1 Protecting Your Devices and Network (Proteger dispositivos y red)

- Lista básica en todos tus equipos:
  - **Firewall activado** y actualizado.
  - **Antivirus y antispyware** al día; descargar software solo de sitios de confianza.
  - **Sistema operativo y navegador actualizados**.
  - Proteger **todos** los dispositivos: también móviles, tablets y los IoT de casa.
- Wi-Fi doméstica: cambiar SSID y contraseñas por defecto, cifrado WPA2/WPA3 y firmware al día. En redes Wi-Fi públicas, nada sensible sin **VPN**.
- Contraseñas: únicas por servicio, largas, sin datos personales. Mejor aún, **frases de contraseña** (passphrases) largas y fáciles de recordar, y un **gestor de contraseñas** para no repetir.

## 3.2 Data Maintenance (Mantenimiento de los datos)

- **Cifrado:** convierte la información en ilegible sin la clave; protege los archivos aunque roben el equipo (EFS en Windows, BitLocker, FileVault).
- **Copias de seguridad:** en ubicación distinta al original; combinación de copia local (disco externo, NAS) y en la nube, automática y periódica.
- **Borrado definitivo:** vaciar la papelera no borra nada; hace falta borrado seguro por software (varias pasadas) o destrucción física del disco para que los datos no se recuperen.

## 3.3 Who Owns Your Data? (¿De quién son tus datos?)

- Al aceptar los **términos de servicio** de una app o red social, a menudo cedes derechos de uso sobre lo que subes y autorizas la recogida de datos.
- Antes de registrarte: leer qué datos recogen, con quién los comparten y qué pasa con tu cuenta al darte de baja.

## 3.4 Safeguarding Your Online Privacy (Proteger tu privacidad)

- **Autenticación de dos factores (2FA):** añade a la contraseña un segundo factor (código del móvil, llave física, biometría). Actívala en correo, banca y redes sociales.
- **OAuth:** permite entrar en una web con tu cuenta de Google o similar sin darle tu contraseña; cómodo, pero conecta servicios entre sí.
- Hábitos de riesgo que conviene abandonar: compartir de más en redes sociales (ubicación, rutinas, vacaciones), usar la misma contraseña en todo, conectarse a Wi-Fi abiertas para gestiones sensibles y guardar contraseñas en el navegador de equipos compartidos.
- El modo privado del navegador no te hace anónimo: solo evita el rastro local (historial, cookies); tu operador y las webs siguen viéndote.

### Para el examen
- Passphrase larga > contraseña compleja corta. Gestor de contraseñas para no reutilizar.
- El cifrado protege la confidencialidad; la copia de seguridad, la disponibilidad.
- Borrar ≠ destruir: hace falta borrado seguro o destrucción física.
- 2FA = contraseña + otro factor de distinta categoría.
- El modo incógnito no anonimiza: solo limpia el rastro local.

[⬆ Volver al índice](#índice)

---

# MÓDULO 4 — Protecting the Organization

**(Cómo se defiende una organización)**

## 4.1 Cybersecurity Devices and Technologies (Dispositivos y tecnologías)

- Ningún aparato lo resuelve todo: la defensa combina capas de equipos y software.
- Tipos de **firewall** que distingue el curso:

| Tipo | Qué filtra |
|---|---|
| **De capa de red** | IPs de origen y destino |
| **De capa de transporte** | Puertos y estados de conexión |
| **De capa de aplicación** | Aplicaciones, programas y servicios concretos |
| **Proxy** | Peticiones web en nombre de los clientes |
| **Proxy inverso** | Protege los servidores recibiendo las peticiones por ellos |
| **NAT** | Oculta las direcciones internas de la red |
| **Basado en host** | Protege el equipo individual donde se instala |

- **Escaneo de puertos** (nmap): descubre qué servicios expone una máquina. Respuestas posibles de un puerto: **abierto, cerrado o filtrado**. Los atacantes lo usan para reconocimiento; los administradores, para auditar.
- Otros equipos de seguridad: **IDS** (detecta y alerta, trabaja sobre copias del tráfico) e **IPS** (detecta y bloquea en línea), VPNs y antimalware centralizado.

## 4.2 Behavior Approach to Cybersecurity (Enfoque basado en comportamiento)

- La detección por firmas no basta: el enfoque de comportamiento busca anomalías en la actividad.
  - **Honeypot:** señuelo que imita un sistema vulnerable para atraer, observar y estudiar a los atacantes sin exponer nada real.
  - **NetFlow:** registra quién habla con quién en la red y cuánto; la base para establecer el comportamiento normal y detectar desviaciones.
- **Kill chain** (cadena de un ciberataque), los 7 pasos en orden:
  1. Reconocimiento
  2. Armamento (weaponization)
  3. Entrega (delivery)
  4. Explotación
  5. Instalación
  6. Mando y control (C2)
  7. Acción sobre el objetivo
- Cuanto antes se corte la cadena, menor el daño.

## 4.3 Cisco's Approach to Cybersecurity (El enfoque corporativo)

- **CSIRT:** el equipo de respuesta a incidentes de seguridad: previene, investiga y coordina la respuesta.
- **Playbook de seguridad:** colección de consultas e informes repetibles sobre los eventos de seguridad: qué mirar, cómo detectar y cómo responder a cada tipo de incidente.
- Herramientas habituales del arsenal: SIEM (correlación de eventos y alertas), **DLP** (evita fugas de información), sistemas de control de acceso a la red y la inteligencia de amenazas (como Cisco Talos) que actualiza las defensas en tiempo real.

### Para el examen
- IDS detecta y avisa; IPS detecta y bloquea. La pareja cae seguro.
- Honeypot = señuelo para estudiar al atacante. NetFlow = registro de flujos para detectar anomalías.
- Los 7 pasos de la kill chain en orden.
- Escaneo de puertos: abierto, cerrado o filtrado.
- CSIRT responde a incidentes; el playbook documenta cómo detectar y responder.

[⬆ Volver al índice](#índice)

---

# MÓDULO 5 — Will Your Future Be in Cybersecurity?

**(Cuestiones legales y carrera profesional)**

## 5.1 Legal and Ethical Issues (Cuestiones legales y éticas)

- **Legal personal:** lo que haces en la red deja rastro; acceder a sistemas ajenos sin permiso es delito aunque no haya daño.
- **Legal corporativo:** las empresas deben cumplir las leyes de protección de datos (en Europa, el RGPD) y notificar las brechas; el incumplimiento acarrea multas.
- **Ética:** que algo sea técnicamente posible o incluso legal no lo hace correcto. Ante la duda, el criterio es no hacer a otros lo que no querrías para tus datos.
- Los sombreros blancos trabajan siempre con autorización escrita y dentro del alcance pactado.

## 5.2 Education and Careers (Formación y carrera)

- La demanda de profesionales de ciberseguridad supera con mucho la oferta: es uno de los campos con más futuro de IT.
- Puestos de entrada típicos: analista de SOC, técnico de soporte de seguridad, analista junior de ciberseguridad.
- Certificaciones de entrada: **CCST Cybersecurity** (la meta de este itinerario), CompTIA Security+, y después CyberOps Associate y otras.
- Cómo ganar experiencia: labs y plataformas de práctica, CTFs (capture the flag), prácticas en empresa y comunidades.

### Para el examen
- Acceder sin autorización es ilegal, haya o no daño.
- Las empresas tienen obligación legal de proteger los datos y notificar las brechas.
- El hacking ético exige permiso previo y por escrito.

[⬆ Volver al índice](#índice)

---

# Examen final del curso

El examen final cubre los 5 módulos. Recomendaciones de repaso:

1. Vuelve a los apartados "Para el examen" de cada módulo.
2. De memoria: la tríada CIA, los tipos de atacante (sombreros incluidos), la tabla de malware, las 5 categorías de vulnerabilidad de software, los tipos de firewall, IDS vs IPS y los 7 pasos de la kill chain.
3. El examen es de escenarios cortos: clasificar el ataque descrito o elegir la protección adecuada. Practica asociando cada técnica con su nombre en inglés.
4. Si vienes de la serie CCST Networking, los módulos 2 y 4 te resultarán repaso: céntrate en lo nuevo (scareware, APT, blended attack, honeypot, NetFlow, kill chain, playbook).

El siguiente curso del itinerario CCST Cybersecurity pendiente de cursar es **Endpoint Security** (los cursos 2 y 3, Networking Basics y Networking Devices, ya están completados en la serie Networking).

[⬆ Volver al índice](#índice)

---

# Anexo: palabras clave por módulo

**Módulo 1:** *cybersecurity · online identity · personal data · organizational data · intellectual property · IoT · Big Data · CIA triad · confidentiality · integrity · availability · data breach · script kiddie · white/grey/black hat · hacktivist · state-sponsored · internal/external threat · cyberwarfare · Stuxnet*

**Módulo 2:** *malware · virus · worm · trojan · ransomware · spyware · adware · scareware · rootkit · backdoor · social engineering · pretexting · tailgating · quid pro quo · DoS · DDoS · botnet · zombie · on-path attack (MitM) · SEO poisoning · brute force · dictionary attack · password spraying · APT (advanced persistent threat) · vulnerability · exploit · buffer overflow · non-validated input · race conditions · access control problems · zero-day · blended attack · impact reduction*

**Módulo 3:** *firewall · antivirus · antispyware · software updates · WPA2/WPA3 · public Wi-Fi · VPN · strong password · passphrase · password manager · encryption · EFS/BitLocker/FileVault · backup · local/cloud backup · secure erase · terms of service · data ownership · two-factor authentication (2FA) · OAuth · private browsing · oversharing*

**Módulo 4:** *security appliances · network/transport/application layer firewall · proxy · reverse proxy · NAT firewall · host-based firewall · port scanning · nmap · open/closed/filtered · IDS · IPS · behavior-based security · honeypot · NetFlow · kill chain (reconnaissance, weaponization, delivery, exploitation, installation, command and control, action on objectives) · CSIRT · security playbook · SIEM · DLP · threat intelligence · Cisco Talos*

**Módulo 5:** *legal issues · GDPR/RGPD · data breach notification · ethics · written authorization · security analyst · SOC · CCST Cybersecurity · CompTIA Security+ · CyberOps Associate · CTF (capture the flag)*

[⬆ Volver al índice](#índice)

---

# Glosario de términos

| Término | Definición |
|---|---|
| **Amenaza interna** | La que procede de empleados o colaboradores, por error o malicia; parte con acceso y confianza ya concedidos. |
| **APT (amenaza persistente avanzada)** | Campaña de ataque sigilosa y prolongada contra un objetivo concreto, con grandes recursos detrás. |
| **Ataque combinado (blended attack)** | El que mezcla varias técnicas a la vez (gusano, troyano, phishing, spam) para maximizar el daño. |
| **Autenticación de dos factores (2FA)** | Contraseña más un segundo factor de otra categoría: código del móvil, llave física o biometría. |
| **Big Data** | Volúmenes masivos de datos, en gran parte generados por el IoT, cuyo almacenamiento y análisis hay que proteger. |
| **Botnet** | Red de equipos infectados (zombis) a las órdenes de un atacante; el motor de los DDoS. |
| **Buffer overflow** | Escribir más allá de la memoria asignada para corromper el programa o ejecutar código. |
| **Ciberguerra** | Uso de ataques informáticos entre estados para espiar, sabotear o desestabilizar; Stuxnet es el ejemplo clásico. |
| **Cifrado** | Transformación de los datos en ilegibles sin la clave; protege la confidencialidad en disco y en tránsito. |
| **CSIRT** | Equipo de respuesta a incidentes de seguridad: previene, investiga y coordina la reacción. |
| **DLP** | Prevención de pérdida de datos: vigila que la información sensible no salga de la organización. |
| **Escaneo de puertos** | Sondeo de los servicios expuestos de una máquina; cada puerto responde abierto, cerrado o filtrado. |
| **Exploit** | Programa escrito para aprovechar una vulnerabilidad conocida. |
| **Firewall** | Sistema que aplica una política de control de acceso entre redes; existe en variantes de red, transporte, aplicación, proxy y host. |
| **Gestor de contraseñas** | Aplicación que genera y guarda contraseñas únicas por servicio, cifradas tras una clave maestra. |
| **Hacktivista** | Atacante movido por motivos políticos o ideológicos. |
| **Honeypot** | Sistema señuelo que imita un objetivo vulnerable para atraer y estudiar a los atacantes. |
| **Identidad en línea** | Quién eres en internet: cuentas, perfiles y hábitos; un activo que los atacantes quieren suplantar. |
| **IDS** | Sistema de detección de intrusiones: analiza copias del tráfico y alerta, pero no bloquea. |
| **IoT** | Internet de las cosas: la red de sensores y objetos conectados, gran fuente de datos y de superficie de ataque. |
| **IPS** | Sistema de prevención de intrusiones: analiza el tráfico en línea y bloquea lo malicioso al momento. |
| **Kill chain** | Los 7 pasos de un ciberataque: reconocimiento, armamento, entrega, explotación, instalación, mando y control, y acción sobre el objetivo. |
| **NetFlow** | Tecnología que registra los flujos de la red (quién habla con quién y cuánto) para establecer el comportamiento normal y detectar anomalías. |
| **OAuth** | Estándar que permite iniciar sesión en un servicio con la cuenta de otro sin entregarle la contraseña. |
| **Passphrase (frase de contraseña)** | Frase larga usada como contraseña: más segura y fácil de recordar que una clave corta compleja. |
| **Playbook de seguridad** | Colección de consultas e informes repetibles que documentan cómo detectar y responder a cada tipo de incidente. |
| **Ransomware** | Malware que cifra los datos y exige rescate; la mejor defensa son las copias de seguridad. |
| **Scareware** | Malware que asusta con falsas alertas de infección para que la víctima instale o pague algo. |
| **SEO poisoning** | Manipular el posicionamiento en buscadores para colocar webs maliciosas en los primeros resultados. |
| **Sombrero blanco, gris y negro** | Hacker con permiso y fines legítimos; sin permiso pero sin ánimo de daño; y malicioso, respectivamente. |
| **Stuxnet** | Malware de ciberguerra que dañó físicamente centrifugadoras nucleares iraníes; se propagó incluso por USB. |
| **VPN** | Túnel cifrado que protege el tráfico, imprescindible en redes Wi-Fi públicas. |
| **Vulnerabilidad** | Defecto de hardware o software que un exploit puede aprovechar. |
| **Zero-day** | Vulnerabilidad explotada antes de que exista parche; las firmas no la detectan. |

[⬆ Volver al índice](#índice)

---

*Manual de repaso del curso Cisco NetAcad «Introduction to Cybersecurity», primer curso del itinerario alineado con el CCST Cybersecurity cursado desde Barcelona Activa. Material libre para compartir con la clase.*
