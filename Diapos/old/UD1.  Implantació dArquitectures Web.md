# Unitat Didàctica 1 - Implantació d'Arquitectures Web

## Diapositiva 1: Títol de la Unitat

- **Títol Principal:** Implantació d'Arquitectures Web
    
- **Subtítol:** Mòdul Professional "Desplegament d'Aplicacions Web"
    
- **Contingut Addicional:**
    
    - Aquest tema és fonamental per entendre com funcionen les aplicacions web i com les prepararem per a la seva posada en marxa.
        
    - Veurem des dels conceptes bàsics fins als models més utilitzats avui dia.
        
- **Element visual suggerit:** Un gràfic abstracte que representi la interconnexió de diferents elements.
    

---

## Diapositiva 2: Aspectes Generals d'Arquitectures Web

- **Títol:** Què és una Arquitectura Web?
    
- **Contingut:**
    
    - **Definició:** L'arquitectura web es refereix a l'estructura fonamental d'un sistema web. Inclou els components de programari (servidors, bases de dades, APIs, etc.), les seves propietats externes i les relacions entre ells.
        
    - **Propòsit:** Defineix com interactuen els diferents elements per oferir una aplicació funcional i robusta als usuaris.
        
    - **Importància:** Una bona arquitectura és clau per al rendiment, l'escalabilitat, la seguretat i el manteniment a llarg termini d'una aplicació web.
        
    - **Evolució:** Les arquitectures han evolucionat des de simples pàgines estàtiques fins a sistemes complexos distribuïts.
        
    - **Preguntes per a l'audiència:** Quins elements creieu que componen una aplicació web típica?
        
- **Element visual suggerit:** Un diagrama senzill d'un navegador connectant-se a un servidor.
    

---

## Diapositiva 3: Pilars d'una Arquitectura Robusta

- **Títol:** Propietats Clau de les Arquitectures Web
    
- **Contingut:**
    
    - **Escalabilitat:** Capacitat del sistema per gestionar un augment de la càrrega de treball (usuaris, dades, transaccions) sense sacrificar el rendiment.
        
        - **Escalat Vertical:** Augmentar els recursos d'un únic servidor (més CPU, RAM).
            
        - **Escalat Horitzontal:** Afegir més servidors per distribuir la càrrega.
            
    - **Portabilitat:** Facilitat amb la qual una aplicació o els seus components poden ser migrats o executats en diferents entorns de maquinari o programari amb poca o cap modificació.
        
    - **Componentització:** Descomposició d'una aplicació en mòduls o components independents, reutilitzables i amb responsabilitats ben definides. Facilita el desenvolupament, el manteniment i el desplegament.
        
    - **Patrons de Disseny:** Solucions generals i reutilitzables a problemes comuns en el disseny de programari. No són solucions finals, sinó plantilles.
        
        - **Exemples:** MVC (Model-Vista-Controlador), Injecció de Dependències, Singleton.
            
- **Element visual suggerit:** Icones representatives d'escalabilitat (fletxes cap amunt i als costats), portabilitat (maleta o caixa que es mou), components (peces de Lego) i patrons (un trencaclosques encaixant).
    

---

## Diapositiva 4: Arquitectures Web: Models (I)

- **Títol:** Models Arquitectònics Clàssics
    
- **Contingut:**
    
    - **Arquitectura Monolítica:**
        
        - Totes les funcionalitats (interfície d'usuari, lògica de negoci, accés a dades) s'empaqueten en una única unitat.
            
        - **Avantatges:** Fàcil de desenvolupar inicialment, desplegar i provar per a projectes petits.
            
        - **Desavantatges:** Dificultat per escalar components individualment, gran base de codi, desplegaments lents, risc d'"efecte dominó" en fallades.
            
    - **Arquitectura de N-Capes (o Multi-Capes):**
        
        - Separa les responsabilitats en capes lògiques diferents.
            
        - **Comuns:** Presentació (UI), Lògica de Negoci (Backend), Accés a Dades (Persistència).
            
        - **Avantatges:** Millora l'organització, la mantenibilitat i l'escalabilitat de cada capa.
            
        - **Desavantatges:** Pot generar una comunicació complexa entre capes.
            
- **Element visual suggerit:** Diagrames clars per a Monolítica (una caixa gran) i N-Capes (caixes apilades).
    

---

## Diapositiva 5: Arquitectures Web: Models (II)

- **Títol:** Models Arquitectònics Moderns
    
- **Contingut:**
    
    - **Arquitectura Orientada a Serveis (SOA):**
        
        - L'aplicació es construeix com una col·lecció de serveis feblement acoblats que es comuniquen entre ells.
            
        - Enfocament en la reutilització de serveis.
            
        - **Exemples:** Ús de SOAP o REST.
            
    - **Microserveis:**
        
        - Evolució de SOA. Aplicació composta per petits serveis autònoms, cadascun amb la seva pròpia base de dades i lògica de negoci.
            
        - **Avantatges:** Major agilitat, escalat independent, resiliència a fallades, flexibilitat tecnològica.
            
        - **Desavantatges:** Major complexitat de gestió, monitorització i desplegament.
            
    - **Serverless (Funcions com a Servei - FaaS):**
        
        - Permet executar codi sense haver de provisionar o gestionar servidors. El proveïdor del núvol gestiona tota la infraestructura.
            
        - **Exemples:** AWS Lambda, Google Cloud Functions, Azure Functions.
            
        - **Avantatges:** Pagament per ús real, escalat automàtic, reducció de la sobrecàrrega operativa.
            
- **Element visual suggerit:** Diagrames per a SOA (serveis interconnectats), Microserveis (petites caixes distribuïdes) i Serverless (un núvol amb funcions flotant).
    

---

## Diapositiva 6: Plataformes Web Lliures i Propietàries

- **Títol:** Elecció de l'Ecosistema de Desenvolupament i Desplegament
    
- **Contingut:**
    
    - **Plataformes Lliures (Open Source):**
        
        - **Definició:** Programari el codi font del qual està disponible públicament, permetent el seu ús, modificació i distribució lliurement.
            
        - **Avantatges:** Sense costos de llicència, gran comunitat de suport, flexibilitat, transparència, innovació constant.
            
        - **Exemples:**
            
            - **Sistemes Operatius:** Linux (Ubuntu, Debian, CentOS).
                
            - **Servidors Web:** Apache HTTP Server, Nginx.
                
            - **Servidors d'Aplicacions:** Apache Tomcat, JBoss/WildFly, Node.js.
                
            - **Bases de Dades:** MySQL, PostgreSQL, MongoDB.
                
            - **Llenguatges/Frameworks:** PHP, Python (Django, Flask), Ruby (Rails), Java (Spring Boot), JavaScript (Node.js, React, Angular, Vue).
                
    - **Plataformes Propietàries:**
        
        - **Definició:** Programari amb restriccions en el seu ús, modificació i distribució; el codi font no és públic i requereix llicències.
            
        - **Avantatges:** Suport tècnic i garanties directes del proveïdor, solucions integrades, certificacions.
            
        - **Exemples:**
            
            - **Sistemes Operatius:** Microsoft Windows Server.
                
            - **Servidors Web:** Microsoft IIS (Internet Information Services).
                
            - **Servidors d'Aplicacions:** Microsoft .NET (IIS), Oracle WebLogic, IBM WebSphere, Adobe ColdFusion.
                
            - **Bases de Dades:** Microsoft SQL Server, Oracle Database.
                
- **Element visual suggerit:** Logos d'algunes de les tecnologies esmentades, dividits en dues columnes.
    

---

## Diapositiva 7: Servidors Web i d'Aplicacions (I)

- **Títol:** Servidors Web: La Porta d'Entrada
    
- **Contingut:**
    
    - **Funció Principal:** Gestionar les peticions HTTP/HTTPS dels clients (navegadors) i lliurar contingut web.
        
    - **Contingut que serveixen:**
        
        - Principalment contingut estàtic: fitxers HTML, CSS, JavaScript, imatges, vídeos, fonts.
            
        - Poden reenviar peticions a servidors d'aplicacions per a contingut dinàmic.
            
    - **Com funcionen:** Escolten en ports específics (ex. 80 per a HTTP, 443 per a HTTPS) i responen a les sol·licituds.
        
    - **Instal·lació i Configuració Bàsica:**
        
        - Generalment instal·lats com un servei del sistema operatiu.
            
        - Configuració inicial implica definir el port d'escolta, la carpeta arrel dels fitxers web (`document root`) i la gestió de fitxers d'índex (ex. `index.html`).
            
    - **Exemples Comuns:**
        
        - **Apache HTTP Server:** Molt estès, modular, flexible.
            
        - **Nginx:** Lleuger, d'alt rendiment, excel·lent per servir fitxers estàtics i com a proxy invers.
            
        - **Microsoft IIS:** Integrat amb Windows Server, per a entorns .NET.
            
- **Element visual suggerit:** Un diagrama que mostri un navegador connectant-se a un servidor web i aquest servint un fitxer HTML.
    

---

## Diapositiva 8: Servidors Web i d'Aplicacions (II)

- **Títol:** Servidors d'Aplicacions: El Cervell Dinàmic
    
- **Contingut:**
    
    - **Funció Principal:** Executar la lògica de negoci de l'aplicació, interactuar amb bases de dades, generar contingut dinàmic i gestionar sessions d'usuari.
        
    - **Contingut que serveixen:** HTML generat dinàmicament, APIs RESTful, serveis web, etc.
        
    - **Relació amb Servidor Web:** Sovint, un servidor web actua com a proxy invers, rebent les peticions del client i reenviant-les al servidor d'aplicacions per processar la lògica dinàmica.
        
    - **Instal·lació i Configuració Bàsica:**
        
        - Depèn del llenguatge i framework (JVM per a Java, Node.js runtime per a JavaScript, etc.).
            
        - Configuració inicial implica la definició de ports, fonts de dades (connexions a DB), pools de fils, etc.
            
    - **Exemples Comuns:**
        
        - **Apache Tomcat:** Servidor d'aplicacions Java EE (Servlet/JSP Container).
            
        - **JBoss / WildFly:** Servidor d'aplicacions Java EE complet.
            
        - **Node.js (amb Express/NestJS):** Entorn d'execució JavaScript del costat del servidor.
            
        - **Gunicorn / uWSGI (per a Python):** Servidors WSGI per a aplicacions Python.
            
- **Element visual suggerit:** Un diagrama que estengui l'anterior: navegador -> servidor web -> servidor d'aplicacions -> base de dades.
    

---

## Diapositiva 9: Estructura i Recursos d'una Aplicació Web

- **Títol:** Components Interns d'una Aplicació Web
    
- **Contingut:**
    
    - **Fitxers Estàtics:** HTML, CSS, JavaScript, imatges, fonts, vídeos. Solen anar en directoris específics (`public`, `static`, `assets`).
        
    - **Fitxers Dinàmics / Lògica de Negoci:** Codi font de l'aplicació (Java, Python, PHP, Node.js) que processa sol·licituds, interactua amb la base de dades, etc.
        
    - **Llibreries i Dependències:** Biblioteques de tercers que l'aplicació necessita per funcionar (ex. JARs a Java, `node_modules` a Node.js, `vendor` a PHP).
        
    - **Fitxers de Configuració:** Defineixen paràmetres de l'aplicació, com cadenes de connexió a bases de dades, claus API, variables d'entorn.
        
    - **Recursos de Base de Dades:** Scripts SQL per a la creació de l'esquema (`schema.sql`), dades inicials (`data.sql`), migracions.
        
    - **Concepte de Build / Empaquetament:** El procés de compilar, optimitzar i empaquetar tots aquests recursos en un format desplegable (ex. WAR, JAR, Docker Image, ZIP).
        
- **Element visual suggerit:** Una estructura d'arbre de directoris amb exemples de cada tipus de fitxer.
    

---

## Diapositiva 10: El Descriptor de Desplegament

- **Títol:** Descriptor de Desplegament: El Full de Ruta del Servidor
    
- **Contingut:**
    
    - **Definició:** Un fitxer (o conjunt de fitxers) que proporciona al servidor informació sobre com desplegar i executar l'aplicació web. Actua com un contracte entre l'aplicació i l'entorn de desplegament.
        
    - **Propòsit:**
        
        - Defineix la configuració de l'aplicació: rutes d'accés, servlets/controladors, filtres, _listeners_.
            
        - Declara recursos externs que l'aplicació necessita (fonts de dades, cues JMS).
            
        - Especifica el comportament de seguretat (rols, permisos).
            
        - Gestiona errors i redireccions.
            
    - **Exemples Comuns:**
        
        - `web.xml` (Java EE/Servlet): El descriptor de desplegament estàndard per a aplicacions web Java.
            
        - `package.json` (Node.js): Tot i que no és un descriptor de desplegament en el mateix sentit, defineix scripts d'inici i dependències que són crucials per al desplegament.
            
        - `Procfile` (Heroku/PaaS): Fitxer que especifica les comandes que s'executen en iniciar l'aplicació en plataformes PaaS.
            
        - `docker-compose.yml` (Docker Compose): Defineix i executa aplicacions Docker multi-contenidor.
            
    - **Importància:** Assegura que l'aplicació es configuri correctament en diferents entorns de desplegament, facilitant l'automatització.
        
- **Element visual suggerit:** Una icona d'un "plànol" o "mapa", i un exemple de fragment d'un `web.xml` o similar.
    

---

## Diapositiva 11: Resum i Propers Passos

- **Títol:** Recapitulació: La Base del Desplegament
    
- **Contingut:**
    
    - Hem explorat els fonaments de les arquitectures web, des de la seva definició fins als seus models més complexos.
        
    - Hem diferenciat entre plataformes lliures i propietàries, i comprès els rols dels servidors web i d'aplicacions.
        
    - Finalment, hem analitzat l'estructura interna de les aplicacions web i la importància del descriptor de desplegament.
        
- **Propers Passos:**
    
    - En la següent unitat, ens endinsarem en l'**Administració de Servidors Web**, on aprendrem a configurar i gestionar a fons aquestes eines.
        
- **Preguntes:** Alguna pregunta o comentari abans de concloure aquest tema?
    
- **Element visual suggerit:** Un gràfic de progrés o un "tick" verd per als temes coberts.
    

---

Espero que aquesta estructura detallada et sigui molt útil per preparar les teves Google Slides. Molt èxit amb la presentació!