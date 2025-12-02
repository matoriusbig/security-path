# 🏛️ 4.3 - Infraestructura y Arquitectura de Red Segura

Aquí diseñamos el "blindaje": la arquitectura que previene que los ataques (del archivo 4.2) tengan éxito.

---

## 1. Infraestructura Física: El Centro de Datos On-Premises

Cuando operas tu propio centro de datos, asumes la responsabilidad total.

* **💨 HVAC (Calefacción, Ventilación y Aire Acondicionado):**
    * Vital para prevenir el sobrecalentamiento.
    * Estándar: **18°C - 27°C** (64°F - 81°F).
    * Un fallo de HVAC puede causar pérdida de disponibilidad o daños permanentes.
* **⚡ Energía:**
    * **Suministro Ininterrumpido (UPS):** Baterías de respaldo para soportar la carga crítica hasta que arranquen los generadores.
    * **Generadores de Respaldo:** Suministran energía a largo plazo.
* **🔥 Sistemas contra Incendios:**
    * Desafío: El agua destruye los equipos electrónicos.
    * **Solución (Sistemas de Tubería Seca):** Las tuberías sobre el data center están vacías y solo se llenan de agua cuando un sensor detecta *activamente* un incendio.
* **🔄 Redundancia:**
    * Diseñar sistemas sin un **punto único de fallo (SPOF)**.
    * **Ejemplo:** Un servidor con dos fuentes de alimentación, cada una conectada a un UPS diferente, cada UPS en una red eléctrica distinta, respaldada por generadores redundantes.

<img width="791" height="713" alt="Diagrama de Redundancia de Energía" src="https://github.com/user-attachments/assets/f7218c39-6672-4826-80cf-d46c7d3708fa" />

---

## 2. Acuerdos y Proveedores

* **🤝 MOU (Memorando de Entendimiento) vs. SLA (Acuerdo de Nivel de Servicio):**
    * **MOU:** Un acuerdo (a menudo no vinculante) de cooperación, generalmente para BC/DR.
        * *Ejemplo:* El Hospital A y el Hospital B (competidores) acuerdan ayudarse mutuamente si uno sufre un desastre.
    * **SLA:** Un **contrato legalmente vinculante** que define métricas de servicio (disponibilidad, rendimiento, penalizaciones).
        * *Ejemplo:* "99.99% de tiempo de actividad" y "soporte 24/7/365".
* **👨‍💼 Proveedor de Servicios Gestionados (MSP):**
    * Una empresa externa que gestiona proactivamente tu TI (ej. Help Desk, gestión de nóminas, o incluso seguridad como un **MDR**).

---

## 3. ☁️ Computación en la Nube (Cloud Computing)

Un modelo de entrega de servicios de TI basado en el **NIST SP 800-145**.

* **Características Esenciales:** Servicio Medido (pagas por uso), Elasticidad Rápida, Agrupación de Recursos.

<img width="929" height="564" alt="Modelos de Servicio en la Nube" src="https://github.com/user-attachments/assets/bbc22ddb-35a5-4b51-acff-e3d837b0bf25" />

### 📦 Modelos de Servicio (Matriz de Responsabilidad)

| **Modelo** | **Tú Gestionas** | **Proveedor Gestiona** | **Ejemplo** |
| :--- | :--- | :--- | :--- |
| **SaaS** (Software) | Tus Datos, Acceso | **TODO:** Aplicación, OS, Hardware. | **Gmail, Salesforce** |
| **PaaS** (Plataforma) | Tus Aplicaciones, Tus Datos | OS, Middleware, Hardware. | **Heroku, AWS Beanstalk** |
| **IaaS** (Infra.) | Aplicaciones, Datos, OS | **Solo lo básico:** Servidores, Almacenamiento. | **AWS EC2, Google Compute** |

### 🌐 Modelos de Implementación

* **Pública:** Alojada por un CSP (AWS, Azure) y vendida al público (multitenancy).
* **Privada:** Infraestructura dedicada exclusivamente a una sola organización.
* **Híbrida:** Combinación de nube pública y privada orquestadas para trabajar juntas.
* **Comunitaria:** Compartida por varias organizaciones con intereses comunes (ej. una nube para el sector financiero).

---

## 4. 📐 Diseño y Arquitectura de Red Segura

### 🏰 Defensa en Profundidad (Defense in Depth)

La filosofía de seguridad fundamental: **la seguridad debe ser en capas**. Si un atacante supera una capa, debe encontrarse con otra.

* **Analogía del Castillo:** Un castillo tiene un foso, un muro, guardias en el muro y una bóveda cerrada.
* **Capas en Ciberseguridad:**
    1.  Políticas y Concienciación
    2.  Físico (Cerraduras)
    3.  Perímetro (Firewall)
    4.  Red Interna (Segmentación, IDS)
    5.  Host (Antivirus, Parches)
    6.  Aplicación (WAF)
    7.  Datos (Cifrado, IAM)

<img width="932" height="701" alt="Capas de Defensa en Profundidad" src="https://github.com/user-attachments/assets/2268e6c6-bb96-4024-949d-b765fb09bf6d" />

### ⛔ Confianza Cero (Zero Trust)

Una evolución de la Defensa en Profundidad.

* **Filosofía Central:** "Nunca confíes, siempre verifica".
* **Suposición:** Asume que la red *ya está comprometida*.
* **Enfoque:** La seguridad se basa en la *identidad* (quién eres), no en el *perímetro* (dónde estás). Se requiere autenticación y autorización **frecuentes** para **cada recurso**.

<img width="927" height="569" alt="Diagrama de Confianza Cero" src="https://github.com/user-attachments/assets/7b861bb9-efbb-4214-ada5-9cda85990447" />

### 🧩 Segmentación de Red y Aislamiento

Dividir una red grande en sub-redes más pequeñas para controlar el flujo de tráfico (especialmente el **Este-Oeste** o lateral).

| **Técnica** | **Definición** | **Propósito Principal** |
| :--- | :--- | :--- |
| **VLAN** (Virtual LAN) | Segmentación **Lógica** a Nivel 2 (en switches). | Organizar la red, limitar *broadcast*. Ej: VLAN de VoIP, VLAN de Invitados. |
| **DMZ** (Zona Desmilitarizada) | Una subred aislada entre Internet y la red interna. | Alojar servicios públicos (servidor web, email) sin exponer la red interna. |
| **Microsegmentación** | Segmentación **extremadamente granular** (a nivel de aplicación). | **Prevenir el movimiento lateral**. Un pilar de *Zero Trust*. |

### 🤖 Riesgos de IoT y Sistemas Embebidos

* **Riesgo:** A menudo tienen múltiples vectores de red (Wi-Fi, Bluetooth), son difíciles de parchear y tienen contraseñas débiles.
* **Solución:** **Segmentación estricta**. Todos los dispositivos IoT deben estar en su propia **VLAN** o segmento, **aislados** y sin acceso a los servidores críticos.

### 🚪 Control de Acceso a la Red (NAC)

Actúa como el "guardia de seguridad" en la puerta de la red (cableada o inalámbrica).

* **Función:** Interroga a los dispositivos *antes* de permitirles el acceso.
* **Validación de Postura (Posture Assessment):** Comprueba que el dispositivo cumple con la política (¿Antivirus actualizado? ¿Parches al día?).
* **Acción:** Puede **Permitir**, **Denegar** o **Poner en Cuarentena** en una VLAN restringida.

<img width="451" height="336" alt="Diagrama de Control de Acceso a la Red (NAC)" src="https://github.com/user-attachments/assets/5fb8d156-89f8-4e8e-ad25-47f72ea823cb" />

### 🔒 Red Privada Virtual (VPN)

Crea un **túnel de comunicación cifrado** que permite extender una red privada sobre una red no confiable (Internet).

* **Acceso Remoto:** Un empleado trabajando desde casa se conecta como si estuviera en la oficina.
* **Sitio-a-Sitio:** Conecta dos oficinas (ej. Santiago y Lima) de forma segura.
