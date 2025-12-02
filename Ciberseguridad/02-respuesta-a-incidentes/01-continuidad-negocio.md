# 🏛️ 2.1 - Continuidad del Negocio (BCP & BIA)

La Continuidad del Negocio (BC) son las acciones, procesos y herramientas para asegurar que las operaciones **críticas** de una organización puedan continuar durante una contingencia.

Este plan es la misión del "Paramédico" 🚑: Mantener al negocio **vivo** (operaciones críticas) **durante** la crisis. Responde a la pregunta: "¿Cómo seguimos tomando pedidos si la fábrica está en llamas?"

---

## 📊 Análisis de Impacto al Negocio (BIA): El Fundamento

Antes de escribir un solo plan (IR, BC o DR), **debes** hacer un BIA. Es la base de toda la resiliencia. No puedes proteger lo que no entiendes.

**💡 Definición Práctica:** El BIA es el proceso de **investigación** que descubre qué partes del negocio son las más importantes. Responde a tres preguntas clave:

1.  ¿Cuáles son nuestras **funciones de negocio críticas**? (Ej. "procesar pagos", "atender pacientes", "fabricar producto X").
2.  ¿Cuáles son las **dependencias** de esas funciones? (Ej. "Procesar pagos" depende de: la aplicación de pagos, el servidor de BBDD, la red y el personal de finanzas).
3.  ¿Cuál es el **impacto** (financiero, de reputación, legal) si esta función se detiene por 1 hora, 1 día o 1 semana?

### El BIA en Acción: El Caso del Incendio en Facturación 🔥

Este ejemplo ilustra perfectamente el **valor** de un BIA:

* **La Situación:** El departamento de facturación sufre una pérdida total en un incendio.
* **La Preparación (El BIA):** Un BIA realizado **4 meses antes** del incidente ya había identificado:
    * **Función Crítica:** La facturación es "muy importante".
    * **Impacto / Tolerancia:** La empresa podía sobrevivir **una semana** sin facturación gracias a las reservas de efectivo. (Esto define el **RTO - Recovery Time Objective** o "Tiempo Objetivo de Recuperación").
    * **Dependencias:** Las consultas de facturación también eran manejadas por Servicio al Cliente.
* **El Resultado:** Gracias al BIA, no hubo pánico. La gerencia sabía que tenía una semana. El BCP (que se creó **basado en este BIA**) ya tenía un plan: Servicio al Cliente asumiría las llamadas temporalmente y se activaría un sitio alterno (pre-contratado) en menos de 7 días.

> **🧠 Dato:** El BIA es tu herramienta de negociación más poderosa. Cuando la alta dirección te pregunta por qué necesitas 1 millón de dólares para un sitio de DR, el BIA es tu respuesta. No dices "necesito backups"; dices "El BIA demostró que si el sistema de pagos cae por más de 4 horas (el RTO), la empresa pierde 2.5 millones de dólares por día y enfrenta multas regulatorias".

---

## 🛡️ Plan de Continuidad del Negocio (BCP)

Si el incidente es una catástrofe, el BCP se activa para mantener el negocio vivo. Es el documento que describe cómo se mantendrán los procesos de negocio/misión durante y después de una interrupción significativa.

### Componentes Clave de un BCP Ganador

* **👥 Equipo de BCP:** Lista de miembros clave, sus respaldos y múltiples métodos de contacto.
* **📣 Sistemas de Notificación:** Cómo y cuándo se activa (promulga) el plan. Esto incluye los **Árboles Telefónicos (Cadenas de Llamadas)**, un sistema eficiente donde una persona llama a 3, y cada una de esas 3 llama a otras 3.
* **📋 Listas de Verificación (Checklists):** La memoria falla bajo presión. Se necesitan *checklists* para todo (procedimientos de respuesta inmediata, seguridad física, supresión de incendios).
* **🏛️ Autoridad y Gestión:** Orientación clara. ¿Quién tiene la autoridad para tomar decisiones críticas (ej. "apagar el sistema X" o "evacuar el edificio") si el CEO no está disponible?
* **🔗 Cadena de Suministro y Contactos Críticos:** Números de proveedores clave, clientes, fuerzas del orden y sitios alternativos.

### 💡 El Concepto del "Libro Rojo" (La Salvaguarda Analógica)

* **El Problema:** Almacenar el BCP **únicamente** en la red corporativa. Si un ransomware cifra la red, el plan es inaccesible.
* **La Solución:** Mantener copias físicas (impresas) del BCP en una ubicación segura y accesible **fuera de las instalaciones** (off-site).
* **La Disciplina:** Este "Libro Rojo" debe actualizarse **cada vez** que se actualiza la versión digital. La consistencia es clave.

---

### 📖 Términos Clave del Glosario

* **📊 Análisis de impacto comercial (BIA):** un análisis de los requisitos, funciones e interdependencias de un sistema de información que se utiliza para caracterizar los requisitos y prioridades de contingencia del sistema en caso de una interrupción significativa.
* **🏢 Continuidad Comercial (BC):** Acciones, procesos y herramientas para garantizar que una organización pueda continuar con las operaciones críticas durante una contingencia.
* **📜 Plan de continuidad comercial (BCP):** la documentación de un conjunto predeterminado de instrucciones o procedimientos que describen cómo se mantendrán los procesos comerciales/misión de una organización durante y después de una interrupción significativa.
