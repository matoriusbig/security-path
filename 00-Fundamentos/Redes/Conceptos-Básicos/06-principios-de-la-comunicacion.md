# Conceptos Básicos De Redes \
Principios de la Comunicación


# 🌐 Los Principios de Comunicación en Redes

## Objetivo: Desmitificar cómo se "hablan" las computadoras entre sí, entendiendo las reglas (protocolos), los idiomas universales (estándares) y los mapas que usamos para estudiarlos (modelos OSI y TCP/IP).

## 
## 1. ¿Cómo nos comunicamos? (La Analogía Humana) 🗣️

## Antes de entrar en cables y chips, miremos cómo funcionamos nosotros. La comunicación, ya sea una charla informal o una entrevista de trabajo, siempre necesita reglas preestablecidas.

## Imagina que intentas pedir café en un país cuyo idioma desconoces y usando señas que nadie entiende. Un caos, ¿verdad? Para que la comunicación sea exitosa, necesitamos acordar tres cosas antes de empezar:

1. El Método: ¿Cómo hablamos? (Lenguaje de señas, notas escritas, teléfono, cara a cara).

2. El Idioma: ¿Japonés? ¿Español? ¿Inglés? (Ambos deben hablar el mismo).

3. La Confirmación: Saber si el otro entendió.

- *Tú:* "Quiero 3 camisas negras".

- *Vendedor:* "Entendido, 3 camisas negras".

- *Tú:* "Correcto, gracias".

## Nota del Profesor: En redes, esto es exactamente igual. Las computadoras necesitan un emisor, un receptor, un medio (canal), un idioma común y velocidad acordada. A estas "reglas de etiqueta" informática las llamamos Protocolos.

## 
## 2. Protocolos de Comunicación de Red 📜

## Las computadoras son ciegas. Imagina que cada dispositivo vive en una burbuja solitaria.

- Solo conoce su propia dirección (su "yo").

- No sabe quién está afuera.

- No sabe si el destinatario está en su red o en China.

## Los protocolos son los que rompen esa burbuja. Son las reglas que definen cómo salir y conectar. Si todos los dispositivos en una red local (LAN) no "hablan el mismo protocolo", es como tener a personas gritando en idiomas distintos en una misma sala.

### **Los 6 Requisitos de un Protocolo**

## Para que un mensaje viaje de A a B, los protocolos definen estrictamente estos aspectos:

| Requisito | Explicación Simple | Ejemplo de la vida real |
|---|---|---|
| 1. Formato del mensaje | La estructura exacta que debe tener el mensaje. | Una carta debe tener sobre, estampilla y dirección en el lugar correcto. |
| 2. Tamaño del mensaje | Reglas sobre cuán grande o pequeño puede ser un paquete de datos. | Si envías una enciclopedia por correo, debes dividirla en cajas más pequeñas. |
| 3. Sincronización (Timing) | Control de flujo y velocidad. ¿Cuándo hablar? ¿Qué tan rápido? | Si hablas muy rápido, nadie te entiende. Debes pausar. |
| 4. Codificación | Convertir el mensaje en algo que pueda viajar (bits a luz/electricidad). | Convertir tus pensamientos en sonidos vocales al hablar. |
| 5. Encapsulamiento | Meter el mensaje dentro de "sobres" con información de dirección (Origen/Destino). | Poner una carta dentro de un sobre con el Remitente y Destinatario. |
| 6. Patrón del mensaje | ¿Espero respuesta o no? (Acuse de recibo). | Enviar un mensaje certificado (requiere firma) vs. dejar una nota en la mesa. |

### **La "Pila" de Protocolos en Acción (Ejemplo Real) 🥞**

## Cuando ves un video o cargas una web, no usas *un* protocolo, usas una pila (varios trabajando juntos en capas).

## Al nosotros entrar a una web, por ejemplo: www.ejemplo.com pasan lo siguiente:

1. DNS (Protocolo): Tu PC pregunta: "¿Cuál es la IP de ejemplo.com?".

2. HTTP (Aplicación): Pide la página web.

3. TCP (Transporte): Divide la web en pedacitos seguros y garantiza que lleguen. Si uno se pierde, TCP lo reenvía.

4. IP (Internet): Pone la dirección de destino y ruta (como el GPS).

5. Ethernet (Acceso): Transmite físicamente por la tarjeta de red (NIC).

## 
## 3. Estándares de Comunicación ⚖️

## Con tantos dispositivos nuevos (teléfonos, neveras inteligentes, servidores), ¿cómo logramos que todos se entiendan? Gracias a los Estándares.

## Un estándar es un conjunto de reglas que asegura la interoperabilidad.

- Gracias a los estándares, puedes enviar un email desde una PC y leerlo en un iPhone.

- Sin estándares, cada marca tendría su propia "internet" privada que no conecta con las demás.

## ¿Cómo nace un estándar?

## No aparecen por arte de magia. Siguen un ciclo riguroso gestionado por organizaciones (como la IETF - Internet Engineering Task Force). Estas organizaciones tienen un proceso bastante riguroso para determinar los estándares de las comunicaciones de la red, estos se basan en:

1. Discusión del problema.

2. Propuesta de solución.

3. RFC (Request for Comments): Es un documento numerado donde se registra el borrador.

4. Pruebas y Resolución de problemas.

![Enter image alt description](Images/NRD_Image_1.png)

## 
## 4. Modelos de Comunicación de Red 🗺️

## Para estudiar redes, usamos "mapas" o modelos en capas. ¿Por qué capas? Porque divide el problema gigante de "comunicar el mundo" en trozos pequeños y manejables.

## Ventajas de usar capas:

- Diseño: Si creas un protocolo nuevo, solo te preocupas de tu capa.

- Competencia: Distintos fabricantes pueden trabajar juntos.

- Independencia: Puedes cambiar la tecnología física (de cobre a fibra óptica) sin tener que reescribir las aplicaciones (como tu navegador web).

## Existen dos modelos principales que debes dominar:

### **A. El Modelo TCP/IP (El Modelo de Protocolo)**

## Es el modelo práctico, el que realmente usa Internet hoy en día (creado en los 70s). Tiene 4 Capas:

1. Aplicación: Datos para el usuario + codificación (Ej: HTTP, SMTP).

2. Transporte: Comunicación entre dispositivos. Garantiza fiabilidad (Ej: TCP, UDP).

3. Internet: Determina la mejor ruta (el camino) a través de la red (Ej: IP).

4. Acceso a la Red: Controla el hardware y los medios físicos (cables, ondas).

### **B. El Modelo OSI (El Modelo de Referencia)**

## Creado por la ISO. Es más detallado y teórico. Se usa mundialmente para enseñar redes y diagnosticar problemas. Tiene 7 Capas.

## *Memoriza esto de arriba (7) a abajo (1):*

- 7. Aplicación: Procesos de red a aplicaciones (lo que ve el usuario).

- 6. Presentación: Traduce los datos (formato, encriptación) para que la aplicación los entienda.

- 5. Sesión: Organiza el diálogo, inicia y termina la conversación.

- 4. Transporte: Segmenta los datos y los reensambla. (El director de orquesta).

- 3. Red: Enrutamiento y direccionamiento (IPs). Aquí deciden "por dónde ir".

- 2. Enlace de Datos: Habla de tramas y direcciones físicas (MAC). Comunicación nodo a nodo.

- 1. Física: Cables, voltajes, pines, luz. La transmisión pura de bits.

## 
## 5. Comparación: OSI vs. TCP/IP 🥊

## Esta es la parte más importante para tu carrera. Aunque TCP/IP es el que usamos, solemos hablar usando los números de capas del modelo OSI (ej: "Hubo un fallo en capa 2").

## 
## Aquí tienes la tabla comparativa entre los dos modelos:

| Modelo OSI (Referencia) | Modelo TCP/IP (Protocolo) | Relación / Notas |
|---|---|---|
| 7. Aplicación | Aplicación | TCP/IP agrupa las capas 5, 6 y 7 de OSI en una sola capa gigante de "Aplicación". |
| 6. Presentación | Aplicación | (Ver arriba) |
| 5. Sesión | Aplicación | (Ver arriba) |
| 4. Transporte | Transporte | Coincidencia directa. Ambas manejan la entrega confiable y segmentación. |
| 3. Red | Internet | Coincidencia funcional. Ambas manejan direccionamiento y rutas (IP). |
| 2. Enlace de Datos | Acceso a la Red | TCP/IP agrupa lo físico y el enlace en una sola capa. OSI lo separa para mayor detalle. |
| 1. Física | Acceso a la Red | (Ver arriba) |

## Diferencias Clave:

- TCP/IP es un Modelo de Protocolo: Describe las funciones de la suite de protocolos que realmente usamos en Internet.

- OSI es un Modelo de Referencia: Describe *qué* se debe hacer en cada capa, pero no dice exactamente *cómo* (no es específico a un protocolo).

- La Capa 3 de OSI (Red) se alinea con la Capa de Internet de TCP/IP.

- La Capa 4 de OSI (Transporte) se alinea con la Capa de Transporte de TCP/IP.

## 
### **📝 Resumen para llevar**

- Las redes funcionan porque acordamos Protocolos (reglas de formato, tiempo y confirmación).

- Los Estándares permiten que equipos de diferentes marcas hablen entre sí.

- Usamos Modelos en Capas para visualizar la complejidad.

- TCP/IP es la realidad (4 capas). OSI es la teoría perfecta para estudiar (7 capas).

- La Encapsulación es como poner una carta dentro de sobres sucesivos, cada uno con información para una capa específica.
