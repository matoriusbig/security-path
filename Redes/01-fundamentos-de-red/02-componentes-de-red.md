# 2 - Componentes de Red: El Elenco de la Obra Digital 🎭
> **🎯 Objetivo:** Conocerás a los actores principales que hacen posible la magia de las redes. Desde los dispositivos que usas a diario hasta los guardianes invisibles que protegen tus datos, entenderás quién es quién y qué función vital desempeñan.

---

### 1. Los Protagonistas: Clientes y Servidores 👥
Toda red existe con un propósito: mover datos de A a B. Para empezar, necesitamos entender los roles básicos, como si estuviéramos en un restaurante.

* **Clientes (Clients):** Son los que "piden la comida". Son los dispositivos que los usuarios utilizan para acceder a la red.
    * *Ejemplos:* Tu portátil, smartphone, tablet, e incluso ese termostato inteligente con Wi-Fi
* **Servidores (Servers):** Son la cocina que "prepara y sirve el pedido". Proporcionan recursos al resto de la red.
    * *Ejemplos:* Servidores de correo, servidores web o de archivos

> **💡 Nota:** Un servidor no siempre es una supercomputadora gigante en un armario oscuro.Un software especializado puede convertir tu PC normal en un servidor para otros dispositivos de la red

---

### 2. Conectividad: Hubs vs. Switches (El tonto y el listo) 🧠
Aquí es donde conectamos los cables. Históricamente ha habido una evolución importante. Imagina que estás en una fiesta intentando hablar con un amigo.

* **Hub (Concentrador) - La Tecnología Antigua:**
    Imagina que para decirle algo a tu amigo, **gritas** el mensaje para que todos en la fiesta lo escuchen, aunque solo sea para él.
    * Un Hub recibe datos y los reenvía a *todos* los puertos (difusión).
    * **Problema:** Genera mucho ruido (tráfico inútil) y errores.

* **Switch (Conmutador) - El Estándar Moderno:**
    El Switch es inteligente. Es como si te acercaras a tu amigo y le **susurraras** el mensaje al oído.
    * Sabe qué dispositivo está en cada puerto y envía el tráfico *solo* al destinatario
    * **Ventaja:** Más seguridad y eficiencia

| Característica | Hub (Concentrador) | Switch (Conmutador) |
| :--- | :--- | :--- |
| **Inteligencia** | "Tonto" (No sabe quién es quién) | Inteligente (Sabe direcciones) |
| **Envío de Datos** | A todos (Broadcast) | Solo al destino (Unicast) |
| **Eficiencia** | Baja (Muchos errores/colisiones) | Alta (Ancho de banda eficiente) |
| **Estado Actual** | Obsoleto (Pero aparece en exámenes) | Estándar actual |

<img width="829" height="486" alt="image" src="https://github.com/user-attachments/assets/809fd19e-399f-429f-a895-a737adcf69a3" />

---

### 3. Dirigiendo el Tráfico: Routers y WAPs 🚦
Ahora que estamos conectados localmente, necesitamos salir al mundo y movernos sin cables.

* **Wireless Access Points (Puntos de Acceso Inalámbricos - WAP/AP):**
    Funcionan igual que un Hub o Switch, pero sin cables. Permiten conectar dispositivos a la red cableada usando ondas de radio
* **Routers (Enrutadores):**
    Son los **diplomáticos** de la red. Conectan redes *diferentes* entre sí (ej: tu red de casa con Internet).
    * Toman decisiones inteligentes sobre la mejor ruta para los datos basándose en **Direcciones IP**

    <img width="583" height="380" alt="image" src="https://github.com/user-attachments/assets/9e1eb4e0-9dca-4957-81d5-1a8014aef2d0" />


---

### 4. Los Guardianes de Seguridad 🛡️
La red es un lugar peligroso. Necesitamos protección.

* **Firewall (Cortafuegos):**
    Es el portero de seguridad de la discoteca. Se para entre tu red interna (la zona VIP) e Internet (la calle).
    * Controla quién entra y sale basándose en reglas estrictas (Listas de Control de Acceso)
* **Proxy Server:**
    Actúa como un **intermediario**. Tú le pides algo al Proxy, y el Proxy se lo pide a Internet por ti.
    * Oculta tu dirección IP real y puede filtrar contenido o guardar datos en caché para ir más rápido

    <img width="865" height="613" alt="image" src="https://github.com/user-attachments/assets/8c91200e-3f20-474a-ac58-74d645c92b5e" />


#### Detectives vs. Guardaespaldas (IDS vs. IPS)
Ambos vigilan el tráfico buscando a los "chicos malos" (intrusos), pero reaccionan diferente:

| Sistema | Nombre Completo | Función Principal | Analogía |
| :--- | :--- | :--- | :--- |
| **IDS** | Intrusion *Detection* System |**Detecta** y **Alerta** al administrador | Una alarma antirrobo (hace ruido, pero no atrapa al ladrón). |
| **IPS** | Intrusion *Prevention* System |**Detecta** y **Actúa** (Bloquea/Descarta) | Un guardaespaldas (ve al intruso y lo saca del edificio). |

<img width="589" height="331" alt="image" src="https://github.com/user-attachments/assets/03e7f8ec-675d-47f9-82f0-6dd2351fd9e9" />


> **🛡️ Nota:** En el examen, recuerda: si solo "alerta", es IDS. Si "toma medidas" o "bloquea", es IPS.

---

### 5. Optimización y Gestión Avanzada 🚀
Cuando la red crece, necesitamos herramientas más potentes.

* **Load Balancer (Equilibrador de Carga):**
    Imagina una fila en el supermercado. El equilibrador es el empleado que te dice: *"La caja 3 está vacía, pase por ahí"*. Distribuye el tráfico entre varios servidores para que ninguno se sature
* **Controladores (Controllers):**
    El cerebro en las **SDN (Redes Definidas por Software)**. Permiten gestionar todos los switches y routers desde un software centralizado, dándonos flexibilidad total

<img width="434" height="477" alt="image" src="https://github.com/user-attachments/assets/a9398468-062b-4415-91b3-4ec4a9dd24df" />****

#### Almacenamiento de Datos (NAS vs. SAN)
***NAS (Network Attached Storage):** Es como un disco duro gigante conectado a la red para compartir archivos fácilmente entre varios clientes
* **SAN (Storage Area Network):** Una red de *alta velocidad* dedicada solo a almacenamiento.Mueve bloques de datos masivos, usada en grandes empresas para servidores

<img width="657" height="364" alt="image" src="https://github.com/user-attachments/assets/b495b4d8-f550-4088-af9b-4e184d824f36" />

---

### 6. La Infraestructura Física 🛣️
Finalmente, ¿por dónde viajan los datos?

* **Medios (Media):** Los materiales físicos. Cables de cobre, fibra óptica o el aire (inalámbrico).Cada uno tiene sus límites de velocidad y distancia
* **Enlaces WAN:** Son las superautopistas que conectan ciudades o países (enlaces de larga distancia).Usan satélites, fibra o redes celulares para la conectividad global

<img width="734" height="441" alt="image" src="https://github.com/user-attachments/assets/9d5203f8-01b4-4c82-9b04-3c539817c745" />


---

### 🎓 Resumen para llevar
* **Switch > Hub:** Los Hubs gritan (broadcast), los Switches susurran (unicast). Siempre prefiere el Switch.
* **Router = IP:** Los routers conectan redes diferentes y toman decisiones basándose en direcciones IP.
*Seguridad en capas:** Usamos Firewalls para filtrar, Proxies para intermediar, e IPS para detener ataques activamente.
* **Disponibilidad:** Los Balanceadores de Carga aseguran que ningún servidor colapse por exceso de trabajo.
