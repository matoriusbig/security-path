# 📶 4.4 - Seguridad en Redes Inalámbricas (WPA2/WPA3)

Las redes inalámbricas (Wi-Fi) son un vector de ataque único porque la "red" ya no termina en la pared; se transmite por el aire. Un atacante puede intentar romper la red desde el estacionamiento.

* **Riesgo Fundamental:** Una red cableada requiere acceso físico. Una red inalámbrica solo requiere estar dentro del rango de la señal.

---

### 1. 🔒 Estándares de Cifrado (La Evolución de la Seguridad)

| Estándar | Cifrado | ¿Por qué es Inseguro? | Estado Actual |
| :--- | :--- | :--- | :--- |
| **WEP** (Wired Equivalent Privacy) | RC4 | **Totalmente Roto.** Fallos fundamentales en el IV (Vector de Inicialización). Se puede *crackear* en minutos. | **Obsoleto.** Ver esto es una bandera roja de auditoría. |
| **WPA** (Wi-Fi Protected Access) | RC4 + **TKIP** | Una "curita" temporal para WEP. TKIP era mejor, pero también demostró ser vulnerable. | **Obsoleto.** |
| **WPA2** (Wi-Fi Protected Access 2) | AES + **CCMP** | **El estándar de oro por una década.** Fuerte, basado en el cifrado AES. | **Requisito Mínimo.** (Vulnerable al ataque KRACK). |
| **WPA3** | AES + (Mejoras) | **El estándar moderno.** Reemplaza PSK con **SAE** (Simultaneous Authentication of Equals), lo que lo hace resistente a ataques de diccionario *offline*. | **Recomendado.** |

### 2. 🔑 Modos de Autenticación (¿Quién puede conectarse?)

* **Personal (WPA2/WPA3-PSK):**
    * **Qué es:** **Clave Pre-Compartida (Pre-Shared Key)**. Es la "contraseña del Wi-Fi" que todos en tu casa u oficina comparten.
    * **Riesgo:** Si una persona se va, debes cambiar la contraseña para *todos*. No hay contabilidad individual.
* **Enterprise (WPA2/WPA3-Enterprise):**
    * **Qué es:** Usa el estándar **IEEE 802.1X**. No hay una sola contraseña.
    * **Cómo funciona:** Cada usuario se autentica con sus **propias credenciales** (usuario y contraseña de red) contra un servidor central (**RADIUS**).
    * **Ventaja CISO:** Permite **control de acceso granular** (RBAC), **contabilidad** (sabes quién se conectó) y *offboarding* instantáneo (simplemente desactivas la cuenta del empleado).

### 3. 📡 Ataques Inalámbricos Comunes

* **Access Point (AP) Malicioso (Rogue AP):**
    * Un empleado (generalmente sin mala intención) conecta un router Wi-Fi barato a un puerto de red en la pared de la oficina para tener "mejor señal".
    * **Resultado:** Crea un punto de entrada a la red corporativa que *evita* todos los controles de seguridad perimetrales.
* **Gemelo Maligno (Evil Twin):**
    * Un atacante configura un AP con el mismo nombre (SSID) que la red legítima (ej. "Starbucks_Gratis").
    * **Resultado:** Los dispositivos de los usuarios se conectan automáticamente al AP del atacante (que tiene señal más fuerte). El atacante ahora está en una posición de **Man-in-the-Middle (MitM)**, listo para robar credenciales y espiar el tráfico.
* **Ataque de Desautenticación:**
    * El atacante envía paquetes de "desautenticación" (spoofing) al AP, forzando a los usuarios legítimos a desconectarse.
    * **Propósito:** Forzar a los usuarios a volver a conectarse, permitiendo al atacante capturar el *handshake* de WPA2 para un ataque de *cracking* offline.

### 4. 🛡️ Mejores Prácticas de Endurecimiento

1.  **Segmentación:** La red Wi-Fi de **Invitados** debe estar en su propia **VLAN** y **totalmente aislada** de la red corporativa interna.
2.  **Usar WPA3-Enterprise:** Siempre que sea posible. Si no, WPA2-Enterprise. Usar PSK solo en entornos muy pequeños o domésticos.
3.  **Deshabilitar WPS (Wi-Fi Protected Setup):** El "botón" para conectarse fácilmente es notoriamente vulnerable a ataques de fuerza bruta.
4.  **Ocultar el SSID (Nombre de Red):** Considerado "seguridad por oscuridad". No detiene a un atacante serio (que puede encontrarlo fácilmente), pero puede disuadir a los oportunistas.
5.  **Filtrado de Direcciones MAC:** Solo permitir que direcciones MAC *conocidas* se conecten.
    * **Advertencia:** Un atacante puede suplantar (spoof) fácilmente una dirección MAC permitida, por lo que esto no debe ser tu *único* control.
