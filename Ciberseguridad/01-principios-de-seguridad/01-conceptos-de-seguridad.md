# 🛡 Los Pilares de la Seguridad (La Tríada CIA)

En ciberseguridad, todo gira en torno a proteger los **activos** (principalmente, la información). Para definir qué significa "proteger", usamos la **Tríada de la CIA**: Confidencialidad, Integridad y Disponibilidad.

Piénsalo como las tres patas de un taburete: si falla una, todo el sistema se cae.

### 1. Confidencialidad (El Secreto 🤫)

- **Definición Clara:** Asegurarse de que **solo las personas autorizadas puedan ver** la información.
- **El Desafío:** No se trata de esconderlo todo, sino de *regular el acceso*. Tú debes poder ver tu correo, pero no el de tu jefe. RRHH debe poder ver los salarios de todos, pero un desarrollador no.
- **Ejemplo Práctico:** El **cifrado**. Cuando envías un WhatsApp, el mensaje va cifrado "de extremo a extremo". Si alguien lo intercepta en el camino, solo verá un galimatías ilegible. Solo tú y el receptor (las partes autorizadas) pueden leerlo.
- **Términos Clave:**
    - **PII (Información de Identificación Personal):** Cualquier dato que pueda identificar a una persona (Ej: tu RUT, nombre + dirección, número de teléfono).
    - **PHI (Información de Salud Protegida):** Tu historial médico. Es un tipo de PII extremadamente sensible.

### 2. Integridad (La Confianza 🤝)

- **Definición Clara:** Asegurarse de que la información es **exacta, completa y no ha sido modificada** sin autorización.
- **El Desafío:** Debemos confiar en nuestros datos. Si los datos pueden ser alterados, no sirven de nada.
- **Ejemplo Práctico:** Una **transferencia bancaria**. Si envías $10.000, la **integridad** garantiza que el banco reciba $10.000, y no $1.000 (corrupción accidental) o $100.000 (modificación maliciosa por un atacante).
- **Términos Clave:**
    - **Baseline (Línea Base):** ¿Cómo sabes si un archivo del sistema fue modificado por un virus? Porque tienes una "foto" de cómo se veía cuando estaba limpio (la *baseline*). Si comparas el archivo actual con la *baseline* y no coinciden, ¡alerta roja!

### 3. Disponibilidad (La Luz Encendida 💡)

- **Definición Clara:** Asegurarse de que los sistemas y los datos estén **accesibles para los usuarios autorizados cuando los necesiten**.
- **El Desafío:** No significa que deba funcionar el 100% del tiempo, sino que debe cumplir con las *necesidades del negocio*.
- **Ejemplo Práctico:** Un ataque **DDoS (Denegación de Servicio Distribuido)**. Un atacante inunda un sitio web (como un e-commerce) con tanto tráfico basura que los usuarios legítimos no pueden entrar. La información sigue siendo *confidencial* e *íntegra*, pero como nadie puede acceder a ella, la **disponibilidad** se ha roto.
- **Términos Clave:**
    - **Criticidad:** ¿Qué tan importante es el sistema? Un e-commerce en Black Friday tiene una criticidad altísima.

---

### Más Allá de la Tríada: Conceptos Clave de Acceso

- **Autenticación (¿Realmente eres tú?):** Es el proceso de *probar* tu identidad. Existen 3 factores:
    - 🧠 **Algo que sabes:** Una contraseña, un PIN.
    - 📱 **Algo que tienes:** Tu celular (para un código 2FA), un token USB (YubiKey).
    - 👁️ **Algo que eres:** Biometría (tu huella digital, tu cara).
- **MFA (Autenticación Multifactor):** Usar *dos o más* métodos de categorías *diferentes*.
    
    > ¡Ojo con esto! Pedir un usuario y una contraseña NO es MFA. Ambos son "Algo que sabes".
    MFA real es: Tu contraseña (sabes) + un código de tu celular (tienes).
    > 
- **No Repudio (Sin "Yo No Fui"):** Un concepto legal que crea una **prueba irrefutable** de que una persona específica realizó una acción. (Ej: una firma digital).
- **Privacidad (Tu Derecho a Controlar):** Es el derecho de un individuo a controlar cómo se recopila, usa y distribuye su información personal. Puedes tener seguridad sin privacidad (una red social *segura* que *legalmente* vende tus datos), pero no puedes tener privacidad sin seguridad.
