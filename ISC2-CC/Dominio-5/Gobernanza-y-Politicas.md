# 🏛️ 5.5 - Gobernanza y Políticas Clave

Las políticas no son "reglas"; son la **Constitución** de la seguridad de una organización. Definen formalmente la postura de seguridad y traducen los objetivos del negocio en requisitos de control.

El objetivo es encontrar el equilibrio entre:
* **Seguridad:** Proteger los activos.
* **Operabilidad:** Permitir que el negocio funcione.
* **Asequibilidad:** Gestionar los costos.
* **Riesgo:** Aceptar un nivel de riesgo tolerable.

---

## 📜 El Fundamento: Gobernanza y Aplicación (Enforcement)

Una política debe estar alineada con la misión de la organización y tener peso.

> **Una política sin sanciones (consecuencias) adjuntas no es una política; es una sugerencia.**

* **Documentación:** Las políticas deben ser firmadas por los empleados durante la incorporación (*onboarding*).
* **Comprensión:** Se debe validar la comprensión (Ej: con un breve cuestionario).
* **Sanciones:** Las consecuencias por incumplimiento deben estar claramente definidas.

---

## 🔑 Las 6 Políticas Pilares de Seguridad

### 1. 🗃️ Política de Manejo de Datos (Data Handling)

* **Qué es:** Define cómo deben tratarse los datos basándose en su **clasificación** (valor y sensibilidad).
* **Por qué Importa:** Es la implementación práctica de la "Clasificación de Datos".
* **Ejemplo Práctico (PCI DSS):**
    * *Clasificación:* Los datos de tarjetas de crédito se clasifican como "Altamente Restringidos".
    * *Política:* La política de manejo de datos estipula que todos los datos "Altamente Restringidos" deben cumplir con PCI DSS.
    * *Acción:* Esto obliga a los equipos de TI a cifrar los números de tarjeta (PAN) en reposo y en tránsito.

### 2. 🔑 Política de Contraseñas (Password Policy)

* **Qué es:** Establece los estándares mínimos para la creación, gestión y protección de credenciales.
* **Por qué Importa:** Es la primera línea de defensa (y la más atacada).
* **Componentes Clave:**
    * **Formulación:** Requisitos de complejidad (longitud, caracteres especiales).
    * **Gestión:** Frecuencia de cambio (rotación) e historial (no reutilizar).

### 3. 💻 Política de Uso Aceptable (AUP)

* **Qué es:** El "manual de reglas" para el uso diario de los activos de la empresa (red, ordenadores, Internet).
* **Por qué Importa:** Protege a la organización de la responsabilidad legal y reduce el riesgo de malware.
* **Componentes Clave:**
    * Uso de Internet (Prohibición de sitios).
    * **Expectativa de Privacidad:** Una declaración clara de que los empleados no deben tener ninguna expectativa de privacidad al usar los activos de la empresa (la empresa se reserva el derecho de monitorear).

### 4. 📱 Política de BYOD (Bring Your Own Device)

* **Qué es:** Define las reglas para que los empleados usen sus dispositivos personales para acceder a datos de la empresa.
* **Por qué Importa:** Es un equilibrio crítico entre la moral del empleado (flexibilidad) y la pérdida de control de seguridad.
* **Desafíos Clave:**
    * **Contención de Datos:** ¿Cómo se evita que los datos de la empresa se copien a aplicaciones personales? (Herramientas de **Mobile Device Management - MDM**).
    * **Forense y Legal:** Si un empleado es despedido, ¿cómo se borran *solo* los datos de la empresa sin tocar sus fotos personales?

### 5. 🔒 Política de Privacidad (Privacy Policy)

* **Qué es:** Documenta el compromiso para manejar legal y éticamente la Información de Identificación Personal (PII) o la Información Médica Protegida (ePHI).
* **Por qué Importa:** El cumplimiento legal no es opcional (GDPR, HIPAA).
* **Doble Audiencia:**
    * **Interna:** Para capacitar al personal sobre cómo manejar los datos.
    * **Pública (Aviso de Privacidad):** Para informar a clientes y usuarios.

### 6. 🔄 Política de Gestión de Cambios (Change Management)

* **Qué es:** La disciplina formal que aprueba y gestiona todas las transiciones para asegurar que los cambios no introduzcan vulnerabilidades.
* **Por qué Importa:** Previene que cambios bien intencionados (un parche) causen interrupciones catastróficas.
* **Componentes del Proceso:**

| Componente | Descripción |
| :--- | :--- |
| **Documentación (RFC)** | "Solicitud de Cambio" (Request for Change - RFC) que detalla el qué, por qué, y el impacto. |
| **Aprobación** | Un comité (CCB - Change Control Board) revisa el riesgo y aprueba o rechaza. |
| **Prueba y Verificación** | El cambio debe ser probado en un entorno de *staging*. Se deben verificar los procedimientos de reversión. |
| **Implementación** | El cambio se programa y se implementa en producción. |
| **Reversión (Rollback)** | El plan de "deshacer". Si el cambio falla, ¿cómo se vuelve al estado funcional anterior? |
| **Monitoreo y Cierre** | Se monitorea el sistema post-cambio y se cierra el RFC. |

---

## 🎯 Conclusión: Alinear la Política con el Riesgo

Las políticas no son universales. Su rigurosidad debe estar alineada con la **tolerancia al riesgo** de la organización.
* Un **contratista de defensa** (tolerancia nula) tendrá una AUP extremadamente estricta.
* Una **agencia de marketing** (mayor tolerancia) puede tener una AUP más relajada para fomentar la creatividad.
