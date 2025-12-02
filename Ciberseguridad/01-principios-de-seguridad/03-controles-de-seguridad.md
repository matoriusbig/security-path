## 🚨 Controles de Seguridad (Nuestras Defensas)

Si el riesgo es el problema, los controles son la solución (o, más bien, la **mitigación**). Un control es una **salvaguarda** o **contramedida** que implementamos para proteger la Tríada CIA y reducir el riesgo a un nivel aceptable.

### 1. Controles Físicos 🚪

Son salvaguardas tangibles que controlan el movimiento de personas y equipos.

- **Ejemplos:** Cerraduras, guardias de seguridad, puertas de acceso, lectores de credenciales, extintores de incendios, generadores de respaldo.
- **Dato Clave:** Un lector de tarjetas (físico) es inútil sin una base de datos (técnico) que le diga qué tarjeta está autorizada.

### 2. Controles Técnicos 💻 (Lógicos)

Son las salvaguardas implementadas directamente en el software y el hardware.

- **Ejemplos:** Listas de Control de Acceso (ACLs), Firewalls, Cifrado, Biometría (Face ID), Sistemas de Detección de Intrusos (IDS).

### 3. Controles Administrativos 📜 (Gerenciales)

Son las reglas del juego para las personas. Se centran en las directivas, políticas y procedimientos.

- **Ejemplos:** **Política de Uso Aceptable (AUP)**, **Capacitación de Concienciación de Seguridad** (¡el más importante!), Procedimientos de Operaciones de Emergencia, Políticas de contratación y despido.

### 💡 Poniéndolo Todo Junto: Conectando Controles y la CIA

| Control | Tipo de Control | Cómo Protege la Tríada CIA |
| --- | --- | --- |
| **Cerradura en un Archivador** | Físico | Protege la **Confidencialidad** (nadie ve los papeles) y la **Integridad** (nadie los modifica). |
| **Generador de Respaldo** | Físico | Protege la **Disponibilidad** durante un corte de energía. |
| **Política de Contraseñas** | Administrativo (la regla) + Técnico (el sistema que la obliga) | Protege la **Confidencialidad** (impide acceso) y la **Integridad** (impide cambios). |
| **Cifrado de Datos** | Técnico | Es el pilar de la **Confidencialidad**. También puede proteger la **Integridad**. |

### ⚠️ Casos Reales: ¿Qué Pasa Cuando los Controles Fallan?

- **Caso 1: La Contraseña Compartida**
    - **Escenario:** Joe le da su contraseña a Joanne. Joanne es despedida y, descontenta, usa la contraseña de Joe para borrar archivos.
    - **Control Fallido:** **Administrativo** (Falla de la "Política de Contraseñas" y de la "Capacitación de Concienciación").
    - **Tríada Violada:** **Confidencialidad** (acceso no autorizado) e **Integridad** (borrado de archivos).
- **Caso 2: El Portátil Desatendido en Casa**
    - **Escenario:** Un empleado en teletrabajo deja su laptop de trabajo desbloqueada. Su hijo la usa para descargar un juego que contiene malware.
    - **Control Fallido:** **Físico** (no aseguró el activo), **Técnico** (no había un "bloqueo de pantalla automático") y **Administrativo** (Falla en la "Política de teletrabajo").
    - **Tríada Violada:** **Integridad** (estación de trabajo corrupta).
- **Caso 3: El Desastre Natural**
    - **Escenario:** Un corte de energía tumba los sistemas porque los generadores de respaldo fallaron por falta de mantenimiento.
    - **Control Fallido:** **Físico** (falla del generador) y **Administrativo** (falla en los "Planes de Continuidad del Negocio").
    - **Tríada Violada:** **Disponibilidad** (¡sistemas caídos!).
