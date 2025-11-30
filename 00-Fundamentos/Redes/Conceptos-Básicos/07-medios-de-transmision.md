# Conceptos Básicos De Redes \
 \
🌐Medios de Transmisión (Capa Física) \


## **🎯 Objetivo**

Desmitificar y comprender en profundidad los **medios de red**. Entenderemos qué son, cómo se clasifican y los criterios físicos que permiten que un mensaje viaje desde un punto A (origen) hasta un punto B (destino).


## **1. ¿Qué es un Medio de Red? 🛣️**

Imagina que quieres enviar una carta física a un amigo. Para que esa carta llegue, necesita un camino: puede ir por una carretera en un camión, por aire en un avión o por mar en un barco.

En redes, el **medio** es esa carretera. Es el canal físico a través del cual viajan nuestros datos. Sin un medio, los dispositivos son islas aisladas; con un medio, se convierten en un archipiélago conectado.

### **Los 3 Titanes de la Transmisión**

| Tipo de Medio | ¿Qué transporta? | ¿Cómo se ven los datos? | Analogía |
|---|---|---|---|
| Cobre (Hilos metálicos) | Electricidad ⚡ | Impulsos eléctricos (Voltaje). | Como el código Morse a través de un telégrafo. |
| Fibra Óptica (Vidrio/Plástico) | Luz 🔦 | Pulsos de luz. | Como encender y apagar una linterna en un túnel oscuro. |
| Inalámbrico (Aire/Vacío) | Ondas 📡 | Ondas electromagnéticas. | Como sintonizar una estación de radio en tu auto. |

Las redes modernas no usan magia, usan física. Principalmente, existen tres formas de "codificar" (traducir) los datos para que viajen:

## **2. Criterios para elegir el Medio Adecuado 🧠**

Como ingeniero, no eliges un cable "porque se ve bonito". Debes tomar decisiones basadas en 4 preguntas críticas (piensa en esto como el "Cuadrante de Decisión"):

1. **📏 Distancia Máxima:** ¿Hasta dónde puede llegar la señal antes de debilitarse (atenuarse)?

- *Ejemplo:* No usarías un cable USB para conectar dos edificios a 1km de distancia; la señal moriría mucho antes.

- **🏭 Entorno:** ¿Dónde se instalará?

- *Ejemplo:* Si es una fábrica con mucha maquinaria pesada (que genera interferencia magnética), el cable de cobre podría fallar.

- **🚀 Cantidad y Velocidad de Datos:** ¿Cuánto ancho de banda necesito?

- *Ejemplo:* Un centro de datos de Google necesita tuberías gigantes (fibra), mientras que un sensor de temperatura pequeño necesita muy poco.

- **💰 Costo:** ¿Cuánto cuesta el cable y su instalación?

- *Ejemplo:* La fibra es rápida, pero instalarla requiere herramientas y técnicos especializados (caro).


## **3. Cables de Red Comunes: Análisis Profundo 🕵️‍♂️**

Profundicemos en los tres actores principales que verás en el campo.

### **A. Cable de Par Trenzado (Twisted Pair) 🌀**

Este es el rey de las redes locales (LAN). Si miras detrás de tu PC o router ahora mismo, probablemente veas uno. Es la base de la tecnología **Ethernet**.

- **¿Cómo es?** Son cables de cobre agrupados en pares.

- **La gran pregunta:** *¿Por qué están trenzados?*

- **Explicación:** Cuando la electricidad pasa por un cable, crea un campo magnético que puede interferir con el cable de al lado (esto se llama *crosstalk* o diafonía). Al trenzarlos, los campos magnéticos de cada cable se cancelan mutuamente.

- **Analogía:** Imagina dos personas hablando a la vez. Si se gritan al oído, se confunden. Si se giran (trenzan) de cierta forma, el ruido se cancela.

- **Identificación:** Vienen codificados por colores. En cada par, hay un cable de color sólido (ej. Azul) y su compañero a rayas (Blanco con rayas Azules).

![Enter image alt description](Images/LHg_Image_1.png)

### **B. Cable Coaxial 📺**

El veterano. Fue de los primeros en usarse en redes, pero hoy es más famoso por ser el cable de la televisión por cable o las antenas satelitales.

- **Estructura (De adentro hacia afuera):**

1. **Núcleo:** Un hilo de cobre rígido (por donde van los datos).

2. **Aislante:** Capa plástica que rodea al núcleo.

3. **Blindaje:** Una malla metálica trenzada. *¡Esto es vital!* Actúa como una jaula de Faraday, protegiendo los datos de interferencias externas.

4. **Funda:** La capa exterior negra o blanca.

2. **Uso:** Transmisión de alta frecuencia (Banda ancha).

![Enter image alt description](Images/5kQ_Image_2.png)

### **C. Cable de Fibra Óptica ✨**

El Ferrari de los medios de red. No usa electrones, usa **fotones** (luz).

- **Material:** Hecho de vidrio o plástico extremadamente puro.

- **Grosor:** Increíblemente fino, similar al diámetro de un cabello humano.

- **La Superventaja (Inmunidad):**

- Cómo usa luz, **NO le afecta la interferencia eléctrica**. Puedes poner fibra al lado de un generador industrial o en medio de una tormenta eléctrica, y los datos ni se enterarán.

- **Capacidad:** Ancho de banda masivo. Puede transportar terabytes de información a velocidades increíbles y a distancias de kilómetros sin perder señal.

- **Usos:**

- **Redes Troncales (Backbones):** Las "autopistas" principales de Internet que conectan países y ciudades.

- **Empresas y Data Centers:** Donde la velocidad es crítica.

![Enter image alt description](Images/Ir5_Image_3.png)

**🛡️ Nota de Seguridad:** La fibra es mucho más difícil de "pinchar" o interceptar que el cobre sin ser detectado. Si cortas la fibra para escuchar, la luz se corta y la conexión se cae, alertando a los administradores.


## **4. Resumen Visual Comparativo 📊**

| Característica | Par Trenzado (Ethernet) | Coaxial | Fibra Óptica |
|---|---|---|---|
| Señal | Eléctrica ⚡ | Eléctrica ⚡ | Luz 🔦 |
| Velocidad | Moderada/Alta | Moderada | Muy Alta 🚀 |
| Distancia | Corta (máx 100m) | Media | Muy Larga (Kms) |
| Inmunidad EMI
( Interferencia Electromagnética) | Baja (depende del trenzado) | Media (gracias al blindaje) | Total (es inmune) |
| Costo | Bajo 💵 | Medio 💵💵 | Alto 💵💵💵 |

