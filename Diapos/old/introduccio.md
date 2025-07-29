
# Introducción a la Simulación de Entornos Remotos

## Simulación de Escenarios Reales
En este módulo, vamos a simular un entorno de trabajo donde la mayoría de nuestras operaciones no se realizarán en nuestro ordenador local. En su lugar, utilizaremos una **máquina virtual** para replicar la experiencia de trabajar con una máquina remota.

---

## ¿Por qué Simular un Entorno Remoto?
* **Preparación para la Realidad:** En el mundo real, los despliegues de software y la gestión de servidores suelen ocurrir en máquinas remotas, como los **VPS (Virtual Private Servers)**.
* **Conexión Remota:** Aprenderemos a conectarnos y trabajar de forma remota, una habilidad fundamental en el desarrollo y la administración de sistemas.

---

# ¿Qué es un VPS?

## Concepto de Servidor
Un **servidor** es una computadora que almacena los archivos y bases de datos necesarios para un sitio web. Cuando alguien visita un sitio web, su navegador envía una solicitud al servidor, que a su vez transfiere los archivos necesarios a través de Internet.

---

## Servidor Privado Virtual (VPS)
* **Definición:** El **alojamiento VPS** te proporciona un servidor en la nube que simula un servidor físico, aunque en realidad, la máquina se comparte entre varios usuarios.
* **Tecnología de Virtualización:** Tu proveedor de alojamiento web instala una capa virtual sobre el sistema operativo del servidor. Esta capa divide el servidor en particiones, permitiendo a cada usuario instalar su propio sistema operativo y software.
* **Control Absoluto:** Un VPS es tanto **virtual** como **privado** porque tienes control absoluto sobre tu partición, separada de otros usuarios a nivel del sistema operativo. Esto es similar a crear particiones en tu propio ordenador para ejecutar múltiples sistemas operativos (por ejemplo, Windows y Linux).

---

## Ventajas del VPS
* **Recursos Garantizados:** Un VPS te permite configurar tu sitio web dentro de un contenedor seguro con recursos dedicados (memoria, espacio en disco, núcleos de CPU) que no compartes con otros.
* **Acceso Root:** Tienes el mismo acceso de nivel raíz que si alquilaras un servidor dedicado, pero a un costo mucho más bajo.
* **Seguridad y Estabilidad:** Es una solución más segura y estable que el **hosting compartido**, donde no obtienes espacio de servidor dedicado.
* **Escalabilidad:** Ideal para sitios web con tráfico de nivel medio que exceden los límites del hosting compartido pero que aún no necesitan los recursos de un servidor dedicado completo.

---

# Conexión Mediante SSH

## Introducción a SSH
* **Simulación de VPS Remoto:** Aunque nuestra máquina virtual esté en nuestro ordenador, la simularemos como un VPS remoto. Para conectarnos de forma segura a una máquina remota, la opción más recomendable es **SSH (Secure Shell)**.
* **Protocolo Criptográfico:** SSH es un protocolo de red criptográfico que permite operar servicios de red de forma segura a través de una red no protegida.

---

## Funcionamiento de SSH
* **Arquitectura Cliente-Servidor:** SSH proporciona un canal seguro mediante una arquitectura cliente-servidor, conectando una aplicación cliente SSH con un servidor SSH.
* **Puerto Estándar:** El puerto TCP estándar para SSH es el **22**, utilizado comúnmente para acceder a sistemas operativos similares a Unix, pero también compatible con Microsoft Windows.
* **Mecanismo:** Proporciona un mecanismo para autenticar un usuario remoto, transferir entradas desde el cliente al host y retransmitir la salida de vuelta al cliente.

---

## Aplicaciones de SSH
* Gestión de servidores remotos.
* Transferencia segura de archivos.
* Creación de copias de seguridad.
* Conexión cifrada de extremo a extremo entre ordenadores.
* Mantenimiento remoto.

---

# Autenticación en SSH

## Métodos de Autenticación
Los dos métodos de autenticación de usuario SSH más comunes son:

1.  **Contraseñas (Cifrado Simétrico):**
    * Los clientes envían contraseñas cifradas al servidor de forma segura.
    * **Riesgo:** La seguridad depende de la fortaleza de la contraseña elegida por el usuario.

2.  **Claves SSH (Cifrado Asimétrico o de Clave Pública):**
    * Utiliza pares de claves pública-privada SSH encriptados asimétricamente.
    * **Mayor Seguridad:** Una vez que el cliente descifra el mensaje con su clave privada, el servidor le otorga acceso al sistema.

---

## Cifrado Híbrido en SSH
* SSH utiliza un **cifrado híbrido**: se emplea cifrado asimétrico para intercambiar las claves, y luego estas claves se utilizan en el cifrado simétrico para el intercambio real de información.

---

## Cifrado Simétrico o de Clave Privada

### Características
* Utiliza la **misma clave** para cifrar y descifrar la información.
* La clave debe ser **secreta** y conocida solo por el emisor y el receptor.

### Ventajas
* **Muy rápidos:** El proceso de cifrado y descifrado es eficiente.

### Inconvenientes
* **Riesgo de Intercepción:** Si la clave es interceptada, la comunicación puede ser espiada.
* **Distribución de la Clave:** Es un desafío inicial cómo emisor y receptor pueden conocer la clave sin transmitirla por un canal inseguro (Ejemplos: PIN de tarjeta bancaria, archivo comprimido con contraseña).

---

## Cifrado Asimétrico o de Clave Pública

### Características
* Cada usuario utiliza un **par de claves**: una **clave pública** y una **clave privada**.
* Un mensaje cifrado con la clave pública solo se puede descifrar con su correspondiente clave privada, y viceversa.

### Claves
* **Clave Pública:** Accesible a cualquier persona; no necesita ser transmitida por un canal seguro.
* **Clave Privada:** Solo debe ser conocida por su dueño.

### Funcionamiento
1.  El emisor cifra un mensaje con la clave pública del receptor.
2.  El receptor recibe el mensaje y es el único que puede descifrarlo porque posee la clave privada asociada.

### Ventajas
* No se necesita un canal seguro adicional para transmitir la clave.

### Inconvenientes
* **Más lentos:** Son más lentos que los cifrados simétricos.
* **Protección de la Clave Privada:** La clave privada debe protegerse muy bien y estar siempre disponible.
* **Autenticidad de la Clave Pública:** Es crucial asegurarse de que la clave pública pertenece a quien dice ser y no a un impostor.

---

## Nuestra Práctica
* **Primera Conexión:** Para nuestra primera conexión SSH y para verificar la conectividad, utilizaremos el **cifrado simétrico (una contraseña)**.
* **Entorno Realista y Seguro:** Posteriormente, para simular un entorno real que ofrezca comodidad (evitar introducir la contraseña en cada inicio de sesión) y, sobre todo, por seguridad, emplearemos el **cifrado asimétrico (un par de claves)**.

---