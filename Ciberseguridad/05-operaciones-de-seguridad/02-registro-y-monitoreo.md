# 📈 5.2 - Registro y Monitoreo de Eventos (Logging)

El registro (logging) es la práctica de capturar eventos que ocurren en un sistema. Sin logs, investigar un incidente de seguridad es **imposible**. Demuestra tu habilidad para la *detección*.

---

## 🔍 Qué registrar (Ejemplos):

* IDs de usuario
* Fechas y horas (con zona horaria)
* Direcciones IP (origen y destino)
* Intentos de acceso (exitosos y **fallidos**)
* Cambios de configuración
* Acceso a recursos (archivos, bases de datos)

### Ejemplo de Log (Análisis de Intrusión)



El siguiente es un análisis de un log en bruto (RAW LOG) de un sistema de detección de intrusiones (HIDS):

* **RC: "SQL injection attempt"**: Es la regla que se activó. Detectó un intento de Inyección SQL.
* **SRCIP: "172.20.1.127"**: La IP de origen del atacante.
* **EVENT: ... "GET /dashboard/pages.php?id=999999+union+select+..."**: Este es el *payload* del ataque. El atacante está intentando usar una consulta `UNION SELECT` para extraer datos de la base de datos.

---

## 🚨 Mejores Prácticas de Monitoreo

No solo monitoreamos lo que entra, sino también lo que sale.

| Tipo de Monitoreo | Objetivo | Herramientas Comunes |
| :--- | :--- | :--- |
| **Monitoreo de Ingreso (Ingress)** | Vigilar el tráfico entrante en busca de amenazas. | Firewalls, IDS/IPS, Gateways, Servidores de Autenticación, **SIEM**, Antimalware. |
| **Monitoreo de Egreso (Egress)** | Vigilar el tráfico saliente para prevenir fugas de datos. | **DLP (Prevención de Pérdida de Datos)**, que inspecciona correos, USB, FTP, etc. |
