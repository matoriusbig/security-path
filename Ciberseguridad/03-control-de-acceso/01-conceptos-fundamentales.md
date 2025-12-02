# 🔑 3.1 - Conceptos Fundamentales (Sujetos, Objetos, AAA)

Todo escenario de control de acceso, ya sea físico o lógico, se reduce a tres componentes que se alinean con los principios de AAA (Autenticación, Autorización, Contabilidad/Auditoría).

---

## 1. Los 3 Elementos Fundamentales del Acceso

1.  **Sujetos (El Solicitante) 👤**
    * Es la entidad **activa** que solicita acceso a un recurso.
    * No es solo un usuario humano.
    * **Ejemplos:** Un usuario (`ana.garcia`), un proceso (un script `backup.sh`), un dispositivo (un endpoint) o un servicio (una API).

2.  **Objetos (El Recurso) 📦**
    * Es la entidad **pasiva** a la que se intenta acceder.
    * **Ejemplos:** Un archivo (`nomina.xlsx`), una base de datos, una impresora, un puerto de red o un edificio.

3.  **Reglas (El Árbitro / Autorización) 📜**
    * Son las instrucciones que determinan si un Sujeto puede realizar una acción sobre un Objeto. Esto es la **Autorización**.
    * Comparan la identidad validada del sujeto contra una lista de permisos.
    * **Ejemplos:** Una Lista de Control de Acceso (ACL) en un router, permisos de archivo NTFS (Leer, Escribir, Ejecutar) o una política de IAM en la nube.

> **Ejemplo Práctico (Sujeto/Objeto/Regla) 🧑‍💻:**
> * **Sujeto:** Ana (analista de marketing).
> * **Objeto:** El archivo `Resultados_Q4.xlsx`.
> * **Regla (Autorización):** La ACL del servidor verifica si "Ana" pertenece al grupo "Marketing". Si es así, le concede acceso de "Solo Lectura".

## 2. Auditoría y Contabilidad (Accounting) 🧾

Un control no sirve de nada si no podemos verificar que funciona o auditar qué ha sucedido. Esta es la "A" de **Contabilidad** (Accounting) en AAA.

### Gestión de Registros (Logs) ✍️

* **Definición:** Los registros (logs) son el registro de eventos, tanto físicos como lógicos.
* **Propósito:** Son esenciales para demostrar el **cumplimiento** (ej. PCI DSS), ayudar en **investigaciones forenses** y **detectar** actividades maliciosas.
* **Protección:** Los registros deben ser protegidos contra la manipulación (Integridad) y la divulgación no autorizada (Confidencialidad).
* **Revisión y Retención:**
    * Se debe tener una política para revisar los registros regularmente.
    * La **retención de datos** (cuánto tiempo guardarlos) depende de los requisitos comerciales y legales. El departamento legal debe definir la política.
* **Anomalía de Registro:** Es cualquier cosa fuera de lo común.
    * *Evidentes:* Lagunas en las marcas de tiempo, bloqueos de cuentas.
    * *Sutiles:* Alguien intentando escribir datos en un directorio protegido, una puerta de acceso físico abierta por más tiempo del normal.

### El Control de Acceso en el Mundo Real 🌎

* **Es un PROCESO, no un Producto:** El éxito depende de procesos sólidos y de la cultura organizacional.
* **El Desafío del Equilibrio (Riesgo vs. Operación):** Cada empleado necesita el acceso suficiente para hacer su trabajo. Cada permiso adicional incrementa el riesgo.
* **El Socio Estratégico: Recursos Humanos (RRHH):**
    * *Descripciones de Puesto:* Son la "receta" para construir tus roles de RBAC.
    * *Ciclo de Vida del Empleado:* RRHH te avisa para el **Onboarding** (dar acceso) y, crucialmente, para el **Offboarding** (revocar acceso *inmediatamente*).

---

### 📖 Términos Clave del Glosario

* **💻 Asunto (Subject):** Generalmente un individuo, proceso o dispositivo que hace que la información fluya entre los objetos.
* **📦 Objeto (Object):** Entidad pasiva (p. ej., archivos, registros, tablas) que contiene o recibe información.
* **📜 Regla (Rule):** Una instrucción desarrollada para permitir o denegar el acceso a un sistema.
* **🧐 Auditoría (Audit):** Revisión y examen independientes de registros y actividades para evaluar la idoneidad de los controles.
* **✍️ Registro (Logging):** Recopilar y almacenar las actividades de los usuarios en un registro.
* **📊 Anomalía de registro (Log Anomaly):** Una irregularidad del sistema que se identifica al estudiar las entradas de registro.
