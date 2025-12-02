# 💻 3.3 - Controles de Acceso Lógico (Modelos DAC, MAC, RBAC)

Los sistemas de control de acceso lógico son los sistemas automatizados que controlan la capacidad de una persona para acceder a recursos del sistema (estaciones de trabajo, redes, aplicaciones).

Una vez que un usuario se autentica (prueba quién es), la **autorización** (qué puede hacer) se gestiona a través de estos modelos:

---

## 1. 👤 Control de Acceso Discrecional (DAC)

* **Definición:** El modelo DAC se basa en la **discreción del propietario**. El creador o propietario de un objeto (como un archivo) tiene control total para decidir quién más puede acceder a él.
* **Características:** Cada objeto tiene un propietario; es flexible.
* **Implementación Común:** La mayoría de los sistemas operativos de usuario final (Windows, macOS, Linux) usan DAC para sus sistemas de archivos.
* **Ejemplo (Documento Compartido) 📄:** Creas un documento en Google Drive. Tú eres el propietario. Decides compartirlo con "Ana" (permisos de "Editor") y "Carlos" (permisos de "Lector"). Esta decisión fue enteramente tuya.

## 2. 🛡️ Control de Acceso Obligatorio (MAC)

* **Definición:** El modelo MAC es mucho más estricto. El acceso **no lo decide el propietario**, sino una **política de seguridad global** gestionada centralmente e impuesta **obligatoriamente** por el sistema operativo.
* **Características:** Se basa en **Etiquetas (Labels)**. Tanto los sujetos (usuarios) como los objetos (archivos) reciben etiquetas de clasificación (ej. `Top Secret`, `Secret`).
* **Regla Central:** Un usuario solo puede acceder a un archivo si su nivel de autorización es igual o superior al nivel de clasificación del archivo.
* **Implementación Común:** Entornos de alta seguridad (militares, agencias de inteligencia).
* **Ejemplo (Militar) 🏛️:** Un analista con autorización `Top Secret` puede leer archivos `Top Secret` y `Secret`. Un analista con autorización `Confidential` **no puede** leer un archivo `Secret`, incluso si el primer analista quisiera compartirlo. El sistema lo prohíbe.

## 3. 🧑‍💼 Control de Acceso Basado en Roles (RBAC)

* **Definición:** Es el modelo más utilizado en entornos corporativos. En lugar de asignar permisos directamente a usuarios individuales (una pesadilla de gestionar), RBAC **asigna permisos a Roles**, y luego los usuarios son asignados a esos roles.
* **Características:** Gestión centralizada, eficiente y alineada con el Principio de Privilegio Mínimo (PoLP).
* **Ejemplo (Corporativo) 📈:**
    * **Rol "Finanzas":** Tiene acceso R/W al software de nómina.
    * **Rol "Ventas":** Tiene acceso R/W al CRM (Salesforce).
    * **Rol "RRHH":** Tiene acceso a los archivos privados del personal.
* **Gestión:** Cuando se contrata a un nuevo vendedor, el administrador simplemente lo añade al rol "Ventas". Hereda automáticamente todos los permisos necesarios.

---

### 📖 Términos Clave del Glosario

* **🖥️ Sistemas de control de acceso lógico:** Un sistema automatizado que controla la capacidad de una persona para acceder a recursos del sistema informático.
* **👤 Control de acceso discrecional (DAC):** El control de acceso se deja a discreción del propietario del objeto.
* **🏛️ Control de acceso obligatorio (MAC):** El control de acceso requiere que el propio sistema gestione los controles de acuerdo con las políticas de seguridad.
* **🧑‍💼 Control de acceso basado en funciones (RBAC):** Un sistema de control de acceso que configura los permisos de usuario en función de las funciones.
* **🐧 Linux / 🖥️ Unix / 📱 iOS:** Ejemplos de sistemas operativos que implementan estos modelos.
