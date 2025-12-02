# ⚙️ 5.4 - Gestión de Configuración y Endurecimiento

Esta es la disciplina fundamental de construir la fortaleza y asegurarse de que *permanezca* segura. Combina el "endurecimiento" (la configuración inicial) con la "gestión de la configuración" (el mantenimiento y control de cambios).

---

## 🚀 Endurecimiento (Hardening)

El endurecimiento es el proceso metódico de **reducir la superficie de ataque** de un sistema. Piensa en ello como cerrar y asegurar todas las puertas y ventanas innecesarias de una fortaleza.

* **Objetivo:** Minimizar las vulnerabilidades y las vías de explotación.
* **Alcance:** No se limita solo al sistema operativo (SO). Se aplica a toda la pila tecnológica:
    * Hardware y Firmware
    * Sistemas Operativos (Ej: Deshabilitar servicios innecesarios, aplicar parches)
    * Servidores de Aplicaciones (Ej: Configurar permisos de archivos)
    * Servidores Web (Ej: Ocultar banners de versión)
    * Aplicaciones (Ej: Validación de entradas, gestión de errores)
* **Estándar:** El objetivo es alinear las configuraciones con los estándares de seguridad de la industria (Ej: **CIS Benchmarks**) y las políticas internas.

---

## 🗂️ Gestión de la Configuración (CM)

La Gestión de la Configuración (CM) es la disciplina formal que nos permite mantener el control sobre el estado de nuestros sistemas. Garantiza que solo los cambios autorizados y validados se implementen.

### Los 4 Pilares del Proceso de CM

1.  **Identificación:** Identificar y documentar todos los componentes (hardware, software, etc.).
2.  **Línea Base (Baseline):** Establecer un punto de referencia conocido y seguro.
3.  **Control de Cambios:** El proceso formal para solicitar, revisar, aprobar y gestionar todos los cambios a esa línea base.
4.  **Verificación y Auditoría:** "Confiar pero verificar". Validar que la configuración actual coincide con la línea base aprobada.

### 🗺️ 1. Inventario de Activos: El Punto de Partida

* **Principio Clave:** 🚨 **No puedes proteger lo que no sabes que tienes.**
* **Desafío:** Mantener el inventario actualizado en un entorno dinámico (VMs, contenedores).
* **Alcance:** Debe incluir todo: hosts físicos, endpoints, software, dispositivos de red y activos de información (datos).

### 📜 2. Líneas Base (Baselines): El Estándar de Oro

Una línea base (o *baseline*) es la configuración documentada y aprobada de un sistema.

* **Propósito:**
    * **Consistencia:** Asegura que todos los servidores web similares estén configurados de la misma manera segura.
    * **Referencia:** Sirve como punto de comparación para detectar "desvíos de configuración".
* **Conexión con la Clasificación:** Las líneas base deben estar ligadas a la clasificación de los datos que maneja el sistema.
    * **Sistema "Alto" (Datos Restringidos):** La línea base exigirá cifrado FIPS 140-2, logging verboso, MFA obligatorio.
    * **Sistema "Bajo" (Datos Públicos):** La línea base será menos estricta.

### 🩹 3. Gestión de Parches y Actualizaciones

Aquí es donde la teoría se encuentra con la realidad operativa.

### **Velocidad vs. Estabilidad**
* El reto es balancear la **velocidad** (parchar antes de ser explotado) con la **estabilidad** (asegurarse de que el parche no rompa la aplicación).

* **El Proceso de Gestión de Parches (No Negociable)**
    1.  **Evaluar:** ¿Es este parche crítico?
    2.  **Testear:** Probar el parche en un entorno de *staging* (pruebas).
    3.  **Validar (Pruebas de Regresión):** Verificar que la funcionalidad principal no se haya roto.
    4.  **Aprobar:** Aprobación formal por el Comité de Control de Cambios (CCB).
    5.  **Implementar:** Desplegar el parche (a menudo en fases).
    6.  **Monitorizar:** Vigilar de cerca los sistemas tras el parche.

* **🛑 El Componente Más Crítico: El Plan de Reversión (Rollback)**
    * Incluso con pruebas perfectas, las cosas pueden salir mal. Un plan de reversión es el "botón de deshacer".
    * **Un plan de cambio sin un plan de reversión es solo una lista de deseos.**
    * Debes ser capaz de restaurar el sistema a su estado funcional anterior rápidamente.

* **El Dilema: Parches Automatizados (Desatendidos)**

| Ventaja (Pro) | Riesgo (Con) |
| :--- | :--- |
| **Velocidad:** Cierra vulnerabilidades de día cero muy rápido. | **Interrupciones:** Un reinicio automático puede ocurrir en un momento de alta demanda. |
| **Consistencia:** Asegura que ningún sistema quede olvidado. | **Daño Colateral:** Un parche defectuoso se propaga instantáneamente a todos los sistemas. |
| **Eficiencia:** Reduce la carga de trabajo manual del equipo de TI. | **Pérdida de Control:** Elimina la revisión humana del proceso de cambio. |
