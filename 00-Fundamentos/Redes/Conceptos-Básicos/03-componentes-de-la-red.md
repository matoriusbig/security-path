# 📚 Guía de Estudio Componentes de la Red

## Módulo: Componentes de Red, Tipos y Conexiones
**Objetivo:** Explicar los roles de los dispositivos de infraestructura de red.

### 1. La Infraestructura de Red 🏗️

> La **Infraestructura de Red** es la plataforma completa que soporta la comunicación. Es el conjunto de hardware y medios que actúa como el "canal" estable y confiable por donde viajan los datos.

La infraestructura se compone de tres categorías principales de hardware.

---

### 2. Las 3 Categorías de Componentes de Red

Tu red, ya sea en casa o en una empresa, está hecha de estos tres tipos de componentes:

1.  **Dispositivos Finales (Hosts)**
2.  **Dispositivos Intermedios**
3.  **Medios de Red**

<img width="800" height="564" alt="image" src="https://github.com/user-attachments/assets/a8bf5da5-deb5-4f2a-971d-97afe251d0b9" />


---

### 3. Categoría 1: Dispositivos Finales (Hosts) 🖥️📱

Estos son los dispositivos con los que interactuamos directamente.

> **Definición Práctica:** Los **Dispositivos Finales** (también llamados **Hosts**) son el **origen** o el **destino** de un mensaje. Forman la interfaz entre el usuario humano y la red.

Si un dispositivo es la *razón* por la que se envía un mensaje, es un dispositivo final.

* **Ejemplos Clave:**
    * **Computadoras:** Estaciones de trabajo, Laptops, Servidores (un servidor es un *host* con un rol especial).
    * **Periféricos de Red:** Impresoras de red, Cámaras de seguridad IP.
    * **Dispositivos de Comunicación:** Teléfonos VoIP, Equipos de teleconferencia.
    * **Dispositivos Móviles:** Smartphones, Tablets, lectores de códigos de barras.


---

### 4. Categoría 2: Dispositivos Intermedios ↔️

Estos dispositivos conectan a los dispositivos finales entre sí o conectan redes. Son el "tráfico" de la red.

> **Definición Práctica:** Los **Dispositivos Intermedios** gestionan el flujo de datos. Reciben datos, toman decisiones (como a *dónde* enviarlos) y los retransmiten. **No son el origen ni el destino** final del mensaje.

*(Nota: Tus apuntes mencionan esta categoría pero la exploran en módulos posteriores. Ejemplos comunes incluyen Switches, Routers y Puntos de Acceso Inalámbrico (AP)).*

---

### 5. Categoría 3: Medios de Red 〰️

Este es el componente físico o invisible por donde viaja la señal.

> **Definición Práctica:** Los **Medios de Red** son el "camino" o canal físico que transporta las señales eléctricas, de luz u ondas de radio entre los dispositivos.

* **Medios Visibles (Cableados):**
    * Cables de Cobre (Ej. Ethernet)
    * Cables de Fibra Óptica (Luz)
* **Medios Invisibles (Inalámbricos):**
    * Ondas de Radio (Wi-Fi, Bluetooth)
    * Frecuencias de telefonía celular
    <img width="802" height="471" alt="image" src="https://github.com/user-attachments/assets/d4911fbe-b04f-4493-b313-7600dfdc9414" />

    # 📚 ISP y Conexiones a Internet

### 1. ¿Qué es un ISP? 🌐

> Un **Proveedor de Servicios de Internet (ISP)** es la empresa que actúa como el **eslabón** entre tu red privada (hogar u oficina) y la Internet pública y global.
<img width="799" height="577" alt="image" src="https://github.com/user-attachments/assets/538d0353-54f1-4dd4-be93-e9f1458a9b32" />

* **Servicios Adicionales:** Además de solo "darte internet", los ISPs suelen ofrecer:
    * Cuentas de correo electrónico.
    * Alojamiento de sitios web (Web Hosting).
    * Almacenamiento en la nube o servicios de backup.
* **El Backbone de Internet:** Los ISPs se conectan entre sí usando enlaces de muy alta velocidad, principalmente de **fibra óptica**, que forman la "columna vertebral" (Backbone) de Internet. Esta estructura jerárquica asegura que el tráfico tome el camino más eficiente.


---

### 2. Topología de Conexión Doméstica 🏠

¿Cómo te conectas físicamente al ISP?

#### ❌ Opción 1: La Forma INSEGURA (Módem Directo)
`ISP --- (Módem) --- PC`

* **Descripción:** Conectar una PC directamente al módem del ISP.
* **¡Riesgo de Seguridad! 🚨:** Esta configuración **no debe usarse**. Expone tu computadora directamente a Internet sin ninguna protección (firewall), haciéndola un blanco fácil para ataques.

#### ✅ Opción 2: La Forma SEGURA (Router Integrado)
`ISP --- (Módem) --- Router --- (Hosts Cableados / Hosts Inalámbricos)`

* **Descripción:** Esta es la conexión estándar y más común.
* **El Rol del Router:** El **router integrado** (como el que sueles tener en casa) es un dispositivo multifunción que generalmente incluye:
    * Un **Router:** Para dirigir el tráfico entre tu red e Internet.
    * Un **Switch:** Varios puertos para conectar dispositivos con cable Ethernet.
    * Un **AP Inalámbrico (WAP):** Para conectar dispositivos por Wi-Fi.
    * Un **Firewall Básico:** Proporciona seguridad esencial para tus dispositivos.
<img width="803" height="456" alt="image" src="https://github.com/user-attachments/assets/84ba0156-2d82-4f95-b8f6-4665186a03af" />

---

### 3. Comparativa: Tecnologías de Conexión al ISP 📡

Existen múltiples maneras de "contratar" Internet. La disponibilidad varía según tu ubicación geográfica.

| Tecnología | Medio Físico | Características Clave | Consideraciones de Seguridad/Rendimiento |
| :--- | :--- | :--- | :--- |
| **Cable** | Cable Coaxial (el de la TV) | Ancho de banda elevado. <br> Conexión "siempre activa". <br> La señal de Internet y TV viajan juntas. | Es un medio **compartido** en el vecindario. El rendimiento puede variar según la cantidad de usuarios conectados. |
| **DSL** (Línea de Abonado Digital) | Línea Telefónica (Cobre) | Ancho de banda elevado (generalmente). <br> Conexión "siempre activa". <br> Usa la línea telefónica sin interrumpir las llamadas de voz. | La velocidad **depende de la distancia** a la oficina central de la compañía telefónica. Más lejos = más lento. |
| **Celular** | Ondas de Radio (Red Móvil) | Acceso donde haya cobertura móvil. <br> Ideal para movilidad. | El rendimiento depende de la señal y la congestión de la torre. <br> **¡Cuidado con los límites de datos (data caps)!** |
| **Satélite** | Ondas de Radio (Satélite) | Buena opción para áreas rurales sin Cable/DSL. <br> Requiere una antena parabólica con línea de visión clara. | Costos de instalación altos. <br> Sufre de **alta latencia** (retraso) debido a la distancia física que viaja la señal. |
| **Dial-Up** (Acceso Telefónico) | Línea Telefónica (Cobre) | Opción de muy bajo costo y muy baja velocidad. <br> Usa un módem para "llamar" al ISP. | **Obsoleto** para uso moderno. No es "siempre activo"; bloquea la línea telefónica mientras se usa. |
| **Fibra Óptica** | Fibra Óptica (Luz) | La opción más rápida y moderna. <br> Velocidades simétricas (igual subida y bajada). <br> Común en áreas metropolitanas. | La mejor opción disponible, pero su despliegue es costoso y limitado geográficamente. |
<img width="809" height="486" alt="image" src="https://github.com/user-attachments/assets/01380503-2574-413e-941c-426a473b3e88" />


