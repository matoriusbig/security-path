# 🗂 Redes Inalámbricas y móviles 
## 🎯 3.0.2 Objetivos del Módulo

En este módulo nos centramos en la **movilidad**, un vector crítico en la infraestructura moderna. El objetivo no es solo conectar dispositivos, sino entender *cómo* se transmiten los datos a través del espectro electromagnético y cómo asegurar esas transmisiones.

- 📡 **Infraestructura:** Comprender la diferencia entre redes celulares (GSM/4G/5G) y redes locales (Wi-Fi/Bluetooth).
- 📱 **Configuración:** Provisionamiento de conectividad en SO móviles (Android/iOS).
- 🛡️ **Seguridad:** Implementación de VPNs y cifrado en medios no guiados.

---

## 📡 3.1.3 El Espectro de Conectividad Móvil

Los dispositivos modernos (Smartphones, Tablets, IoT) utilizan múltiples radios para comunicarse. Como analistas, debemos saber cuál usar según el alcance y la necesidad de ancho de banda.

### Tabla Comparativa de Tecnologías

| **Tecnología** | **Alcance** | **Uso Principal** | **Definición Técnica** |
| --- | --- | --- | --- |
| **GPS** (Global Positioning System) | Global 🌍 | Geolocalización | Sistema de navegación por satélite. El dispositivo **recibe** señales de tiempo de múltiples satélites para triangular su posición (precisión ~10m). *Nota: El GPS convencional no transmite datos, solo recibe.* |
| **Wi-Fi** (IEEE 802.11) | Local (LAN) 🏠 | Acceso a Internet de alta velocidad | Protocolo de red inalámbrica que conecta dispositivos a un **Access Point (AP)**. Crea una WLAN (Wireless LAN). |
| **Bluetooth** (IEEE 802.15.1) | Corto (PAN) 🎧 | Periféricos y accesorios | Tecnología de baja potencia para **WPAN (Wireless Personal Area Network)**. Ideal para conectar auriculares, relojes o transferir archivos pequeños. |
| **NFC** (Near Field Communication) | Inmediato (<4cm) 💳 | Pagos y Credenciales | Subconjunto de RFID. Permite comunicación bidireccional segura a distancias extremadamente cortas mediante inducción electromagnética. |

### 💡 Concepto Clave: Red Celular

Las redes móviles (GSM, 3G, 4G/LTE, 5G) funcionan mediante una malla de **Celdas (Cells)**.

- El teléfono se comunica con una torre base a través de ondas de radio.
- Al moverse, la señal se transfiere de una torre a otra sin cortar la conexión. Esto se llama **Handover**.

---

## 🛡️ 3.2.1 Seguridad en Wi-Fi (Critical for Cybersecurity)

El Wi-Fi es intrínsecamente inseguro por defecto porque el medio de transmisión es el **aire** (cualquiera con una antena puede interceptar la señal).

> ⚠️ Advertencia: Las redes Wi-Fi públicas (Cafeterías, Aeropuertos) son zonas hostiles. Un atacante puede realizar ataques Man-in-the-Middle (MitM) fácilmente.
> 

### Mejores Prácticas de Seguridad Móvil

1. **Evitar Texto Plano:** NUNCA envíes credenciales (usuario/contraseña) sobre HTTP o protocolos no cifrados (Telnet, FTP).
2. **Uso de VPN (Virtual Private Network):**
    - *Definición:* Crea un túnel cifrado sobre una red insegura. Aunque intercepten tu tráfico Wi-Fi, solo verán basura cifrada.
    - *Acción:* Activar VPN siempre que se use Wi-Fi público.
3. **Cifrado Robusto:**
    - En redes domésticas o corporativas, usar **WPA2 (Wi-Fi Protected Access 2)** o superior (WPA3).
    - Evitar WEP (obsoleto y vulnerable).

<img width="3999" height="2283" alt="image" src="https://github.com/user-attachments/assets/8c6ffb7e-5224-4fb9-9f18-527e1b3bfd6a" />

---

## ⚙️ 3.2.2 - 3.2.4 Configuración de Wi-Fi y Datos Móviles

La configuración de red en móviles se divide en dos grandes mundos: **Android** y **iOS**.

### 📶 Conexión a Wi-Fi (SSID)

El **SSID (Service Set Identifier)** es el nombre técnico de la red.

- **Broadcast activado:** La red aparece en la lista automáticamente.
- **Broadcast desactivado (Red Oculta):** Debes ingresar el SSID y la contraseña manualmente. Requiere coincidencia exacta (Mayúsculas/Minúsculas).

**Flujo de conexión manual:**

1. Ir a Ajustes > Wi-Fi.
2. Seleccionar "Otra red" o "Agregar red".
3. Ingresar **SSID**.
4. Seleccionar **Tipo de Seguridad** (ej. WPA2-PSK).
5. Ingresar **Passphrase** (Contraseña).

### 📶 Datos Celulares (Mobile Data)

Cuando no hay Wi-Fi, el dispositivo usa la red celular.

- **Prioridad:** Los móviles están programados para priorizar Wi-Fi sobre Datos Celulares para ahorrar batería y consumo de plan de datos.
- **Roaming (Itinerancia):** Capacidad de usar torres de otros operadores (generalmente con costo extra).

> Tip Práctico: En incidentes de seguridad o forense, poner el dispositivo en Modo Avión es el primer paso para aislarlo de la red y evitar el borrado remoto de datos.
> 

---

## 🦷 3.2.6 - 3.2.7 Bluetooth & Emparejamiento

Bluetooth elimina los cables para crear una **WPAN**. Puede conectar hasta **8 dispositivos** simultáneamente en una "Piconet".

### Casos de Uso Comunes

- **Manos libres / Audio:** (Headsets, Car Audio).
- **HID (Human Interface Device):** Teclados y ratones.
- **Tethering (Anclaje a red):** Compartir la conexión de internet del móvil a una laptop vía Bluetooth (aunque es más lento que vía Wi-Fi).

### El Proceso de Emparejamiento (Pairing)

Es el proceso de establecer confianza entre dos dispositivos Bluetooth.

1. **Discovery (Descubrimiento):** Un dispositivo se pone en modo "Visible" (transmite su nombre y dirección MAC).
2. **Request:** El dispositivo iniciador solicita conexión.
3. **Authentication (PIN):** Se intercambia un PIN numérico para asegurar que te estás conectando al dispositivo correcto y no a un atacante cercano.
4. **Connection:** Se guarda la llave de enlace para no repetir el proceso.

<img width="2500" height="3000" alt="image" src="https://github.com/user-attachments/assets/243b09c2-2a76-4e6a-b2a9-890b06b0829b" />

---

## 📝 Resumen:

- **Diversidad de Redes:** Un dispositivo móvil es un hub de comunicaciones que gestiona GPS (ubicación), Cellular (WAN), Wi-Fi (WLAN), Bluetooth (WPAN) y NFC (Proximidad).
- **La Seguridad es Prioridad:** Como futuros profesionales de ciberseguridad, entendemos que **Wi-Fi Público = Peligro**. El uso de VPNs y protocolos cifrados (WPA2/HTTPS) no es opcional, es obligatorio.
- **Gestión de Energía:** El Wi-Fi consume menos batería que los datos celulares 4G/5G.
- **Handover:** La capacidad de mantener una llamada mientras te mueves entre torres celulares es la base de la telefonía móvil moderna.
