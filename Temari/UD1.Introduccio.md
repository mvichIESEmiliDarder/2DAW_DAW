
---

## Introducció

En aquest mòdul simularem escenaris reals on gairebé no treballarem en local, al nostre propi ordinador. Simularem, mitjançant una **màquina virtual** (que és on realment treballarem), que tots els nostres desplegaments ocorren en una màquina remota, tal com passa en la realitat.

De fet, se simularà un escenari on tindrem contractat un **VPS (Virtual Private Server)** i ens haurem de connectar de forma remota per poder-hi treballar. Un escenari molt comú al món real.

---

## Què és un VPS?

Un **servidor** és un ordinador on el teu proveïdor d'allotjament web emmagatzema els fitxers i les bases de dades necessaris per al teu lloc web. Cada vegada que un visitant en línia vol accedir al teu lloc web, el seu navegador envia una sol·licitud al teu servidor i transfereix els fitxers necessaris a través d'Internet. L'**allotjament VPS** et proporciona un servidor al núvol que simula un servidor físic; tanmateix, en realitat, la màquina es comparteix entre diversos usuaris.

En utilitzar la tecnologia de virtualització, el teu proveïdor d'allotjament web instal·la una capa virtual sobre el sistema operatiu del servidor. Aquesta capa divideix el servidor en particions i permet a cada usuari instal·lar el seu propi sistema operatiu i programari.

Per tant, un **servidor privat virtual (VPS)** és tant virtual com privat perquè tens control absolut. Està separat d'altres usuaris del servidor a nivell del sistema operatiu. De fet, la tecnologia VPS és similar a la creació de particions al teu ordinador quan vols executar més d'un sistema operatiu (per exemple, Windows i Linux) sense haver de reiniciar.

![[Pasted image 20250729124908.png]]
Un VPS et permet configurar el teu lloc web dins d'un contenidor segur amb **recursos garantits** (memòria, espai en disc, nuclis de CPU, etc.) que no has de compartir amb altres usuaris. Amb l'allotjament VPS, tens el mateix accés de nivell d'arrel que si lloguessis un servidor dedicat, però a un cost molt més baix.

El VPS és una solució més segura i estable que l'allotjament compartit, amb el qual no obtens espai de servidor dedicat. No obstant això, és de menor escala i més barat que llogar un servidor complet.

L'allotjament VPS generalment és triat pels propietaris de llocs web que tenen un trànsit de nivell mitjà que excedeix els límits dels plans d'allotjament compartit, però que encara no necessiten els recursos d'un servidor dedicat.

---

## Connexió mitjançant SSH

Encara que la nostra màquina virtual estigui al nostre ordinador, ja hem dit que estem simulant un VPS remot. Per connectar-nos a una màquina de forma remota i segura, l'opció més recomanable és **SSH**.

![[Pasted image 20250729124923.png]]
**SSH o Secure Shell** és un protocol de xarxa criptogràfic per operar serveis de xarxa de forma segura a través d'una xarxa no protegida. Les aplicacions típiques inclouen línia de comandes remota, inici de sessió i execució de comandes remota, però qualsevol servei de xarxa pot protegir-se amb SSH.

SSH proporciona un canal segur a través d'una xarxa no segura mitjançant l'ús d'una arquitectura **client-servidor**, connectant una aplicació client SSH amb un servidor SSH. El port TCP estàndard per a SSH és el **22** i s'utilitza generalment per accedir a sistemes operatius similars a Unix, però també es pot utilitzar a Microsoft Windows.

Proporciona un mecanisme per autenticar un usuari remot, transferir entrades des del client a l'amfitrió i retransmetre la sortida de tornada al client.

SSH té moltes aplicacions diferents:

* Gestió de servidors als quals no es pot accedir localment
* Transferència segura de fitxers
* Creació de còpies de seguretat
* Connexió entre dos ordinadors amb encriptació d'extrem a extrem
* Manteniment remot des d'altres ordinadors

---

## Autenticació

Els dos mètodes d'autenticació d'usuari SSH més comuns que s'utilitzen són les **contrasenyes (xifrat simètric)** i les **claus SSH (xifrat asimètric o de clau pública)**. Els clients envien contrasenyes xifrades al servidor de forma segura. No obstant això, les contrasenyes són un mètode d'autenticació arriscat perquè la seva solidesa depèn que l'usuari sàpiga què fa que una contrasenya sigui segura.

Els **parells de claus pública-privada SSH** xifrades asimètricament són una millor opció. Una vegada que el client desxifra el missatge, el servidor li atorga accés al sistema.

És a dir, SSH opta pel **xifrat híbrid**, on s'utilitza el xifrat asimètric per intercanviar unes claus que seran les que s'utilitzaran posteriorment en l'intercanvi d'informació.

---

### Xifrats simètrics o de clau privada

Aquest tipus de xifrat utilitza la mateixa clau per xifrar i per desxifrar la informació. Per aquest motiu, la clau ha de ser secreta i només coneguda per l'emissor i el receptor del missatge.

![[Pasted image 20250729124942.png]]

**Avantatges**

* Molt ràpids $\rightarrow$ xifrar i desxifrar un missatge cada vegada requereix un cert temps, que si l'algoritme és complex, pot ser elevat.

**Inconvenients**

* Si algú no autoritzat aconsegueix la clau, podrà espiar la comunicació sense problemes.
* Com fem perquè emissor i receptor coneguin la clau en un primer moment? $\rightarrow$ no es pot transmetre pel canal insegur $\rightarrow$ cal transmetre-la per un altre canal segur. Exemples: PIN de la targeta del banc o fitxer comprimit amb contrasenya.

---

### Xifrats asimètrics o de clau pública

En aquest tipus de xifrats cada usuari utilitza un parell de claus: una **clau pública** i una **clau privada**. Un missatge xifrat amb la clau pública només es pot desxifrar amb la seva corresponent clau privada i viceversa.

![[Pasted image 20250729125002.png]]

* La **clau pública** és accessible a qualsevol persona que vulgui consultar-la, no cal que sigui transmesa per un canal segur com en el cas anterior.
* La **clau privada** només la ha de conèixer el seu amo.

**Funcionament:**

1.  L'emissor xifra un missatge amb la clau pública del receptor.
2.  El receptor rep el missatge i és l'únic que podrà desxifrar-lo perquè és l'únic que posseeix la clau xifrada associada.

**Avantatges**

* No es necessita un nou canal independent i segur per transmetre la clau.

**Inconvenients**

* Són més lents que els xifrats simètrics.
* Cal protegir molt bé la clau privada i tenir-la sempre disponible per poder desxifrar els missatges (no és una contrasenya).
* Cal assegurar-se que la clau pública és de qui diu ser i no d'un impostor que s'està fent passar per ell.

---

**Nota**

Nosaltres, per connectar-nos per primera vegada per SSH i comprovar la connectivitat, utilitzarem el xifrat simètric (una contrasenya).

Després d'això, simulant un entorn real que aporti comoditat (no introduir contrasenya cada vegada que fem *login*), però també i sobretot, per seguretat, utilitzarem xifrat asimètric. Això és, un parell de claus.