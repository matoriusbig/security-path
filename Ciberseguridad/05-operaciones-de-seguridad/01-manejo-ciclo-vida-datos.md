# 🗃️ 5.1 - Manejo y Ciclo de Vida de los Datos

Para proteger los datos, primero debemos entender su viaje. El manejo de datos (Data Handling) es la implementación de políticas y procedimientos para gestionar el ciclo de vida de los datos, aplicando los controles correctos en el momento adecuado.

---

## 🌀 El Ciclo de Vida de los Datos

1.  **Crear:** La generación de nuevos datos (Ej: Un usuario escribe un informe).
2.  **Almacenar:** Guardar los datos en un medio (Ej: Un disco duro, una base de datos).
3.  **Usar:** Datos en uso activo (Ej: Abiertos en una aplicación, siendo procesados).
4.  **Compartir:** Transferir datos a otros usuarios o sistemas (Ej: Envío por correo, vía API).
5.  **Archivar:** Respaldo a largo plazo de datos que no están en uso activo.
6.  **Destruir:** Eliminación permanente y segura de los datos.

Estos pasos se alinean con los **tres estados de los datos**:

* **Datos en Reposo (Data at Rest):** Almacenados (Ej: Cifrado de disco).
* **Datos en Movimiento (Data in Motion):** Transfiriéndose (Ej: Cifrado TLS/SSL).
* **Datos en Uso (Data in Use):** Siendo procesados (Ej: Cifrado homomórfico, TEEs).

---

## 🔑 Prácticas Clave para el Manejo de Datos

### 1. El Porqué: Regulaciones y Riesgo

No todos los datos son iguales. Su valor (y el riesgo asociado) dictan cómo deben protegerse.

**Ejemplo Práctico: Cumplimiento Normativo**

* **HIPAA (Salud, EE. UU.):** Los registros médicos tienen requisitos de retención específicos (Ej: 10 años).
* **OSHA (Laboral, EE. UU.):** Un registro de lesión laboral puede requerir retención por más de 30 años.
* **PCI DSS (Financiero, Global):** Regula estrictamente cómo se almacena y procesa la información de tarjetas de crédito.
* **GDPR / RGPD (Privacidad, UE):** Impone reglas severas sobre el manejo de datos personales y financieros.

**Conclusión:** Una sola pieza de datos puede estar sujeta a múltiples regulaciones. El incumplimiento genera riesgos legales y financieros.

### 2. El Cómo: Clasificación, Retención y Destrucción

#### 🏷️ Clasificación y Etiquetado

* **Clasificación:** Es el proceso de evaluar el impacto para la organización si la Confidencialidad, Integridad o Disponibilidad (C.I.A.) de los datos se ve comprometida.
* **Etiquetado:** Es la implementación práctica de la clasificación. Es la "etiqueta" física o digital que indica el nivel de sensibilidad y las reglas de manejo.

**Niveles de Sensibilidad (Ejemplo Práctico)**

| Etiqueta | Nivel de Sensibilidad | Descripción | Ejemplo |
| :--- | :--- | :--- | :--- |
| **Altamente Restringido** | Alto | Su compromiso amenaza la existencia de la organización. | Secretos comerciales, claves raíz de cifrado. |
| **Moderadamente Restringido** | Medio | Su compromiso causa pérdida de ventaja competitiva o interrupciones. | Planes de marketing, datos financieros internos. |
| **Sensibilidad Baja** | Bajo | "Solo para uso interno". Su compromiso causa molestias menores. | Políticas internas, organigramas. |
| **Público** | Nulo | Ya está publicado. No hay daño por su divulgación. | Comunicados de prensa, sitio web público. |

#### 💾 Retención de Datos

Las políticas de retención definen cuánto tiempo deben conservarse los datos.

* **Regla de Oro:** Conservar los datos solo durante el tiempo que sea **legalmente requerido** o que **aporte valor comercial**, ni más ni menos.
* **Error Común:** Aplicar el período de retención más largo a todos los datos. Esto es un error costoso:
    * Aumenta los costos de almacenamiento.
    * Incrementa el riesgo de exposición en caso de brecha.
    * Puede violar regulaciones (como el GDPR, que exige eliminar datos cuando ya no son necesarios).

#### 💥 Destrucción y Remanencia de Datos

* **Remanencia de Datos:** Los datos residuales que quedan en un medio después de un intento de eliminación (Ej: Vaciar la "papelera de reciclaje" no borra los datos).
* **Destrucción Defendible:** Tener un mandato regulatorio o una política que respalde la decisión de destruir los datos.
* **Métodos de Destrucción:**
    * **Limpiar (Clearing):** Sobrescribir los datos con nuevos datos (Ej: Escribir patrones de ceros y unos). Generalmente se hace por software.
    * **Purgar (Purging):** Un borrado más avanzado que elimina la posibilidad de recuperación.
        * **Desmagnetización (Degaussing):** Usar un imán potente para neutralizar el campo magnético en discos duros (HDD) y cintas.
    * **Destrucción Física:** El método más seguro.
        * Trituración, pulverización, incineración o grabado con ácido.
