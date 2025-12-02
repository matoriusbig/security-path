# 🚀 2.2 - Recuperación ante Desastres (DRP, RTO/RPO)

La Recuperación ante Desastres (DR) son las actividades necesarias para **restaurar** los servicios de TI y comunicaciones de una organización después de una interrupción.

Este plan es la misión del "Cirujano Reconstructivo" 🩺: **Restaurar** la tecnología (servidores, datos, redes) a sus operaciones **normales** lo más rápido posible **después** del desastre.

El DRP es el componente técnico del BCP.

---

## 🎯 Definiendo los Objetivos (RTO & RPO)

El BIA nos da dos métricas críticas que **dictan** cómo debe ser nuestro DRP:

1.  **RTO (Recovery Time Objective) - Tiempo Objetivo de Recuperación**
    * **Qué es:** El tiempo máximo tolerable que un sistema o función crítica puede estar **caído** después de un desastre.
    * **Pregunta Clave:** "¿Cuán rápido debemos levantarnos?"
    * **Ejemplo (del BIA):** "La empresa puede sobrevivir **una semana** sin facturación". El RTO es <= 1 semana. Un RTO de 1 hora (ej. sistema de trading) es muchísimo más caro de implementar que un RTO de 1 semana.

2.  **RPO (Recovery Point Objective) - Punto Objetivo de Recuperación**
    * **Qué es:** La cantidad máxima tolerable de **pérdida de datos** medida en tiempo (el "gap").
    * **Pregunta Clave:** "¿Cuántos datos podemos permitirnos perder?"
    * **Ejemplo:** Si hacemos backups cada 24 horas, nuestro RPO es de 24 horas. Si el sistema cae a las 5 PM y el último backup fue a la medianoche, hemos perdido 17 horas de datos. El BIA debe decir si eso es aceptable.

---

## 🛠️ Anatomía de un DRP de Élite

Un DRP no es un solo documento; es una **biblioteca de documentos** adaptada a diferentes audiencias:

* **📄 Resumen Ejecutivo:** Visión general de alto nivel para la alta dirección (C-Suite).
* **📑 Planes Específicos del Departamento:** Qué deben hacer los líderes de negocio (Finanzas, RRHH, etc.).
* **💻 Guías Técnicas (Runbooks):** Instrucciones detalladas (paso a paso) para que el personal de TI restaure los sistemas críticos en el **orden correcto** (¡dependencias!).
* **✅ Listas de Verificación (Checklists):**
    * Para el Equipo de DR: Acciones inmediatas para guiar la respuesta en el caos.
    * Para Gerentes y RR.PP.: Documentos fáciles de seguir para comunicar con precisión.

---

## 💥 Desafíos Críticos del DR (Donde fallan los planes)

Un DRP que solo dice "restaurar el último backup" es un plan fallido.

### Desafío 1: El Backup Infectado (El Peligro del *Dwell Time* ⏳)

Los atacantes a menudo permanecen latentes (*dwell time*) para infectar también los backups.

* **Ejemplo (Hospital LA):** 🏥 Tomó **260 días** (casi 9 meses) descubrir una brecha. Al intentar restaurar desde el "último backup", el malware (basado en tiempo) simplemente se reactivaba.
* **La Solución Real:** Tuvieron que retroceder casi un año para encontrar un **"Último Backup Confiable Conocido" (Last Known Good Backup)** y luego reconstruir manualmente los 9 meses de datos perdidos.



El gráfico anterior ilustra este momento de la verdad:

1.  **Eventos 1-13 (Verde):** Transacciones normales y backups limpios (Backup 13 es el último confiable).
2.  **🔴 INCIDENTE OCURRE 🔴:** Un malware entra al sistema.
3.  **Eventos 15-21 (Naranja):** Transacciones comprometidas.
4.  **Backups (Naranja):** Backups tomados **después** del incidente. ¡Están infectados!
5.  **⚫ DETECCIÓN ⚫:** El equipo descubre el incidente.
6.  **La Decisión del DR:** El equipo **no puede** restaurar desde el último backup (naranja). Debe retroceder hasta el **Backup 13**.
7.  **La Pérdida de Datos (El "Gap"):** El negocio perderá todos los datos entre el Backup 13 y la Detección. Esto es el **RPO** en la práctica.

### Desafío 2: Las Dependencias Ocultas (El Flujo de Datos) 🔗

Restaurar un sistema es inútil si no se entienden sus dependencias (identificadas en el BIA).

* **Ejemplo (Hospital 2):** 🩺 El sistema de Radiología es diferente al del Laboratorio. Pero ambos se alimentan de una BBDD central de registros de pacientes.
* **Fracaso del DR:** Un plan que solo respalda el servidor de Radiología, pero no la BBDD central de la que depende, es inútil. No se podrían crear nuevos pacientes.

> **🧠 Dato:** El DRP **debe** estar alineado con el BIA para entender el **flujo de datos** y las dependencias entre aplicaciones, no solo hacer un inventario de servidores.

---

### 📖 Términos Clave del Glosario

* **🌀 Recuperación ante desastres (DR):** en términos de sistemas de información, las actividades necesarias para restaurar los servicios de comunicaciones y de TI en una organización durante y después de una interrupción, interrupción o perturbación de cualquier tipo o escala.
* **🚑 Plan de recuperación ante desastres (DRP):** los procesos, políticas y procedimientos relacionados con la preparación para la recuperación o la continuación de las funciones comerciales críticas, la infraestructura tecnológica, los sistemas y las aplicaciones de una organización después de que la organización experimente un desastre.
