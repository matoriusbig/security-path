# 🌐 Conceptos Básicos de Red: La Capa de Acceso 

**🎯Objetivo**: Entender cómo funciona la comunicación en una red local (LAN). Entender esto es la base absoluta para comprender ataques de red posteriores.

> **💡 Nota** : En ciberseguridad, si no entiendes cómo viaja el dato, no puedes protegerlo (ni interceptarlo). Ataques como el MAC Flooding o ARP Spoofing ocurren exactamente aquí. ¡Presta atención!

## 1. ¿Qué es la Capa de Acceso?
Antes de entrar en detalles, ubiquémonos. La Capa de Acceso es la "puerta de entrada" a la red. Es el lugar donde los dispositivos finales (tu PC, impresora, cámara) se conectan físicamente a la red cableada.
El rey de esta capa es el Switch. Pero para entender al Switch, primero debemos entender el lenguaje que habla: **Ethernet**.

## Encapsulación: El Arte de Enviar Mensajes ✉️
Para que las computadoras se entiendan, deben seguir reglas estrictas de formato.
* Encapsulamiento: Es el proceso de meter un mensaje dentro de otro formato (como meter una carta en un sobre).
* Desencapsulamiento: Es abrir el sobre y sacar el mensaje al recibirlo.
Es como dejar una carta (con datos) adentro de un sobre (con todos los datos del remitente) 
Imagina que quieres enviar una carta física. No puedes simplemente tirar el papel al buzón; necesitas un sobre con datos específicos. En redes pasa lo mismo:

### Carta (datos) y sobre (datos del remitente) ✉

<img width="422" height="447" alt="unnamed" src="https://github.com/user-attachments/assets/b4c71227-fe8c-4f8b-a45d-0acdeb1e2d54" />

### Datos 📨

<img width="614" height="333" alt="unnamed" src="https://github.com/user-attachments/assets/874ad606-8422-4490-b16c-d28eec4b8022" />


## 2. La Trama Ethernet (Ethernet Frame) 📦

En la Capa 2 (Enlace de Datos), la información viaja en Tramas. Piensa en la trama como un "vagón de tren" rígido que transporta tu información por el cable.
La estructura de este vagón es la siguiente:
* **Preámbulo (8 bytes)**: Sincronización. Sirve para que la tarjeta de red receptora se "ponga a ritmo" con la emisora.
* **Delimitador de Inicio (SFD)**: Avisa: "Atención, justo después de este bit comienza la información importante".
* **Dirección MAC de Destino (6 bytes)**: La identificación física de quién debe recibir el paquete.
* **Dirección MAC de Origen (6 bytes)**: La identificación física de quién lo envió.
* **Longitud / Tipo**: Dice qué tan largo es el mensaje o qué protocolo viene adentro (ej. IPv4 o IPv6).
* **Datos Encapsulados (Payload)**: Aquí va la carga útil. A Ethernet no le importa qué llevas (puede ser un fragmento de Netflix o un virus), él solo lo transporta.
* **FCS (Secuencia de Verificación)**: Un cálculo matemático para asegurar que no hubo interferencias en el cable.

### 📊 Comparativa: Carta vs. Trama Ethernet
Esta tabla compara los elementos de un correo postal con los de una trama de red.
| Elemento de la Carta (Analógico) | Elemento de la Trama (Digital) |	Función |
|---|---|---|
| Destinatario (1400 Main St...)	| Dirección MAC de Destino	| ¿A quién va dirigido el mensaje? |
| Remitente (4085 SE Pine St...) | Dirección MAC de Origen	| ¿Quién escribió el mensaje? |
| Saludo ("Querida Jane")	| Preámbulo	| Alerta al receptor: "¡Despierta, viene un mensaje!". |
| Contenido ("Acabo de regresar...") | Datos (Payload) |	El mensaje real (una foto, un email, un paquete IP). |
| Sello / Firma final |	FCS (Secuencia de Verificación) |	Garantiza que la carta no llegó rota o modificada. |

## 3. La Tabla de Direcciones MAC : Funcionamiento Técnico 📋
Técnicamente, esta tabla reside en la memoria del switch y a menudo se le conoce como Tabla CAM (Content Addressable Memory). Su función es mapear la capa física (puertos) con la capa de enlace de datos (direcciones MAC).
El proceso se rige por un algoritmo cíclico de dos fases principales:
### 1. 🧠 Fase de Aprendizaje (Ingress - Entrada)
* El switch analiza la Dirección MAC de Origen (Source MAC) de cada trama que entra por un puerto.
* Si la MAC no está en la tabla: El switch crea una nueva entrada relacionando esa MAC con el puerto de entrada.
* Si la MAC ya existe: El switch actualiza el temporizador de envejecimiento (Aging Timer).
> **Nota:** Por defecto, las entradas se eliminan tras 300 segundos (5 minutos) de inactividad para liberar memoria.
### 2. 📨 Fase de Reenvío (Egress - Salida)
* El switch analiza la Dirección MAC de Destino (Destination MAC) para decidir qué hacer.
* Destino Conocido (Known Unicast): Si la MAC de destino está en la tabla, el switch filtra la trama y la envía exclusivamente por el puerto asociado.
* Destino Desconocido (Unknown Unicast): Si la MAC de destino no está en la tabla, el switch inunda (Floods) la trama por todos los puertos activos, excepto por el que se recibió.

## 4. El Switch Ethernet: El "Conserje" del Edificio 🏢
Aquí es donde muchos se confunden, así que vamos a usar una analogía infalible para que se entienda mejor.
El Switch es un dispositivo chismoso pero muy ordenado. Su trabajo es conectar cables, pero a diferencia de un Hub (que es tonto y grita todo), el Switch toma decisiones inteligentes.

### La Analogía 👮
* El Edificio = El Switch.
* Los Apartamentos = Los Puertos (Puerto 1, Puerto 2...).
* Los Inquilinos = Las Direcciones MAC (PC-Alicia, PC-Beto...).
* El Conserje = El procesador del Switch.
* La Libreta del Conserje = La Tabla de Direcciones MAC.
### **✔️La Regla de Oro del Conserje**
El conserje empieza su turno con la libreta en blanco. Sigue solo dos pasos:
1. **🧠APRENDE (Origen)**: "Si alguien me habla desde el apartamento 1, anoto que vive ahí".
2. **🔍BUSCA (Destino)**: "Si llega carta para alguien, miro mi lista para saber en qué puerta entregarla".

## 5. Funcionamiento Lógico: Escenarios A y B
Veamos cómo el Switch llena su tabla paso a paso.
* **📋La Tabla Inicial**: Al encender el switch, la memoria RAM está vacía:


| Dirección MAC | Puerto |
|---|---|
| (Vacío) | (Vacío) |

## 🌊 Escenario A: "No sé dónde estás" (Inundación / Flooding)
**Situación:** PC-Alicia (en Puerto 1) quiere enviar un mensaje a PC-Beto (en Puerto 4). El Switch no conoce a nadie aún.
### **Paso 1 (Envío) ✉️**: 
* Alicia envía el mensaje: "Para: PC-Beto, De: PC-Alicia".
### **Paso 2 (Aprendizaje) 📨**: 
* El Switch recibe el mensaje en el Puerto 1.
### El Conserje piensa 🧠: 
* "No conozco a Alicia, pero me está hablando desde el Puerto 1. ¡Apuntado!".
* 📝 Tabla Actualizada: PC-Alicia ➝ Puerto 1.
### **Paso 3 (Búsqueda Fallida)** ❌:
* El Switch mira que es para PC-Beto.
### El Conserje piensa 🧠: 
* "Busco a Beto en mi lista... ¡No está! No sé dónde vive". 😱
### **Paso 4 (Inundación) 🌊**: 
* Como no sabe, el Switch grita (envía copia) del mensaje a TODOS los puertos, excepto al de Alicia.
* El vecino del Puerto 2 lo rechaza.
* El vecino del Puerto 3 lo rechaza.
* PC-Beto en el Puerto 4 dice: "¡Es para mí!" y lo recibe.

## 🎯 Escenario B: "Ya te conozco" (Unicast / Filtrado)
**Situación**: PC-Beto (Puerto 4) responde a PC-Alicia (Puerto 1).
### **Paso 1 (Respuesta) ✉️:** 
* Beto envía: "Para: PC-Alicia, De: PC-Beto".
### **Paso 2 (Aprendizaje) 📨:** 
* El mensaje entra por el Puerto 4.
### El Conserje piensa 🧠:  
* "¡Ah! Un inquilino nuevo en el Puerto 4 llamado Beto. Apuntado".
* 📝 Tabla Actualizada:
PC-Alicia ➝ Puerto 1
PC-Beto ➝ Puerto 4
### **Paso 3 (Búsqueda Exitosa) ✔️:** 
* El Switch mira que es para PC-Alicia.
### El Conserje piensa: 
* "¿Dónde vive Alicia? ¡Aquí está en mi lista! Vive en el Puerto 1". 💡
* **Paso 4 (Envío Directo) 📩:** El Switch crea un circuito privado y entrega el mensaje SOLO al Puerto 1.
* Nadie más se entera. La red es más segura y rápida.

### 6. Resumen Lógico (Cheat Sheet) 📝
Para que nunca se te olvide, este es el algoritmo del Switch:
* Llega una trama.
* ¿Está la MAC de ORIGEN en mi tabla?

**NO❌:** La anoto junto con su puerto (Aprendizaje).

**SÍ✔️:** Reinicio su temporizador (para no borrarla por inactividad).

* ¿Está la MAC de DESTINO en mi tabla?

**SÍ✔️:** Envío la trama solo a ese puerto (Unicast).

**NO❌:** Envío la trama a todos los puertos menos al origen (Flooding).

> 💀 **Nota: El Ataque MAC Flooding**
Entender la tabla MAC es vital para entender este ataque. Un hacker puede usar una herramienta para enviar millones de direcciones MAC falsas al Switch en segundos.
¿Qué pasa? La "Libreta del Conserje" (Tabla MAC) tiene un límite. Si se llena de datos falsos, no cabe espacio para las direcciones reales.
¿El resultado? El Switch entra en pánico y, por seguridad, empieza a funcionar como un Hub (Escenario A permanente), enviando TODO el tráfico a TODOS los puertos. En ese momento, el hacker puede capturar tus contraseñas y datos porque el Switch se los está enviando directamente a su computadora.

## Resumen de Conceptos Clave 🎓

- **Trama Ethernet:** El contenedor de datos en la capa 2. Tiene direcciones MAC de origen y destino.

- **Encapsulación:** El proceso de "empaquetar" datos (como meter una carta en un sobre).

- **Switch:** Dispositivo inteligente que conecta equipos y evita colisiones creando circuitos temporales.

- **Tabla MAC:** La base de datos del Switch. Mapea Dirección MAC -> Puerto Físico.

- **Aprendizaje (Source MAC):** El Switch aprende mirando **quién envía** (MAC de origen).

- **Reenvío (Destination MAC):** El Switch decide a dónde enviar mirando **a quién va dirigido** (MAC de destino).
