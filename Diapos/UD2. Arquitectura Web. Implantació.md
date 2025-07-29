## Arquitectura Web: Implantació i Administració de Servidors Web

### Com publiquem i gestionem els nostres projectes al món?

---

## Introducció: La Web Avui

- Internet ens ha obert la porta a la **publicació de pàgines web**.
    
- Podem emmagatzemar continguts atractius i fer-los accessibles des de qualsevol lloc del món.
    
- Empreses i usuaris necessiten un punt per anunciar els seus productes o donar publicitat a les seves aficions.
    

---

## El Cor de la Web: Les Pàgines HTML

- Les pàgines web, majoritàriament en format **HTML**, requereixen ser allotjades en màquines.
    
- Aquestes màquines han de disposar d'espai en disc per emmagatzemar arxius HTML, imatges, codi o vídeo.
    
- Han de ser capaces d'entendre tot tipus d'extensió d'arxius en la comunicació.
    

---

## Seguretat: Un Punt Clau

- La seguretat és vital davant els perills d'Internet.
    
- Les pàgines han de dissenyar-se amb protocols de comunicació segurs, com **HTTPS (Hyper Text Transfer Protocol secure)**.
    
- HTTPS utilitza claus i estratègies de xifrat pròpies de les eines **SSL (Secure Sockets Layer)**.
    

---

## Els Servidors Web: El Nostre Host

- Les màquines que allotgen les pàgines web reben la categoria de **servidors web**.
    
- Requeriments clau:
    
    - **Espai de disc** suficient per a l'estructura de la pàgina.
        
    - Una **bona connexió de xarxa**.
        
    - Consum de CPU baix.
        

---

## Funcionament dels Servidors Web: Pic i Vall

- El seu funcionament és especial, com una dent de serra: tenen consums de recursos puntuals.
    
- Poden estar un temps sense peticions i, de sobte, tenir una allau de peticions.
    
- Això fa que els servidors web acostumin a tenir un nombre baix de processos en espera, que es van engegant a mesura que són necessaris.
    
- Les pàgines amb interacció amb l'usuari o xifrat (HTTPS) consumeixen més recursos.
    

---

## Què és un Servidor Web (Repàs)?

- Els **servidors web** serveixen per emmagatzemar continguts d'Internet i facilitar la seva disponibilitat constant i segura.
    
- Quan visites una pàgina, el servidor web envia els seus components directament al teu ordinador.
    
- Perquè una pàgina sigui accessible, el servidor web ha d'estar permanentment en línia.
    

---

## Servidors Web: Propi o Arrendat?

- Tota pàgina accessible a Internet necessita un servidor especial.
    
- Grans empreses poden tenir un servidor web propi per a Intranet i Internet.
    
- La majoria d'administradors recorren a centres de dades de proveïdors d'allotjament web.
    
- Sempre necessitaràs programari per gestionar les dades i mantenir la pàgina actualitzada.
    

---

## Tecnologia de Servidors Web: El Programari HTTP

- Principalment, el **programari d'un servidor HTTP** és l'encarregat de proporcionar les dades per a la visualització del contingut web.
    
- Quan s'accedeix a una URL, el navegador envia una sol·licitud al servidor web, que respon amb la pàgina (HTML, per exemple).
    
- La pàgina pot ser un document estàtic o generada dinàmicament (executant codi com Java o PHP).
    

---

## El Flux de la Informació

- El navegador interpreta la resposta, i això sol generar més sol·licituds al servidor (per imatges, arxius CSS, etc.).
    
- El protocol utilitzat per a la transmissió és **HTTP** (o la seva variant xifrada **HTTPS**).
    
- HTTP es basa en els protocols de xarxa **IP i TCP** (i molt poques vegades en UDP).
    
- Un servidor web pot lliurar continguts simultàniament a diversos ordinadors o navegadors.
    

---

## Rendiment i Càrrega

- La quantitat de sol·licituds i la velocitat de processament depenen del _hardware_ i la càrrega del host.
    
- Els continguts web dinàmics necessiten més recursos que els continguts estàtics.
    
- La selecció de l'equip i si és dedicat, virtual o al núvol, ha de pensar en evitar sobrecàrregues.
    
- Risc de _downtime_ (inactivitat) per fallades tècniques o talls d'energia.
    

---

## Altres Funcions dels Servidors Web

- **Seguretat**: Xifrat HTTPS, autenticació d'usuari, autenticació HTTP per àrees específiques.
    
- **Redirecció**: D'una sol·licitud de document per mitjà de _Rewrite Engine_.
    
- **Emmagatzematge en memòria cau (_caching_)**: De documents dinàmics per a respostes eficients i evitar sobrecàrrega.
    
- **Assignació de _cookies_**: Enviament i processament de _cookies_ HTTP.
    

---

## Més enllà del Web

- Un host pot contenir altres programes, com un servidor **FTP** (per a càrrega d'arxius) o un servidor de **base de dades** (per a continguts dinàmics).
    
- Existeixen diferents tipus de servidors per a nombrosos propòsits: correu, jocs, _proxy_, etc..
    

---

## El Protocol HTTP: El Motor de la Web

- El **protocol de transferència d'hipertext (HTTP)** és la base per a la **web (WWW)**.
    
- Va ser creat el 1989 al **CERN** per la necessitat de col·laboració entre científics de diferents països.
    
- La **versió 0.9 (1990)** només transferia pàgines HTML.
    
- La **versió 1.0** va permetre transferir missatges amb encapçalats que descrivien el contingut.
    

---

## Versions d'HTTP: Evolució

- **HTTP/1 (v0.9)**: Només sol·licitava un arxiu HTML i el servidor el transferia.
    
- **HTTP/1.1 (Estàndard oficial)**:
    
    - Connexions reutilitzables.
        
    - _Pipelining_: Segona petició abans de la resposta de la primera.
        
    - Respostes dividides en subparts.
        
    - Negociació de contingut (idioma, codificació).
        
    - **Capçalera _Host_**: Allotjar diversos dominis a la mateixa IP.
        

---

## HTTP/2: Major Rendiment

- Les pàgines web es van tornar més àmplies i complexes, amb moltes sol·licituds HTTP.
    
- HTTP/1.1 processa sol·licituds una rere l'altra, causant latència.
    
- Google va desenvolupar **SPDY (Speedy)**, que va donar lloc a **HTTP/2 (2015)**.
    
- HTTP/2 accelera la càrrega de les pàgines web.
    
- Actualment (gener de 2020), un 42% de les pàgines web utilitzen HTTP/2.
    

---

## El Futur: HTTP/3

- Punt feble de versions anteriors: **TCP**.
    
- TCP requereix confirmació de cada paquet, i si un es perd, tots esperen.
    
- **HTTP/3 no funcionarà amb TCP, sinó amb UDP**.
    
- Es basa en el protocol **QUIC (Quick UDP Internet Connections)**.
    

---

## Funcionament del Protocol HTTP: Pas a Pas

1. **Usuari accedeix a una URL** (enllaç o introduint-la al navegador).
    
2. **Client Web descodifica la URL**: Separa protocol, adreça DNS/IP, port (defecte 80) i objecte requerit.
    
    - Exemple: `http://www.mevaweb.com/document.html`.
        
3. **S'obre una connexió TCP/IP amb el servidor**: Al port TCP corresponent.
    
    - Es realitza la **petició HTTP**: S'envia la comanda (GET, POST, HEAD,...), l'adreça de l'objecte, la versió del protocol i informació del navegador.
        

---

## Funcionament del Protocol HTTP: La Resposta

4. **El servidor retorna la resposta al client**: Consisteix en un codi d'estat, el tipus de dada MIME de la informació i la pròpia informació.
    
5. **Es tanca la connexió TCP**.
    
    - Aquest procés es repeteix en cada accés: si hi ha 2 imatges i 1 vídeo en un HTML, el procés es repeteix 4 vegades.
        

---

## Comandes o Mètodes HTTP

- HTTP defineix un conjunt de mètodes de petició per indicar l'acció desitjada per a un recurs.
    
- **HTTP/1.0**:
    
    - **GET**: Sol·licitar informació o recurs.
        
    - **HEAD**: Sol·licitar informació sobre el recurs (mida, tipus, data de modificació).
        
    - **POST**: Enviar informació al servidor (dades d'un formulari).
        

---

## Mètodes HTTP: Versions Posteriors

- **HTTP/1.1** incorpora: **OPTIONS, PUT, DELETE, TRACE i CONNECT**.
    
    - **OPTIONS**: Retorna els mètodes HTTP que el servidor suporta per a una URL.
        
    - **DELETE**: Eliminar un recurs (poques vegades permès).
        
    - **TRACE**: Sondatge per saber els dispositius de la xarxa pels quals passa la petició.
        
    - **PUT**: Escriure dades al servidor, crear o reemplaçar un recurs. (Orientat a l'actualització, a diferència de POST, que és més per creació).
        
- **HTTP/2 no inclou mètodes nous**.
    

---

## Exemple: Petició HTTP

- Una **sol·licitud HTTP** és un conjunt de línies que el navegador envia al servidor. Inclou:
    
    - El recurs sol·licitat, el mètode i la versió del protocol.
        
    - **Camps de la capçalera de sol·licitud**: Informació addicional sobre la sol·licitud i/o el client (navegador, OS). Format "Nom: Valor".
        
    - **Cos de la sol·licitud**: Línies opcionals separades per una línia en blanc, permeten la transmissió de dades d'un formulari amb POST.
        

---

## Exemple: Resposta HTTP

- La sintaxi d'una **resposta HTTP** és un conjunt de línies que el servidor envia al navegador. Inclou:
    
    - Una **línia d'estat**: Versió del protocol, codi d'estat/error (3 xifres) i text explicatiu.
        
        - Codis d'estat: 1xx (informatius), 2xx (èxit), 3xx (redirecció), 4xx (error client), 5xx (error servidor).
            
    - Els **camps de la capçalera de la resposta**: Informació addicional sobre la resposta i/o el servidor.
        
    - El **cos de la resposta**: Conté el recurs (objecte) sol·licitat.
        

---

## Capçaleres HTTP: Informació Essencial

- Les **capçaleres HTTP** són paràmetres enviats en una petició o resposta HTTP.
    
- Proporcionen informació essencial sobre la transacció en curs.
    
- Sintaxi: "**Capçalera: Valor**".
    
- Són enviades automàticament pel navegador o el servidor web.
    

---

## Tipus MIME: Més enllà de l'ASCII

- HTTP es va dissenyar per transportar fitxers ASCII (text pla).
    
- Va sorgir la necessitat d'incloure fitxers no ASCII (imatges, vídeos, sons).
    
- Es va resoldre amb els **tipus MIME (Multipurpose Internet Mail Extensions)**.
    
- Especifiquen el format de missatges no-ASCII perquè puguin ser enviats i interpretats correctament.
    

---

## Identificadors de Tipus MIME

- Els **tipus de mitjans d'Internet** (també "tipus de mitjans" o "tipus de contingut") indiquen el tipus d'informació d'un arxiu o conjunt de dades.
    
- Útil per conèixer el tipus d'un arxiu abans de descarregar-lo.
    
- Format: `tipus/subtipus[; paràmetre=valor]`.
    
- Exemples: `text/html`, `image/jpeg`, `audio/mpeg`, `application/json`.
    

---

## HTTPS: El Protocol Segur

- **HTTPS (Hypertext Transfer Protocol Secure)** és la versió segura d'HTTP.
    
- La web és insegura per naturalesa; HTTP no va afegir seguretat fins molt després.
    
- El protocol HTTPS original utilitzava **SSL (Secure Sockets Layer)**, però ara s'empra **TLS (Transport Layer Security, v1.3)**.
    
- L'estàndard d'HTTP sobre TLS es va configurar el maig de l'any 2000.
    

---

## HTTPS: Identificació Visual

- Tradicionalment, els navegadors indiquen una connexió segura amb una icona (generalment un cadenat).
    
- L'aspecte canvia segons el navegador, però tots mostren el "cadenat" al costat de l'adreça.
    
- Fins ara, els navegadors consideraven HTTP la norma i HTTPS l'excepció, marcant-lo així.
    

---

## Servidors Web: Apache vs Nginx

- Un servidor web necessita un sistema operatiu (95% **Linux**), gestió de bases de dades (**MySQL**) i programari per continguts dinàmics (**PHP**).
    
- L'elecció del servidor web és clau: **Apache** i **Nginx** són els més coneguts (més del 85% d'ús).
    
- Altres: **Microsoft IIS** (Windows), **LiteSpeed, Node.js**, etc..
    
- No hi ha un millor que l'altre; cadascun té fortaleses i debilitats segons les circumstàncies.
    

---

## Nginx: Rendiment i Eficiència

- **Nginx** està orientat a millorar el rendiment, suportant majors càrregues de trànsit i usuaris (**Problema C10K**).
    
- Ofereix funcionalitats com fer de _proxy_.
    
- Als seus orígens, era especialment eficient oferint contingut estàtic.
    
- Inicialment, s'usava per servir arxius estàtics i com a balancejador de càrrega o _proxy_ invers davant d'instal·lacions Apache.
    

---

## Nginx: Desplegament de Pàgines Estàtiques

- Exemples de serveis que utilitzen Nginx per a desplegament de pàgines estàtiques:
    
    - Netlify
        
    - Surge
        
    - GitHub Pages
        
    - GitLab Pages
        
    - Firebase
        
    - Vercel
        
    - Neocities
        

---

## Raons per Usar Nginx

- **És lleuger**: Redueix el consum de RAM.
    
- **És multiplataforma i fàcil d'instal·lar**: Disponible als repositoris de la majoria de distribucions GNU/Linux.
    
- **Es pot usar juntament amb Apache!**: Algunes empreses usen Nginx per servir contingut estàtic i Apache per al contingut dinàmic.
    
- **Memòria cau**: Es pot usar com a memòria cau per millorar l'eficiència.
    
- **Balancejador de càrrega**: Distribueix el trànsit entre diversos servidors, permetent major escalabilitat.
    
- **Suport comunitari i professional**: Nginx, Inc i la comunitat donen suport.
    
- **Compatibilitat amb les aplicacions web més populars**: Compatible amb CMS com Wordpress, Joomla, Drupal, phpBB, etc..