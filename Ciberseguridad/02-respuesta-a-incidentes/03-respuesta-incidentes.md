# 🔥 2.3 - Respuesta a Incidentes (IRP & NIST)

La Respuesta a Incidentes (IR) es la mitigación de las violaciones de las políticas de seguridad y las prácticas recomendadas.

Este plan es la misión del "Bombero" 🧑‍🚒: **Detectar, analizar y contener** el problema (el fuego) **ahora mismo**. Es la respuesta táctica e inmediata para detener el daño.

---

## 📖 El Léxico del Defensor: Glosario de Ataque

Para gestionar una crisis, primero debemos hablar el mismo idioma. Estos términos no son intercambiables.

* **Vulnerabilidad (Vulnerability) 🐛**
    * **Definición Clara:** Es la **debilidad** o el agujero. Es la "puerta sin candado" en tu sistema, política, procedimiento o personal.
    * **Ejemplo Práctico:** Un servidor sin parches, o personal no capacitado en phishing.

* **Amenaza (Threat) 👤**
    * **Definición Clara:** Es **quien (o qué)** puede explotar esa "puerta sin candado".
    * **Ejemplo Práctico:** Un grupo de ransomware (actor de amenaza) o un huracán (amenaza ambiental).

* **Exploit 💥**
    * **Definición Clara:** El **cómo**. Es la herramienta, el código o la técnica específica diseñada para **aprovechar** una vulnerabilidad.
    * **Ejemplo Práctico:** Un script de Python que envía un paquete malformado a un servidor (RCE).

* **Evento (Event) 👁️**
    * **Definición Clara:** Cualquier ocurrencia observable en un sistema o red. El 99% del tiempo, es solo ruido benigno (ej. un usuario inicia sesión).

* **Evento Adverso (Adverse Event) 📉**
    * **Definición Clara:** Un evento con una **consecuencia negativa** real. (Ej. un bloqueo del sistema, un uso no autorizado de privilegios).

* **Intrusión (Intrusion) 🚪**
    * **Definición Clara:** Un evento deliberado (o intento) donde un intruso **obtiene o intenta obtener** acceso no autorizado.

* **Incidente (Incident) 🔥**
    * **Definición Clara:** ¡Alerta! Es un evento (o serie de eventos) que **real o potencialmente** pone en peligro la tríada CIA (Confidencialidad, Integridad o Disponibilidad).
    * **Ejemplo Práctico:** Se detecta un malware, un ataque DDoS tumba la web. Un incidente es un evento que **requiere una respuesta activa**.

* **Violación (Breach) 🔓**
    * **Definición Clara:** El peor escenario. Es un incidente donde se **confirma** la pérdida de control o divulgación no autorizada de datos sensibles.

* **Día Cero (Zero-Day) ⏳**
    * **Definición Clara:** Una vulnerabilidad que es **desconocida** para el fabricante y los defensores. No existe parche. El atacante la explota **antes** de que alguien sepa que existe.

---

## 📜 Plan de Respuesta a Incidentes (IRP)

Este es el *playbook* táctico para gestionar el ciberataque en sí. Es la documentación de un conjunto predeterminado de instrucciones para detectar, responder y limitar las consecuencias.

### Las 4 Fases del IRP (Framework NIST SP 800-61)

Un buen plan de IR es un ciclo de vida, no un documento estático.

1.  **Preparación (Preparation) 🏋️‍♂️**
    * La victoria se logra antes de la batalla.
    * **Acciones:** Identificar activos críticos (info del BIA), crear y entrenar al Equipo de Respuesta (CSIRT), realizar simulacros (*drills*), tener *playbooks* y listas de contactos listas (legales, forenses, FBI/CISA).

2.  **Detección y Análisis (Detection & Analysis) 🔍**
    * Encontrar la aguja en el pajar y decidir si es peligrosa.
    * **Acciones:** Monitorear vectores de ataque (Logs, SIEM, EDR), analizar y validar alertas (¿es un falso positivo?), priorizar (¿es ransomware en el servidor de BBDD?).

3.  **Contención, Erradicación y Recuperación (Containment, Eradication & Recovery) ♻️**
    * El núcleo de la respuesta táctica.
    * **Contención:** ¡Aislar! Desconectar el sistema de la red. Cambiar contraseñas. Bloquear IPs en el firewall. El objetivo es detener la propagación.
    * **Eradicación:** Encontrar la Causa Raíz (RCA). Eliminar el malware, parchear la vulnerabilidad que permitió el acceso.
    * **Recuperación:** Restaurar el sistema a un estado limpio y seguro (ej. desde backups confiables) y monitorear intensivamente.

4.  **Actividad Posterior al Incidente (Post-Incident Activity) ✍️**
    * La fase más importante y la más olvidada.
    * **Acciones:** Crear un informe de **Lecciones Aprendidas**. ¿Qué salió bien? ¿Qué salió mal? ¿Por qué tardamos 4 horas en detectar? Usar este aprendizaje para mejorar la fase de **Preparación**.

---

## 🧑‍🚒 El Equipo de Respuesta (CSIRT / IRT)

Un incidente nunca es trabajo de una sola persona. El CSIRT (Equipo de Respuesta a Incidentes de Seguridad Informática) es un equipo multidisciplinario con roles claros.

**Roles Clave ("La Mesa de Guerra"):**

* **Gerencia Senior:** Toma decisiones de negocio (ej. "¿Pagamos el rescate?").
* **Profesionales de InfoSec:** Los analistas técnicos que investigan y contienen.
* **Representante Legal:** Maneja el *compliance* (GDPR, etc.) y la preservación de evidencia.
* **Comunicaciones / RR.PP.:** Maneja el mensaje a empleados, clientes y medios.
* **Ingeniería (Sistemas/Redes):** Ejecutan las acciones (apagan servidores, restauran backups).

**Responsabilidades Estratégicas del CSIRT:**

* Determinar la cantidad y el **alcance del daño**.
* Determinar si se **comprometió información confidencial**.
* Implementar procedimientos de **recuperación** para restaurar la seguridad.
* Supervisar la implementación de medidas futuras para **prevenir la recurrencia**.

---

### 📖 Términos Clave del Glosario

* **🛡️ Centro de operaciones de seguridad (SOC):** una función organizativa centralizada (un equipo) que monitorea, detecta y analiza eventos para prevenir y resolver incidentes de seguridad.
* **🔵 Evento (Event):** Cualquier ocurrencia observable en una red o sistema.
* **💥 Eventos adversos:** eventos con una consecuencia negativa.
* **💣 Exploit:** Un ataque particular que aprovecha las vulnerabilidades del sistema.
* **⚠️ Incidente (Incident):** un evento que real o potencialmente pone en peligro la tríada CIA.
* **👣 Intrusión (Intrusion):** un evento en el que un intruso obtiene o intenta obtener acceso no autorizado.
* **⚙️ Manejo de incidentes (Incident Handling) / Respuesta a Incidentes (IR):** la mitigación de las violaciones de las políticas de seguridad y las prácticas recomendadas.
* **📑 Plan de respuesta a incidentes (IRP):** la documentación de un conjunto predeterminado de instrucciones para detectar, responder y limitar las consecuencias de un ciberataque.
* **🚫 Violación (Breach):** la pérdida de control o compromiso confirmado de datos.
* **🕳️ Vulnerabilidad (Vulnerability):** debilidad en un sistema, procedimientos o controles que podría ser explotada.
* **0️⃣ Zero Day:** una vulnerabilidad del sistema previamente desconocida.
