### Servei DNS (_Domain Name System_)

#### Introducció

El sistema de noms de domini **DNS** (_Domain Name System_) proporciona un mecanisme eficaç per dur a terme la resolució de noms de domini a adreces IP. Com a usuaris (humans) ens és més fàcil dirigir-nos a un nom de domini (d'amfitrió, de web, de servidor de correu, etc.) utilitzant un text identificatiu (per exemple, `www.gva.es`) que a l'adreça IP pertinent (per exemple, `193.144.127.85`). El servei DNS no només permet fer la resolució de noms de domini a adreces IP, sinó també la resolució inversa. És a dir, a partir d'una IP esbrinar el nom de domini.

El servei DNS proporciona independència del nom de domini respecte a la IP. Així un domini pot canviar d'IP de forma transparent per als usuaris del domini. Fins i tot és usual que un domini s'identifiqui amb més d'una IP com a mesura de redundància contra la caiguda del sistema o com a balanç de càrregues. Altres serveis proporcionats pel DNS són la identificació dels servidors de correu d'un domini, de cadascun dels _hosts_ que pertanyen a la xarxa, servidors d'impressió, etc.

---

### Sistemes de noms plans i jeràrquics

El problema de la identificació d'equips es produeix des del principi de l'existència de les xarxes d'ordinadors i no és una cosa específica de TCP/IP. Feia falta un **llenguatge humà** per realitzar aquesta identificació.

En els inicis de les xarxes, quan ARPANET (la xarxa predecessora d'Internet), els noms dels equips se centralitzaven en un arxiu anomenat `host.txt` (`/etc/hosts` en Linux), que incloïa el nom de l'equip i la seva IP. Això és el que es coneix com un **sistema de noms pla**. Pot ser adequat per a xarxes petites, però no és escalable ni pràctic en xarxes grans i molt menys a Internet.

Exemple de fitxer de noms pla:

```
127.0.0.1       localhost
192.168.1.1     servidor1
192.168.1.2     pc-usuari
```

---

### Elements del sistema de noms de domini

L'**espai de noms de domini** està format pels noms vàlids utilitzats per identificar serveis o màquines en una xarxa. Es pot representar mitjançant una **estructura jeràrquica de topologia arbòria**, és a dir, tots els noms formen un arbre invertit on cada node se separa dels altres nodes per un punt `.`.

![[Pasted image 20250801095318.png]]

---

#### Noms de domini

Els noms de domini poden estar formats per una o més cadenes de caràcters separades per punts i no es distingeix entre majúscules i minúscules. Per exemple, `www.deaw.es.` és el mateix que `WWW.deaw.ES.`.

Els noms de domini s'expressen com a seqüències d'**etiquetes (_labels_)**.

![[Pasted image 20250801095341.png]]

---

#### Dominis arrel

En teoria, tots els dominis han de acabar amb un punt (`.`). És així perquè l'**arbre de noms de domini (espai de noms de domini)** comença amb el domini `.` que es coneix com a **domini arrel (_root_)**. En realitat és un element nul de 0 caràcters que es representa amb un punt (`.`).

Un domini es llegeix de dreta a esquerra, començant pel punt `.`, encara que en la pràctica ho fem d'esquerra a dreta. El punt inicial, generalment s'omet ja que els programes l'afegeixen per defecte i és merament formal, però en ocasions, serà necessari que indiquem el nom de domini complet incloent el **domini arrel**, és el que es coneix com a noms de domini complets (_Fully Qualified Domain Names, FQDN_).

---

#### Dominis i subdominis

Com a conseqüència de l'organització jeràrquica de l'espai de noms de dominis, podem utilitzar els termes domini i subdomini. Per exemple, `deaw.es.` és un subdomini del domini `es.` i `www.deaw.es.` és un subdomini del domini `deaw.es.`.

Els dominis o subdominis que pengen del domini arrel `.` es coneixen com a dominis de primer nivell o dominis de nivell superior (_Top Level Domains, TLD_), els que pengen dels dominis TLD es denominen dominis de segon nivell i així successivament.

---

#### Zones

Una **zona** és una porció de l'espai de nom de domini en el DNS la responsabilitat administrativa de la qual recau sobre un únic responsable.

Els servidors que gestionen la zona tenen informació completa sobre ella i es diu que són autoritzats per a aquesta zona.

Les **zones** s'emmagatzemen en **arxius de text** o en **bases de dades**, segons el tipus de programari que s'utilitzi per muntar el **servidor DNS** i de com es configuri.

Prenguem com a exemple el domini `deaw.es.` i vegem part del seu arxiu de zona:

```
...
deaw.es.         IN NS      ns1.deaw.es.
ns1.deaw.es.     IN A       192.168.1.20
natos.deaw.es. IN   A       192.168.1.21
waor.deaw.es.    IN A       192.168.1.22
www.deaw.es.     IN CNAME   natos.deaw.es.
ftp.deaw.es.     IN CNAME   waor.deaw.es.
...
```

A cadascuna de les línies del fitxer se les coneix com a **registres de recurs (RR: _Resource Records_)** i defineixen els tipus de dades en el _Domain Name System_ (DNS). S'utilitzen per emmagatzemar dades sobre noms de domini i adreces IP. Una base de dades o fitxer de zona està formada per una sèrie de registres de recursos. Cada registre de recurs dóna informació pertinent sobre un objecte determinat. Per exemple, els **registres de tipus (A)** associen un nom d'amfitrió amb una adreça IP, i els **registres de punter de cerca inversa (PTR)** associen una adreça IP amb un nom d'amfitrió i un **registre (NS)** defineix un servidor DNS per a la zona. El servidor DNS utilitza aquests registres de recurs per resoldre les consultes dels _hosts_ de la seva zona.

Quan un **servidor DNS és autoritzat** per a una zona, és el responsable dels noms de domini per a aquesta zona. En el nostre exemple, `ns1.deaw.es` és el servidor autoritzat per a la zona `deaw.es.` i en ell es defineixen els noms que pengen de `deaw.es` com per exemple, `www.deaw.es`, `ftp.deaw.es`, `natos.deaw.es`, etc.

![[Pasted image 20250801095401.png]]

L'organització que administra el servidor DNS i per tant la zona, pot delegar o no algun dels seus subdominis. Suposem que de `deaw.es.` pengen els subdominis `teoria.deaw.es.` i `practicas.deaw.es.` i es decideix delegar només el subdomini `practicas.deaw.es.`. Això implica que existirà un altre servidor DNS autoritzat per al domini `practicas.deaw.es.`, que emmagatzemarà el fitxer de zona per a aquest domini.

Una zona no és el mateix que un domini. **Un domini és un subarbre de l'espai de noms de domini** i les dades associades als noms d'un **domini** poden estar emmagatzemades en una o diverses **zones**, distribuïdes en un o diversos **servidors DNS**.

> Info
> 
> Bàsicament una zona és una porció d'un domini.

Un **servidor DNS** pot ser autoritzat sobre diverses **zones**, per exemple, el mateix **servidor DNS** pot ser autoritzat per a la zona `deaw.es.` i per a la zona `seguridadinformatica.es.`.

![[Pasted image 20250801095453.png]]

---

### Tipus de RR (_Resource Record_)

En aquesta subsecció veurem quins són els registres de recursos o RR més utilitzats. Abans hem d'aclarir alguns conceptes:

---

#### $TTL (_Time To Live_)

El **TTL** o temps de vida determina, en segons, durant quant de temps són vàlids els RR. Poden indicar-se en setmanes (`$TTL 1W`), dies (`$TTL 7D`), hores (`$TTL 168H`) o minuts (`10080M`).

En altres paraules, el TTL indica quant de temps trigaran a aplicar-se els canvis que li fem a un RR des que els fem. En l'exemple del paràgraf anterior, els servidors DNS comprovaran cada setmana si s'ha produït algun canvi en aquests RR. Ha de declarar-se a l'inici de l'arxiu de zona.

---

#### $ORIGIN

La directiva **$ORIGIN** defineix el nom del domini que serà afegit al final de qualsevol nom que no acabi en punt (noms relatius o no qualificats) en els RR, per així transformar-los en noms FQDN (_fully qualified domain name_). Si un nom acaba en punt, es considera un nom FQDN i no s'utilitzaria $ORIGIN.

La seva sintaxi o forma d'escriure'l serà:

```
$ORIGIN nom-domini
```

Per exemple:

```
$ORIGIN deaw.es.
;A partir d'aquí s'afegeix deaw.es. a tots els noms relatius...
```

---

#### Format general dels RR

El format amb el qual s'introdueixen els RR en els arxius de zona és del següent estil:

```
Nom de domini [TTL] Classe Tipus Tipus-Dada
```

Així per exemple, un RR quedaria tal que així:

```
profesor.deaw.es 7200 IN A 192.168.10.254
```

---

#### Tipus de registres

Aclarits els punts anteriors, ara sí que veurem els principals tipus de registres:

- Registre SOA (Start Of Authority): Especifica informació autoritària sobre una zona DNS, incloent el servidor de nom primari, l'email de l'administrador, el número de sèrie o versió de la zona, i diversos temporitzadors.
    
    Exemple:
    
    ```
    deaw.es.   IN   SOA   ns1.deaw.es.   super.deaw.es. (
                20190425001 ; serial
                604800  ; refresh (7 dies)
                86400   ; retry (1 dia)
                2419200 ; expire (28 dies)
                604800 )    ; TTL negatiu (7 dies)
    ...
    ```
    
- **Registre NS (_Name Server_)**: Quan es delega l'administració de subdominis en altres servidors, aquest registre indica quins són aquests servidors autoritzats.
    
    ```
    ...
    deaw.es.    IN  NS  ns1.deaw.es.    ;Servidor DNS mestre
    deaw.es.    IN  NS  ns2.deaw.es.    ;Servidor DNS esclau
    deaw.es.    IN  NS  dns.deaw.net.   ;Servidor DNS esclau
    ns1.deaw.es.    IN  A   192.168.10.20
    ns2.deaw.es.    IN  A   192.168.10.21
    ;DELEGACIÓ
    practicas.deaw.es.  IN  NS  ns1.practicas.deaw.es.
    redes.deaw.es.  IN  NS  dns.deaw.net.
    ```
    
- El **registre A (_Address_)**, també conegut com a registre d'adreça, estableix una correspondència entre un nom de domini completament qualificat (FQDN) i una adreça IP versió 4.
    
    ```
    ...
    ns1.deaw.es.        IN  A   192.168.10.20
    ns2.deaw.es.        IN  A   192.168.10.21
    natos.deaw.es.  IN  A   192.168.10.22
    ...
    ```
    
- El **registre CNAME (_Canonical Name_)** permet crear àlies per a noms de domini especificats en registres A.
    
    ```
    ...
    natos.deaw.es.  IN  A   192.168.1.22
    www.deaw.es.        IN  CNAME   natos.deaw.es.
    ftp.deaw.es.        IN  CNAME   natos.deaw.es.
    ...
    ```
    
    Un registre CNAME també pot apuntar a un nom d'un altre domini.
    
    ```
    ...
    www.deaw.es.    IN  CNAME   www.deaw.com.
    ...
    ```
    
- El **registre MX (_Mail Exchange_)** permet definir els servidors encarregats del lliurament de correu en el domini i la prioritat entre ells. La seva sintaxi és la següent:
    
    ```
    ...
    deaw.es.    IN  MX  10  mail1.deaw.es.
    deaw.es.    IN  MX  20  mail2.deaw.es.
    mail1.deaw.es.  IN  A   192.168.1.100
    mail2.deaw.es.  IN  A   192.168.1.101
    ...
    ```
    
- El registre PTR (Pointer Record) estableix una correspondència entre adreces IPv4 i IPv6 i noms de domini. S'utilitzen en les zones de resolució inversa.
    
    En el cas d'un bloc IPv4 de prefix /24, per exemple el 192.168.1.0/24, els registres PTR serien els següents:
    
    ```
    ...
    20.1.168.192.in-addr.arpa.    IN    PTR    ns1.deaw.es.
    21.1.168.192.in-addr.arpa.    IN    PTR    ns2.deaw.es.
    22.1.168.192.in-addr.arpa.    IN    PTR    natos.deaw.es.
    ...
    ```
    
    o el que és el mateix:
    
    ```
    ...
    20    IN    PTR    ns1.deaw.es.
    21    IN    PTR    ns2.deaw.es.
    22    IN    PTR    natos.deaw.es.
    ...
    ```
    
- El **registre TXT (_plaint text_)** permet associar informació addicional a un domini mitjançant múltiples cadenes de text, amb una longitud màxima de 255 caràcters cadascuna d'elles. Per exemple, utilitzat per emmagatzemar claus de xifrat.
    
    ```
    @   IN  TXT     "Servidor mestre de Serveis en Xarxa"
    @   IN  TXT     "Servidor mestre de Serveis en Xarxa"
    ```
    

---

### Tipus de servidors DNS

---

#### Servidor mestre o primari

Un **servidor mestre o primari**, defineix una o diverses zones de les quals és autoritzat. Els seus arxius de zona són de lectura i escriptura i és en ells on l'administrador del servidor afegeix, modifica o elimina noms de domini.

- Si un client DNS o un altre servidor DNS li pregunta per algun nom de domini **per al qual és autoritzat**, consulta amb els fitxers de zona i respon a la pregunta.
    
- Si un client DNS o un altre servidor DNS li pregunta per algun nom de domini **per al qual no és autoritzat**, haurà de preguntar a altres servidors DNS o respondre que no coneix la resposta.
    

---

#### Servidor esclau o secundari

Un **servidor esclau o secundari** defineix una o diverses zones per a les quals és autoritzat. La diferència respecte a un servidor mestre és que els fitxers de zona els obté d'un altre servidor autoritzat per a la zona, normalment, d'un servidor mestre mitjançant un procediment anomenat **transferència de zona**. Els fitxers de zona dels servidors esclaus són de només lectura i per tant, l'administrador no ha d'editar-los. La modificació dels arxius de zona ha de realitzar-la el servidor mestre que transfereix la zona.

El funcionament de com responen als clients DNS o a altres servidors DNS és similar al d'un servidor mestre. Un servidor pot ser mestre per a una o diverses zones i al mateix temps ser esclau per a altres.

Poden existir diversos servidors esclaus per a una mateixa zona. Les raons per a això solen ser:

- Reduir i repartir la càrrega entre diversos servidors DNS.
    
- Afavorir la tolerància a fallades.
    
- Oferir major rapidesa.
    

L'ideal és que els servidors DNS per a una mateixa zona estiguin ubicats en xarxes i localitzacions diferents per evitar que, si ocorre algun problema no els afecti simultàniament i deixi sense servei de resolució als noms d'aquesta zona.

![[Pasted image 20250801095645.png]]

---

#### Servidor cau

Els servidors DNS es configuren com a **servidors cau** per millorar els temps de resposta de les consultes, reduir la càrrega dels equips i disminuir el trànsit de xarxa.

Quan un servidor DNS rep una pregunta sobre un domini per al qual no és autoritzat, és a dir, d'un nom del qual no té informació, pot preguntar, si així està configurat, a altres servidors per obtenir la resposta. Si el servidor actua com a cau, guarda durant un temps (**TTL**: _Time To Live_) les respostes a les últimes preguntes que ha realitzat a altres servidors DNS. Cada vegada que un client DNS o un altre servidor DNS li formula una pregunta, comprova si té la resposta en la seva memòria cau, si la té, no haurà de preguntar a un altre servidor DNS per la pregunta.

Un servidor DNS és **només cau (_cache only server_)** quan:

- No té autoritat sobre cap zona.
    
- Pregunta a altres servidors DNS per resoldre les preguntes dels clients DNS i les guarda en la seva memòria cau.
    

En el següent gràfic s'explica com dos clients DNS fan preguntes a un mateix servidor DNS que és autoritzat per a algunes zones i a més actua com a cau.

![[Pasted image 20250801095658.png]]

---

#### Servidor _forwarder_ (reenviador)

Quan a un servidor DNS se li fa una pregunta sobre un nom de domini del qual no disposa d'informació (no és autoritzat), aquest pot preguntar a altres servidors DNS. Simplificant, existeixen dues formes de processar les consultes:

- El servidor DNS processa la consulta preguntant a diversos servidors DNS i començant pels servidors DNS arrel. **Consulta iterativa**.

![[Pasted image 20250801095712.png]]

- El servidor DNS reenvia la consulta a un altre servidor DNS, denominat **reenviador (_forwarder_)**, perquè s'encarregui de resoldre-la. **Consulta recursiva**.

![[Pasted image 20250801095722.png]]


Vist l'anterior, un reenviador (_forwarder_) és un servidor DNS que altres servidors DNS designen per reenviaments de consultes. Són utilitzats per minimitzar les consultes i el trànsit de peticions DNS des d'una xarxa cap a Internet. A més permeten als equips locals utilitzar el seu cau DNS per minimitzar els temps de resposta.

---

#### Servidor només autoritzat

Un **Servidor només autoritzat (_authoritative only_)** és aquell que és autoritzat per a una o diverses zones com a servidor mestre i/o esclau i no respon a preguntes que no siguin relatives a les seves zones. És a dir, no té activada la recursivitat, no és reenviador i no actua com a cau.

---

#### Servidors arrel

A Internet existeixen un conjunt de servidors DNS autoritzats per al domini arrel `.`, coneguts com a **servidors arrel (_root servers_)**. Contenen el fitxer de la zona `.` que conté informació sobre els servidors DNS autoritzats per a cadascun dels dominis TLD.

Els servidors arrel són una part fonamental d'Internet, són el primer pas en la traducció (resolució) dels noms d'amfitrió en adreces IP, que s'utilitzen en la comunicació entre els _hosts_ d'Internet. Són clau en el procés de resolució de noms de domini a Internet, i han de ser coneguts per tots els servidors DNS que responguin a preguntes sobre noms per als quals no són autoritzats.

Existeixen 13 servidors arrel a tot Internet i cadascun d'ells té múltiples còpies distribuïdes per tot el món, és a dir, que físicament no només són 13 servidors. Cada conjunt de còpies d'un dels 13 servidors s'identifica per una mateixa IP. Quan un client realitza una pregunta a una IP d'un servidor arrel, els encaminadors d'Internet encaminen la pregunta cap a la còpia més pròxima mitjançant un procediment anomenat **anycasting**.

Els noms dels servidors arrel són de la forma `lletra.root-servers.net`, on lletra va des de la A a la M.

Llistat de Servidors arrel:

![[Pasted image 20250801095758.png]]

---

### Tipus de consultes: recursives i iteratives

---

#### Consultes recursives

Una **consulta recursiva** és aquella en la qual el servidor DNS dóna una resposta completa o exacta. Poden donar-se tres tipus de resposta:

- **Positives**: es retorna informació sobre el domini consultat.
    
- **Negatives**: no es pot resoldre el nom de domini.
    
- **Error**: a causa d'una fallada en la xarxa.
    

---

#### Consultes iteratives

Una **consulta iterativa** és aquella en la qual el servidor DNS proporciona una resposta parcial. Existeixen quatre possibles respostes:

- **Positives**: es retorna informació sobre el domini consultat.
    
- **Negatives**: no es pot resoldre el nom de domini.
    
- **Referència**: el servidor DNS indica a altres servidors als quals se li pot consultar per resoldre la pregunta.
    
- **Error**: a causa d'una fallada en la xarxa.
    

##### Exemples

Completant la informació de la imatge del primer exemple de l'apartat del reenviador forwarder:

![[Pasted image 20250801095933.png]]

Completant la informació de la imatge del segón exemple de l'apartat del reenviador forwarder:

![[Pasted image 20250801095954.png]]

---

### Resolució inversa

La **resolució inversa** consisteix a obtenir informació d'un nom de domini preguntant per l'adreça IP en comptes de preguntar pel nom de domini com hem explicat en apartats anteriors.

---

#### Mapeig d'adreces i el domini _arpa_

El funcionament de la resolució d'adreces IP és igual al de la resolució de noms de domini. Les adreces IP es tracten com a noms que pengen del domini `in-addr.arpa` per a les adreces IPv4, i del domini `ip6.arpa` per a les adreces IPv6.

![[Pasted image 20250801100023.png]]

Quan usem una adreça IP, per exemple `192.168.1.21`, per realitzar una pregunta DNS inversa, en realitat estem preguntant pel nom de domini `21.1.168.192.in-addr.arpa`. L'estructura jeràrquica de l'adreça IP, tractada com a nom de domini, és de dreta a esquerra, començant pel domini `in-addr.arpa`.

`.arpa` (_Address and Routing Parameter Area_) és un domini de nivell superior genèric utilitzat només per a la infraestructura d'Internet. Els subdominis de .arpa o dominis de segon nivell "in-addr.arpa" i "ip6.arpa" són usats pels servidors DNS inversos per a l'obtenció d'adreces IPv4 i IPv6 respectivament.

Quan mapegem una adreça IP estem associant l'adreça IP al nom en el domini `.arpa`. Per exemple l'adreça `192.168.1.21` és mapejada al nom `21.1.168.192.in-addr.arpa`.

---

#### Zones de resolució inversa

Els servidors DNS emmagatzemen **zones de resolució inversa** amb registres de recursos (RR) que associïn noms de domini amb adreces IP. Les zones de resolució inversa poden ser mestres o primàries i esclaves o secundàries.

Les zones de resolució directa i inversa són independents i és responsabilitat dels administradors dels servidors DNS que aquestes zones continguin informació coherent i que no existeixin discrepàncies.

No és obligatori que l'entitat que administra una zona de resolució directa d'un domini hagi d'administrar la zona de resolució inversa que es correspongui amb les adreces IPs associades a aquest domini.

**Arxiu de zona de resolució directa del domini `deaw.es.`**

```
...
deaw.es.            IN  NS      ns1.deaw.es.
ns1.deaw.es.        IN  A       192.168.1.20
natos.deaw.es.  IN  A       192.168.1.21
waor.deaw.es.       IN  A       192.168.1.22
altea.deaw.es.      IN  A       192.168.1.23
www.deaw.es.        IN  CNAME   natos.deaw.es.
ftp.deaw.es.        IN  CNAME   waor.deaw.es.
...
```

**Arxiu de zona de resolució inversa `1.168.192.in-addr.arpa`** que permet resoldre consultes inverses sobre adreces IP de la xarxa `192.168.1.0/24`

```
...
1.168.192.in-addr.arpa.     IN  NS  ns1.deaw.es.
20.1.168.192.in-addr.arpa.  IN  PTR ns1.deaw.es.
21.1.168.192.in-addr.arpa.  IN  PTR natos.deaw.es.
22.1.168.192.in-addr.arpa.  IN  PTR waor.deaw.es.
123.1.168.192.in-addr.arpa. IN  PTR altea.deaw.es.
...
```

---

#### Procés de resolució

El procés de resolució inversa és similar al de resolució directa. Les adreces IP es tracten com a noms de domini. Per tant, existeixen consultes recursives, iteratives, cau, TTL...

Per exemple, si un client DNS realitza una consulta recursiva de la IP `192.168.1.21` a un servidor DNS, aquest, si no ho té en cau, iniciarà una sèrie de consultes iteratives als servidors DNS arrel, als servidors autoritzats per al domini `192.in-addr.arpa` i així successivament.

---

### Eines

---

#### Nslookup

És un programa per consultar servidors DNS. S'utilitza per saber si un servidor DNS resol correctament els noms DNS i les adreces IP, per solucionar problemes freqüents dels servidors DNS o, per diagnosticar problemes ocasionals de configuració en els servidors DNS.

Amb `nslookup` podem obtenir l'adreça IP associada a un nom DNS i viceversa, a més, podem preguntar als servidors de noms informació relativa als registres de recursos (RR) de la/les zona/es de les quals són autoritzats.

`nslookup` s'usa de dues maneres: interactiva i no interactiva. El mode interactiu permet a l'usuari consultar els servidors DNS per obtenir informació sobre diversos _hosts_ i dominis o per llistar els _hosts_ d'un domini. El mode no interactiu s'usa per presentar només el nom i la informació sol·licitada per a un _host_ o nom DNS.

Aquesta comanda funciona tant en sistemes operatius UNIX/Linux com en Windows. En el seu moment es va tractar a `nslookup` com una aplicació "_deprecated_" o obsoleta, però a dia d'avui sembla que ha tornat a considerar-se apta per al seu ús normal.

![[Pasted image 20250801100151.png]]

![[Pasted image 20250801100232.png]]


---

#### Dig

És un programa utilitzat per preguntar als servidors DNS.

Eina utilitzada per solucionar problemes de DNS gràcies a la seva flexibilitat, facilitat d'ús i claredat en la presentació de la informació. Normalment, `dig` s'usa passant-li arguments des de la línia de comandos (CLI), però també té un mode d'operar per lots, llegint les consultes des d'un arxiu.

Aquesta comanda funciona tant en sistemes operatius UNIX/Linux com en Windows.

![[Pasted image 20250801100349.png]]

![[Pasted image 20250801100413.png]]

---

#### Host

`Host` és una eina CLI senzilla i fàcil d'usar per realitzar consultes DNS, que tradueixen noms de domini a adreces IP i viceversa. També s'utilitza per consultar els registres DNS de les zones que emmagatzemen els servidors DNS, provar i validar el servidor DNS i la connectivitat a Internet, registres de correu no desitjat i llistes negres, diagnòstic de problemes en el servidor DNS...

---

#### Whois

Encara que no és una eina de diagnòstic DNS sí que ens ofereix informació sobre el registre del domini.

`Whois` és un protocol que permet realitzar consultes a bases de dades que contenen informació; de l'usuari, empresa o organització que registra un nom de domini i/o una adreça IP a Internet. El protocol `whois` s'encapsula en TCP i només especifica l'intercanvi de peticions i respostes, no el format de dades a intercanviar. Per això, els resultats de les consultes `whois` poden variar depenent de la base de dades `whois` a la qual es pregunti.