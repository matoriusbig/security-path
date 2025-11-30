Este documento fusiona los conceptos fundamentales de *networking* (qué es una red, cómo viajan los datos)

## 🌍 Sección 1: El Panorama General - ¿Qué es una Red?

Todo en ciberseguridad comienza y termina con la red. Si no hay conexión, no hay riesgo... ni utilidad.

### 1.1 La Red de Redes (Internet)

Internet no es una "nube"; es una colección global masiva de redes interconectadas (**internetwork**) que se comunican usando estándares comunes (como TCP/IP).

- **Propiedad:** Nadie es "dueño" de Internet. Es una entidad descentralizada.
- **Componentes:** Se compone de cables de fibra óptica, cables de cobre, enlaces satelitales y transmisiones inalámbricas.

### 1.2 Tipos de Redes (Escala)

La escala de la red define el primer perímetro de defensa.

| **Tipo de Red** | **Acrónimo** | **Alcance** | **Ejemplo Práctico** |
| --- | --- | --- | --- |
| **Oficina Pequeña/Doméstica** | SOHO | Un solo usuario o una familia. | Tu red Wi-Fi en casa, conectando 2-3 portátiles y una impresora. |
| **Red Local** | LAN | Un edificio o campus. | La red de una escuela o una oficina corporativa. |
| **Mediana a Grande** | (Empresarial) | Múltiples ubicaciones, cientos/miles de hosts. | Un banco con múltiples sucursales conectadas. |
| **Mundial** | WAN / Internet | Todo el planeta. | Conectarse desde Chile a un servidor en Japón. |

### 1.3 El Auge de los Dispositivos Conectados (IoT)

Cada dispositivo conectado es un *endpoint* y un vector de ataque potencial.

- **📱 Dispositivos Móviles:** Smartphones, tabletas, relojes y gafas inteligentes.
- **🏠 Dispositivos Domésticos:** Smart TVs, sistemas de seguridad, termostatos, electrodomésticos.
- **🚗 Otros Dispositivos (IoT):**
    - **Automóviles Inteligentes:** Acceden a mapas y pueden reportar su estado.
    - **Etiquetas RFID:** Rastreo de inventario o activos.
    - **Sensores y Actuadores:** En agricultura o industria, para monitorear y actuar (ej. riego).
    - **Dispositivos Médicos:** Marcapasos, bombas de insulina que reportan datos vitales.

---

## 🚦 Sección 2: Transmisión de Datos - ¿Cómo Hablan las Máquinas?

Para proteger los datos, debemos entender cómo se ven en su forma más básica.

### 2.1 El Lenguaje Binario: Bits y Bytes

Toda comunicación digital se reduce a esto:

- **Bit (Binary Digit):** La unidad más pequeña de datos. Solo puede ser **0** (apagado) o **1** (encendido).
- **Byte:** Un grupo de 8 bits. Se usa comúnmente para representar un carácter.
- **ASCII:** Un estándar que asigna patrones de bits (bytes) a caracteres.

> Ejemplo Práctico: Código ASCII
> 
> 
> Cuando presionas la tecla 'A' en tu teclado:
> 
> - Tu teclado envía la señal: `01000001`
> - La computadora lo interpreta como: **A**
> 
> Un analista de seguridad que mira tráfico de red (en *raw*) puede necesitar interpretar estos valores.
> 

### 2.2 Métodos de Transmisión (El Medio Físico)

Los bits viajan como señales a través de diferentes medios físicos.

| **Método** | **Señal** | **Medio Físico** | **Ejemplo de Uso** |
| --- | --- | --- | --- |
| **Eléctrico** ⚡ | Pulsos eléctricos | Cable de Cobre (Ej. Cat 6) | Conexiones LAN en una oficina. |
| **Óptico** 💡 | Pulsos de luz | Cable de Fibra Óptica | Conexiones troncales de Internet, data centers. |
| **Inalámbrico** 📡 | Ondas de radio/microondas | El aire (Wi-Fi, Bluetooth) | Tu laptop conectada al router Wi-Fi. |

### 2.3 Tipos de Datos del Usuario

Como analistas, no solo protegemos los bits, protegemos la *información* que representan.

- **Datos Voluntarios:** Información que compartes explícitamente (Ej. tu perfil de LinkedIn).
- **Datos Observados:** Registrados por tus acciones (Ej. tu historial de ubicaciones de Google Maps).
- **Datos Inferidos:** Creados sobre ti basándose en otros datos (Ej. tu "puntaje de crédito" o perfil de consumidor).

---

## 🚀 Sección 3: Rendimiento de Red - Velocidad vs. Realidad

Estos conceptos son cruciales para entender ataques como DDoS, que saturan la capacidad de la red.

- **Ancho de Banda (Bandwidth):**
    - **Definición:** La **capacidad teórica** máxima de un medio para transportar datos. Es como el número de carriles en una autopista.
    - **Medición:** Se mide en bits por segundo (bps).
- **Rendimiento (Throughput):**
    - **Definición:** La **medida real** de la transferencia de datos. Es cuántos autos *realmente* pasan por la autopista, considerando el tráfico.
    - **Impacto:** El *throughput* siempre es menor que el ancho de banda debido a la latencia y la sobrecarga (overhead) de los protocolos.
- **Latencia (Latency):**
    - **Definición:** El **retraso** (delay). Es el tiempo que tardan los datos en ir del punto A al punto B.
    - **Impacto:** Una alta latencia (un ping alto) hace que la red se sienta lenta, incluso con un gran ancho de banda.

> Analogía Clave:
> 
> - **Ancho de Banda:** El ancho de una tubería de agua.
> - **Rendimiento:** El flujo real de agua que sale por segundo.
> - **Latencia:** El tiempo que tardas en abrir la llave y que empiece a salir agua.

| **Unidad** | **Abreviatura** | **Equivalencia** |
| --- | --- | --- |
| Kilobits por segundo | Kbps | 1,000 bps |
| Megabits por segundo | Mbps | 1,000,000 bps |
| Gigabits por segundo | Gbps | 1,000,000,000 bps |
| Terabits por segundo | Tbps | 1,000,000,000,000 bps |

---
