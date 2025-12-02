# 🔒 5.3 - Principios Fundamentales de Criptografía

La criptografía es la ciencia de proteger la información. El cifrado es el proceso de transformar datos (texto sin formato) en un formato ilegible (texto cifrado).

Proporciona servicios clave:
* **Confidencialidad:** Oculta el contenido del mensaje.
* **Integridad:** Asegura que el mensaje no ha sido alterado.
* **(No Repudio):** A través de firmas digitales.

---

## 1. Cifrado Simétrico (Clave Secreta)

Usa la **misma clave** para cifrar y descifrar. Es **rápido** y eficiente.

* **Flujo:**
    Texto sin formato ➔ (Cifrar con Clave A) ➔ Texto Cifrado ➔ (Descifrar con Clave A) ➔ Texto sin formato
* **Desafíos:**
    * **Distribución de Claves:** ¿Cómo compartes la clave secreta de forma segura con el receptor? (Requiere un canal "fuera de banda" o *out-of-band*).
    * **Escalabilidad:** Si 1000 personas necesitan comunicarse de forma segura entre sí, se necesitarían 499,500 claves únicas.
* **Usos Principales:** Cifrado masivo de datos (discos duros, copias de seguridad), cifrado de canales (IPsec, TLS), *streaming*.

## 2. Cifrado Asimétrico (Clave Pública/Privada)

Usa un **par de claves** matemáticamente relacionadas: una pública (se comparte) y una privada (se mantiene en secreto).

* **Flujo (Confidencialidad):**
    * El Emisor cifra el mensaje con la **clave pública** del Receptor.
    * Solo el Receptor puede descifrarlo con su **clave privada**.
* **Ventajas:**
    * Resuelve la distribución de claves (la clave pública puede enviarse por canales no seguros).
    * Resuelve la escalabilidad.
    * Permite **Firmas Digitales (No Repudio):** Si cifras algo con tu clave *privada*, cualquiera puede verificar que fuiste tú usando tu clave *pública*.
* **Desventaja:** Es muy **lento** comparado con el simétrico.
* **Uso Real (Híbrido):** Se usa lo mejor de ambos. El cifrado asimétrico se usa para intercambiar de forma segura una clave simétrica (clave de sesión), y luego toda la comunicación masiva se cifra con esa clave simétrica rápida.

## 3. Funciones Hash (Integridad)

Un hash (o resumen) es una **huella digital** única de los datos. Toma una entrada de cualquier tamaño y produce una salida de tamaño fijo.

* **Flujo:** Datos de entrada ➔ (Algoritmo Hash) ➔ Valor Hash (Ej: `8ACAD682...`)
* **Propiedades Clave:**
    * **Determinista:** La misma entrada siempre da el mismo hash.
    * **No Reversible:** No se puede obtener la entrada original a partir del hash.
    * **Resistente a Colisiones:** Es computacionalmente inviable que dos entradas diferentes produzcan el mismo hash.
    * **Efecto Avalancha:** Un cambio mínimo en la entrada (Ej: una letra) cambia drásticamente el hash de salida.
* **Usos:**
    * **Verificación de Integridad (Checksums):** Se usa para asegurar que un archivo descargado no se ha corrompido o alterado.
    * **Almacenamiento de Contraseñas:** NUNCA almacenes contraseñas en texto plano. Almacena su hash. Cuando el usuario inicia sesión, haces un hash de la contraseña que te da y la comparas con el hash almacenado.
