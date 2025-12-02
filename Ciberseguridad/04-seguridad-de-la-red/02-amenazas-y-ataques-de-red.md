# 🐛 4.2 - Amenazas y Ataques de Red

Comprender las herramientas y las tácticas del adversario es esencial para construir una defensa.

---

## 1. 🧠 SIEM: Más Allá de un Colector de Logs

Un **SIEM (Security Information and Event Management)** no es un simple repositorio de logs. Su verdadero valor está en generar **inteligencia accionable**.

* **Definición Práctica:** Es una "torre de control" que agrega datos de *todas* tus fuentes (firewalls, servidores, endpoints) y los **correlaciona** en tiempo real para encontrar patrones que un humano no vería.
* **Ejemplo:**
    * **Evento (Ruido):** Un log de firewall muestra un escaneo de puertos.
    * **Inteligencia (Señal):** El SIEM correlaciona ese escaneo con:
        1.  Un correo de phishing recibido por un usuario.
        2.  Ese usuario visitando un sitio web malicioso.
        3.  Intentos de enumeración de Active Directory desde la máquina de ese usuario.
    * **Acción:** El SIEM dispara una alerta de alta prioridad. El equipo de IR puede aislar esa máquina *antes* de la exfiltración de datos.

## 2. 💥 Amenazas del Mundo Real y Lecciones Aprendidas

### Nube: Brecha de Capital One

* **Vulnerabilidad:** Una **Falsificación de Solicitud del Lado del Servidor (SSRF)** en una aplicación web.
* **Mecánica del Ataque:** El atacante usó la aplicación vulnerable para "engañar" al servidor y hacerle una petición a sí mismo (al **Servicio de Metadatos de la Instancia - IMDS**).
* **Resultado:** El atacante robó credenciales temporales del IMDS y las usó para exfiltrar datos de buckets S3.
* **Lección:** La seguridad en la nube depende de la **gestión de permisos (IAM)** y la configuración segura de aplicaciones.

### Cadena de Suministro: SolarWinds / Sunburst

* **Vector:** Los atacantes comprometieron el **servidor de compilación** de SolarWinds.
* **Técnica:** Inyectaron su malware *después* de la compilación pero *antes* de que el software fuera firmado digitalmente.
* **Resultado:** Miles de clientes descargaron una actualización *legítima y firmada* que contenía un *backdoor*.
* **Lección:** No puedes confiar ciegamente en el software de terceros. La segmentación de red y el *threat hunting* son cruciales.

### Segmentación: Incidente de TJ Maxx

* **Vector:** Una red Wi-Fi insegura (WEP) en una tienda.
* **Fallo Clave:** **Falta de segmentación de red.** El atacante pudo "pivotar" desde la red Wi-Fi de la tienda hasta la red corporativa que procesaba tarjetas de crédito.
* **Consecuencia:** Robo de ~94 millones de tarjetas.
* **Impacto en la Industria:** Fue un catalizador para la adopción estricta del **Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS)**.
* **Lección (PCI DSS):** Un pilar de PCI es la **segmentación** para reducir el *alcance*. La red de tarjetas debe estar *totalmente aislada* del resto.

---

## 3. 🎯 Ofensiva Informada: Definiendo las Tácticas

* **🕵️‍♂️ Threat Hunting (Caza de Amenazas):**
    * **Mentalidad:** "Ya estamos comprometidos. ¿Cómo los encontramos?" (Asume la brecha).
    * **Acción:** Búsqueda *proactiva* de Indicadores de Compromiso (IoCs) o Tácticas (TTPs) *dentro* de tu red.
* **🎯 Pruebas de Penetración (Pentesting):**
    * **Mentalidad:** "¿*Podemos* entrar? ¿Qué tan lejos podemos llegar?"
    * **Acción:** Un ataque *simulado* y *autorizado* para encontrar y explotar vulnerabilidades.
* **📋 Análisis de Vulnerabilidades (Scanning):**
    * **Mentalidad:** "¿Qué *vulnerabilidades conocidas* tenemos?"
    * **Acción:** Un escaneo (generalmente automatizado) que compara sistemas con una base de datos de CVEs.

---

## 4. 🐛 El Bestiario: Léxico de Amenazas

| **Amenaza** | **Definición Práctica** | **Ejemplo Práctico** |
| :--- | :--- | :--- |
| **Suplantación (Spoofing)** | Falsificar una identidad (IP, MAC, email) para parecer una fuente confiable. | Un email que *parece* venir de `soporte@tuempresa.com`. |
| **Phishing** | Un ataque de ingeniería social (email) para engañar al usuario y hacer que revele información. | Un email de "Netflix" que dice "Tu pago fue rechazado" y te lleva a una página falsa. |
| **DoS / DDoS** | **Denegación de Servicio (Distribuida).** Inundar un sistema con tráfico para que los usuarios legítimos no puedan acceder. | Una *botnet* de dispositivos IoT inundando un sitio web. |
| **Virus** | Código malicioso que se adjunta a un programa legítimo y requiere *intervención humana* para propagarse. | Abres un `factura.exe` adjunto. |
| **Gusano (Worm)** | **Autorreplicante.** Se propaga *sin* intervención humana, explotando vulnerabilidades de red. | *WannaCry* escaneaba la red en busca de sistemas vulnerables a EternalBlue. |
| **Troyano (Trojan)** | Software que se disfraza de algo útil (un juego, un "limpiador") pero contiene una carga maliciosa. | Un "crack" para Photoshop que instala un *keylogger*. |
| **Ataque en Ruta (MitM)** | **Man-in-the-Middle.** El atacante se sitúa *entre* dos partes e intercepta la comunicación. | Conectarse a un "Wi-Fi Gratis" falso en un aeropuerto. |
| **APT** | **Amenaza Persistente Avanzada.** Un actor (a menudo estado-nación) con alta sofisticación y paciencia para el espionaje a largo plazo. | El grupo de *SolarWinds* (APT29). |
| **Amenaza Interna (Insider)** | Una amenaza que proviene de dentro (empleado, contratista). Puede ser maliciosa o accidental. | *Maliciosa:* Un empleado descontento roba la BBDD de clientes. *Accidental:* Un empleado cae en phishing. |
| **Ransomware** | Malware que **cifra** los archivos de la víctima y exige un pago (rescate) por la clave. | Un adjunto malicioso cifra todos los archivos del servidor compartido. |

---

## 5. 🛡️ El Escudo: Herramientas de Detección y Prevención

La seguridad se logra mediante una **defensa en profundidad**.

### Detección y Monitoreo

* **IDS (Sistema de Detección de Intrusos):** 🚨 Es la "alarma de humo". Detecta y alerta, pero *no* detiene.
    * **HIDS (Basado en Host):** Se instala en un *endpoint* (Wazuh, OSSEC).
    * **NIDS (Basado en Red):** Analiza el *tráfico* de red (Snort, Suricata).
* **SIEM (Gestión de Eventos e Info. de Seguridad):** 🧠 La "torre de control". Ingiere logs de *todas* las herramientas (HIDS, NIDS, Firewalls) para correlacionar eventos.

### Prevención y Protección

* **IPS (Sistema de Prevención de Intrusos):** ⛔️ Es un "guardia armado". Es un IDS que puede *bloquear* activamente el tráfico malicioso.
* **Firewall:** 🧱 El "control fronterizo". Filtra el tráfico basándose en reglas (puertos, IPs).
    * **NGFW (Firewall de Próxima Generación):** Más inteligente. Inspecciona el contenido (Capa 7) y entiende de *aplicaciones*.
* **Anti-malware / Antivirus:** 🔬 El "médico" del endpoint. Escanea archivos en busca de *firmas* conocidas o *comportamientos* sospechosos.

### La Filosofía de Volver a lo Básico

La tecnología avanzada es inútil si no dominas los fundamentos:

1.  **Inventario de Activos:** No puedes proteger lo que no sabes que tienes.
2.  **Gestión de Parches:** La mayoría de las brechas explotan vulnerabilidades *ya conocidas*.
3.  **Reducir la Superficie de Ataque:** Deshabilita servicios innecesarios.
4.  **Segmentación de Red:** (Lección de TJ Maxx). Aísla las redes críticas.
5.  **Logs y Monitoreo:** (Lección de SIEM). Asegúrate de que *alguien* esté revisando las alertas.
6.  **Copias de Seguridad (Backups):** Tu mejor defensa contra el ransomware. Asegúrate de que estén *offline* y pruébalas.
