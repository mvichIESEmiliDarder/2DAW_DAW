> [!TIP]**Info** Aquest curs està pres íntegrament de la pàgina [Taller de Git](https://aulasoftwarelibre.github.io/taller-de-git/). La seva llicència original permet la reutilització i difusió del mateix. Donem les gràcies des d'aquí a [Aula de Software Libre de la Universidad de Córdoba](https://www.uco.es/aulasoftwarelibre).

# Inici

## Contingut

- Inici
    
- [[#Sistemes de control de versions]]
    
- [[#Introducció a git]]
    
- [[#Aspectes bàsics de Git]]
    
- [[#Ús bàsic de Git]]
    
- [[#Ús avançat de Git]]
    
- [[#Branques]]
    
- Administració de repositoris
    
- Flux de treball amb Git (git flow)
    
- Github
    
- Referències
    

---

# Sistemes de control de versions

## Definició, classificació i funcionament

S'anomena control de versions a la gestió dels diversos canvis que es realitzen sobre els elements d'algun producte o una configuració del mateix. Una versió, revisió o edició d'un producte, és l'estat en el qual es troba aquest producte en un moment donat del seu desenvolupament o modificació. Encara que un sistema de control de versions es pot realitzar de forma manual, és molt aconsellable disposar d'eines que facilitin aquesta gestió donant lloc als anomenats sistemes de control de versions o SVC (de l'anglès System Version Control).

Aquests sistemes faciliten l'administració de les diferents versions de cada producte desenvolupat, així com les possibles especialitzacions realitzades (per exemple, per a algun client específic). Exemples d'aquest tipus d'eines són entre d'altres: CVS, Subversion, SourceSafe, ClearCase, Darcs, Bazaar, Plastic SCM, Git, Mercurial, Perforce.

## Terminologia

_Repositori ("repository")_

El repositori és el lloc en el qual s'emmagatzemen les dades actualitzades i històriques de canvis.

_Revisió ("revision")_

Una revisió és una versió determinada de la informació que es gestiona. Hi ha sistemes que identifiquen les revisions amb un comptador (Ex. subversion). Hi ha altres sistemes que identifiquen les revisions mitjançant un codi de detecció de modificacions (Ex. git utilitza SHA1).

_Etiqueta ("tag")_

Els tags permeten identificar de forma fàcil revisions importants en el projecte. Per exemple, se solen usar tags per a identificar el contingut de les versions publicades del projecte.

_Branca ("branch")_

Un conjunt d'arxius pot ser ramificat o bifurcat en un punt en el temps de manera que, a partir d'aquest moment, dues còpies d'aquests arxius es poden desenvolupar a velocitats diferents o en formes diferents de forma independent l'un de l'altre.

_Canvi ("change")_

Un canvi (o diff, o delta) representa una modificació específica d'un document sota el control de versions. La granularitat de la modificació que és considerada com un canvi varia entre els sistemes de control de versions.

_Desplegar ("checkout")_

És crear una còpia de treball local des del repositori. Un usuari pot especificar una revisió en concret o obtenir l'última. El terme 'checkout' també es pot utilitzar com un substantiu per a descriure la còpia de treball.

_Confirmar ("commit")_

Confirmar és escriure o barrejar els canvis realitzats en la còpia de treball del repositori. Els termes 'commit' i 'checkin' també es poden utilitzar com a substantius per a descriure la nova revisió que es crea com a resultat de confirmar.

_Conflicte ("conflict")_

Un conflicte es produeix quan diferents parts realitzen canvis en el mateix document, i el sistema és incapaç de conciliar els canvis. Un usuari ha de resoldre el conflicte mitjançant la integració dels canvis, o mitjançant la selecció d'un canvi a favor de l'altre.

_Cap ("head")_

També a vegades es diu tip (punta) i es refereix a l'última confirmació, ja sigui en el tronc ('trunk') o en una branca ('branch'). El tronc i cada branca tenen el seu propi cap, encara que HEAD s'utilitza a vegades lliurement per a referir-se al tronc.

_Tronc ("trunk")_

L'única línia de desenvolupament que no és una branca (a vegades també anomenada línia base, línia principal o màster).

_Fusionar, integrar, barrejar ("merge")_

Una fusió o integració és una operació en la qual s'apliquen dos tipus de canvis en un arxiu o conjunt d'arxius. Alguns escenaris d'exemple són els següents:

- Un usuari, treballant en un conjunt d'arxius, actualitza o sincronitza la seva còpia de treball amb els canvis realitzats i confirmats, per altres usuaris, en el repositori.
    
- Un usuari intenta confirmar arxius que han estat actualitzats per altres usuaris des de l'últim desplegament ('checkout'), i el programari de control de versions integra automàticament els arxius (per norma general, després de preguntar-li a l'usuari si s'ha de procedir amb la integració automàtica, i en alguns casos només es fa si la fusió pot ser clara i raonablement resolta).
    
- Un conjunt d'arxius es bifurca, un problema que existia abans de la ramificació es treballa en una nova branca, i la solució es combina després en l'altra branca.
    
- Es crea una branca, el codi dels arxius és independentment editat, i la branca actualitzada s'incorpora més tard en un únic tronc unificat.
    

## Classificació

Podem classificar els sistemes de control de versions atenent a l'arquitectura utilitzada per a l'emmagatzematge del codi: _locals, centralitzats i distribuïts_.

### Locals

Els canvis són guardats localment i no es comparteixen amb ningú. Aquesta arquitectura és l'antecessora de les dues següents.

![[Pasted image 20250801142011.png]]

### Centralitzats

Existeix un repositori centralitzat de tot el codi, del qual és responsable un únic usuari (o conjunt d'ells). Es faciliten les tasques administratives a canvi de reduir flexibilitat, ja que totes les decisions fortes (com crear una nova branca) necessiten l'aprovació del responsable. Alguns exemples són CVS i Subversion.

![[Pasted image 20250801161205.png]]

### Distribuïts

Cada usuari té el seu propi repositori. Els diferents repositoris poden intercanviar i barrejar revisions entre ells. És freqüent l'ús d'un repositori, que està normalment disponible, que serveix de punt de sincronització dels diferents repositoris locals. Exemples: Git i Mercurial.

![[Pasted image 20250801161256.png]]

#### Avantatges de sistemes distribuïts

- No és necessari estar connectat per a guardar canvis.
    
- Possibilitat de continuar treballant si el repositori remot no està accessible.
    
- El repositori central està més lliure de branques de proves.
    
- Es necessiten menys recursos per al repositori remot.
    
- Més flexibles en permetre gestionar cada repositori personal com es vulgui.
    

---

# Introducció a git

Git és un sistema de control de versions distribuït que es diferencia de la resta en la manera en què modela les seves dades. La majoria dels altres sistemes emmagatzemen la informació com una llista de canvis en els arxius, mentre que Git modela les seves dades més com un conjunt d'instantànies d'un mini sistema d'arxius.

![[Pasted image 20250801161345.png]]

![[Pasted image 20250801161415.png]]

## Els tres estats

Git té tres estats principals en els quals es poden trobar els teus arxius: _confirmat (committed), modificat (modified), i preparat (staged)_.

- **Confirmat** vol dir que les dades estan emmagatzemades de manera segura en la teva base de dades local.
    
- **Modificat** vol dir que has modificat l'arxiu però encara no l'has confirmat a la teva base de dades.
    
- **Preparat** vol dir que has marcat un arxiu modificat en la seva versió actual perquè vagi en la teva pròxima confirmació.
    

Això ens porta a les tres seccions principals d'un projecte de Git:

- El directori de Git (Git directory)
    
- El directori de treball (working directory)
    
- L'àrea de preparació (staging area).
    

![[Pasted image 20250801161449.png]]

## Fluxos de treball distribuïts amb git

Hem vist en què consisteix un entorn de control de versions distribuït, però més enllà de la simple definició, existeix més d'una manera de gestionar els repositoris. Aquests són els fluxos de treball més comuns en Git.

### Flux de treball centralitzat

Existeix un únic repositori o punt central que guarda el codi i tothom sincronitza el seu treball amb ell. Si dos desenvolupadors clonen des del punt central, i ambdós fan canvis; només el primer d'ells en enviar els seus canvis de tornada ho podrà fer netament. El segon desenvolupador haurà de fusionar prèviament el seu treball amb el del primer, abans d'enviar-lo, per a evitar sobreescriure els canvis del primer.

![[Pasted image 20250801161512.png]]

### Flux de treball del Gestor-d'Integracions

En permetre múltiples repositoris remots, en Git és possible tenir un flux de treball on cada desenvolupador tingui accés d'escriptura al seu propi repositori públic i accés de lectura als repositoris de tots els altres. Habitualment, aquest escenari sol incloure un repositori canònic, representant "oficial" del projecte.

![[Pasted image 20250801161531.png]]

> ℹ️ **Info** Aquest model es va posar molt de moda arran de la forja GitHub que es veurà més endavant.

### Flux de treball amb Dictador i Tinent

És una variant del flux de treball amb múltiples repositoris. S'utilitza generalment en projectes molt grans, amb centenars de col·laboradors. Un exemple molt conegut és el del kernel de Linux. Uns gestors d'integració s'encarreguen de parts concretes del repositori; i s'anomenen tinents. Tots els tinents rendeixen comptes a un gestor d'integració; conegut com el dictador benevolent. El repositori del dictador benevolent és el repositori de referència, del qual recuperen (pull) tots els col·laboradors.

![[Pasted image 20250801161619.png]]

---

# Aspectes bàsics de Git

## Instal·lació

### Instal·lant en Linux

Si vols instal·lar Git en Linux a través d'un instal·lador binari, en general pots fer-ho a través de l'eina bàsica de gestió de paquets que porta la teva distribució. Si estàs en Fedora, pots usar yum:

Bash

```
yum install git-core
```

O si estàs en una distribució basada en Debian com Ubuntu, prova amb apt-get:

Bash

```
apt-get install git
```

### Instal·lant en Windows

Instal·lar Git en Windows és molt fàcil. El projecte msysGit té un dels processos d'instal·lació més senzills. Simplement descarrega l'arxiu exe de l'instal·lador des de la pàgina de GitHub, i executa'l:

[http://msysgit.github.com/](http://msysgit.github.com/)

Una vegada instal·lat, tindràs tant la versió de línia de comandaments (inclòs un client SSH que ens serà útil més endavant) com la interfície gràfica d'usuari estàndard. Es recomana no modificar les opcions que porta per defecte l'instal·lador.

### Instal·lant en MacOS

En MacOS es recomana tenir instal·lada l'eina [homebrew](https://brew.sh/). Després, és tan fàcil com executar:

```
brew install git
```

## Configuració

### La teva identitat

El primer que hauries de fer quan instal·les Git és establir el teu nom d'usuari i adreça de correu electrònic. Això és important perquè les confirmacions de canvis (commits) en Git usen aquesta informació, i és introduïda de manera immutable en els commits que envies:

Bash

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com`
```

També es recomana configurar el següent paràmetre:

Bash

```
git config --global push.default simple
```

El valor `simple` li indica a Git que `git push` ha de fer el següent:

1. **Pujar només la branca actual:** `git push` només pujarà els commits de la branca en la qual et trobes en aquest moment. Això evita pujades accidentals d'altres branques.
    
2. **Exigir que les branques tinguin el mateix nom:** Només funcionarà si el nom de la teva branca local (`main`) coincideix amb el nom de la branca remota (`main`).
    
3. **Configuració explícita (la clau):** Si la branca actual no està rastrejant a una branca remota amb el mateix nom, `git push` fallarà i et suggerirà que ho facis de forma explícita. Això t'obliga a usar un comandament com `git push -u origin <branca>` la primera vegada, establint clarament la relació de seguiment (`upstream`) entre la branca local i la remota.
    

### Bash Completion

_Bash completion_ és una utilitat que permet a bash completar ordres i paràmetres. Per defecte sol venir desactivada en Ubuntu i és necessari modificar l'arxiu `$HOME/.bashrc` per a poder activar-la. Simplement cal descomentar les línies que ho activen.

Bash

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
# if ! shopt -oq posix; then
#   if [ -f /usr/share/bash-completion/bash_completion ]; then
#     . /usr/share/bash-completion/bash_completion
#   elif [ -f /etc/bash_completion ]; then
#     . /etc/bash_completion
#   fi
# fi
```

---

# Ús bàsic de Git

## Crear un projecte

### Crear un programa "Hola Món"

Creem un directori on col·locar el codi

Bash

```
mkdir curs-de-git
cd curs-de-git
```

Creem un fitxer `hola.php` que mostri Hola Món.

PHP

```
<?php
echo "Hola Món\n";
```

### Crear el repositori

Per a crear un nou repositori s'usa l'ordre `git init`

Bash

```
git init
Inicializado repositorio Git vacío en /home/marti/Documentos/IES/2DAW_DAW/Practiques/practicasgit1/.git/
```

### Afegir l'aplicació

Anem a emmagatzemar l'arxiu que hem creat en el repositori per a poder treballar, després explicarem per a què serveix cada ordre.

Bash

```
git add hola.php
git commit -m "Creació del projecte"
[master (commit-raíz) ce4fd76] Creación del proyecto
 1 file changed, 2 insertions(+)
 create mode 100644 hola.php

```

![[Pasted image 20250801174901.png]]

![[Pasted image 20250801134511.png]] _Gràfics fets amb "Mermaid Chart"_. Documentació [aquí](https://docs.mermaidchart.com/blog/posts/how-to-make-a-git-graph-with-mermaid-chart).

### Comprovar l'estat del repositori

Amb l'ordre `git status` podem veure en quin estat es troben els arxius del nostre repositori.

Bash

```
git status
En la rama master
nada para hacer commit, el árbol de trabajo está limpio
```

Si modifiquem l'arxiu `hola.php`:

PHP

```
<?php
@print "Hola {$argv[1]}\n";
```

I tornem a comprovar l'estat del repositori:

Bash

```
git status
En la rama master
Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
	modificados:     hola.php

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
```

### Afegir canvis

Amb l'ordre `git add` indiquem a git que prepari els canvis perquè siguin emmagatzemats.

Bash

```
git add hola.php
git status
En la rama master
Cambios a ser confirmados:
  (usa "git restore --staged <archivo>..." para sacar del área de stage)
	modificados:     hola.php
```

### Confirmar els canvis

Amb l'ordre `git commit` confirmem els canvis definitivament, la qual cosa fa que es guardin permanentment en el nostre repositori.

Bash

```
git commit -m "Parametrització del programa"
[master 03f5c1c] Parametrización del programa
 1 file changed, 1 insertion(+), 1 deletion(-)
```

![[Pasted image 20250801175346.png]]

![[Pasted image 20250801135647.png]]

### Diferències entre _workdir_ i _staging_.

Modifiquem la nostra aplicació perquè suporti un paràmetre per defecte i afegim els canvis.

PHP

```
<?php
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

Aquesta vegada afegim els canvis a la fase de _staging_ però sense confirmar-los (_commit_).

Bash

```
git add hola.php
```

Tornem a modificar el programa per a indicar amb un comentari el que hem fet.

PHP

```
<?php
// El nom per defecte és Món
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

I veiem l'estat en el qual està el repositori

Bash

```
git status
En la rama master
Cambios a ser confirmados:
  (usa "git restore --staged <archivo>..." para sacar del área de stage)
	modificados:     hola.php

Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
	modificados:     hola.php
```

Podem veure com apareixen l'arxiu _hola.php_ dues vegades. El primer està preparat per a ser confirmat i està emmagatzemat en la zona de _staging_. El segon indica que el directori hola.php està modificat una altra vegada en la zona de treball (_workdir_).

> ⚠️ **Warning** Si tornéssim a fer un `git add hola.php` sobreescriuríem els canvis previs que hi havia en la zona de _staging_.

Emmagatzemem els canvis per separat:

Bash

```
git commit -m "S'afegeix un paràmetre per defecte"
[master 1cfddf9] Se añade un parámetro por defecto
 1 file changed, 1 insertion(+)
git status
En la rama master
Cambios no rastreados para el commit:
  (usa "git add <archivo>..." para actualizar lo que será confirmado)
  (usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
	modificados:     hola.php

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
git add .
git status
En la rama master
Cambios a ser confirmados:
  (usa "git restore --staged <archivo>..." para sacar del área de stage)
	modificados:     hola.php
```

![[Pasted image 20250801175727.png]]

![[Pasted image 20250801135955.png]]

> ℹ️ **Info** El valor "." després de `git add` indica que s'afegeixin tots els arxius de forma recursiva.

> ⚠️ **Warning** Compte quan usis `git add .` assegura't que no estàs afegint arxius que no vols afegir.

### Ignorant arxius

L'ordre `git add .` o `git add nom_directori` és molt còmoda, ja que ens permet afegir tots els arxius del projecte o tots els continguts en un directori i els seus subdirectoris. És molt més ràpid que haver d'anar afegint-los un per un. El problema és que, si no es té cura, es pot acabar per afegir arxius innecessaris o amb informació sensible.

En general s'ha d'evitar afegir arxius que s'hagin generat com a producte de la compilació del projecte, els que generin els entorns de desenvolupament (arxius de configuració i temporals) i aquells que continguin informació sensible, com a contrasenyes o tokens d'autenticació. Per exemple, en un projecte de `C/C++`, els arxius objecte no s'han d'incloure, només els que continguin codi font i els make que els generin.

Per a indicar-li a _git_ que ha d'ignorar un arxiu, es pot crear un fitxer anomenat _.gitignore_, bé en l'arrel del projecte o en els subdirectoris que vulguem. Aquest fitxer pot contenir patrons, un en cada línia, que especifiquen quins arxius s'han d'ignorar. El format és el següent:

Bash

```
.gitignore
dir1/           # ignora tot el que contingui el directori dir1
!dir1/info.txt  # L'operador ! exclou de l'ignore a dir1/info.txt (sí es guardaria)
dir2/*.txt      # ignora tots els arxius txt que hi ha en el directori dir2
dir3/**/*.txt   # ignora tots els arxius txt que hi ha en el dir3 i els seus subdirectoris
*.o             # ignora tots els arxius amb extensió .o en tots els directoris
```

Cada tipus de projecte genera els seus fitxers temporals, així que per a cada projecte hi ha un `.gitignore` apropiat. Existeixen repositoris que ja tenen creades plantilles. Podeu trobar-ne un a [https://github.com/github/gitignore](https://github.com/github/gitignore)

### Ignorant arxius globalment

Si bé els arxius que hem posat en `.gitignore` han de ser aquells fitxers temporals o de configuració que es poden crear durant les fases de compilació o execució del programa, en ocasions hi haurà altres fitxers que tampoc hem d'introduir en el repositori i que són recurrents en tots els projectes. En aquest cas, és més útil tenir un _gitignore_ que sigui global a tots els nostres projectes. Aquesta configuració seria complementària a la que ja tenim. Exemples del que es pot ignorar de forma global són els fitxers temporals del sistema operatiu (`*~`, `.nfs*`) i els que generen els entorns de desenvolupament.

Per a indicar a _git_ que volem tenir un fitxer de _gitignore_ global, hem de configurar-ho amb la següent ordre:

Bash

```
git config --global core.excludesfile $HOME/.gitignore_global
```

Ara podem crear un arxiu anomenat `.gitignore_global` en l'arrel del nostre compte amb aquest contingut:

Bash

```
# Compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
*~
*.swp

# IDEs               #
######################
.idea
.settings/
.classpath
.project
```

## Treballant amb l'historial

### Observant els canvis

Amb l'ordre `git log` podem veure tots els canvis que hem fet:

Bash

```
git log
commit 1cfddf928af6df33e94ce6644f5b7ee2524aaa51 (HEAD -> master)
Author: marti <marti.vich@gmail.com>
Date:   Fri Aug 1 17:55:53 2025 +0200

    S'afegeix un paràmetre per defecte

commit 03f5c1c415d0f9010b4a1ae3cc63523ab9efa6c4
Author: marti <marti.vich@gmail.com>
Date:   Fri Aug 1 17:53:08 2025 +0200

    Parametrització del programa

commit ce4fd761e3fc738ec8bf3dc9a8ed50b1fd3fcd1b
Author: marti <marti.vich@gmail.com>
Date:   Fri Aug 1 17:12:58 2025 +0200

    Creació del projecte
```

També és possible veure versions abreujades o limitades, depenent dels paràmetres:

Bash

```
git log --oneline
1cfddf9 (HEAD -> master) S'afegeix un paràmetre per defecte
03f5c1c Parametrització del programa
ce4fd76 Creació del projecte
```

Una versió molt útil de `git log` és la següent, ja que ens permet veure en quins llocs està main i HEAD, entre altres coses:

Bash

```
git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
* 1cfddf9 2025-08-01 | S'afegeix un paràmetre per defecte (HEAD -> master) [marti]
* 03f5c1c 2025-08-01 | Parametrització del programa [marti]
* ce4fd76 2025-08-01 | Creació del projecte [marti]
```

### Crear àlies

Com que aquestes ordres són massa llargues, Git ens permet crear àlies per a crear noves ordres parametritzades. La forma més comuna i recomanada de crear un àlies és usant el comandament `git config` amb la bandera `--global` perquè l'àlies estigui disponible en tots els teus repositoris.

La sintaxi és la següent:

```
git config --global alias.<nom-de-l'alias> <comandament-real>
```

Aquí tens alguns exemples dels àlies més comuns que la gent usa:

#### Exemples d'àlies simples:

- **`st` per a `status`:**
    
    ```
    git config --global alias.st status
    # Ara pots escriure 'git st' en lloc de 'git status'
    ```
    

> ✍️ **Example** Pots configurar fins i tot àlies per a abreujar comandaments. Alguns exemples d'àlies útils:

Bash

```
git config --global alias.br branch
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st "status -u"
git config --global alias.cane "commit --amend --no-edit"
```

### Recuperant versions anteriors

Cada canvi és etiquetat per un hash, per a poder tornar a aquest moment de l'estat del projecte s'usa l'ordre `git checkout`.

Bash

```
git checkout e19f2c1
Note: checking out 'e19f2c1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at e19f2c1... Creació del projecte
cat hola.php
<?php
echo "Hello, World\n";
```

L'avís que ens surt ens indica que estem en un estat on no treballem en cap branca concreta. Això significa que els canvis que fem podrien "perdre's" perquè si no són guardats en una nova branca, en principi no podríem tornar a recuperar-los. Cal pensar que Git és com un arbre on un node té informació del seu node pare, no dels seus nodes fills, amb el que sempre necessitaríem informació d'on es troben els nodes finals o d'una altra manera no podríem accedir a ells.

### Tornar a l'última versió de la branca main

Usem `git checkout` indicant el nom de la branca:

Bash

```
git checkout main
Previous HEAD position was e19f2c1... Creació del projecte
```

### Etiquetant versions

Per a poder recuperar versions concretes en la història del repositori, podem etiquetar-les, la qual cosa és més fàcil que usar un hash. Per a això usarem l'ordre `git tag`.

Bash

```
git tag v1
```

Ara anem a etiquetar la versió immediatament anterior com a v1-beta. Per a això podem usar els modificadors `^` o `~` que ens portaran a un ancestre determinat. Les següents dues ordres són equivalents:

Bash

```
git checkout v1^
git checkout v1~1
git tag v1-beta
```

Si executem l'ordre sense paràmetres ens mostrarà totes les etiquetes existents.

Bash

```
git tag
v1
v1-beta
```

I per a veure-les en l'historial:

Bash

```
git hist main --all
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1, main) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (HEAD, tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801140742.png]]

### Esborrar etiquetes

Per a esborrar etiquetes:

```
git tag -d nombre_etiqueta
```

### Visualitzar canvis

Per a veure els canvis que s'han realitzat en el codi usem l'ordre `git diff`. L'ordre sense especificar res més, mostrarà els canvis que no han estat afegits encara, és a dir, tots els canvis que s'han fet abans d'usar l'ordre `git add`. Després es pot indicar un paràmetre i donarà els canvis entre la versió indicada i l'estat actual. O per a comparar dues versions entre si, s'indica la més antiga i la més nova. Exemple:

Bash

```
git diff v1-beta v1
diff --git a/hola.php b/hola.php
index a31e01f..25a35c0 100644
--- a/hola.php
+++ b/hola.php
@@ -1,3 +1,4 @@
 <?php
+// El nom per defecte és Món
 $nombre = isset($argv[1]) ? $argv[1] : "Mundo";
 @print "Hola, {$nombre}\n";
```

---

# Ús avançat de Git

## Desfer canvis

### Desfent canvis abans de la fase de staging.

Tornem a la branca màster i anem a modificar el comentari que vam posar:

Bash

```
git checkout main
Previous HEAD position was 3283e0d... S'afegeix un paràmetre per defecte
Switched to branch 'main'
```

Modifiquem _hola.php_ de la següent manera:

PHP

```
<?php
// Aquest comentari està malament i cal esborrar-lo
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

I comprovem:

Bash

```
git status
# On branch main
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   hola.php
#
no changes added to commit (use "git add" and/or "git commit -a")
```

El mateix Git ens indica que hem de fer per a afegir els canvis o per a desfer-los:

Bash

```
git checkout hola.php
git status
# On branch main
nothing to commit, working directory clean
cat hola.php
<?php
// El nom per defecte és Món
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

### Desfent canvis abans del commit

Anem a fer el mateix que la vegada anterior, però aquesta vegada sí que afegirem el canvi al _staging_ (sense fer _commit_). Així que tornem a modificar _hola.php_ igual que l'anterior ocasió:

PHP

```
<?php
// Aquest comentari està malament i cal esborrar-lo
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

I l'afegim al _staging_

Bash

```
git add hola.php
git status
# On branch main
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hola.php
#
```

De nou, Git ens indica què hem de fer per a desfer el canvi:

Bash

```
git reset HEAD hola.php
Unstaged changes after reset:
M   hola.php
git status
# On branch main
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   hola.php
#
no changes added to commit (use "git add" and/or "git commit -a")
git checkout hola.php
```

I ja tenim el nostre repositori net una altra vegada. Com veiem cal fer-ho en dos passos: un per a esborrar les dades del _staging_ i un altre per a restaurar la còpia de treball.

### Desfent commits no desitjats.

Si malgrat tot hem fet un commit i ens hem equivocat, podem desfer-lo amb l'ordre `git revert`. Modifiquem una altra vegada l'arxiu com abans:

PHP

```
<?php
// Aquest comentari està malament i cal esborrar-lo
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

Però ara sí que fem commit:

Bash

```
git add hola.php
git commit -m "Ups... aquest commit està malament."
main 5a5d067] Ups... este commit está mal
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Bé, una vegada confirmat el canvi, anem a desfer el canvi amb l'ordre `git revert`:

Bash

```
git revert HEAD --no-edit
[main 817407b] Revert "Ups... este commit está mal"
1 file changed, 1 insertion(+), 1 deletion(-)
git hist
* 817407b 2013-06-16 | Revert "Ups... este commit está mal" (HEAD, main) [Sergio Gómez]
* 5a5d067 2013-06-16 | Ups... este commit está mal [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801115738.png]]

### Esborrar commits d'una branca

L'anterior apartat reverteix un commit, però deixa empremta en l'historial de canvis. Per a fer que no aparegui cal usar l'ordre `git reset`.

Bash

```
git reset --hard v1
HEAD is now at fd4da94 S'afegeix un comentari al canvi del valor per defecte
git hist
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (HEAD, tag: v1, main) [Sergio Góme
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801115821.png]]

La resta de canvis no s'han esborrat (encara), simplement no estan accessibles perquè git no sap com referenciar-los. Si sabem el seu hash podem accedir encara a ells. Passat un temps, eventualment Git té un recol·lector d'escombraries que els esborrarà. Es pot evitar etiquetant l'estat final.

> ⚠️ **Danger** L'ordre _reset_ és una operació delicada. S'ha d'evitar si no se sap bé el que s'està fent, sobretot quan es treballa en repositoris compartits, perquè podríem alterar la història de canvis la qual cosa pot provocar problemes de sincronització.

### Modificar un commit

Això s'usa quan hem oblidat afegir un canvi a un commit que acabem de realitzar. Tenim el nostre arxiu _hola.php_ de la següent manera:

PHP

```
<?php
// Autor: Sergio Gómez
// El nom per defecte és Món
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

I el confirmem:

Bash

```
git commit -a -m "Afegit l'autor del programa"
[main cf405c1] Afegit l'autor del programa
 1 file changed, 1 insertion(+)
```

![[Pasted image 20250801120100.png]]

> 💡 **Tip** El paràmetre `-a` fa un `git add` abans de fer _commit_ de tots els arxius modificats o esborrats (dels nous no), amb el que ens estalviem un pas.

Ara ens adonem que se'ns ha oblidat posar el correu electrònic. Així que tornem a modificar el nostre arxiu:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
// El nom per defecte és Món
$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
@print "Hola, {$nombre}\n";
```

I en aquesta ocasió usem `commit --amend` que ens permet modificar l'últim estat confirmat, substituint-lo per l'estat actual:

Bash

```
git add hola.php
git commit --amend -m "Afegit l'autor del programa i el seu email"
[main 96a39df] Afegit l'autor del programa i el seu email
 1 file changed, 1 insertion(+)
git hist
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email (HEAD, main) [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801120403.png]]

> ⚠️ **Danger** Mai modifiquis un _commit_ que ja hagis sincronitzat amb un altre repositori o que hagis rebut d'ell. Estaries alterant la història de canvis i provocaries problemes de sincronització.

## Movent i esborrant arxius

### Moure un arxiu a un altre directori amb git

Per a moure arxius usarem l'ordre `git mv`:

Bash

```
mkdir lib
git mv hola.php lib
git status
# On branch main
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   renamed:    hola.php -> lib/hola.php
#
```

### Moure i esborrar arxius

Podíem haver fet el pas anterior amb l'ordre del sistema _mv_ i el resultat hagués estat el mateix. El següent és a manera d'exemple i no és necessari que l'executis:

Bash

```
mkdir lib
mv hola.php lib
git add lib/hola.php
git rm hola.php
```

I, ara sí, ja podem guardar els canvis:

Bash

```
git commit -m "Mogut hola.php a lib."
[main 8c2a509] Mogut hola.php a lib.
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename hola.php => lib/hola.php (100%)
```

![[Pasted image 20250801120609.png]]

---

# Branques

## Administració de branques

### Crear una nova branca

Quan anem a treballar en una nova funcionalitat, és convenient fer-ho en una nova branca, per a no modificar la branca principal i deixar-la inestable. Encara que l'ordre per a manejar branques és `git branch` podem usar també `git checkout`.

Anem a crear una nova branca:

```
git branch hola
```

![[Pasted image 20250801104100.png]]

> ℹ️ **Info** Si usem `git branch` sense cap argument, ens retornarà la llista de branques disponibles.

L'ordre anterior no retorna cap resultat i tampoc ens canvia de branca, per a això hem d'usar _checkout_:

```
git checkout hola Switched to branch 'hola'`
```

> 💡 **Tip** Hi ha una forma més ràpida de fer ambdues accions en un sol pas. Amb el paràmetre `-b` de `git checkout` podem canviar-nos a una branca que, si no existeix, es crea instantàniament. `git checkout -b hola` Switched to a new branch 'hola'`

### Modificacions en la branca secundària

Afegim un nou arxiu en el directori `lib` anomenat `HolaMundo.php`:

PHP

```
<?php

class HolaMundo
{
   private $nombre;

   function __construct($nombre)
   {
      $this->nombre = $nombre;
   }

   function __toString()
   {
      return sprintf ("Hola, %s.\n", $this->nombre);
   }
}
```

I modifiquem `hola.php`:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
// El nom per defecte és Món
require('HolaMundo.php');

$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
print new HolaMundo($nombre);
```

Podríem confirmar els canvis tots de cop, però ho farem d'un en un, amb el seu comentari.

Bash

```
git add lib/HolaMundo.php
git commit -m "Afegida la classe HolaMundo"
[hola 6932156] Afegida la classe HolaMundo
 1 file changed, 16 insertions(+)
 create mode 100644 lib/HolaMundo.php
git add lib/hola.php
git commit -m "hola usa la classe HolaMundo"
[hola 9862f33] hola usa la clase HolaMundo
 1 file changed, 3 insertions(+), 1 deletion(-)
```

![[Pasted image 20250801104629.png]]

I ara amb l'ordre `git checkout` podem moure'ns entre branques:

Bash

```
git checkout main
Switched to branch 'main'
git checkout hola
Switched to branch 'hola'
```

### Modificacions en la branca main

Podem tornar i afegir un nou arxiu a la branca principal:

Bash

```
git checkout main Switched to branch 'main'
```

Creem un arxiu anomenat `README.md` en l'arrel del nostre projecte amb el següent contingut:

```
# Curs de GIT

Aquest projecte conté el curs d'introducció a GIT
```

I l'afegim al nostre repositori en la branca en la qual estem:

Bash

```
git add README.md
git commit -m "Afegit README.md"
[main c3e65d0] Añadido README.md
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
git hist --all
* c3e65d0 2013-06-16 | Afegit README.md (HEAD, main) [Sergio Gómez]
| * 9862f33 2013-06-16 | hola usa la classe HolaMundo (hola) [Sergio Gómez]
| * 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
|/
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

I veiem com `git hist` mostra la bifurcació en el nostre codi.

![[Pasted image 20250801104911.png]]

## Fusió de branques i resolució de conflictes

### Barrejar branques

Podem incorporar els canvis d'una branca a una altra amb l'ordre `git merge`

Bash

```
git checkout hola
Switched to branch 'hola'
git merge main
Merge made by the 'recursive' strategy.
 README.md | 3 +++
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
git hist --all
* 9c6ac06 2013-06-16 | Merge commit 'c3e65d0' into hola (HEAD, hola) [Sergio Gómez]
|\
* | 9862f33 2013-06-16 | hola usa la classe HolaMundo [Sergio Gómez]
* | 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
| |
| * c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
|/
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801105034.png]]

D'aquesta forma es pot treballar en una branca secundària incorporant els canvis de la branca principal o d'una altra branca.

### Resoldre conflictes

Un conflicte és quan es produeix una fusió que Git no és capaç de resoldre. Anem a modificar la branca main per a crear-ne un amb la branca hola.

Bash

```
$ git checkout main
Switched to branch 'main'
```

Modifiquem el nostre arxiu _hola.php_ de nou:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
print "Introdueix el teu nom:";
$nombre = trim(fgets(STDIN));
@print "Hola, {$nombre}\n";
```

I guardem els canvis:

Bash

```
git add lib/hola.php
git commit -m "Programa interactiu"
[main 9c85275] Programa interactiu
 1 file changed, 2 insertions(+), 2 deletions(-)
git hist --all
* 9c6ac06 2013-06-16 | Merge commit 'c3e65d0' into hola (hola) [Sergio Gómez]
|\
* | 9862f33 2013-06-16 | hola usa la classe HolaMundo [Sergio Gómez]
* | 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
| | * 9c85275 2013-06-16 | Programa interactiu (HEAD, main) [Sergio Gómez]
| |/
| * c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
|/
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801105238.png]]

Tornem a la branca hola i fusionem:

Bash

```
git checkout hola
Switched to branch 'hola'
git merge main
Auto-merging lib/hola.php
CONFLICT (content): Merge conflict in lib/hola.php
Automatic merge failed; fix conflicts and then commit the result.
```

Si editem el nostre arxiu `lib/hola.php` obtindrem quelcom similar a això:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
<<<<<<< HEAD
// El nom per defecte és Món
require('HolaMundo.php');

$nombre = isset($argv[1]) ? $argv[1] : "Mundo";
print new HolaMundo($nombre);
=======
print "Introdueix el teu nom:";
$nombre = trim(fgets(STDIN));
@print "Hola, {$nombre}\n";
>>>>>>> main
```

La primera part marca el codi que estava en la branca on treballàvem (HEAD) i la part final el codi d'on fusionàvem. Resolem el conflicte, deixant l'arxiu com segueix:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
require('HolaMundo.php');

print "Introdueix el teu nom:";
$nombre = trim(fgets(STDIN));
print new HolaMundo($nombre);
```

I resolem el conflicte confirmant els canvis:

Bash

```
git add lib/hola.php
git commit -m "Solucionat el conflicte en fusionar amb la branca main"
[hola a36af04] Solucionado el conflicto al fusionar con la rama main
```

![[Pasted image 20250801105440.png]]

### Rebasing vs Merging

Rebasing és una altra tècnica per a fusionar diferent a merge i usa l'ordre `git rebase`. Anem a deixar el nostre projecte com estava abans de la fusió. Per a això necessitem anotar el hash anterior al de l'acció de _merge_. El que té l'anotació _"hola usa la classe HolaMundo"_.

Per a això podem usar l'ordre `git reset` que ens permet moure HEAD on vulguem.

Bash

```
git checkout hola
Switched to branch 'hola'
git hist
* a36af04 2013-06-16 | Solucionado el conflicto al fusionar con la rama main (HEAD, hola) [Sergio Gómez]
|\
| * 9c85275 2013-06-16 | Programa interactivo (main) [Sergio Gómez]
* |   9c6ac06 2013-06-16 | Merge commit 'c3e65d0' into hola [Sergio Gómez]
|\ \
| |/
| * c3e65d0 2013-06-16 | Añadido README.md [Sergio Gómez]
|/
* 9862f33 2013-06-16 | hola usa la classe HolaMundo [Sergio Gómez]
* 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
$ git reset --hard 9862f33
HEAD is now at 9862f33 hola usa la clase HolaMundo
```

I el nostre estat serà:

Bash

```
git hist --all
* 9862f33 2013-06-16 | hola usa la classe HolaMundo (HEAD, hola) [Sergio Gómez]
* 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
| * 9c85275 2013-06-16 | Programa interactiu (main) [Sergio Gómez]
| * c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
|/
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801105553.png]]

Hem desfet tots els _merge_ i el nostre arbre està _"net"_. Anem a provar ara a fer un rebase. Continuem en la branca `hola` i executem el següent:

Bash

```
git rebase main
First, rewinding head to replay your work on top of it...
Applying: Afegida la classe HolaMundo
Applying: hola usa la classe HolaMundo
Using index info to reconstruct a base tree...
M   lib/hola.php
Falling back to patching base and 3-way merge...
Auto-merging lib/hola.php
CONFLICT (content): Merge conflict in lib/hola.php
error: Failed to merge in the changes.
Patch failed at 0002 hola usa la clase HolaMundo
The copy of the patch that failed is found in: .git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```

El conflicte, per descomptat, se segueix donant. Resolem guardant l'arxiu `hola.php` com en els casos anteriors:

PHP

```
<?php
// Autor: Sergio Gómez <sergio@uco.es>
require('HolaMundo.php');

print "Introdueix el teu nom:";
$nombre = trim(fgets(STDIN));
print new HolaMundo($nombre);
```

Afegim els canvis en _staging_ i en aquesta ocasió, i tal com ens indicava en el missatge anterior, no hem de fer `git commit` sinó continuar amb el _rebase_:

Bash

```
git add lib/hola.php
git status
rebase in progress; onto 269eaca
You are currently rebasing branch 'hola' on '269eaca'.
  (all conflicts fixed: run "git rebase --continue")

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    modified:   lib/hola.php
git rebase --continue
Applying: hola usa la classe HolaMundo
```

I ara veiem que el nostre arbre té un aspecte diferent, molt més net:

Bash

```
git hist --all
* 9862f33 2013-06-16 | hola usa la classe HolaMundo (HEAD -> hola) [Sergio Gómez]
* 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
* 9c85275 2013-06-16 | Programa interactiu (main) [Sergio Gómez]
* c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801105753.png]]

El que fa rebase és tornar a aplicar tots els canvis a la branca màster, des del seu node més recent. Això significa que es modifica l'ordre o la història de creació dels canvis. Per això rebase no s'ha d'usar si l'ordre és important o si la branca és compartida.

## Barrejant amb la branca main

Ja hem acabat d'implementar els canvis en la nostra branca secundària i és hora de portar els canvis a la branca principal. Usem `git merge` per a fer una fusió normal:

Bash

```
git checkout main
Switched to branch 'main'
git merge hola
Updating c3e65d0..491f1d2
Fast-forward
 lib/HolaMundo.php | 16 ++++++++++++++++
 lib/hola.php      |  4 +++-
 2 files changed, 19 insertions(+), 1 deletion(-)
 create mode 100644 lib/HolaMundo.php
 $ git hist --all
 * 9862f33 2013-06-16 | hola usa la classe HolaMundo (HEAD -> main, hola) [Sergio Gómez]
 * 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
 * 9c85275 2013-06-16 | Programa interactiu [Sergio Gómez]
 * c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
 * 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
 * 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
 * fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
 * 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
 * efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
 * e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

Veiem que indica que el tipus de fusió és _fast-forward_. Aquest tipus de fusió té el problema que no deixa rastre de la fusió, per això sol ser recomanable usar el paràmetre `--no-ff` perquè quedi constància sempre que s'ha fusionat una branca amb una altra.

Anem a tornar a provar ara sense fer _fast-forward_. Resetegem _main_ a l'estat _"Programa interactiu"_.

Bash

```
git reset --hard 9c85275
git hist --all
* 9862f33 2013-06-16 | hola usa la classe HolaMundo (HEAD -> hola) [Sergio Gómez]
* 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
* 9c85275 2013-06-16 | Programa interactiu (main) [Sergio Gómez]
* c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

Veiem que estem com al final de la secció anterior, així que ara barregem:

Bash

```
git merge -m "Aplicant els canvis de la branca hola" --no-ff hola
Merge made by the 'recursive' strategy.
 lib/HolaMundo.php | 16 ++++++++++++++++
 lib/hola.php      |  4 +++-
 2 files changed, 19 insertions(+), 1 deletion(-)
 create mode 100644 lib/HolaMundo.php
git hist --all
* 2eab8ca 2013-06-16 | Aplicant els canvis de la branca hola (HEAD -> main) [Sergio Gomez]
*\
| * 9862f33 2013-06-16 | hola usa la classe HolaMundo (hola) [Sergio Gómez]
| * 6932156 2013-06-16 | Afegida la classe HolaMundo [Sergio Gómez]
|/
* 9c85275 2013-06-16 | Programa interactiu (main) [Sergio Gómez]
* c3e65d0 2013-06-16 | Afegit README.md [Sergio Gómez]
* 81c6e93 2013-06-16 | Mogut hola.php a lib [Sergio Gómez]
* 96a39df 2013-06-16 | Afegit l'autor del programa i el seu email [Sergio Gómez]
* fd4da94 2013-06-16 | S'afegeix un comentari al canvi del valor per defecte (tag: v1) [Sergio Gómez]
* 3283e0d 2013-06-16 | S'afegeix un paràmetre per defecte (tag: v1-beta) [Sergio Gómez]
* efc252e 2013-06-16 | Parametrització del programa [Sergio Gómez]
* e19f2c1 2013-06-16 | Creació del projecte [Sergio Gómez]
```

![[Pasted image 20250801105934.png]]

En la següent imatge es pot veure la diferència: