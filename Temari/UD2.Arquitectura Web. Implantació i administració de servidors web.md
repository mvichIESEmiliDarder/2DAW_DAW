-----

# Introducció

Amb l'evolució i l'accés lliure a Internet, un dels principals al·licients que han sorgit és la publicació de **pàgines web** on es poden emmagatzemar uns continguts força atractius per a nosaltres i que, al mateix temps, poden ser consultats des de qualsevol lloc del món per a tothom.

Cal dir que, amb la popularització d'Internet, tant empreses com usuaris han vist la necessitat d'establir un punt des d'on anunciar els seus productes, o bé, a títol particular, donar publicitat a les aficions o capacitats personals mitjançant la publicació de pàgines web.

Les pàgines web, majoritàriament en format **HTML**, requereixen ser allotjades en màquines que disposin d'espai en disc per emmagatzemar arxius HTML, imatges, blocs de codi o arxius de vídeo en directoris específics i, al mateix temps, han de ser capaces d'entendre tot tipus d'extensió dels arxius que són enviats en ambdós sentits de la comunicació.

![[Pasted image 20250729125106.png]]

Paral·lelament, no podem deixar de banda la importància de les **mesures de seguretat** davant els perills existents a Internet. Per a això, les pàgines hauran d'estar dissenyades considerant la incorporació de protocols de comunicació segurs com, per exemple, els desenvolupats amb el **protocol segur de transferència d'hipertext (HTTPS, Hyper Text Transfer Protocol secure)** que utilitzen claus i estratègies de xifrat pròpies de les eines del **protocol de capa de connexió segura (SSL, Secure Sockets Layer)**.

Les màquines que allotgen les pàgines web reben la categoria de **servidors web**. Des del punt de vista dels servidors, els requeriments més rellevants són l'espai de disc necessari per poder emmagatzemar l'estructura de la pàgina web i una bona connexió de xarxa perquè el consum de la unitat de processament central (CPU, central processing unit) sigui força baix.

El funcionament dels servidors web és especial, ja que, com si es tractés d'una dent de serra, tenen consums de recursos puntuals perquè podem estar un temps sense peticions i, de sobte, tenir una allau de peticions. Això fa que els servidors web acostumin a tenir un nombre baix de processos en espera. A mesura que resulten necessaris, es van engegant de nous.

Cal dir que no totes les peticions consumeixen el mateix, i, per exemple, aquelles pàgines web que executin programes d'interacció amb l'usuari o requereixin xifrat (HTTPS) consumeixen més recursos que altres pàgines web amb menys interacció.

-----

# Què és un servidor web?

Els **servidors web** serveixen per emmagatzemar continguts d'Internet i facilitar-ne la disponibilitat de forma constant i segura. Quan visites una pàgina web des del teu navegador, és en realitat un servidor web el que envia els components individuals d'aquesta pàgina directament al teu ordinador. Això vol dir que, perquè una pàgina web sigui accessible en qualsevol moment, el servidor web ha d'estar permanentment en línia.

![[Pasted image 20250729125119.png]]

Tota pàgina accessible a Internet necessita un servidor especial per als seus continguts web. Sovint, les grans empreses i organitzacions disposen d'un servidor web propi per a posar els seus continguts a la Intranet i Internet. No obstant això, la majoria d'administradors recorren als centres de dades de proveïdors d'allotjament web per als seus projectes. Independentment de si tens un servidor web propi o si n'arrendes un d'extern, sempre necessitaràs un programari per gestionar les dades de la teva pàgina i mantenir-la actualitzada. En aquest sentit, tens la possibilitat de triar entre diverses solucions de programari per a servidors web dissenyades per a diferents aplicacions i sistemes operatius.

-----

# Tecnologia de servidors web

Principalment, el **programari d'un servidor HTTP** és l'encarregat de proporcionar les dades per a la visualització del contingut web.

Per obrir una pàgina web, l'usuari només ha d'escriure la **URL** corresponent a la barra d'adreces del seu navegador web. El navegador envia una sol·licitud al servidor web, que respon, per exemple, lliurant una pàgina HTML. Aquesta pot estar allotjada com un document estàtic a l'host o ser generada de forma dinàmica, la qual cosa significa que el servidor web ha d'executar un codi de programa (p. ex., Java o PHP) abans de tramitar la seva resposta.

El navegador interpreta la resposta, la qual cosa sol generar automàticament més sol·licituds al servidor a propòsit de, per exemple, imatges integrades o arxius **CSS (fulls d'estil)**.

![[Pasted image 20250729125134.png]]

El protocol utilitzat per a la transmissió és **HTTP** (o la seva variant xifrada **HTTPS**), que es basa, al seu torn, en els protocols de xarxa **IP i TCP** (i molt poques vegades en UDP). Un servidor web pot lliurar els continguts simultàniament a diversos ordinadors o navegadors web. La quantitat de sol·licituds (*requests*) i la velocitat amb què poden ser processades depèn, entre altres coses, del *hardware* i la càrrega (nombre de sol·licituds) de l'host. No obstant això, la complexitat del contingut també juga un paper important: els continguts web dinàmics necessiten més recursos que els continguts estàtics.

![[Pasted image 20250729125143.png]]

La selecció de l'equip adequat per al servidor i la decisió de si aquest ha de ser dedicat, virtual o al núvol, s'ha de fer pensant sempre en evitar sobrecàrregues al servidor. Encara que s'hagi trobat un servidor web que s'adapta perfectament a les necessitats del projecte, sempre es corre el risc que es presentin fallades en ell com a conseqüència d'imprecisions tècniques o talls d'energia al centre de dades de l'host. Encara que no és molt freqüent, durant un període d'inactivitat d'aquest tipus (*downtime*), la web no estarà disponible.

-----

# Altres funcions dels servidors web

Encara que la seva principal funció és la transferència de contingut web, molts programes de servidor web ofereixen característiques addicionals:

  * **Seguretat**
      * Xifrat de la comunicació entre el servidor web i el client via **HTTPS**
      * Autenticació de l'usuari
      * Autenticació HTTP per a àrees específiques d'una aplicació web
  * **Redirecció**
      * Redirecció d'una sol·licitud de document per mitjà de *Rewrite Engine*
  * **Emmagatzematge en memòria cau**
      * Emmagatzematge en memòria cau de documents dinàmics per a la resposta eficient de sol·licituds i per evitar una sobrecàrrega del servidor web
  * **Assignació de *cookies***
      * Enviament i processament de *cookies* HTTP

A més del programari del servidor, un host pot contenir un altre tipus de programes, com per exemple un servidor **FTP** per a la càrrega d'arxius o un servidor de **base de dades** per a continguts dinàmics. En general, existeixen diferents tipus de servidors web que poden ser utilitzats per a nombrosos propòsits, per exemple, els servidors de correu, els servidors de jocs o els servidors *proxy*.

-----

# El protocol HTTP

## Història

El **protocol de transferència d'hipertext (HTTP, Hypertext Transfer Protocol)** és el motor que dona vida a Internet, ja que és la base per a la **web (WWW, World Wide Web)**.

Des d'un punt de vista històric, la web va ser creada el 1989 al **Consell Europeu per a la Recerca Nuclear (CERN, Centre Européen pour la Recherche Nucléaire)**, amb seu a Ginebra, just a la frontera entre Suïssa i França. Cal dir que aquest organisme disposava (i disposa) d'una àmplia plantilla de científics de diferents països d'Europa que treballen en els seus acceleradors de partícules. En conseqüència, molts equips de treballadors estan integrats per membres de nacionalitats diferents. A més, molts dels experiments que es realitzen destaquen per la seva complexitat i requereixen anys i anys de planificació i de construcció d'equipaments.

Va ser arran de la necessitat de disposar de múltiples grups de científics repartits pel món i col·laborant entre ells (enviant-se informes, dibuixos, esquemes, fotos i tot tipus de documents) que va néixer la web.

![[Pasted image 20250729125225.png]]

És en els inicis del protocol HTTP, a mitjans de l'any 1990, quan trobem la **versió 0.9**. Aquesta versió tenia com a única finalitat transferir dades per Internet en forma de pàgines web escrites en **llenguatge de marcat d'hipertext (HTML, HyperText Markup Language)**. A partir de la **versió 1.0** del protocol va sorgir la possibilitat de transferir missatges amb encapçalats que descrivien el contingut dels missatges.

## Versions

#### La primera versió: HTTP/1

La història d'HTTP va començar el 1989, quan Tim Berners-Lee i el seu equip del CERN (Suïssa) van començar a desenvolupar la World Wide Web. La versió inicial d'HTTP va ser batejada amb el número de versió **0.9**, consistia en una sola línia i només permetia sol·licitar un arxiu HTML del servidor cada vegada.

El servidor llavors no feia més que transferir l'arxiu sol·licitat, de manera que aquesta versió del protocol només podia manejar arxius HTML.

#### El primer estàndard oficial: HTTP/1.1

**HTTP/1.1** va aclarir ambigüitats i va afegir nombroses millores:

  * Una connexió podia ser reutilitzada, estalviant així el temps de reobrir-la repetides vegades.
  * L'**encaminament** (*Pipelining* en anglès) es va afegir a l'especificació, permetent realitzar una segona petició de dades abans que fos resposta la primera, disminuint d'aquesta manera la latència de la comunicació.
  * Es va permetre que les respostes a peticions podien ser dividides en subparts.
  * La **negociació de contingut**, incloent el llenguatge, el tipus de codificació o tipus, es van afegir a l'especificació, permetent que servidor i client acordessin el contingut més adequat per intercanviar-se.
  * Gràcies a la **capçalera *Host***, va ser possible allotjar diversos dominis a la mateixa adreça IP.

#### Un protocol de major rendiment HTTP/2

A mesura que passaven els anys, les pàgines web es tornaven cada vegada més àmplies i complexes. Per carregar una web moderna al navegador, aquest ha de sol·licitar molts megabytes de dades i enviar fins a cent sol·licituds HTTP. HTTP/1.1 està pensat per processar sol·licituds una rere l'altra en una mateixa connexió, de manera que com més complexa sigui una pàgina web, més temps trigarà a carregar-se i mostrar-se.

Per aquesta raó, Google va desenvolupar un nou i experimental protocol, el **SPDY o Speedy**, que va despertar un gran interès entre els desenvolupadors i va permetre que el 2015 es publiqués la **versió HTTP/2** del protocol. Aquest estàndard inclou múltiples millores que tenen com a objectiu accelerar la càrrega de les pàgines web.

La versió HTTP/2 es va estendre ràpidament i les pàgines web amb molt trànsit van ser de les primeres a adoptar-la. Actualment (amb data de gener de 2020), segons W3Techs, un 42% de les pàgines web utilitzen la versió HTTP/2.

![[Pasted image 20250729125237.png]]

#### El futur: HTTP/3

Un punt feble de totes les versions d'HTTP usades fins ara és el **protocol de control de transmissió (TCP)** en què es basen. Aquest protocol requereix que el receptor de cada paquet de dades confirmi la recepció abans que es pugui enviar el següent paquet. D'aquesta manera, n'hi ha prou amb què es perdi un paquet perquè tots els altres hagin d'esperar que aquest paquet sigui transmès de nou.

Per evitar-ho, la nova versió **HTTP/3** no funcionarà amb TCP, sinó amb **UDP**, que no aplica aquest tipus de mesures correctives. A partir d'UDP, s'ha creat el protocol **QUIC (Quick UDP Internet Connections)**, que serà la base d'HTTP/3.

-----

## Funcionament del protocol HTTP

Ja hem comentat que el protocol HTTP té un funcionament força senzill basat en l'enviament de missatges entre client i servidor.

Gràficament podem resumir el procés de comunicació HTTP com segueix:

![[Pasted image 20250729125251.png]]

1.  Un usuari accedeix a una **URL**, seleccionant un enllaç d'un document HTML o introduint-la directament al camp corresponent del client Web.
2.  El client Web descodifica la URL, separant les seves diferents parts: el protocol d'accés, l'adreça DNS o IP del servidor, el possible port opcional (el valor per defecte és 80) i l'objecte requerit del servidor. `http://adreça[:port][ruta]`
    Exemple: `http://www.mevaweb.com/document.html`
3.  S'obre una **connexió TCP/IP** amb el servidor, trucant al port TCP corresponent. En aquest moment, es realitza la **petició HTTP**. Per a això, s'envia la comanda necessària (**GET, POST, HEAD,...**), l'adreça de l'objecte requerit (el contingut de la URL que segueix a l'adreça del servidor), la versió del protocol HTTP emprada i un conjunt variable d'informació, que inclou dades sobre les capacitats del navegador (*browser*), dades opcionals per al servidor, etc.
4.  El servidor retorna la **resposta al client**. Consisteix en un codi d'estat i el tipus de dada MIME de la informació de retorn, seguit de la pròpia informació.
5.  Es tanca la connexió TCP. Aquest procés es repeteix en cada accés al servidor HTTP. Per exemple, si es recull un document HTML en el qual hi ha inserides 2 imatges i 1 vídeo, el procés anterior es repeteix quatre vegades, una per al document HTML i tres més per als recursos (les dues imatges i el vídeo).

-----

## Comandes o mètodes HTTP

HTTP defineix un conjunt de mètodes de petició per indicar l'acció que es desitja realitzar per a un recurs determinat.

![[Pasted image 20250729125313.png]]

L'estàndard **HTTP/1.0** recull únicament tres comandes, que representen les operacions de recepció i enviament d'informació i verificació d'estat:

  * **GET**: s'utilitza per sol·licitar qualsevol tipus d'informació o recurs al servidor. Cada vegada que es prem sobre un enllaç o es tecleja directament una URL, s'utilitza aquesta comanda. Com a resultat, el servidor HTTP enviarà el recurs corresponent.
  * **HEAD**: s'utilitza per sol·licitar informació sobre el recurs: la seva mida, el seu tipus, la seva data de modificació… És usat pels gestors de memòries cau de pàgines o els servidors *proxy*, per saber quan és necessari actualitzar la còpia que es manté del recurs. Amb HEAD es podrà comprovar l'última data de modificació d'un recurs abans de portar una nova còpia del mateix.
  * **POST**: serveix per enviar informació al servidor, per exemple, les dades contingudes en un formulari. El servidor passarà aquesta informació a un procés encarregat del seu tractament.

La **versió 1.1** del protocol incorpora unes poques comandes més com són: **OPTIONS, PUT, DELETE, TRACE i CONNECT**. Vegem-ne algunes:

  * **OPTIONS**: Retorna els mètodes HTTP que el servidor suporta per a una URL específica. Això pot ser utilitzat per comprovar la funcionalitat d'un servidor web mitjançant petició en lloc d'un recurs específic.
  * **DELETE**: serveix per eliminar un recurs especificat a la URL, encara que poques vegades serà permès per un servidor web.
  * **TRACE**: comanda que permet fer un sondeig per saber tots els dispositius de la xarxa pels quals passa la nostra petició. Així podrem descobrir si la petició passa a través de dispositius intermedis o *proxys* abans d'arribar al servidor Web.
  * **PUT**: pot veure's com la comanda inversa a GET. Ens permet escriure dades al servidor o, el que és el mateix, posar un recurs a la URL que s'especifiqui. Si el recurs no existeix el crea, si no el reemplaça. La diferència amb POST pot ser una mica confusa; mentre que POST està orientat a la creació de nous continguts, PUT està més orientat a l'actualització dels mateixos (encara que també podria crear-los).

**HTTP/2** no inclou mètodes nous.

-----

## Exemple de petició i resposta

Una **sol·licitud HTTP** és un conjunt de línies que el navegador envia al servidor. Inclou:

  * El recurs sol·licitat, el mètode que s'aplicarà i la versió del protocol utilitzada.
  * Els **camps de la capçalera de sol·licitud**: és un conjunt de línies opcionals que permeten aportar informació addicional sobre la sol·licitud i/o el client (navegador, sistema operatiu, etc.). Cadascuna d'aquestes línies està formada per un nom que descriu el tipus de capçalera, seguit de dos punts (:) i el valor de la capçalera.
  * El **cos de la sol·licitud**: és un conjunt de línies opcionals que han d'estar separades de les línies precedents per una línia en blanc i que, per exemple, permeten la transmissió de dades al servidor d'un formulari a través del mètode POST.
![[Pasted image 20250729125346.png]]
La sintaxi d'una **resposta HTTP** és un conjunt de línies que el servidor envia al navegador. Inclou:

  * Una **línia d'estat** on figura la versió del protocol usada, un codi d'estat/error i un text amb el significat d'aquest codi.
      * Els possibles **codis d'estat** s'identifiquen amb nombres de tres xifres i es classifiquen en cinc grups segons siguin informatius (1xx), d'èxit en la sol·licitud (2xx), per redireccionar la sol·licitud (3xx), per error generat al client (4xx) o bé per errors generats al servidor (5xx) $\\rightarrow$ [Codis d'estat/error](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
  * Els **camps de la capçalera de la resposta**. Conjunt de línies opcionals que aporten informació addicional sobre la resposta i/o el servidor.
  * El **cos de la resposta** que conté el recurs (objecte) sol·licitat.

![[Pasted image 20250729125350.png]]

-----

## Capçaleres HTTP

Les **capçaleres HTTP** són els paràmetres que s'envien en una petició o resposta HTTP al client o al servidor per proporcionar informació essencial sobre la transacció en curs. Aquestes capçaleres proporcionen informació mitjançant la sintaxi '**Capçalera: Valor**' i són enviades automàticament pel navegador o el servidor Web. $\\rightarrow$ [Capçaleres HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Headers)

-----

### Tipus MIME

El protocol HTTP va ser dissenyat per transportar per xarxa fitxers en format ASCII, formats per text pla. Amb el pas del temps, va sorgir la necessitat d'incloure diferents tipus de fitxers no ASCII en les aplicacions per Internet (imatges, vídeos, sons, etc.) i, com a conseqüència d'això, va ser necessari buscar una solució: calia transformar aquests formats a tipus ASCII (o altres jocs de caràcters compatibles) per a la seva correcta recepció al navegador web.

Aquest problema ja havia sorgit en les aplicacions de correu electrònic, quan es va necessitar enviar per MAIL fitxers no formats per text pla, i per tant, no compatibles amb els jocs de caràcters permesos.

Per solucionar aquest problema es van crear els **tipus MIME (Multipurpose Internet Mail Extensions)**, especificacions per donar format a missatges no-ASCII, de manera que poguessin ser enviats per Internet i interpretats correctament pels programes de correu locals.

Els **tipus de mitjans d'Internet**, prèviament coneguts com a "tipus de mitjans" o "tipus de contingut", és un estàndard dissenyat per indicar el tipus d'informació que presenta un arxiu o un conjunt de dades. A Internet, aquest identificador pot ser útil per conèixer el tipus d'un arxiu abans de descarregar-lo i tenir accés a ell. És una bona pràctica proveir informació de tipus de mitjans sempre que sigui possible, com en el cas dels elements que compten amb atributs com *type*, *enctype*, *formenctype* i *accept*.

![[Pasted image 20250729125529.png]]

Tot identificador de tipus de mitjà d'Internet ha d'ajustar-se al següent format:
`tipus/subtipus[; paràmetre=valor]`

Així doncs, el "tipus" i el "subtipus" han d'estar presents en qualsevol tipus de mitjà d'Internet. A la llista següent hi ha alguns exemples que contenen cadascuna de les parts delineades anteriorment:

  * `text/html`
  * `image/jpeg`
  * `audio/mpeg`
  * `application/json`

-----

## HTTPS

El **Protocol segur de transferència d'hipertext (en anglès, Hypertext Transfer Protocol Secure o HTTPS)** és un protocol d'aplicació basat en el protocol HTTP, destinat a la transferència segura de dades d'hipertext, és a dir, és la versió segura d'HTTP.

La web és insegura per naturalesa. Quan es van dissenyar els protocols en què està basada (**TCP/IP**) no es van tenir en compte molts dels problemes que té la Internet moderna. I el protocol HTTP, per transferir pàgines web, no va afegir res al respecte tampoc fins molt després, amb la introducció del protocol HTTPS (la "s" és de "Segur") allà per 1994 per l'empresa Netscape. El protocol HTTPS original utilitzava **SSL (Secure Sockets Layer)** com a protocol segur d'intercanvi de claus i xifrat, però en l'actualitat està obsolet i s'empra **TLS (Transport Layer Security, que va per la seva versió 1.3)**. L'estàndard d'HTTP sobre TLS, en realitat, no es va configurar fins al maig de l'any 2000.

Tradicionalment, els navegadors han indicat als seus usuaris que s'estaven connectant a un lloc segur utilitzant una icona, generalment una amb un cadenat.

Segons el navegador, l'aspecte canvia una mica, però tots mostren el proverbial "cadenat" al costat de l'adreça:

![[Pasted image 20250729125604.png]]

És a dir, l'important aquí és que fins ara els navegadors consideren HTTP com la norma, i HTTPS com l'excepció, i per això el marquen d'aquesta manera.

-----

### Funcionament de HTTPS

![[Pasted image 20250729125648.png]]

-----

## Servidors web: Apache vs Nginx

Quan anem a posar en marxa un servidor web, el primer que necessitem és utilitzar un sistema operatiu sobre el qual executarem els diferents serveis, sistema operatiu que en més del 95% de les ocasions sol ser un sistema **Linux**, així com un programari que s'encarregui de la gestió de les bases de dades, **MySQL** habitualment, i un programari per gestionar el contingut dinàmics de les webs, que sol ser **PHP**. A més d'aquest programari essencial, una altra de les parts més importants del servidor sol ser l'elecció del servidor web, i aquí és on entren els dubtes.

Quan busquem muntar una web podem triar una gran quantitat de servidors web diferents, des d'**Apache** i **Nginx**, els més coneguts i utilitzats amb més d'un 85% d'ús entre tots dos, fins a altres servidors menys coneguts com **Microsoft IIS** (si usem un servidor Windows), **LiteSpeed, Node.js**, etc.

Els dos servidors més utilitzats per muntar pàgines web avui dia són Apache i Nginx, no obstant això, és impossible dir que un és millor que l'altre ja que cadascun d'ells té les seves pròpies fortaleses i debilitats i pot millorar millor sota certes circumstàncies o simplement ser més senzill d'utilitzar.

**Nginx** està orientat a millorar el rendiment, suportant majors càrregues de trànsit i usuaris que Apache (**Problema C10K**), a més d'oferir altres funcionalitats com fer de *proxy*. En els seus orígens era especialment eficient oferint contingut estàtic.

![[Pasted image 20250729125701.png]]

Després de ser llançat, Nginx va ser usat principalment per servir arxius estàtics i com un balancejador de càrrega o *proxy* invers davant d'instal·lacions Apache.

Exemples de serveis de desplegament de pàgines estàtiques:

  * Netlify
  * Surge
  * GitHub Pages
  * GitLab Pages
  * Firebase
  * Vercel
  * Neocities

Mentre evolucionava la xarxa, i la necessitat d'esprémer fins a l'última gota de la velocitat i eficiència d'ús de *hardware* amb aquest, més llocs van començar a reemplaçar Apache amb Nginx per complet, gràcies a un programari molt més madur.

![[Pasted image 20250729125715.png]]

-----

### Raons per usar Nginx

  * **És lleuger**
      * Nginx redueix el consum de RAM.
  * **És multiplataforma i fàcil d'instal·lar**
      * La majoria de les grans distribucions de GNU/Linux tenen Nginx als seus repositoris.
  * **Es pot usar juntament amb Apache\!**
      * Sí, tal com ho llegeixes, algunes empreses només usen Nginx per servir contingut estàtic i Apache per al contingut dinàmic.
  * **Memòria cau**
      * Pots usar Nginx com a memòria cau, amb una mica de configuració, permetent millorar l'eficiència de la teva aplicació sense tocar la programació de la mateixa.
  * **Balancejador de càrrega**
      * Aquest servidor web pot funcionar com a balancejador de càrrega, distribuint el trànsit entre diversos servidors, permetent major escalabilitat.
  * **Suport comunitari i professional**
      * Nginx, Inc està darrere del desenvolupament de Nginx, a més de la comunitat en general, permetent tenir un suport tant professional com comunitari.
  * **Compatibilitat amb les aplicacions web més populars**
      * Nginx és compatible amb una gran quantitat de CMS existents al mercat, i hi ha molts tutorials i documentació per instal·lar-los sota Nginx, com per exemple: Wordpress, Joomla, Drupal, phpBB i més\!