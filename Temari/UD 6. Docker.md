
# Contingut de la Presentació Docker

## Secció 1: Introducció i Conceptes Clau (Diapositives 1-4)

### 1. Títol: Desplegament i Administració de Contenidors

|Element|Contingut|
|---|---|
|**Títol Principal**|**Desplegament i Administració de Contenidors**|
|**Subtítol**|Iniciació a Docker|
|**Imatge Suggerida**|Logo de **Docker (la balena 🐳)** gran i atractiu.|

---

### 2. Què és Docker? 🐳

- Programari lliure (Docker Inc., 2013).
    
- Permet crear **entorns independents i aïllats** per a les teves aplicacions.
    
- Aquests entorns s'anomenen **contenidors**.
    
- L'aplicació s'executa **exactament igual a qualsevol màquina**.
    
- **Objectiu:** Eliminar problemes de dependències o compilació ("A la meva màquina funciona!").
    

|Imatge Suggerida|Descripció|
|---|---|
|**Diagrama senzill**|Un contenidor amb una icona d'aplicació dins i la frase: "Funciona a qualsevol lloc".|

---

### 3. Contenidors vs. Virtualització

| Característica       | Contenidors (Docker)                    | Virtualització (VMs)                          |
| -------------------- | --------------------------------------- | --------------------------------------------- |
| **Pes / Velocitat**  | **Lleugers**, arranquen en segons.      | **Pesades**, arrenquen en minuts.             |
| **Sistema Operatiu** | **Comparteixen el Kernel** del SO Host. | Cada VM té el seu propi **SO Guest complet**. |
| **Aïllament**        | A nivell de procés.                     | Aïllament total (de hardware).                |

|Imatge Suggerida|Descripció|
|---|---|
|**Diagrama d'Arquitectura**|Mostrar les capes: Contenidors (SO Host ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Docker Engine ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Contenidors) vs. VMs (SO Host ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Hypervisor ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) SO Guest ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Apps).|

---

### 4. Conceptes Essencials

|Concepte|Definició|
|---|---|
|**Imatge (Image)**|Plantilla immutable que conté tot el necessari per executar una aplicació. **La recepta**.|
|**Contenidor (Container)**|Instància en execució d'una Imatge. **El plat cuinat**.|
|**Docker Hub / Registry**|Repositori públic o privat on s'emmagatzemen i es comparteixen Imatges. **El magatzem**.|
|**Docker Engine**|El servei o motor que construeix, executa i gestiona els contenidors a la màquina Host.|

|Imatge Suggerida|Descripció|
|---|---|
|**Icones Clau**|Imatge (Iceberg), Contenidor (Caixa de transport), Registry (Núvol), Engine (Engranatge).|

---

---

## Secció 2: Gestió i Comandes Bàsiques (Diapositives 5-10)

### 5. Instal·lació i Verificació

- Docker és compatible amb Linux, Windows i Mac (**Docker Desktop**).
    
- Seguiu la documentació oficial per a la instal·lació.
    
- **Verificació:** Comprova que s'ha instal·lat correctament.
    
    - `docker --version`
        
- **Prova ràpida (Hello World):**
    
    - `docker run hello-world`
        

|Imatge Suggerida|Descripció|
|---|---|
|**Terminal**|Captura de pantalla de la sortida d'èxit del `docker run hello-world`.|

---

### 6. Comandes: Llençar Contenidors

|Acció|Comanda|Explicació|
|---|---|---|
|**Descarregar Imatge**|`docker pull [IMATGE]`|Baixa la Imatge d'un Registry (ex: Docker Hub).|
|**Executar (Run)**|`docker run [IMATGE]`|Crea un contenidor nou i l'inicia.|
|**Segon Plà (Detached)**|`docker run -d [IMATGE]`|Executa el contenidor en _background_.|
|**Publicar Port**|`docker run -p HOST:CONTAINER [IMATGE]`|Fa accessible l'app des de la màquina Host.|
|**Exemple**|`docker run -d -p 8080:80 nginx`|Llança un servidor web Nginx al port 8080 de la màquina.|

|Imatge Suggerida|Descripció|
|---|---|
|**Fletxa de flux**|Fletxa des del núvol (`pull`) a una icona d'execució (`run`).|

---

### 7. Comandes: Estat dels Contenidors

- Serveixen per veure i controlar els contenidors en marxa.
    

|Acció|Comanda|Funció|
|---|---|---|
|**Llistar Actius**|`docker ps`|Mostra només els contenidors en execució.|
|**Llistar Tots**|`docker ps -a`|Mostra tots (actius i parats).|
|**Aturar Suau**|`docker stop [ID/NOM]`|Envia un senyal de _stop_ (temps per tancar-se).|
|**Aturar Forçat**|`docker kill [ID/NOM]`|Mata el procés immediatament.|
|**Inspeccionar**|`docker inspect [ID/NOM]`|Mostra informació detallada (JSON) del contenidor.|

|Imatge Suggerida|Descripció|
|---|---|
|**Terminal**|Una captura de la sortida del `docker ps -a` amb l'estat dels contenidors.|

---

### 8. Comandes: Neteja i Imatges

- És important netejar les Imatges i Contenidors que ja no s'utilitzen.
    

|Objecte|Acció|Comanda|
|---|---|---|
|**Contenidor**|**Eliminar** (si està parat)|`docker rm [ID/NOM]`|
|**Contenidor**|**Eliminar Forçat** (si està actiu)|`docker rm -f [ID/NOM]`|
|**Imatges**|**Llistar Imatges**|`docker images`|
|**Imatges**|**Eliminar Imatge**|`docker rmi [IMATGE]`|
|**Accés Intern**|**Executar comanda dins**|`docker exec -it [ID] bash`|
|**Logs**|**Veure sortida**|`docker logs [ID/NOM]`|

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de Paperera**|Amb les comandes de `rm` i `rmi` al costat.|

---

### 9. Networking: Comunicació

- Per defecte, els contenidors estan aïllats.
    
- **Xarxes Virtuals** permeten la comunicació entre ells.
    

|Concepte|Explicació|
|---|---|
|**Bridge Network**|La xarxa per defecte. Permet la comunicació entre contenidors i amb l'exterior.|
|**Publicació de Ports**|Utilitzem l'opció **`-p`** per mapar un port del Host a un port del Contenidor. (Ex: `-p 80:80`).|
|**DNS Intern**|Dins de la mateixa xarxa, els contenidors es poden trobar pel seu nom (si es fan servir _Compose_ o xarxes definides).|

|Imatge Suggerida|Descripció|
|---|---|
|**Diagrama de Xarxa**|Dos contenidors comunicant-se a través d'una xarxa _bridge_. Una fletxa surt a l'Host via un port.|

---

### 10. Storage: Dades Persistents

- **ATENCIÓ:** Les dades creades dins del contenidor es **perden** si aquest s'elimina.
    
- Necessitem persistència per a bases de dades o fitxers d'usuari.
    

|Mètode|Característica|Ús Recomanat|
|---|---|---|
|**Volumes**|Emmagatzematge persistent i gestionat per Docker. Més eficient.|Bases de dades i dades crítiques.|
|**Bind Mounts**|Enllaça un directori **concret** de la màquina Host al contenidor.|Desenvolupament (per veure canvis de codi en temps real).|
|**Sintaxi**|**`-v host_path:container_path`** (per a Bind Mounts) o **`-v volum_nom:ruta`** (per a Volumes).||

|Imatge Suggerida|Descripció|
|---|---|
|**Flux de Dades**|Un diagrama que mostra un disc dur (Host) connectat a un contenidor de Base de Dades (Volum).|

---

---

## Secció 3: Construcció d'Imatges (Dockerfile) (Diapositives 11-19)

### 11. El Dockerfile: La Recepta 📝

- Fitxer de text anomenat exactament **`Dockerfile`** (sense extensió).
    
- Conté totes les **instruccions seqüencials** per construir la Imatge.
    
- Defineix l'entorn base, el codi, les dependències i el punt d'entrada.
    
- **Comanda de construcció (Build):**
    
    - `docker build -t [NOM_IMATGE]:[TAG] .` (El punt final indica el directori on es troba el Dockerfile).
        

|Imatge Suggerida|Descripció|
|---|---|
|**Exemple de `Dockerfile`**|Captura de pantalla d'un `Dockerfile` senzill: `FROM`, `COPY`, `CMD`.|

---

### 12. Instrucció 1: `FROM` (La Base)

- **`FROM [IMATGE_BASE]`**: És la primera instrucció, defineix la **imatge inicial** sobre la qual es construirà la nostra.
    
- Defineix el **Sistema Operatiu Base** i les eines preinstal·lades.
    
- **Exemples:**
    
    - `FROM ubuntu:latest`
        
    - `FROM node:18-alpine` (Imatge de Node sobre el petit SO Alpine)
        
- **Consell clau:** Triar la imatge **més petita** i específica possible (`-alpine` o `-slim`) per reduir la mida final del contenidor.
    

|Imatge Suggerida|Descripció|
|---|---|
|**Pila de capes**|Un gràfic que mostra la capa base (`FROM`) a sota de tot.|

---

### 13. Instrucció 2: `WORKDIR` (El Directori de Treball)

- **`WORKDIR /ruta/al/projecte`**: Estableix el directori de treball **principal** dins de la Imatge.
    
- Totes les instruccions següents (`RUN`, `CMD`, `COPY`) s'executaran des d'aquesta ruta.
    
- Si el directori no existeix, Docker el crea automàticament.
    
- **Simplifica rutes** i organitza els fitxers.
    
    - _Exemple:_ Si el `WORKDIR` és `/app`, un `COPY . .` copiarà els fitxers a `/app`.
        

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de Carpeta**|Amb una etiqueta que diu `/app` o `/usr/src/app`.|

---

### 14. Instrucció 3: `COPY` i `ADD` (Afegir Codi)

- Serveixen per transferir fitxers des del directori local (Host) al directori de la Imatge.
    

|Instrucció|Funció|Ús|
|---|---|---|
|**`COPY origen_host desti_imatge`**|**Copia** fitxers i directoris locals.|**Més recomanada** i usada per la seva claredat.|
|**`ADD origen desti`**|Similar a `COPY`, però també pot: * Desempaquetar fitxers **comprimits** (`.tar`). * Copiar fitxers des d'una **URL**.|Només quan es necessiten les funcions extra.|

|Imatge Suggerida|Descripció|
|---|---|
|**Fletxa de transferència**|Una fletxa que representa el moviment d'un fitxer del PC al contenidor.|

---

### 15. Instrucció 4: `RUN` (Instal·lar Dependències)

- **`RUN [COMANDA]`**: Executa una comanda **durant el procés de construcció** de la Imatge.
    
- S'utilitza per:
    
    - Actualitzar el SO: `RUN apt-get update`
        
    - Instal·lar paquets: `RUN apk add python3`
        
    - Instal·lar dependències del projecte: `RUN npm install`
        

|Exemple de Dockerfile|Explicació|
|---|---|
|`FROM ubuntu`|Iniciem des d'Ubuntu.|
|`RUN apt-get update && apt-get install -y git`|**Instal·lem Git** dins de la Imatge.|
|`RUN apt-get clean`|**Neteja** per reduir la mida de la Imatge.|

|Imatge Suggerida|Descripció|
|---|---|
|**Terminal de comandes**|Una icona de línia de comandes (`>`) o una barra de progrés d'instal·lació.|

---

### 16. Optimització 1: Capes (Layers)

- Cada instrucció del Dockerfile (`FROM`, `RUN`, `COPY`, etc.) crea una **capa** pròpia.
    
- Docker emmagatzema aquestes capes en **memòria cau (cache)**.
    
- Si una instrucció i els seus fitxers d'entrada no canvien, la capa es reutilitza (no es torna a construir), **accelerant el _build_**.
    

|Consell d'Optimització|Raó|
|---|---|
|**Agrupar `RUN`**|Agrupar comandes (`RUN apt-get update && apt-get install...`) en un sol `RUN` redueix el nombre de capes.|
|**Ordre correcte**|Posar les capes que **canvien menys** (dependències, instal·lacions) abans de les que **canvien molt** (el codi de l'aplicació).|

|Imatge Suggerida|Descripció|
|---|---|
|**Diagrama de Capes**|Un pastís o una pila de 3-4 caixes (capes) per representar el concepte.|

---

### 17. Instrucció 5: `EXPOSE` (Documentar Port)

- **`EXPOSE [PORT]`**: Simplement declara quin port utilitza l'aplicació dins del contenidor.
    
- És una **documentació interna** de la Imatge.
    
- **Important:** No obre el port a la màquina Host. Això només es fa amb l'opció `-p` al `docker run`.
    
    - _Exemple:_ `EXPOSE 3000`
        

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de Far o Rètol**|Un rètol d'indicació de port o un far il·luminant.|

---

### 18. Instrucció 6: `CMD` i `ENTRYPOINT` (Punt d'Inici)

- Defineixen el que s'executarà quan el contenidor s'iniciï.
    

|Instrucció|Funció|Sobre-escriptura|
|---|---|---|
|**`CMD` (Command)**|La comanda a executar per defecte.|Es pot sobreescriure fàcilment al `docker run`. **Més usat**.|
|**`ENTRYPOINT`**|Defineix el binari principal que s'executarà. Les comandes del `CMD` es passen com a arguments.|Més difícil de sobreescriure. Útil per a contenidors amb una única funció (ex: un _wrapper_).|
|**Exemple (`CMD`)**|`CMD ["npm", "start"]`|S'executarà `npm start` en iniciar el contenidor.|

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de Play/Start**|Un botó de _Play_ per indicar l'inici.|

---

### 19. Docker Registry: Compartir Imatges

- El **Registry** és el magatzem d'Imatges (públic o privat).
    

|Acció|Comanda|Objectiu|
|---|---|---|
|**Login**|`docker login`|Autenticar-se al Registry (ex: Docker Hub).|
|**Taggejar**|`docker tag [ID] [USER]/[NOM]:[TAG]`|Donar un nom i una etiqueta a la Imatge per pujar-la.|
|**Pujar (Push)**|`docker push [USER]/[NOM]:[TAG]`|Pujar la Imatge al teu repositori al Registry.|
|**Descarregar**|`docker pull [USER]/[NOM]:[TAG]`|Descarregar la Imatge en qualsevol altre lloc.|

|Imatge Suggerida|Descripció|
|---|---|
|**Flux de Dades**|Icona de núvol o magatzem amb fletxes d'entrada i sortida (_push/pull_).|

---

---

## Secció 4: Aplicacions Multi-Contenidor i Orquestració (Diapositives 20-22)

### 20. Docker Compose: Gestió Complexa

- Eina per gestionar **aplicacions multi-contenidor** (Frontend, Backend, DB, Cache...).
    
- Utilitza un fitxer de configuració anomenat **`docker-compose.yml`** (format YAML).
    
- Permet definir tots els serveis, xarxes i volums en un sol lloc.
    
- **Comandes senzilles:**
    
    - `docker compose up` ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Crea i inicia l'entorn sencer.
        
    - `docker compose down` ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAACWCAYAAABkW7XSAAAAAXNSR0IArs4c6QAABGJJREFUeF7t1AEJAAAMAsHZv/RyPNwSyDncOQIECEQEFskpJgECBM5geQICBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAAYPlBwgQyAgYrExVghIgYLD8AAECGQGDlalKUAIEDJYfIEAgI2CwMlUJSoCAwfIDBAhkBAxWpipBCRAwWH6AAIGMgMHKVCUoAQIGyw8QIJARMFiZqgQlQMBg+QECBDICBitTlaAECBgsP0CAQEbAYGWqEpQAgQdWMQCX4yW9owAAAABJRU5ErkJggg==) Atura i elimina l'entorn sencer.
        

|Imatge Suggerida|Descripció|
|---|---|
|**Diagrama de Composició**|Un diagrama que mostra el fitxer `.yml` controlant tres contenidors interconnectats (Web, App, DB).|

---

### 21. Introducció a l'Orquestració

- **Necessitat:** Gestionar el desplegament de **milions** de contenidors en un **clúster** de màquines (Nodes).
    
- **Funció:** Automatitza l'escalat, el balanç de càrrega, la recuperació davant fallades i l'administració de recursos.
    
- **No és necessari per a projectes petits.**
    
- **Eines Principals:**
    
    - **Docker Swarm:** Eina d'orquestració integrada a Docker.
        
    - **Kubernetes (K8s):** El standard de la indústria, més potent i complex.
        

|Imatge Suggerida|Descripció|
|---|---|
|**Director d'Orquestra**|Un "director" controlant molts contenidors.|

---

### 22. Kubernetes (K8s) Breu

- Plataforma **líder** d'orquestració de contenidors.
    
- Permet gestionar grans càrregues de treball en un clúster.
    
- **Conceptes clau:**
    
    - **Node:** Màquina física o virtual que forma part del clúster.
        
    - **Pod:** La unitat de desplegament més petita (un o més contenidors que comparteixen recursos).
        
    - **Service:** Mètode estable per accedir a un conjunt de Pods (balanç de càrrega).
        

|Imatge Suggerida|Descripció|
|---|---|
|**Logo de Kubernetes**|El timó de Kubernetes.|

---

---

## Secció 5: Pràctica i Final (Diapositives 23-26)

### 23. Exercici Pràctic: Construcció

- **Objectiu:** Crear una Imatge pròpia i llançar-la.
    

1. Creeu un `Dockerfile` al vostre projecte.
    
2. Definiu el `FROM`, `COPY` i `CMD`.
    
3. **Construïu la Imatge:** `docker build -t meuapp:v1 .`
    
4. **Executeu el contenidor:** `docker run -d -p 8000:8000 meuapp:v1`
    

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de _Challenge_**|Un _checklist_ a mig fer o una icona de _coding_.|

---

### 24. Exercici Pràctic: Compose

- **Objectiu:** Desplegar una aplicació amb Base de Dades.
    

1. Creeu el fitxer **`docker-compose.yml`** amb dos serveis (ex: Web i Redis).
    
2. **Llançar l'entorn:** `docker compose up -d`
    
3. **Verificar** els contenidors: `docker ps`
    
4. **Aturar i eliminar** l'entorn: `docker compose down`
    

|Imatge Suggerida|Descripció|
|---|---|
|**Terminal**|Captura de la sortida del `docker compose up` amb els serveis iniciant-se.|

---

### 25. Consells Clau per al Desenvolupament

|Consell|Per què?|
|---|---|
|**Utilitzar `.dockerignore`**|Evita que fitxers innecessaris (ex: `.git`, `node_modules`) es copiïn a la Imatge, reduint la mida.|
|**Variables d'Entorn**|**Mai posar dades sensibles** (passwords, _API keys_) al Dockerfile. Utilitzar l'opció `-e` o secrets.|
|**Cache (Build)**|Posar les instruccions que **canvien menys** al principi del Dockerfile.|
|**Imatge Base Petita**|Utilitzar bases com `alpine` o `slim` per a contenidors més lleugers i ràpids.|

|Imatge Suggerida|Descripció|
|---|---|
|**Icona de "Tip" o "Bombilla"**|Per destacar els consells.|

---

### 26. Gràcies! / Preguntes

- **Conclusió:** Docker és una eina clau per a l'eficiència en el desplegament de software.
    
- El domini del **Dockerfile** és el pas més important per al control total.
    
- Us animem a seguir explorant la documentació oficial.
    

|Imatge Suggerida|Descripció|
|---|---|
|**Final**|Logo de Docker i un signe d'interrogació gran.|

---