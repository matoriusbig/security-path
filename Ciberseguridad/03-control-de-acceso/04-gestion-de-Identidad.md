# ⚙️ 3.4 - Gestión de Identidad (PAM, Ciclo de Vida)

Aquí es donde los principios teóricos se encuentran con la tecnología y los procesos operativos. La gestión de la identidad es el proceso de negocio de **quién** eres, mientras que la gestión del acceso es **qué** puedes hacer.

---

## 1. Gestión de Acceso Privilegiado (PAM) 🔑

* **Definición:** Se enfoca en controlar, monitorear y asegurar las cuentas que tienen privilegios elevados (Administrador, `root`, cuentas de servicio).
* **Objetivo:** Estas cuentas son el objetivo número uno de los atacantes.
* **Concepto Clave: Acceso "Just-in-Time" (JIT):** Introduce la idea de que los privilegios de administrador **no están "siempre activos"**. El usuario solicita el privilegio, este es aprobado, y se le concede solo por el tiempo necesario para completar la tarea.

> **Ejemplo Práctico (El Desastre del Admin) 💥:**
> * **El Problema:** Un administrador de TI (Admin) navega por internet con su cuenta de administrador de dominio (privilegios máximos 24/7). Abre un correo de phishing y el ransomware se ejecuta con privilegios de administrador, cifrando toda la red.
> * **Solución con PAM (JIT):** El Admin usa una cuenta estándar para su correo. Cuando necesita hacer tareas administrativas, solicita acceso JIT por 30 minutos. El ransomware, si se ejecuta, solo afecta su máquina local (privilegio mínimo).

### Cuentas Privilegiadas vs. Estándar

Debido a su alto riesgo, las cuentas privilegiadas requieren controles más estrictos:

* Registro (Logging) más extenso y detallado.
* Control de acceso más estricto (MFA obligatorio).
* Verificación de confianza más profunda (verificaciones de antecedentes).
* Auditorías más frecuentes.

## 2. El Ciclo de Vida del Acceso (Aprovisionamiento de Usuarios) 🔄

El aprovisionamiento es el proceso de gestión de identidad para crear, modificar y gestionar el acceso a los recursos.

1.  **Nuevo Empleado (Onboarding):**
    * Se crea una nueva identidad de usuario.
    * Se le asignan permisos basados en su rol (RBAC) y PoLP.
    * *MEJOR PRÁCTICA:* Nunca copies el perfil de un usuario existente para crear uno nuevo.
2.  **Cambio de Puesto (Transferencia):**
    * Cuando un empleado es promovido o se mueve lateralmente.
    * Se deben **revocar todos los permisos del rol anterior**.
    * Se deben asignar los nuevos permisos del nuevo rol.
3.  **Separación (Offboarding/Licencia):**
    * Cuando un empleado deja la empresa o toma una licencia larga.
    * La cuenta debe ser **DESACTIVADA inmediatamente**.
    * *Nota:* Desactivar, no eliminar. Las cuentas deshabilitadas preservan la pista de auditoría (logs).

### Riesgo Clave: "Permission Creep" (Aumento de Privilegios) 📈

* **Definición:** Ocurre cuando un empleado cambia de roles y **acumula permisos**. Se le otorgan los permisos de su nuevo rol, pero nunca se le revocan los permisos del rol antiguo.
* **Impacto:** Con el tiempo, este usuario tiene muchos más privilegios de los que necesita, violando el PoLP y convirtiéndose en un riesgo de seguridad masivo (una forma de amenaza interna).

---

### 📖 Términos Clave del Glosario

* **👨‍💼 Aprovisionamiento de usuarios (User Provisioning):** El proceso de creación, mantenimiento y desactivación de identidades de usuarios en un sistema.
* **🔑 Cuenta privilegiada (Privileged Account):** Una cuenta del sistema de información con autorizaciones aprobadas de un usuario privilegiado.
* **🪶 Principio de privilegio mínimo (PoLP):** El principio de que los usuarios y los programas deben tener solo los privilegios mínimos necesarios para completar sus tareas.
* **🧑‍🤝‍🧑 Segregación de funciones (SoD):** La práctica de garantizar que un proceso organizacional no pueda ser completado por una sola persona.
* **🕵️ Amenaza interna (Insider Threat):** Una entidad con acceso autorizado que tiene el potencial de dañar un sistema de información.
