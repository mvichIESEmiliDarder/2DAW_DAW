# Unitat Didàctica 2 - Administració de Servidors Web

## Diapositiva 1: Títol de la Unitat

- **Títol Principal:** Administració de Servidors Web
    
- **Subtítol:** Mòdul Professional "Desplegament d'Aplicacions Web"
    
- **Contingut Addicional:**
    
    - En aquesta unitat, aprofundirem en el funcionament i la configuració dels servidors web.
        
    - Veurem com preparar i optimitzar un servidor per allotjar aplicacions web de manera eficient i segura.
        
- **Element visual suggerit:** Una icona que representi un servidor o un centre de dades.
    

---

## Diapositiva 2: Característiques Generals d'un Servidor Web

- **Títol:** El Cor de la Web: Servidors Web
    
- **Contingut:**
    
    - **Funció Essencial:** Rebre peticions HTTP/HTTPS dels clients (navegadors) i lliurar el contingut web sol·licitat.
        
    - **Model Client-Servidor:** Actua com un oient constant esperant connexions.
        
    - **Concurrència:** Capacitat per gestionar múltiples peticions simultàniament.
        
    - **Gestió de Contingut Estàtic:** Fitxers HTML, CSS, JavaScript, imatges, vídeos, etc.
        
    - **Reenviament de Contingut Dinàmic:** Col·labora amb servidors d'aplicacions (com vam veure a la UD1) per generar respostes dinàmiques.
        
    - **Registres (Logs):** Genera registres d'accés i errors crucials per al monitoratge i la depuració.
        
    - **Seguretat:** Implementa mecanismes per protegir el servidor i les dades.
        
- **Element visual suggerit:** Un diagrama simple que mostri múltiples clients (navegadors) enviant fletxes a un únic servidor web.
    

---

## Diapositiva 3: Protocol HTTP

- **Títol:** El Llenguatge de la Web: HTTP
    
- **Contingut:**
    
    - **HTTP (Hypertext Transfer Protocol):** Protocol de comunicació principal per a la transferència d'informació a la World Wide Web.
        
    - **Basat en text:** Els missatges són llegibles per humans (tot i que encapsulats).
        
    - **Sense estat (Stateless):** Cada petició HTTP és independent de les anteriors. El servidor no "recorda" la interacció prèvia amb el client.
        
    - **Mètodes HTTP:**
        
        - `GET`: Sol·licitar un recurs.
            
        - `POST`: Enviar dades per ser processades.
            
        - `PUT`: Actualitzar un recurs.
            
        - `DELETE`: Eliminar un recurs.
            
        - `HEAD`, `OPTIONS`, `PATCH`, etc.
            
    - **Codis d'Estat HTTP:**
        
        - `2xx` (Èxit): `200 OK`, `201 Created`.
            
        - `3xx` (Redirecció): `301 Moved Permanently`.
            
        - `4xx` (Error del Client): `404 Not Found`, `403 Forbidden`, `400 Bad Request`.
            
        - `5xx` (Error del Servidor): `500 Internal Server Error`, `503 Service Unavailable`.
            
- **Element visual suggerit:** Un gràfic de flux d'una petició HTTP (client demana, servidor respon amb codi d'estat).
    

---

## Diapositiva 4: Tipus MIME

- **Títol:** Tipus MIME: Dient al Navegador Què Rep
    
- **Contingut:**
    
    - **MIME (Multipurpose Internet Mail Extensions):** Estàndard que indica la naturalesa i el format d'un document, fitxer o conjunt de bytes.
        
    - **Funció:** Els servidors web envien capçaleres `Content-Type` en les respostes HTTP amb el tipus MIME, perquè els navegadors sàpiguen com interpretar i renderitzar el contingut.
        
    - **Estructura:** `tipus/subtipus` (ex. `text/html`, `image/png`, `application/json`, `application/pdf`).
        
    - **Importància:** Sense el tipus MIME correcte, el navegador podria mostrar el contingut com a text pla, intentar descarregar-lo o fallar en renderitzar-lo.
        
    - **Configuració:** Els servidors web tenen una llista predefinida de tipus MIME, però es poden afegir o modificar per servir nous tipus de fitxers o assegurar la correcta interpretació.
        
- **Element visual suggerit:** Una taula senzilla amb exemples de tipus MIME i el seu propòsit.
    

---

## Diapositiva 5: Configuració Avançada del Servidor Web (I)

- **Títol:** Fitxers de Configuració i Conceptes Avançats
    
- **Contingut:**
    
    - **Fitxers de Configuració:** On es defineix el comportament del servidor.
        
        - **Apache HTTP Server:** `httpd.conf` (principal), `.htaccess` (per directori), fitxers de configuració a `conf.d/` o `sites-available/`.
            
        - **Nginx:** `nginx.conf` (principal), fitxers a `conf.d/` o `sites-available/`.
            
        - **Microsoft IIS:** `web.config` (a nivell d'aplicació), configuració al Manager d'IIS.
            
    - **Directives Comunes:**
        
        - Rutes d'accés a documents (`DocumentRoot`).
            
        - Ports d'escolta (`Listen`).
            
        - Noms de servidor (`ServerName`).
            
        - Configuració de logs (`ErrorLog`, `CustomLog`).
            
        - Opcions de directori (`Options`, `AllowOverride`).
            
    - **Reescriptura d'URLs (URL Rewriting):**
        
        - Permet transformar dinàmicament les URLs que veu l'usuari o les que arriben al servidor.
            
        - Millora l'estètica, el SEO i la seguretat (ex. `mod_rewrite` a Apache, `rewrite` a Nginx).
            
- **Element visual suggerit:** Fragments de codi de configuració d'Apache o Nginx.
    

---

## Diapositiva 6: Mòduls, Hosts Virtuals i Autenticació

- **Títol:** Ampliant Capacitats: Mòduls i Hosts Virtuals
    
- **Contingut:**
    
    - **Mòduls (Extensions):**
        
        - Components de programari que estenen la funcionalitat base del servidor web.
            
        - Exemples: Mòduls per a llenguatges de scripting (PHP, Python), per a compressió (gzip), seguretat, SSL/TLS, balanç de càrrega.
            
        - **Instal·lació, Configuració i Ús:** Es carreguen i configuren dins dels fitxers de configuració del servidor.
            
    - **Hosts Virtuals (Virtual Hosts):**
        
        - Permeten a un únic servidor web allotjar múltiples llocs web o dominis diferents a la mateixa màquina física o IP.
            
        - **Tipus:**
            
            - _Basats en Nom:_ El servidor diferencia els llocs pel nom de domini en la petició HTTP (el més comú).
                
            - _Basats en IP:_ Cada lloc té la seva pròpia adreça IP (menys comú avui dia a causa de l'esgotament d'IPs).
                
        - **Creació, Configuració i Utilització:** Es defineixen blocs de configuració separats per a cada host virtual.
            
    - **Autenticació i Control d'Accés:**
        
        - **Autenticació Bàsica:** Protecció de directoris o fitxers mitjançant usuari i contrasenya (ex. `.htpasswd` a Apache).
            
        - **Control d'Accés per IP:** Restringir l'accés a certs recursos basant-se en l'adreça IP del client.
            
- **Element visual suggerit:** Diagrama mostrant un servidor web amb múltiples "hosts virtuals" servint diferents dominis.
    

---

## Diapositiva 7: El Protocol HTTPS i Certificats

- **Títol:** HTTPS: Seguretat al Web
    
- **Contingut:**
    
    - **HTTPS (Hypertext Transfer Protocol Secure):** Versió segura d'HTTP. La comunicació entre el client i el servidor està xifrada.
        
    - **Per què HTTPS?:**
        
        - **Confidencialitat:** Impedeix que tercers interceptin i llegeixin les dades.
            
        - **Integritat:** Garanteix que les dades no han estat alterades en trànsit.
            
        - **Autenticació:** Verifica la identitat del servidor (i opcionalment del client).
            
    - **Funcionament:** Utilitza SSL/TLS (Secure Sockets Layer/Transport Layer Security) per xifrar la comunicació.
        
    - **Certificats Digitals (SSL/TLS Certificates):**
        
        - Un fitxer digital que vincula una clau pública amb la identitat d'una organització o individu.
            
        - Emesos per **Autoritats de Certificació (CA)** de confiança (ex. Let's Encrypt, DigiCert).
            
        - Contenen informació sobre el propietari del certificat, la clau pública, la CA que el va emetre i la seva data de validesa.
            
    - **Instal·lació i Configuració:** Implica obtenir el certificat, la clau privada i configurar el servidor web per usar-los al port 443.
        
- **Element visual suggerit:** Un cadenat o un diagrama simple de com HTTPS afegeix una capa de seguretat.
    

---

## Diapositiva 8: Navegadors Web i la seva Configuració

- **Títol:** Els Clients: Navegadors Web
    
- **Contingut:**
    
    - **Funció:** Els navegadors web (Chrome, Firefox, Edge, Safari) són els clients que sol·liciten, interpreten i mostren el contingut de la World Wide Web.
        
    - **Procés:** Envien peticions HTTP/HTTPS, renderitzen HTML, apliquen CSS, executen JavaScript i mostren multimèdia.
        
    - **Paràmetres d'Aparença i Ús:**
        
        - **Caché:** Com i quan el navegador emmagatzema còpies locals de recursos per accelerar la navegació. (¡Important per a desenvolupadors i desplegaments!).
            
        - **Galetes (Cookies):** Emmagatzematge de petites dades al client per mantenir l'estat o preferències.
            
        - **Configuració de Seguretat i Privadesa:** Bloqueig de finestres emergents (pop-ups), permisos de micròfon/càmera, gestió de rastrejadors.
            
        - **Extensions/Plugins:** Funcionalitats addicionals.
            
        - **Eines de Desenvolupament:** Consola, inspector d'elements, monitor de xarxa (crucials per depurar el desplegament).
            
    - **Compatibilitat:** És vital provar les aplicacions web en diferents navegadors i dispositius.
        
- **Element visual suggerit:** Icones de navegadors populars i un esquema de la finestra de configuració.
    

---

## Diapositiva 9: Desplegament i Proves d'Aplicacions en Servidors Web

- **Títol:** Posant l'Aplicació en Marxa
    
- **Contingut:**
    
    - **Desplegament d'Aplicacions sobre Servidors Web:**
        
        - El procés de copiar els fitxers de l'aplicació (HTML, CSS, JS, imatges, scripts del costat del servidor) al directori de documents del servidor web.
            
        - Per a aplicacions dinàmiques, assegurar que el servidor web sàpiga com passar les peticions a l'intèrpret de llenguatge (PHP, Python) o al servidor d'aplicacions (Tomcat, Node.js).
            
        - **Mètodes:** FTP/SFTP, SCP, Git (pull al servidor), eines d'automatització.
            
    - **Proves de Funcionament de l'Aplicació Web:**
        
        - **Verificació d'Accés:** Comprovar que l'aplicació és accessible des d'un navegador utilitzant la seva URL.
            
        - **Proves de Funcionalitat Bàsica:** Provar les característiques principals (formularis, enllaços, bases de dades).
            
        - **Revisió de Registres (Logs):** Examinar els logs d'accés i errors del servidor web per identificar problemes.
            
        - **Proves de Rendiment:** Avaluar la velocitat de càrrega i resposta de l'aplicació sota càrrega.
            
        - **Proves de Seguretat:** Verificar que la configuració de seguretat està activa (HTTPS, autenticació).
            
        - **Proves en Diferents Navegadors/Dispositius:** Confirmar la compatibilitat.
            
- **Element visual suggerit:** Un diagrama de flux del procés de desplegament i un checklist simple de proves.
    

---

## Diapositiva 10: Resum i Mirada Endavant

- **Títol:** Conclusions de l'Administració de Servidors Web
    
- **Contingut:**
    
    - Hem cobert els fonaments dels servidors web, el protocol HTTP i la importància dels tipus MIME.
        
    - Hem explorat configuracions avançades com hosts virtuals, mòduls i la crucial implementació d'HTTPS.
        
    - Finalment, hem entès com desplegar i realitzar proves inicials de les nostres aplicacions web.
        
- **Propers Passos:**
    
    - La següent unitat se centrarà en l'**Administració de Servidors d'Aplicacions**, on aprendrem a gestionar l'entorn d'execució per a la lògica de negoci dinàmica de les nostres aplicacions.
        
- **Preguntes i Debat:** Obrim un espai per a qualsevol dubte o per discutir experiències.
    
- **Element visual suggerit:** Una icona d' "engranatge" o "configuració" i una fletxa cap a la propera unitat.
    

---

Espero que aquest desglossament detallat et serveixi d'excel·lent base per a les teves diapositives de Google Slides. ¡A construir aquesta presentació!