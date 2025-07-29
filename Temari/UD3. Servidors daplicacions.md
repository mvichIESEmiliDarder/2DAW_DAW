## Servidors d'aplicacions

### Introducció

Un **servidor d'aplicacions** és un marc de programari mixt que permet tant la creació d'aplicacions web com un entorn de servidor per executar-les. Sovint pot ser una pila complexa de diferents elements computacionals que executen tasques específiques que necessiten funcionar com una unitat per alimentar múltiples núvols i programari i aplicacions basades en la web.

Situat entre el servidor web i el nivell de _backend_ del servidor de bases de dades, el servidor d'aplicacions és essencialment un intermediari per al servidor de bases de dades i els usuaris de les aplicacions empresarials o de consum que suporta mitjançant l'ús de diversos protocols i interfícies de programació d'aplicacions (API).

![[Pasted image 20250729133416.png]]

És habitual que s'utilitzi juntament amb un servidor web o que contingui un servidor web, de manera que tots dos poden convergir i anomenar-se **servidor d'aplicacions web**. També és prou versàtil com per ser utilitzat amb altres servidors d'aplicacions simultàniament. Els servidors d'aplicacions també poden contenir les seves pròpies interfícies gràfiques d'usuari per a la seva gestió a través de PC, però també poden ocupar-se dels seus propis recursos, així com del processament de transaccions, la missatgeria, l'agrupació de recursos i connexions, i la realització de tasques de seguretat.

---

### Servidor d'aplicacions

Les aplicacions es presenten en totes les formes, mides i casos d'ús. En un món en què depenem d'una sèrie de processos empresarials crítics, els servidors d'aplicacions són els ordinadors de gran potència que proporcionen recursos d'aplicacions als usuaris i clients web.

Els servidors d'aplicacions, com ja hem dit, se situen físicament o virtualment entre els servidors de bases de dades que emmagatzemen les dades de les aplicacions i els servidors web que es comuniquen amb els clients. Els servidors d'aplicacions i el _middleware_ afí són els sistemes operatius que suporten el desenvolupament i el lliurament d'una aplicació. Ja sigui una aplicació d'escriptori, mòbil o web, els servidors d'aplicacions tenen un paper fonamental en la connexió d'un món de dispositius.

---

### Terminologia dels servidors d'aplicacions

|Terme|Descripció|
|---|---|
|**Servidor web**|Responsable d'emmagatzemar, processar i lliurar les dades d'E/S de les pàgines web|
|**Client web**|Punt final que intenta accedir als recursos de la web o de l'aplicació|
|**HTTPS**|Protocol de comunicació segur entre el servidor web i els clients web|
|**JSON**|Llenguatge per a l'intercanvi entre els servidors web i d'aplicacions|
|**Lògica de negoci**|Regles per a l'emmagatzematge de dades i la transferència de recursos de l'aplicació|
|**Aplicació**|Un programa de programari o un lloc web unit a una base de dades|

---

### El paper del servidor d'aplicacions en l'arquitectura de serveis

Quan els usuaris de les aplicacions, ja siguin usuaris físics o els clients web, sol·liciten accés a una aplicació, el servidor d'aplicacions sol fer la feina pesada al _backend_ per emmagatzemar i processar les sol·licituds dinàmiques de les aplicacions.

---

### Per què necessitem servidors d'aplicacions?

Milers de milions de clients web fan peticions HTTP cada dia, esperant un accés instantani a l'aplicació en qüestió. Headspace durant la rutina del matí, Google Docs per a l'informe extens, Twitter durant la pausa per al cafè, no importa l'aplicació en ús, està sent consultada en un servidor d'aplicacions i retornada a través d'un servidor web.

Els servidors web s'encarreguen de servir als clients web peticions HTTP amb respostes HTTP. A diferència dels servidors d'aplicacions, el disseny del servidor web és prou lleuger per processar les sol·licituds de dades estàtiques de diverses aplicacions (o llocs web), mantenint la seguretat. Les peticions dinàmiques, sovint en forma d'aplicacions, requereixen assistència addicional.

---

### Els servidors d'aplicacions optimitzen el trànsit i afegeixen seguretat

Per aconseguir una agilitat òptima del servidor web, no serveix gestionar tant les peticions HTTP dels clients web com passar o emmagatzemar recursos de múltiples llocs web. Els servidors d'aplicacions omplen aquest buit amb un disseny d'alta potència construït per manejar les sol·licituds de contingut web dinàmic.

Els servidors d'aplicacions també proporcionen redundància de programes i una capa addicional de seguretat. Un cop desplegat entre una base de dades i un servidor web, la feina de preservar i duplicar l'arquitectura de l'aplicació a través de la xarxa és més factible. El pas addicional entre les potencials comunicacions web malicioses i les joies de la corona al servidor de base de dades afegeix una capa de seguretat addicional. Atès que els servidors d'aplicacions poden processar sol·licituds de lògica empresarial, un intent d'injecció SQL és també molt més difícil.

Les organitzacions poden protegir encara més les seves dades amb un servidor _proxy_ invers col·locat davant de les seves bases de dades. Els servidors _proxy_ i les VPN poden fer meravelles per anonimitzar i xifrar la comunicació per protegir els usuaris i les dades de l'empresa.

![[Pasted image 20250729133436.png]]

---

### Com funcionen els servidors d'aplicacions?

Posem com a exemple un servidor d'aplicacions Java.

---

>#### Què són els _servlets_?
>
Un **servlet** és un programa Java que s'executa en un servidor Web i construeix o serveix pàgines web. D'aquesta manera es poden construir pàgines dinàmiques, basades en diferents fonts variables: dades proporcionades per l'usuari, fonts d'informació variable (pàgines de notícies, per exemple), o programes que extreuen informació de bases de dades.

Comparat amb un CGI, un _servlet_ és més senzill d'utilitzar, més eficient (s'engega un fil per cada petició i no un procés sencer), més potent i portable. Amb els _servlets_ podrem, entre altres coses, processar, sincronitzar i coordinar múltiples peticions de clients, reenviar peticions a altres _servlets_ o a altres servidors o altres.

Com la majoria dels servidors d'avui en dia, els servidors d'aplicacions contenen característiques de seguretat, transaccions, serveis, _clustering_, diagnòstics i bases de dades. En el que es diferencien els servidors d'aplicacions és en la seva capacitat per processar peticions de _servlets_ (programes Java) des d'un servidor web.

En la imatge anterior, es mostra el flux general dels servidors d'aplicacions web:

1. El client obre un navegador i sol·licita accés a un lloc web
    
2. El servidor web rep la petició HTTP i respon amb la pàgina web desitjada
    
3. El servidor web gestiona les peticions de dades estàtiques, però el client vol utilitzar una eina interactiva
    
4. En tractar-se d'una petició de dades dinàmiques, el servidor web transfereix la petició a un servidor d'aplicacions
    
5. El servidor d'aplicacions rep la petició HTTP i la converteix en una petició de _servlet_
    
6. El _servlet_ arriba al servidor de la base de dades, i el servidor d'aplicacions rep una resposta del _servlet_
    
7. El servidor d'aplicacions tradueix la resposta del _servlet_ al format HTTP per a l'accés del client
    

En rebre una sol·licitud de _servlet_ d'un servidor web, el servidor d'aplicacions processa la sol·licitud i respon al servidor web mitjançant la resposta de _servlet_. Atès que els servidors d'aplicacions treballen principalment amb peticions de lògica de negoci, el servidor web tradueix la resposta del _servlet_ i passa una resposta HTTP accessible per a l'usuari.

![[Pasted image 20250729133522.png]]

|Característica|Servidor d'aplicacions|Servidor web|
|---|---|---|
|**Dissenyat per**|Serveix peticions HTTP i d'altra lògica de negoci|Serveix peticions HTTP|
|**Emmagatzema i proporciona**|Lògica de negoci|Contingut web estàtic|
|**La utilització dels recursos és**|Pesada|Lleugera|
|**Suporta**|Transaccions distribuïdes i Enterprise JavaBeans (EJB)|Servlets, Java Server Pages (JSP) i JSON|

---

### Servidors d'aplicacions a la dècada de 2020

El mercat dels servidors d'aplicacions espera créixer a una **CAGR** del 13,2%, passant de prop de 17.000 milions de dòlars el 2020 a 41.000 milions el 2026. El creixement continu no és una sorpresa, ja que la connectivitat a Internet i la dependència de les aplicacions creix.

La migració a les plataformes i serveis al núvol i l'auge dels dispositius IoT són dos impulsors clau en el mercat d'infraestructura d'aplicacions i _middleware_ modern. A això cal afegir un moviment cap a les polítiques BYOD (_Bring Your Own Device_) i una força de treball remota que depèn d'una major connectivitat i eficiència operativa.

---

### Servidors d'aplicacions: El millor amic d'un servidor web

Els servidors d'aplicacions són fonamentals per a les exigències actuals d'interconnexió. Les empreses, en última instància, estan al servei dels interessos dels clients, per la qual cosa sense una connexió escalable i estable als recursos de les aplicacions, els clients moderns fugiran sense mirar enrere.

Els servidors d'aplicacions assumeixen el paper de connector i millor amic dels servidors web. Quan els servidors web tenen una petició del client que és massa per suportar, els servidors d'aplicacions fan possible mantenir la comunicació sense problemes amb el contingut web dinàmic.

---

### Què és el desplegament d'aplicacions web?

El **desplegament** en el desenvolupament de programari i web significa passar els canvis o actualitzacions d'un entorn de funcionament a un altre. En configurar un lloc web, sempre es tindrà el lloc web en viu, que s'anomena l'**entorn en viu** o **entorn de producció**.

Si es vol tenir la capacitat de fer canvis sense afectar un lloc web en producció, es pot (i s'ha de) afegir entorns addicionals. Aquests entorns s'anomenen **entorns de desenvolupament** o **entorns de desplegament**. Els entorns de desenvolupament addicionals solen ser un entorn local, un entorn de desenvolupament i un entorn de preparació o preproducció. El nombre d'entorns que es necessiten depèn de cada cas i de la complexitat del projecte en què s'estigui treballant.

Encara que els models de desplegament poden variar, el més comú és el clàssic model de desplegament "d'esquerra a dreta" quan es treballa amb múltiples entorns de desplegament. En aquest model, els canvis es realitzen en entorns locals, de desenvolupament o de preparació (depenent de la configuració) i es van passant d'esquerra a dreta a través dels diferents entorns, acabant en el de producció.

Un cop completat aquest procés de desplegament, els nous canvis seran visibles en l'entorn actiu.

![[Pasted image 20250729133542.png]]

En la imatge anterior es mostra una forma molt simplificada i clàssica de manejar els desplegaments quan es treballa amb llocs web en un CMS. No necessàriament es necessiten tots els entorns anteriors, però el procés segueix sent el mateix.

En utilitzar múltiples entorns s'obté una llista d'avantatges - la principal és que es poden fer canvis sense que afectin el seu lloc web en viu. Un cop que els canvis es fan, **es proven** i estan llestos per ser passats a producció, el procés de desplegament s'encarrega de la resta.

---

### De quins passos consta el procés de desplegament?

El flux del procés de desplegament consta de 5 passos: **Planificació, desenvolupament, proves, desplegament i supervisió.**

A continuació, ens endinsarem en cadascun dels 5 passos, però abans una nota ràpida.

El flux del procés de desplegament que apareix a continuació cobreix els aspectes fonamentals, que es divideixen en 5 passos. Això no significa que sigui l'única manera de fer-ho - podria haver-hi un procés millor per a cada cas. És una simplificació perquè cobreixi les parts més importants.

---

#### Recordar tenir un pla de desplegament de programari

Per assegurar-se que el procés de desplegament es desenvolupi amb la màxima fluïdesa possible, el millor és tenir un pla de desplegament que se segueixi en tot moment. En tenir un pla ens assegurem que tot es faci de la mateixa manera cada vegada que es realitzin canvis. Això és especialment útil quan diversos usuaris treballen en el mateix projecte.

Un pla de desplegament ha d'incloure regles sobre quan desplegar des dels entorns locals als llocs de desenvolupament o de posada en escena, així com horaris per a quan els nous canvis poden anar a un entorn en viu. En tenir un pla establert, es redueix el risc de conflictes entre els diferents canvis i s'assegura que el procés de desplegament sigui el més fàcil i fluid possible. Si s'està treballant en un projecte de codi obert, també dóna l'oportunitat de fer _Release Candidates_ i deixar que la comunitat el provi per detectar qualsevol error que es pugui haver passat per alt.

A més d'un pla general, també és important planificar cadascun dels canvis que es vagi a realitzar. Aquest procés serà molt ràpid per als canvis menors, però hauria de ser molt més extens per als grans canvis. Si es planifica amb molta antelació, s'estarà molt més preparat per tenir un procés de desplegament sense problemes.

---

#### El desenvolupament pròpiament dit

Un cop que es tingui el pla en marxa, és el moment de realitzar el desenvolupament real. Per garantir que qualsevol desenvolupament pugui realitzar-se simultàniament i sense trencar res, és important treballar únicament en entorns locals o de desenvolupament. Un cop que el procés de desenvolupament està fet, és el moment de començar a provar i desplegar els canvis a través de la configuració del seu entorn.

---

#### Provar els canvis

Provar els canvis és crucial per garantir que no hi hagi errors en l'entorn de producció final. Però les proves no poden completar-se sense desplegar els canvis en nous entorns.

Un cop que s'hagi comprovat que tots els canvis funcionen en l'entorn local o de desenvolupament, és el moment de desplegar els canvis en el següent entorn. Això s'ha de fer fins a l'entorn de preproducció, on s'han de realitzar les proves finals de control de qualitat. Si tot està correctament provat i funciona en un entorn semblant a l'entorn real, és el moment de desplegar-lo en viu.

Si es descobreixen errors pel camí en qualsevol entorn, és important tenir un pla per manejar-los. Generalment, qualsevol canvi que no passi les proves en l'entorn de posada en marxa ha de ser enviat de nou a la fase de desenvolupament i -un cop corregit- tornar a treballar en els entorns.

---

#### Desplegar els canvis en l'entorn real

Un cop que s'han realitzat totes les proves en els entorns anteriors i s'han corregit els errors, és el moment de desplegar els canvis en l'entorn real. Això hauria de ser una cosa bastant segura, però tots els que han treballat en el desenvolupament de programari saben que alguna cosa pot sortir malament.

Així que, encara que és fàcil aturar-se aquí, és important incloure l'últim pas del procés: la supervisió.

---

#### Supervisar els canvis

Un cop que els nous canvis estiguin en marxa i els usuaris reals utilitzin activament el lloc web o l'aplicació, és important supervisar que tot funcioni segons el previst. Independentment de la planificació realitzada, existeix la possibilitat que els usuaris es trobin amb problemes o realitzin accions que vostè no havia previst durant la planificació i el desenvolupament.

Un bon consell per a la monitorització és planificar els llançaments per als moments en què la menor quantitat d'usuaris ho notin i en els quals es tinguin recursos de desenvolupament preparats en cas que s'hagi d'arreglar alguna cosa. D'aquesta manera, el nombre d'usuaris afectats per qualsevol error serà mínim i es tindrà gent preparada per arreglar-lo o revertir els canvis si és necessari.

Si s'han de revertir els canvis, és important mantenir la calma i tenir un procés per manejar-ho amb la mateixa meticulositat amb què es manegen els desplegaments.

---

### Diferents tipus de desplegament

Quan es tracta del tipus de desplegament, sovint es divideix en dues parts. Generalment, es dividirà entre metadades i contingut, ja que aquests tenen diferents impactes en un nou entorn i han de ser manejats de manera diferent.

---

#### Desplegament de metadades

Les **metadades** inclouen els canvis en el codi, les plantilles, els fulls d'estil, els fitxers, etc. Aquests canvis sovint requeriran una comprovació de validació entre entorns per veure si té algun conflicte imprevist que s'hagi de resoldre. Moltes eines de desplegament inclouen comprovacions de coherència i ajuden a guiar-te en cas de conflictes.

---

#### Desplegament de continguts

El **contingut**, com el text, les imatges i els vídeos, es maneja de forma diferent durant el desplegament, ja que és menys complicat moure'l entre entorns que les metadades. Per aquesta raó, sovint veuràs que les eines de desplegament fan que el desplegament de contingut sigui accessible per als editors de contingut i no només per als desenvolupadors. D'aquesta manera, un editor de continguts no depèn d'un desenvolupador quan es tracta d'enviar nous continguts a un entorn actiu.

---

### Bones pràctiques de desplegament

Quan es treballa amb entorns de desplegament, és important, com s'ha esmentat anteriorment, tenir un pla i un procés clar per a això en l'equip. Per ampliar aquest procés hem reunit algunes bones pràctiques que són bones per implementar com a part del seu procés.

S'ha de tenir en compte que les següents pràctiques recomanades es refereixen principalment al desenvolupament de programari i de la web. Si s'estan duent a terme altres tipus de desenvolupament pot haver-hi altres coses a considerar en el flux de treball de desplegament.

---

#### Utilitzar Git

Això pot semblar obvi, però tenir un sistema de control de versions és inestimable per a qualsevol flux de treball de desplegament. Sense ell, és probable que es produeixin errors si es treballa en equip.

Fins i tot si ets l'únic desenvolupador que treballa en un projecte, és molt recomanable utilitzar Git en cas que necessitis tornar a versions anteriors o si algú nou s'uneix al teu equip.

Sense Git serà difícil assegurar la consistència en el flux de treball de desplegament i pot portar a que es cometin més errors per desplegar codi inacabat o per no tenir a tots els membres de l'equip treballant en la mateixa versió del codi.

---

#### Treballar en branques

Com a regla general, el teu equip hauria de treballar en branques. Fer-ho així permetrà treballar en diverses coses al mateix temps sense que s'afectin entre si.

Un exemple és quan es troba un error que ha de ser corregit. Si un desenvolupador està utilitzant una branca per treballar en una nova característica, pot fer ràpidament una nova branca de l'entorn de desenvolupament per treballar en l'error. D'aquesta manera, hi haurà dues branques diferents que no xocaran ni crearan possibles conflictes de fusió més endavant.

Treballar amb branques també ajuda l'equip amb les preguntes i respostes a l'hora de desplegar en un entorn de preproducció. Tenir els canvis en branques separades i fusionar-les donarà als _testers_ una millor visió del que es va empènyer (_push_) i el que han de provar.

---

#### Utilitzar un entorn local com a entorn de desenvolupament

Encara que és possible treballar directament en un entorn de desenvolupament, en la majoria dels casos s'estalviarà molt de temps treballant localment. En instal·lar el lloc web o el programari de forma local, es podrà treballar de forma més eficient i accelerar les proves i la verificació del codi.

En primer lloc, no cal que confirmi, empenyi i desplegui constantment un canvi abans de poder verificar si funciona. I quan alguna cosa no funciona (això ens passa a tots) haurà de revertir-ho, empènyer-ho de nou i tornar a desplegar-ho.

En lloc d'això, pots simplement executar-ho tot localment i, un cop que funcioni com cal, pots empènyer-ho directament a l'entorn de preparació per a una prova més rigorosa.

---

#### Revisar les diferències abans de desplegar-ho en l'entorn real

Un cop que l'equip de proves s'hagi assegurat que tot funciona en l'entorn de proves, és el moment de desplegar el codi en l'entorn real.

Però abans de fer el desplegament final, és important fer una revisió final de les diferències entre l'entorn actual en producció i l'entorn de desenvolupament del que es parteix.

Fins i tot després de les proves exhaustives i la garantia de qualitat, les coses poden anar malament tan aviat com s'arriba a l'entorn real. I un cop que això succeeix, sovint pot ser molt estressant implementar correccions ràpides o fer una reversió completa de la versió. Generalment, es voldrà evitar això a tota costa, per la qual cosa és molt recomanable fer una revisió final del codi abans de prémer el botó de desplegament.

---

#### Considerar tenir grups d'usuaris amb diferents permisos

Mentre que qualsevol desenvolupador ha de ser capaç d'empènyer els canvis als entorns de _test_, pot ser una bona idea restringir qui pot desplegar-los en viu.

Per als equips més petits, això pot no tenir molt de sentit, ja que pot crear un coll d'ampolla per implantar nous canvis. Però si es tracta d'un equip més gran amb un nivell d'experiència molt variat entre els membres de l'equip, pot ser una gran idea deixar que només els desenvolupadors _sènior_ despleguin en l'entorn de producció.

Això assegura efectivament un major nivell de control sobre el flux de _releases_ i també significa que almenys un parell d'ulls _sènior_ han vist el que està passant en l'entorn real. Si el que es té és un enfocament molt iteratiu amb llançaments ràpids com l'utilitzat en la metodologia CD (_Continous Delivery_), això podria alentir-ho tot massa. Així i tot, atès que els canvis que s'empenyen són normalment més petits amb aquest enfocament, probablement no se sofriran grans retards. I si significa detectar alguns errors més, el temps que s'estalvia al no haver de corregir errors compensarà el temps invertit.

Parlant de trencar coses...

---

#### Mantenir la calma, fins i tot si alguna cosa es trenca

Acabes de desplegar en el teu entorn de producció i ara el teu lloc web està trencat. Quina lliada, ara què es fa?

Desgraciadament, aquestes coses ocorren - no importa com de curós que se sigui. Però en lloc d'entrar en pànic i aplicar _hotfixes_ o retrocedir immediatament, és important mantenir la calma i assegurar-se que el que està fent no trencarà les coses encara més.

En primer lloc, s'hauria de comprovar si és possible realitzar una reversió o **rollback** i si realment s'arreglaria alguna cosa. En algunes situacions, és possible que s'hagin fet canvis que són irreversibles i un _rollback_ només causaria problemes encara majors.

També cal comprovar si el que s'ha trencat és una característica existent o nova. De nou, si la cosa que es va trencar no era part de la nova versió, probablement no servirà de res fer un _rollback_.

Així que en lloc d'entrar en pànic, s'ha de tenir un pla preparat i respirar profundament abans de posar-se a treballar en la recerca d'una solució. Pot semblar senzill, però pot ajudar a sortir d'una mala situació molt més ràpid que si es llança directament.

---

### A quina hora del dia s'han de desplegar els canvis?

En cas que alguna cosa es trenqui en desplegar en l'entorn de producció, és important trobar el millor moment per fer-ho. I encara que aquest moment varia molt d'un projecte a un altre, hi ha dues preguntes que poden fer-se per determinar quan desplegar els canvis:

1. **Quan té la menor quantitat d'usuaris actius?**
    
2. **Quan té algú preparat per supervisar i solucionar els problemes després del desplegament?**
    

---

#### Quan té el menor nombre d'usuaris actius?

Generalment, el que es vol és que el menor nombre possible de persones es vegi afectat pels seus nous canvis. Per tant, com a regla general, ha de buscar qualsevol moment del dia en què el menor nombre d'usuaris estigui utilitzant activament el lloc web o programari.

En el cas dels llocs web, això pot fer-se consultant les eines d'anàlisi de dades que es tinguin en marxa, per exemple, Google Analytics. Allà es podran crear informes personalitzats que mostrin a quina hora del dia es té menys trànsit, així com identificar les hores punta en les quals definitivament no s'hauria de fer cap canvi.

A més de mirar l'hora del dia, també pot valer la pena mirar com es reparteix l'activitat dels usuaris entre els dies de la setmana.

Aquesta anàlisi és molt bona, però sovint acabarà amb la mateixa resposta: Haurien de publicar-se els canvis durant la nit. I encara que això podria semblar una gran idea si només ens fixéssim en aquesta qüestió, és important que també tinguem en compte la següent.

---

#### Hi ha algú despert i preparat per solucionar possibles problemes en aquell moment?

Si la resposta és no, llavors desplegar els canvis a la meitat de la nit podria no ser la millor idea.

En el seu lloc, s'haurien d'identificar les franges horàries en les quals puguis trobar el millor equilibri entre el nombre d'usuaris actius i els desenvolupadors disposats a solucionar els problemes. Això variarà molt depenent del projecte i de l'equip, però en general, s'haurien de trobar algunes opcions. I si ja es té un horari fix de desplegament, fins i tot es pot convèncer l'equip que estigui llest a hores estranyes del dia. És molt més fàcil convèncer algú que vingui unes hores abans si sap que només ocorre una vegada cada cicle o _sprint_.

És per aquest motiu que en moltes empreses es treballa amb guàrdies rotatives per oferir una disponibilitat total.

> Info
>
Encara que no hi ha un moment perfecte per al desplegament, definitivament hi ha moments que són millors que altres.

---

### Quins són els avantatges del desplegament i dels entorns múltiples?

---

#### Reducció del risc de trencar un lloc web en producció

Una de les principals raons per utilitzar múltiples entorns i confiar en el desplegament és reduir el risc que els canvis tinguin un impacte negatiu en un lloc web en viu. Mentre que els canvis menors es poden fer fàcilment directament en un lloc web en viu, els canvis més grans es poden fer en entorns separats sense el risc de trencar res en l'entorn en viu.

Tenir diversos usuaris treballant en el mateix lloc web també garanteix que ningú es arrisqui a trencar alguna cosa a causa dels canvis d'un altre usuari.

---

#### Estalvi de temps

Sense la preocupació de trencar alguna cosa en un lloc web en viu, es poden realitzar els canvis en l'ordre que es prefereixi. Això significa que es pot optimitzar el flux de treball per realitzar els canvis sense tenir en compte l'aspecte o el funcionament del lloc web mentre es duu a terme.

Si es treballa en un entorn local també existeix l'avantatge que els canvis es processen més ràpid i no hi ha dependències de cap problema de connectivitat.

A l'hora de desplegar els canvis, també s'estalviarà temps, ja que es podran realitzar tots els canvis al mateix temps en lloc d'haver de fer-ho en diversos passos més petits.

---

#### El contingut sensible al temps és més fàcil de gestionar

Si s'estan duent a terme campanyes que són sensibles al temps i que només poden posar-se en marxa a partir d'un determinat dia o hora, llavors l'execució de múltiples entorns i l'ús del desplegament poden estalviar una gran quantitat d'estrès.

En crear tot el contingut en un entorn de posada en escena/preproducció (o similar) pots acabar la teva campanya sense preocupar-te que sigui visible per als teus usuaris. I quan arribi el moment de llançar-la, podràs fer-la visible en molt poc temps desplegant-la en el seu entorn real.

I si l'eina de desplegament inclou rols d'usuari amb configuració de permisos, és possible que un editor de continguts faci tot això -incloent el desplegament dels canvis- sense involucrar un desenvolupador en el procés.

---

### Desplegament d'aplicacions Java

---

#### Introducció

En el costat del servidor, hem d'aconseguir que el nostre servidor HTTP sigui capaç d'executar programes d'aplicació que recullin els paràmetres de peticions del client, els processin i retornin al servidor un document que aquest passarà al seu torn al client.

Així, per al client el servidor no haurà fet res diferent a l'estipulat en el protocol HTTP, però el servidor podrà valer-se d'eines externes per processar i servir la petició sol·licitada, podent així no limitar-se a servir pàgines estàtiques, sinó utilitzar altres aplicacions (_servlets_, JSP...) per servir documents amb contingut dinàmic.

Els programes d'aplicació són típicament programes que realitzen consultes a bases de dades, processen la informació resultant i retornen la sortida al servidor, entre altres tasques.

Anem a centrar-nos en les aplicacions web JavaEE, en les quals els components dinàmics que rebran les peticions HTTP en el servidor seran els _servlets_ i JSPs. Aquests components podran analitzar aquesta petició i utilitzar altres components Java per realitzar les accions necessàries (_beans_, EJBs, etc.).

---

#### Estructura d'una aplicació Java

Una aplicació web JavaEE que utilitzi _servlets_ o pàgines JSP ha de tenir una estructura de fitxers i directoris determinada:

- En el directori arrel de l'aplicació es col·loquen les pàgines HTML o JSP (podem dividir-les també en directoris si volem).
    
- Penjant del directori inicial de l'aplicació, es té un directori `WEB-INF`, que conté la informació Web rellevant per a l'aplicació.
    
- La resta d'elements de l'aplicació (imatges, etc.), podem estructurar-los com ens convingui.
    

Aquesta estructura estarà continguda dins d'algun directori, que serà el directori corresponent a l'aplicació Web, i que podrem, si ho fem convenientment, copiar al servidor que ens convingui. És a dir, qualsevol servidor Web JavaEE suporta aquesta estructura en una aplicació Web, només haurem de copiar-la en el directori adequat de cada servidor.

Cada aplicació web JavaEE és un context, una unitat que comprèn un conjunt de recursos, classes Java i la seva configuració. Quan parlem de context, ens estarem referint a l'aplicació web en conjunt.

---

#### Empaquetament

Una forma de distribuir aplicacions Web és empaquetar tota l'aplicació (a partir del seu directori inicial) dins d'un fitxer **WAR** (de forma semblant a com es fa amb un TAR o un JAR), i distribuir aquest fitxer. Podem crear un fitxer WAR de la mateixa forma que creem un JAR, utilitzant l'eina JAR.

Aquests fitxers WAR són un estàndard de JavaEE, per la qual cosa podrem utilitzar-los en els diferents servidors d'aplicacions JavaEE existents.

---

#### Desplegament d'arxius WAR

Els arxius WAR, són un tipus especial de JAR utilitzat per distribuir els artefactes o contingut de les aplicacions Web en tecnologia JEE: pàgines Web HTML o JSP, classes Java, _servlets_ Java, arxius XML, llibreries d'etiquetes (_tag libraries_) i altres recursos.

L'empaquetament en arxius WAR és una cosa estàndard, però no així el procés de desplegament, que és dependent del servidor. No obstant això, la majoria de servidors JavaEE funcionen en aquest aspecte de manera similar: permeten desplegar les aplicacions des d'una consola d'administració i també "deixant caure" el fitxer en un determinat directori.

---

### Maven

**Maven** és una eina _open-source_, que es va crear el 2001 amb l'objectiu de simplificar els processos de _build_ (compilar i generar executables a partir del codi font).

Abans d'existir Maven, si volíem compilar i generar executables d'un projecte, havíem d'analitzar quines parts de codi s'havien de compilar, quines llibreries utilitzava el codi, on incloure-les, quines dependències de compilació hi havia en el projecte…

En el millor dels casos, s'empraven uns pocs minuts per saber com fer una _build_ del projecte. En el pitjor dels casos, el procés de _build_ era tan complex que un desenvolupador podia trigar hores a saber com compilar i generar els executables a partir del codi.

Ara, la _build_ de qualsevol projecte Maven, independentment dels seus mòduls, dependències o llibreries, consisteix simplement a executar el comando `mvn install`.

D'altra banda, abans de Maven, cada vegada que sortia una nova versió d'un analitzador estàtic de codi, d'un _framework_ de proves unitàries (com JUnit) o qualsevol llibreria, calia aturar tot el desenvolupament per reajustar el procés de _build_ a les noves necessitats.

I… com s'executaven les proves? Com es generaven informes? Sense Maven, en cada projecte això es feia de diferent manera.

![[Pasted image 20250729133653.png]]

La veritat és que Maven és molt més que una eina que fa _builds_ del codi.

Podríem dir, que **Maven és una eina capaç de gestionar un projecte programari complet**, des de l'etapa en la qual es comprova que el codi és correcte, fins que es desplega l'aplicació, passant per l'execució de proves i generació d'informes i documentació.

Per a això, en Maven es defineixen tres cicles de _build_ del programari amb una sèrie d'etapes diferenciades. Per exemple el cicle per defecte té les etapes de:

- **Validació (`validate`)**: Validar que el projecte és correcte.
    
- **Compilació (`compile`)**.
    
- **Test (`test`)**: Provar el codi font usant un _framework_ de proves unitàries.
    
- **Empaquetar (`package`)**: Empaquetar el codi compilat i transformar-lo en algun format tipus `.jar` o `.war`.
    
- **Proves d'integració (`integration-test`)**: Processar i desplegar el codi en algun entorn on es puguin executar les proves d'integració.
    
- **Verificar** que el codi empaquetat és vàlid i compleix els criteris de qualitat (`verify`).
    
- **Instal·lar** el codi empaquetat en el repositori local de Maven, per usar-lo com a dependència d'altres projectes (`install`).
    
- **Desplegar** el codi a un entorn (`deploy`).
    

Per poder dur a terme alguna d'aquestes fases en el nostre codi, només haurem d'executar `mvn` i el nom de la fase (la paraula que vaig posar entre parèntesis). A més, van en cadena, és a dir, si empaquetem el codi (`package`), Maven executarà des de la fase de validació (`validate`) a empaquetament (`package`). Així de simple.

D'altra banda, amb Maven la gestió de dependències entre mòduls i diferents versions de llibreries es fa molt senzilla. En aquest cas, només hem d'indicar els mòduls que componen el projecte, o quines llibreries utilitza el programari que estem desenvolupant en un fitxer de configuració de Maven del projecte anomenat **POM** (_Project Object Module_).

A més, en el cas de les llibreries, no has ni tan sols de descarregar-les a mà. Maven posseeix un repositori remot (Maven Central) on es troben la majoria de llibreries que s'utilitzen en els desenvolupaments de programari, i que la pròpia eina es descarrega quan sigui necessari.

Diguem que Maven aporta una semàntica comuna al procés de _build_ i desenvolupament del programari.

Fins i tot, estableix una estructura comuna de directoris per a tots els projectes. Per exemple el codi estarà en `${arrel del projecte}/src/main/java`, els recursos en `${arrel del projecte}/src/main/resources`. Els tests estan en `${arrel del projecte}/src/test`.

---

### Desplegament d'aplicacions Node.js amb Express

---

#### Què és Node.js?

**Node JS** és un entorn d'execució de JavaScript ràpid que utilitzem per construir aplicacions del costat del servidor, però per si mateix no sap com servir arxius, manejar peticions ni mètodes HTTP, així que aquí és on entra en joc Express JS.

Node.js no és un llenguatge de programació. Més aviat, és un entorn d'execució que s'utilitza per executar JavaScript fora del navegador.

![](https://raul-profesor.github.io/DEAW/img/nodejs-new-pantone-black.svg)

Node.js tampoc és un _framework_ (una plataforma per desenvolupar aplicacions de programari). El temps d'execució de Node.js es construeix sobre un llenguatge de programació -en aquest cas, JavaScript- i ajuda a l'execució dels propis _frameworks_.

En resum, Node.js no és un llenguatge de programació ni un marc de treball; és un entorn per a ells.

---

#### Què és Express?

**Express JS** és un _framework_ de Node.js dissenyat per construir aplicacions web d'APIs i aplicacions mòbils multiplataforma de forma ràpida i fer que Node.js sigui fàcil.

![[Pasted image 20250729133741.png]]

---

#### Què és npm?

**NPM** respon a les sigles de _Node Package Manager_ o gestor de paquets de node, és l'eina per defecte de JavaScript per a la tasca de compartir i instal·lar paquets.

![[Pasted image 20250729133749.png]]

Tal com diu la seva documentació, npm es compon d'almenys dues parts principals.

- Un repositori online per publicar paquets de programari lliure per ser utilitzats en projectes Node.js.
    
- Una eina per a la terminal (_command line utility_) per interactuar amb aquest repositori que t'ajuda a la instal·lació d'utilitats, maneig de dependències i la publicació de paquets.
    

Així doncs, NPM és un gestor de paquets per a Javascript. És una espècie de Maven per a paquets Javascript, és a dir, serveix per instal·lar i gestionar versions de paquets i llibreries js.

NPM fa molt de temps que és el referent quant a gestors de paquets javascript, però des de fa un temps li ha sortit un competidor: Yarn. Els de Yarn asseguren que el seu gestor de llibreries js és molt més ràpid i potent, però de moment l'ús de NPM és majoritari.

---

#### `package.json`

Cada projecte en JavaScript pot enfocar-se com un paquet npm amb la seva pròpia informació de paquet i el seu arxiu `package.json` per descriure el projecte.

`package.json` es generarà quan s'executi `npm init` per inicialitzar un projecte JavaScript/Node.js, amb les següents metadades bàsiques proporcionades pels desenvolupadors:

- `name`: el nom de la llibreria/projecte JavaScript
    
- `version`: la versió del projecte.
    
- `description`: la descripció del projecte
    
- `license`: la llicència del projecte
    

---

#### NPM scripts

`package.json` també suporta la propietat `scripts` que pot definir-se per executar eines de línia de comandos que s'instal·len en el context local del projecte. Per exemple, la porció de _scripts_ d'un projecte npm pot tenir un aspecte similar a aquest:

JSON

```
{
  "scripts": {
    "build": "tsc",
    "format": "prettier --write **/*.ts",
    "format-check": "prettier --check **/*.ts",
    "lint": "eslint src/**/*.ts",
    "pack": "ncc build",
    "test": "jest",
    "all": "npm run build && npm run format && npm run lint && npm run pack && npm test"
  }
}
```

Amb `eslint`, `prettier`, `ncc`, `jest` no necessàriament instal·lats com a executables globals sinó com a locals del teu projecte dins de `node_modules/.bin/`.

---

### CI/CD (_Continous Integration/Continous Deployment-Delivery_)

La **CI/CD** és un mètode per distribuir les aplicacions als clients amb freqüència mitjançant l'ús de l'automatització en les etapes del desenvolupament d'aplicacions. Els principals conceptes que se li atribueixen són la integració, la distribució i la implementació contínues. Es tracta d'una solució per als problemes que pot generar la integració del codi nou per als equips de desenvolupament i d'operacions (també coneguda com "l'infern de la integració").

En concret, el procés d'integració i distribució contínues incorpora l'automatització i la supervisió permanents en tot el cicle de vida de les aplicacions, des de les etapes d'integració i prova fins a les de distribució i implementació. Aquest conjunt de pràctiques es coneix com a "canals de CI/CD" i compta amb el suport dels equips de desenvolupament i d'operacions que treballen en conjunt de manera àgil, amb un enfocament de DevOps o d'enginyeria de fiabilitat del lloc (SRE).

---

#### Quina és la diferència entre la integració, la distribució i la implementació contínues?

Aquestes sigles tenen diferents significats. "**CI**" sempre es refereix a la **integració contínua**, que és un procés d'automatització per als desenvolupadors. L'èxit de la CI implica que es dissenyin, provin i combinin els canvis nous en el codi d'una aplicació amb regularitat en un repositori compartit. Suposa una solució al problema que es desenvolupin massa divisions d'una aplicació al mateix temps, que després podrien entrar en conflicte entre si.

La sigla "**CD**" es refereix a la **distribució** o la **implementació contínues**, i es tracta de conceptes relacionats que solen usar-se indistintament. Tots dos es refereixen a l'automatització de les etapes posteriors del procés, però de vegades s'usen per separat per explicar fins on arriba l'automatització.

Generalment, la **distribució contínua** es refereix a que els canvis que implementa un desenvolupador en una aplicació se sotmeten a proves automàtiques d'errors i es carreguen en un repositori (com GitHub o un registre de contenidors), perquè després l'equip d'operacions pugui implementar-los en un entorn de producció en viu. És una solució al problema de la falta de supervisió i comunicació entre els equips comercials i de desenvolupament, així que el seu propòsit és garantir que la implementació del codi nou es dugui a terme amb el mínim esforç.

La **implementació contínua** (l'altra definició de "CD") fa referència al llançament automàtic dels canvis que implementa el desenvolupador des del repositori fins a la producció, per posar-los a la disposició dels clients. Així ja no se sobrecarrega els equips d'operacions amb processos manuals que retarden la distribució de les aplicacions. Amb aquest tipus d'implementació, s'aprofiten els beneficis de la distribució contínua i s'automatitza la següent etapa del procés.

![[Pasted image 20250729133834.png]]

La CI/CD pot incloure solament la integració i la distribució contínues, o les tres pràctiques vinculades, amb la implementació contínua. Per complicar una mica més les coses, de vegades s'utilitza el terme "distribució contínua" per abastar també els processos de la implementació contínua.

En realitat, no val la pena aprofundir en la semàntica. Només cal recordar que la integració i la distribució contínues són un procés que sol percebre's com una canalització i implica incorporar un alt nivell d'automatització permanent i supervisió constant al desenvolupament de les aplicacions.

El significat dels termes varia en cada cas i depèn de la quantitat d'automatització que s'hagi incorporat a la canalització d'integració i distribució contínues. Moltes empreses comencen amb la incorporació de la CI, i després van automatitzant la distribució i la implementació, per exemple, amb les aplicacions desenvolupades directament al núvol.

Els nostres especialistes poden ajudar que la seva empresa desenvolupi les pràctiques, les eines i la cultura necessàries per modernitzar les aplicacions actuals i dissenyar-ne de noves amb major eficiència.

---

#### Integració contínua

L'objectiu del disseny de les aplicacions modernes és que els desenvolupadors puguin treballar de forma simultània en diferents funcions de la mateixa aplicació. No obstant això, si una empresa fusiona tot el codi font diversificat en un sol dia (conegut com el "dia de la fusió"), les tasques poden tornar-se tedioses, manuals i molt lentes. Això es deu a que si un desenvolupador que treballa de forma aïllada implementa un canvi en una aplicació, existeix la possibilitat que entri en conflicte amb les modificacions que altres desenvolupadors van implementar al mateix temps. El problema pot agreujar-se encara més si cada desenvolupador personalitza el seu propi entorn de desenvolupament integrat (IDE) local, en lloc que tot l'equip adopti un IDE basat en el núvol.

![[Pasted image 20250729133849.png]]

La **integració contínua (CI)** permet que els desenvolupadors incorporin els canvis del codi a un repositori compartit amb major freqüència, o fins i tot diàriament. Un cop que s'incorporen les modificacions del desenvolupador, es validen amb la compilació automàtica de l'aplicació i l'execució de diferents proves automatitzades (generalment, d'unitat i integració), per garantir que els canvis no hagin introduït una fallada. Això significa que s'ha de provar tot, des de les classes i el funcionament fins als diferents mòduls que conformen tota l'aplicació. Si una prova automàtica detecta un conflicte entre el codi nou i l'actual, la CI facilita la resolució d'aquests errors amb rapidesa.

---

#### Distribució contínua

Després de l'automatització de les compilacions i les proves d'unitat i integració de la CI, la **distribució contínua** automatitza el trasllat del codi validat cap a un repositori. Per això, perquè la distribució contínua sigui eficaç, és important que la CI ja estigui incorporada al procés de desenvolupament. L'objectiu de la distribució contínua és tenir una base de codi que pugui implementar-se en l'entorn de producció en qualsevol moment.

![[Pasted image 20250729133858.png]]

Cada etapa (des de la incorporació dels canvis al codi fins a la distribució de les compilacions llestes per a la producció) implica l'automatització de les proves i del llançament del codi. Al final d'aquest procés, l'equip d'operacions pot implementar una aplicació per a la producció de forma ràpida i senzilla. Descobriu les altres implementacions que podeu automatitzar.

---

#### Implementació contínua

L'última etapa del canal consolidat de CI/CD és la **implementació contínua**, que automatitza el llançament d'una aplicació a la producció, ja que és una extensió de la distribució contínua, la qual automatitza el trasllat d'una compilació llesta per a la producció a un repositori del codi. A causa de que no hi ha cap entrada manual en l'etapa anterior a la producció, la implementació contínua depèn en gran manera del correcte disseny de l'automatització de les proves.

![[Pasted image 20250729133907.png]]

En la pràctica, els canvis que implementen els desenvolupadors en l'aplicació al núvol podrien posar-se en marxa uns quants minuts després de la seva creació (sempre que hagin passat les proves automatitzades). Això facilita molt més la recepció i incorporació permanent dels comentaris dels usuaris. En conjunt, totes aquestes pràctiques de CI/CD permeten que s'implementin les aplicacions amb menys riscos, ja que és més fàcil incorporar els canvis en les aplicacions de mica en mica, en lloc de fer-ho tot de cop. No obstant això, també s'han de realitzar moltes inversions inicials, ja que s'han de dissenyar les proves automatitzades perquè s'adaptin a les diferents etapes de prova i llançament en el canal de la CI/CD.

---

### Conclusió

S'ha explicat en aquest tema quines són les característiques, usos i diferències entre els servidors web i els servidors d'aplicacions.

També hem explicat detalladament en què consisteix un procés de desplegament clàssic d'una aplicació web, quines són les seves fases i característiques. Per reforçar aquest procés, hem llistat una sèrie de bones pràctiques a l'hora de dur-lo a terme.

Per últim, hem presentat les noves tendències en el món del desplegament, com són les tècniques de CI/CD, que abordarem de forma més profunda en el Tema 7.