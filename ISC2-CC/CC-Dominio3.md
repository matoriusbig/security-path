# 🛡️ Guía de Estudio : El Dominio Completo del Control de Acceso

Esta guía de estudio exhaustiva del Dominio 3 (ISC² CC), cubriendo los principios lógicos, estrategias defensivas, controles físicos y las realidades operativas de la gestión de acceso.

## 🚀 1. Fundamentos: ¿Qué es un Control de Seguridad?

Un control es, en esencia, una **salvaguarda o contramedida**. Su único propósito es preservar uno o más pilares de la **Tríada de la CIA**:

* **Confidencialidad 🤫**: Prevenir la divulgación no autorizada de información.
* **Integridad ✍️**: Asegurar que la información sea precisa y no haya sido modificada sin autorización.
* **Disponibilidad 🟢**: Garantizar que los sistemas y datos estén accesibles para los usuarios autorizados cuando los necesiten.

> **Ejemplo Práctico (Cortafuegos) 🔎**:
> Un cortafuegos (firewall) es un control técnico clásico. Actúa como un guardia en la puerta de la red. Impide que el tráfico no autorizado (amenazas externas) entre, pero también puede configurarse para evitar que datos sensibles (información interna) salgan sin permiso, protegiendo así la **Confidencialidad** y la **Integridad**.

---

## 🔑 2. Los 3 Elementos Fundamentales del Acceso

Todo escenario de control de acceso, ya sea físico o lógico, se reduce a tres componentes:

### 1. Sujetos (El Solicitante)
* Es la entidad **activa** que solicita acceso a un recurso.
* No es solo un usuario humano.
* **Ejemplos**: Un usuario (`ana.garcia`), un proceso (un script `backup.sh`), un dispositivo (un endpoint solicitando unirse a la red) o un servicio (una API externa).

### 2. Objetos (El Recurso)
* Es la entidad **pasiva** a la que se intenta acceder.
* No tiene lógica de control propia; debe ser protegido por una capa externa (como el SO o un sistema de IAM).
* **Ejemplos**: Un archivo (`nomina.xlsx`), una base de datos, una impresora, un puerto de red o incluso un edificio.

### 3. Reglas (El Árbitro)
* Son las instrucciones que determinan si un Sujeto puede realizar una acción sobre un Objeto.
* Comparan la identidad validada del sujeto contra una lista de permisos.
* **Ejemplos**: Una Lista de Control de Acceso (ACL) en un router, permisos de archivo NTFS (Leer, Escribir, Ejecutar) o una política de IAM en la nube.

> **Ejemplo Práctico (Sujeto/Objeto/Regla) 🧑‍💻**:
>
> * **Sujeto**: Ana (analista de marketing).
> * **Objeto**: El archivo `Resultados_Q4.xlsx` en el servidor de archivos.
> * **Regla**: La ACL del servidor verifica si "Ana" pertenece al grupo "Marketing". Si es así, le concede acceso de "Solo Lectura". Si un sujeto (p.ej., un proceso de malware) intenta acceder, la regla lo denegará.

---

## 🗺️ 3. Estrategias Clave de Control de Acceso

Estos son los principios de alto nivel que guían *cómo* implementamos los controles.

### Defensa en Profundidad (Defense in Depth)
* No existe una "bala de plata". Esta estrategia aplica **múltiples capas** de controles (físicos, técnicos y administrativos) para proteger un activo.
* La idea es que si una capa falla (y eventualmente lo hará), la siguiente capa debe detener o ralentizar al atacante.

> **Ejemplo Práctico (Protegiendo un Centro de Datos) 🔒**:
>
> * **Capa Administrativa (Política)**: Una política escrita que define quién puede solicitar acceso al data center y un procedimiento de auditoría de registros.
> * **Capa Física (Perímetro)**: Una valla perimetral, guardias de seguridad en la entrada del edificio y una cerradura con tarjeta de acceso en la puerta de la sala de servidores.
> * **Capa Técnica (Lógica)**: Un firewall de red, autenticación multifactor (MFA) para iniciar sesión en el servidor y cifrado de disco (AES-256) en los discos duros.

### Principio de Privilegio Mínimo (PoLP)
* Es la práctica de otorgar solo el **acceso mínimo necesario** para que un sujeto (usuario o proceso) realice su función específica, y nada más.
* Este es, quizás, el concepto más importante para reducir la superficie de ataque y el daño de un incidente.

> **Ejemplo Práctico (Sistema de Nómina) 💸**:
> Gabriela, una empleada, puede enviar su tarjeta de horas (sujeto accede al objeto "sistema de tiempo"). Sin embargo, no puede aprobar cambios ni ver los salarios de otros. Su gerente, Nate, sí tiene ese privilegio. Esto es PoLP: Gabriela solo tiene los permisos estrictamente necesarios para su función.

### Segregación de Funciones (Segregation of Duties - SoD)
* Un principio fundamental para prevenir el fraude y los errores.
* Asegura que **ninguna persona tenga control total** sobre un proceso crítico de alto riesgo (de principio a fin).
* Divide la transacción en partes separadas, requiriendo que diferentes personas ejecuten cada parte.

> **Ejemplo Práctico (Pagos a Proveedores) 🧾**:
> En un sistema financiero, un empleado puede *crear* una orden de pago (Factura A). Sin embargo, esa misma persona no puede *autorizar* el pago. Se necesita una segunda persona (un gerente) para aprobarla. Esto es SoD y previene que un solo empleado cree y pague facturas fraudulentas.

* **Colusión**: Es el riesgo donde dos o más personas conspiran para eludir la SoD.
* **Control Dual (Two-Person Integrity)**: Una implementación de SoD que requiere que dos personas estén presentes *simultáneamente* para realizar una acción (p.ej., dos personas con dos llaves diferentes para abrir la bóveda de un banco).

---

## 💻 4. Modelos de Control de Acceso Lógico

Una vez que un usuario se autentica (prueba quién es), la **autorización** (qué puede hacer) se gestiona a través de estos modelos:

### 👤 Control de Acceso Discrecional (DAC)
* **Definición**: El modelo DAC se basa en la **discreción del propietario**. El creador o propietario de un objeto (como un archivo) tiene control total para decidir quién más puede acceder a él.
* **Características**: Cada objeto tiene un propietario; es flexible.
* **Implementación Común**: La mayoría de los sistemas operativos de usuario final (Windows, macOS, Linux) usan DAC para sus sistemas de archivos.
* **Ejemplo (Documento Compartido) 📄**: Creas un documento en Google Drive. Tú eres el propietario. Decides compartirlo con "Ana" (permisos de "Editor") y "Carlos" (permisos de "Lector"). Esta decisión fue enteramente tuya.

### 🛡️ Control de Acceso Obligatorio (MAC)
* **Definición**: El modelo MAC es mucho más estricto. El acceso **no lo decide el propietario**, sino una **política de seguridad global** gestionada centralmente e impuesta *obligatoriamente* por el sistema operativo.
* **Características**: Se basa en **Etiquetas (Labels)**. Tanto los sujetos (usuarios) como los objetos (archivos) reciben etiquetas de clasificación (o niveles de sensibilidad, ej. `Top Secret`, `Secret`, `Confidential`).
* **Regla Central**: Un usuario solo puede acceder a un archivo si su nivel de autorización es igual o superior al nivel de clasificación del archivo.
* **Implementación Común**: Entornos de alta seguridad (militares, agencias de inteligencia).
* **Ejemplo (Militar) 🏛️**: Un analista con autorización `Top Secret` puede leer archivos `Top Secret` y `Secret`. Un analista con autorización `Confidential` no puede leer un archivo `Secret`, incluso si el primer analista quisiera compartirlo. El sistema lo prohíbe.

### 🧑‍💼 Control de Acceso Basado en Roles (RBAC)
* **Definición**: Es el modelo más utilizado en entornos corporativos. En lugar de asignar permisos directamente a usuarios individuales (una pesadilla de gestionar), RBAC **asigna permisos a Roles**, y luego los usuarios son asignados a esos roles.
* **Características**: Gestión centralizada, eficiente y alineada con el PoLP.
* **Ejemplo (Corporativo) 📈**:
    * **Rol "Finanzas"**: Tiene acceso de R/W al software de nómina.
    * **Rol "Ventas"**: Tiene acceso R/W al CRM (Salesforce).
    * **Rol "RRHH"**: Tiene acceso a los archivos privados del personal.
    * Cuando se contrata a un nuevo vendedor, el administrador simplemente lo añade al rol "Ventas". Hereda automáticamente todos los permisos necesarios (y solo esos).

---

## ⚙️ 5. Gestión Avanzada de Acceso e Identidad

Aquí es donde los principios se encuentran con la tecnología y los procesos.

### Gestión de Acceso Privilegiado (PAM)
* **Definición**: Se enfoca en controlar, monitorear y asegurar las cuentas que tienen privilegios elevados (`Administrador`, `root`, cuentas de servicio).
* **Objetivo**: Estas cuentas son el objetivo número uno de los atacantes.
* **Concepto Clave: Acceso "Just-in-Time" (JIT)**: Introduce la idea de que los privilegios de administrador **no están "siempre activos"**. El usuario solicita el privilegio, este es aprobado (idealmente por un sistema), y se le concede solo por el tiempo necesario para completar la tarea.

> **Ejemplo Práctico (El Desastre del Admin) 💥**:
>
> * **El Problema**: Un administrador de TI (Admin) navega por internet con su cuenta de administrador de dominio (privilegios máximos 24/7). Abre un correo de phishing y el ransomware se ejecuta con privilegios de administrador, cifrando toda la red.
> * **Solución con PAM (JIT)**: El Admin usa una cuenta estándar para su correo. Cuando necesita hacer tareas administrativas, solicita acceso JIT. El acceso se le concede por 30 minutos. El ransomware, si se ejecuta, solo afecta su máquina local (privilegio mínimo).

### Cuentas Privilegiadas vs. Estándar
Debido a su alto riesgo, las cuentas privilegiadas requieren controles más estrictos:
* Registro (Logging) más extenso y detallado.
* Control de acceso más estricto (MFA obligatorio).
* Verificación de confianza más profunda (verificaciones de antecedentes).
* Auditorías más frecuentes.

### El Ciclo de Vida del Acceso (Aprovisionamiento de Usuarios)
El aprovisionamiento es el proceso de gestión de identidad para crear, modificar y gestionar el acceso a los recursos.

* **1. Nuevo Empleado (Onboarding)**:
    * Se crea una nueva identidad de usuario.
    * Se le asignan permisos basados en su rol (RBAC) y PoLP.
    * **MEJOR PRÁCTICA**: Nunca copies el perfil de un usuario existente para crear uno nuevo.
* **2. Cambio de Puesto (Transferencia)**:
    * Cuando un empleado es promovido o se mueve lateralmente.
    * Se deben **revocar todos los permisos del rol anterior**.
    * Se deben asignar los nuevos permisos del nuevo rol.
* **3. Separación (Offboarding/Licencia)**:
    * Cuando un empleado deja la empresa o toma una licencia larga.
    * La cuenta debe ser **DESACTIVADA inmediatamente**.
    * **Nota**: Desactivar, no eliminar. Las cuentas deshabilitadas preservan la pista de auditoría (logs) y los archivos propiedad del usuario.

### Riesgo Clave: "Permission Creep" (Aumento de Privilegios) 📈
* **Definición**: Ocurre cuando un empleado cambia de roles y **acumula permisos**. Se le otorgan los permisos de su nuevo rol, pero nunca se le revocan los permisos del rol antiguo.
* **Impacto**: Con el tiempo, este usuario tiene muchos más privilegios de los que necesita, violando el PoLP y convirtiéndose en un riesgo de seguridad masivo. Es un desafío común en RBAC si no se gestiona el ciclo de vida adecuadamente.

---

## 🏢 6. Controles de Acceso Físico

Los elementos tangibles implementados para prevenir, monitorear o detectar el contacto directo con sistemas o áreas. **La seguridad del personal es siempre la prioridad número uno.**

### 1. Sistemas de Credenciales y Puertas de Acceso
* **Tecnologías**: Torniquetes, esclusas de seguridad (*mantraps*) y cerraduras de puertas controladas.
* **Tipos de Tarjetas (Credenciales)**:
    * Código de barras
    * Banda magnética
    * Proximidad (RFID)
    * Inteligente (Smart Card, con chip)
    * Híbrido

### 2. Diseño Ambiental (CPTED)
* **Definición**: Prevención del Crimen mediante el Diseño Ambiental (CPTED). Es el uso de elementos de diseño pasivo para crear espacios de trabajo más seguros.
* **Métodos**:
    * **Organizacionales**: Personas (guardias, personal de recepción).
    * **Mecánicos**: Tecnología (cámaras, cerraduras, alarmas).
    * **Naturales**: Diseño arquitectónico (buena iluminación, líneas de visión claras, dirigir el flujo de personas, paisajismo).

### 3. Biometría
* **Definición**: Utiliza características únicas de una persona para autenticar su identidad.
* **Proceso**: (1) Enrolamiento (se almacena la plantilla) -> (2) Verificación (se compara con la plantilla).
* **Tipos Fisiológicos (Miden características)**:
    * Huella dactilar
    * Escaneo de iris (el color alrededor de la pupila)
    * Escaneo de retina (patrón de vasos sanguíneos en el fondo del ojo)
    * Escaneo de palma
* **Tipos Conductuales (Miden cómo actúa alguien)**:
    * Huellas de voz
    * Dinámica de firma
    * **Dinámica de pulsación de teclas (Keystroke Dynamics)**: Mide el comportamiento al escribir, como la *tasa de permanencia* (cuánto tiempo se presiona una tecla) y la *tasa de transferencia* (qué tan rápido se mueve entre teclas).

### 4. Vigilancia y Detección
* **Cámaras**: Proporcionan disuasión, detección (con sensores de movimiento) y evidencia forense.
* **Detectores de Movimiento**: Infrarrojos, microondas o láseres.
* **Sensores Perimetrales**: Sensores de vibración en vallas para detectar intentos de escalada.
* **Guardias de Seguridad**: Un control disuasorio y de respuesta muy eficaz. Ayudan a prevenir el **tailgating** (seguir de cerca a una persona autorizada para pasar por una puerta).

---

## 🧾 7. Auditoría y Realidad Operativa

Un control no sirve de nada si no podemos verificar que funciona o auditar qué ha sucedido.

### Gestión de Registros (Logs)
* **Definición**: Los registros (logs) son el registro de eventos, tanto físicos como lógicos.
* **Propósito**: Son esenciales para demostrar el **cumplimiento** de normativas (ej. PCI DSS), ayudar en **investigaciones forenses** y **detectar** actividades maliciosas.
* **Protección**: Los registros deben ser protegidos contra la manipulación (**Integridad**) y la divulgación no autorizada (**Confidencialidad**).
* **Revisión y Retención**:
    * Se debe tener una política para revisar los registros regularmente.
    * La **retención de datos** (cuánto tiempo guardarlos) depende de los requisitos comerciales y legales (ej. PCI DSS requiere un año). El departamento legal debe definir la política.
* **Anomalía de Registro**: Es cualquier cosa fuera de lo común.
    * *Evidentes*: Lagunas en las marcas de tiempo, bloqueos de cuentas.
    * *Sutiles*: Alguien intentando escribir datos en un directorio protegido, una puerta de acceso físico abierta por más tiempo del normal.

### 🧠 El Control de Acceso en el Mundo Real

* **Es un PROCESO, no un Producto**:
    * Muchas organizaciones compran herramientas, pero fallan en la implementación. El éxito depende de procesos sólidos y de la cultura organizacional.
* **El Desafío del Equilibrio (Riesgo vs. Operación)**:
    * Cada empleado necesita el acceso suficiente para hacer su trabajo. Cada permiso adicional incrementa el riesgo. La clave es la simplificación (RBAC).
* **La Realidad de RBAC y SoD**:
    * En el mundo real, la gente usa "muchos sombreros", rompiendo el modelo limpio de RBAC.
    * **¿Qué pasa si la empresa es muy pequeña?** A veces, una sola persona debe hacer todo (ej. la única persona de finanzas).
    * **Solución**: Implementas **Controles Compensatorios o Manuales**.
    * *Ejemplo*: Para procesar la nómina, el empleado debe imprimir un informe y obtener una **firma física** del CFO antes de ejecutar el pago. Esto no previene el fraude en tiempo real, pero crea un rastro de auditoría (audit trail) y un mecanismo de disuasión.
* **El Socio Estratégico: Recursos Humanos (RRHH)**:
    * La seguridad no puede trabajar aislada. RRHH es tu mejor aliado.
    * **Descripciones de Puesto**: Son la "receta" para construir tus roles de RBAC.
    * **Ciclo de Vida del Empleado**: RRHH te avisa para el **Onboarding** (dar acceso) y, crucialmente, para el **Offboarding** (revocar acceso *inmediatamente*).

# 📖 Términos y Definiciones de Control de Acceso

---

### A

* 👨‍💼 **Aprovisionamiento de usuarios (User Provisioning)**
  > El proceso de creación, mantenimiento y desactivación de identidades de usuarios en un sistema.

* 🕵️ **Amenaza interna (Insider Threat)**
  > Una entidad con acceso autorizado que tiene el potencial de dañar un sistema de información a través de la destrucción, divulgación, modificación de datos y/o denegación de servicio. (Fuente: NIST SP 800-32)

* 📊 **Anomalía de registro (Log Anomaly)**
  > Una irregularidad del sistema que se identifica al estudiar las entradas de registro que podrían representar eventos de interés para una mayor vigilancia.

* 💻 **Asunto (Subject)**
  > Generalmente un individuo, proceso o dispositivo que hace que la información fluya entre los objetos o cambie el estado del sistema. (Fuente: NIST SP800-53 R4)

* 🧐 **Auditoría (Audit)**
  > Revisión y examen independientes de registros y actividades para evaluar la idoneidad de los controles del sistema, para garantizar el cumplimiento de las políticas y los procedimientos operativos establecidos. (Fuente: NIST SP 1800-15B)

---

### C

* 🔒 **Cifrar (Encrypt)**
  > Proteger la información privada colocándola en un formato que solo pueden leer las personas que tienen permiso para hacerlo.

* 🧑‍💼 **Control de acceso basado en funciones (RBAC - Role-Based Access Control)**
  > Un sistema de control de acceso que configura los permisos de usuario en función de las funciones.

* 👤 **Control de acceso discrecional (DAC - Discretionary Access Control)**
  > Una cierta cantidad de control de acceso se deja a discreción del propietario del objeto o de cualquier otra persona autorizada para controlar el acceso del objeto. El propietario puede determinar quién debe tener derechos de acceso a un objeto y cuáles deben ser esos derechos. (Fuente: SP 800-192 del NIST)

* 🏛️ **Control de acceso obligatorio (MAC - Mandatory Access Control)**
  > Control de acceso que requiere que el propio sistema gestione los controles de acceso de acuerdo con las políticas de seguridad de la organización.

* 🧱 **Controles de Acceso Físico**
  > Controles implementados a través de un mecanismo tangible. Los ejemplos incluyen muros, vallas, guardias, cerraduras, etc. En las organizaciones modernas, muchos sistemas de control físico están vinculados a sistemas técnicos/lógicos, como lectores de tarjetas conectados a cerraduras de puertas.

* ⚙️ **Controles técnicos**
  > Los controles de seguridad (es decir, salvaguardas o contramedidas) para un sistema de información que son principalmente implementados y ejecutados por el sistema de información a través de mecanismos contenidos en los componentes de hardware, software o firmware del sistema.

* 🔥 **Cortafuegos (Firewall)**
  > Dispositivos que hacen cumplir las políticas de seguridad administrativas al filtrar el tráfico entrante según un conjunto de reglas.

* 🔑 **Cuenta privilegiada (Privileged Account)**
  > Una cuenta del sistema de información con autorizaciones aprobadas de un usuario privilegiado. (Fuente: NIST SP 800-53 Rev. 4)

---

### D

* 겹 **Defensa en capas (Layered Defense)**
  > El uso de múltiples controles dispuestos en serie para proporcionar varios controles consecutivos para proteger un activo; también llamada defensa en profundidad.

* 🏰 **Defensa en profundidad (Defense in Depth)**
  > Estrategia de seguridad de la información que integra personas, tecnología y capacidades operativas para establecer barreras variables en múltiples capas y misiones de la organización. (Fuente: NIST SP 800-53 Rev 4)

---

### I / L

* 📱 **iOS**
  > Un sistema operativo fabricado por Apple Inc. Utilizado para dispositivos móviles.

* 🐧 **Linux**
  > Un sistema operativo de código abierto que hace que su código fuente esté legalmente disponible para los usuarios finales.

---

### M / O

* 🚪 **Mantrap (Esclusa de seguridad)**
  > Una entrada a un edificio o un área que requiere que las personas pasen por dos puertas con solo una puerta abierta a la vez.

* 📦 **Objeto (Object)**
  > Entidad pasiva relacionada con el sistema de información (p. ej., dispositivos, archivos, registros, tablas, procesos, programas, dominios) que contiene o recibe información. El acceso a un objeto (por parte de un sujeto) implica el acceso a la información que contiene. (Fuente: NIST SP 800-53 Rev 4)

---

### P / R

* 🌳 **Prevención del delito a través del diseño ambiental (CPTED)**
  > Un enfoque arquitectónico para el diseño de edificios y espacios que enfatiza las características pasivas para reducir la probabilidad de actividad delictiva.

* 🪶 **Principio de privilegio mínimo (PoLP - Principle of Least Privilege)**
  > El principio de que los usuarios y los programas deben tener solo los privilegios mínimos necesarios para completar sus tareas. (Fuente: SP 800-179 del NIST)

* ☠️ **Ransomware**
  > Un tipo de software malicioso que bloquea la pantalla o los archivos de la computadora, lo que impide o limita el acceso de un usuario a su sistema y datos hasta que se pague el dinero.

* 📜 **Regla (Rule)**
  > Una instrucción desarrollada para permitir o denegar el acceso a un sistema comparando la identidad validada del sujeto con una lista de control de acceso.

* ✍️ **Registro (Logging)**
  > Recopilar y almacenar las actividades de los usuarios en un registro, que es un registro de los eventos que ocurren dentro de los sistemas y redes de una organización. (Fuente: NIST SP 1800-25B)

---

### S / U

* 🧑‍🤝‍🧑 **Segregación de funciones (SoD - Segregation of Duties)**
  > La práctica de garantizar que un proceso organizacional no pueda ser completado por una sola persona; colusión de fuerzas como un medio para reducir las amenazas internas. También conocida comúnmentamente como separación de funciones.

* 🖥️ **Sistemas de control de acceso lógico**
  > Un sistema automatizado que controla la capacidad de una persona para acceder a uno o más recursos del sistema informático, como una estación de trabajo, una red, una aplicación o una base de datos. Un sistema de control de acceso lógico requiere la validación de la identidad de una persona a través de algún mecanismo, como un PIN, una tarjeta, un token biométrico u otro. Tiene la capacidad de asignar diferentes privilegios de acceso a diferentes personas según sus roles y responsabilidades en una organización. (Fuente: NIST SP 800-53 Rev.5)

* 🔄 **Torniquete (Turnstile)**
  > Una puerta o barrera giratoria de un solo sentido que permite que solo una persona a la vez ingrese a un edificio o pase por un área.

* 🖥️ **Unix**
  > Un sistema operativo utilizado en el desarrollo de software.
