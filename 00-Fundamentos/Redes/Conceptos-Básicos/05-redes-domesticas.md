# 📡 Implementación y Seguridad en Redes SOHO (Small Office/Home Office)
---
## 1. Arquitectura y Componentes de la Red 🏠

En el entorno moderno, la red ya no conecta solo computadoras. La superficie de ataque se ha expandido debido al **IoT (Internet of Things)**.

### Dispositivos Típicos (Endpoints)
La red SOHO actual debe soportar una variedad de dispositivos, cada uno con diferentes requisitos de ancho de banda y seguridad:
* 🖥️ **Workstations:** PC de escritorio, Laptops.
* 🎮 **Entretenimiento:** Consolas, Smart TVs.
* 📱 **Móviles:** Smartphones, Tablets.
* 🧊 **IoT:** Termostatos, Cámaras IP, Impresoras.
<img width="798" height="431" alt="image" src="https://github.com/user-attachments/assets/ae93f822-6189-42df-a76c-17652650ad44" />


> **🛡️ Nota:** Cada dispositivo IoT conectado aumenta la "superficie de ataque". Una cámara de seguridad mal configurada puede ser la puerta trasera para comprometer toda la red interna.


---

## 2. El Enrutador Inalámbrico: El Corazón de la Red 🧠

En redes domésticas, lo que llamamos "Router" es en realidad un dispositivo **"Todo en Uno"** que combina tres funciones:
1.  **Router:** Encamina tráfico entre redes (Tu casa e Internet).
2.  **Switch:** Conecta dispositivos cableados en la misma red (LAN).
3.  **Wireless Access Point (WAP):** Conecta dispositivos inalámbricos.

### Puertos Físicos y Segmentación
Es crítico distinguir las zonas de confianza basándose en los puertos:

| Tipo de Puerto | Etiqueta Común | Función Técnica | Nivel de Confianza |
| :--- | :--- | :--- | :--- |
| **Puertos LAN** | Ethernet 1-4 | Conexión al Switch interno. Misma subred local. | 🟢 Alto (Red Interna) |
| **Puerto WAN** | Internet / WAN | Conexión al Módem (ISP). Recibe IP Pública. | 🔴 Bajo (Internet Hostil) |

<img width="675" height="546" alt="image" src="https://github.com/user-attachments/assets/c405a053-c1b1-4007-9ad5-ab90ab8bbb5b" />

---

## 3. Medios de Transmisión: Capa 1 (Física) 🔌

La conectividad se divide en medios guiados (cables) y no guiados (frecuencias de radio).

### 3.1 Tecnologías Inalámbricas (RF Spectrum)
Las redes Wi-Fi operan en bandas **no licenciadas** del espectro electromagnético.

* **Bluetooth (PAN):** Baja energía, corto alcance. Usado para periféricos.
* **Wi-Fi (WLAN):** Alto rendimiento. Opera principalmente en dos frecuencias:
    * **2.4 GHz:** Mayor alcance (atraviesa paredes), pero más interferencia y menor velocidad.
    * **5 GHz:** Menor alcance, pero mayor velocidad y canales más limpios.
<img width="803" height="437" alt="image" src="https://github.com/user-attachments/assets/819f25d2-b214-49fc-b4d3-8a6aac9e86f1" />


### 3.2 Tecnologías Cableadas (Ethernet)
Para tareas críticas (servidores, gaming, streaming 4K), el cable siempre supera al Wi-Fi en estabilidad y seguridad (es más difícil de interceptar).

#### Tipos de Cableado Comunes:

* **Par Trenzado (UTP - Cat5e/Cat6):**
    El estándar de oro para LAN. Los pares están trenzados para cancelar la interferencia electromagnética (EMI).

  <img width="221" height="153" alt="image" src="https://github.com/user-attachments/assets/aaa1daf5-eb04-4776-a309-74b2acda4138" />

* **Cable Coaxial:**
    Usado comúnmente por proveedores de cable para traer Internet a la casa (HFC). Tiene un blindaje robusto.

  <img width="221" height="147" alt="image" src="https://github.com/user-attachments/assets/a4ef85be-e93f-437c-b834-d50d36161141" />

* **Fibra Óptica:**
    Transmisión de datos mediante luz. Inmune a interferencias electromagnéticas y capaz de velocidades extremas y largas distancias.

  <img width="850" height="568" alt="image" src="https://github.com/user-attachments/assets/0829d7f6-c7c9-4379-ae6c-8b6abfdbcc2d" />

---

## 4. Estándares y Gobernanza ⚖️

Para que un iPhone se conecte a un Router (De Cisco por ejemplo), deben hablar el mismo idioma.

* **IEEE (Institute of Electrical and Electronics Engineers):** Crean el estándar técnico (ej. **802.11**).
* **Wi-Fi Alliance:** Certifican que los dispositivos comerciales cumplen con esos estándares (Interoperabilidad).

> **💡 Pro Tip:** En ciberseguridad, conocer el estándar es vital. Por ejemplo, saber que el estándar antiguo **WEP** es inseguro y debe ser reemplazado por **WPA2/WPA3**.

---

## 5. Configuración y Hardening del Router ⚙️

Aquí es donde aplicamos la teoría para asegurar la red. La configuración se realiza típicamente a través de una interfaz web (GUI).

### Configuración Básica de WLAN


#### 1. Modo de Red (Network Mode)
Define qué estándares 802.11 soporta el router (b/g/n/ac/ax).
* **Modo Mixto (Mixed):** Alta compatibilidad. Permite conectar dispositivos viejos y nuevos.
* **Modo Nativo (ej. Solo "n" o "ac"):** Mayor rendimiento, pero excluye dispositivos antiguos.

#### 2. SSID (Service Set Identifier)
Es el nombre de la red.
* **❌ Mala práctica:** Dejar el nombre por defecto (ej. "Linksys", "Netgear"). *Razón:* Revela el modelo del equipo al atacante, facilitando la búsqueda de vulnerabilidades específicas (CVEs).
* **❌ Mala práctica:** Usar nombres personales ("Familia_Perez").
* **✅ Buena práctica:** Usar nombres genéricos o disuasorios.

#### 3. Difusión del SSID (SSID Broadcast)
Determina si el router "anuncia" su presencia.
* **Mito de Seguridad:** "Ocultar el SSID me hace invisible".
* **Realidad:** Un hacker con herramientas básicas (como `airodump-ng`) puede descubrir un SSID oculto en segundos cuando un cliente legítimo intenta conectarse. **La seguridad por oscuridad no es seguridad real.**

#### 4. Canales (Channels)
La configuración `Auto` suele funcionar, pero en edificios densos, fijar un canal menos saturado mejora el rendimiento y evita ataques de denegación de servicio por interferencia.
<img width="850" height="681" alt="image" src="https://github.com/user-attachments/assets/3094a9db-0a83-42bf-bb86-5246dcc6d62f" />

---

## 6. Consideraciones de Diseño Seguro 🛡️

Antes de desplegar la red, hazte estas preguntas como un CISO:

1.  **¿Segmentación de Red?**
    * Usa la función **"Red de Invitados" (Guest Network)**.
    * Esto aísla a las visitas y dispositivos IoT inseguros de tu red principal donde guardas tus datos sensibles.

2.  **¿Compatibilidad vs. Seguridad?**
    * Si habilitas "Modo Legacy" (soporte para 802.11b), podrías estar forzando al router a usar mecanismos de cifrado más débiles. Intenta mantener solo los estándares más recientes posibles.

3.  **¿Gestión de Acceso?**
    * Cambia **siempre** la contraseña de administración del router por defecto (`admin/admin` es lo primero que prueba un atacante).
