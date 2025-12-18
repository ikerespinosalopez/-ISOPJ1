# 🚀 Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers

# 💾 Sistemes de fitxers i particions

Un sistema de fitxers és l'estructura lògica que utilitza un sistema operatiu per organitzar, emmagatzemar i recuperar dades en un disc dur o memòria USB. Sense ell, el disc seria només un conjunt de dades sense sentit.

A continuació, desglosem els tipus més comuns, les seves limitacions i com identificar-los.

## 1. Tipus principals segons el Sistema Operatiu

Cada entorn té els seus formats predilectes, optimitzats per rendiment, seguretat o compatibilitat:

* **Entorn Windows:**
    * **NTFS (New Technology File System):** És l'estàndard actual per als discs durs interns de Windows. Suporta permisos de seguretat avançats i fitxers grans.
    * **FAT32:** Un format antic però molt compatible (funciona en consoles, ràdios de cotxe, Mac, Linux, etc.).
    * **exFAT:** L'evolució del FAT32. Elimina la limitació de mida de fitxer però manté la compatibilitat. 

* **Entorn Linux:**
    * **ext4:** L'estàndard en Linux. És molt estable i redueix la fragmentació del disc, evitant que el sistema es ralentitzi amb el temps.
    * **XFS:** Sovint utilitzat en servidors perquè gestiona molt bé fitxers extremadament grans i volums de dades massius.
 
Per a veure el sistema de fitxers que tenim muntat i el tipus podem fer servir la comanda `df -Th`:

<img width="803" height="250" alt="image" src="https://github.com/user-attachments/assets/5da20936-6585-4d0f-aacb-efed6d4f92e2" />

## Mida sector 
És la unitat mínima física on se guarden les dades en un disc. Per defecte la mida són 512 bytes i no es pot modificar. A la imatge podem veure com se'ns indica la mida del sector:

<img width="784" height="485" alt="image" src="https://github.com/user-attachments/assets/488e91cf-9b35-4619-9790-72821b9c2cd7" />

## Mida block 
També es pot dir clúster, la seva mida és la unitat mínima lògica on es guarden les dades a nivell de sistema operatiu. Per defecte són 4096 bytes (8 sectors) i aquesta mida sí que la podem modificar quan es formateja la partició. Cada partició del disc pot tenir una mida de bloc i un sistema de fitxers diferent.

La comanda `tune2fs -l` s'utilitza per llistar o mostrar tota la informació detallada del superbloc d'un sistema de fitxers de tipus ext2, ext3 o ext4 a Linux. És una eina de diagnòstic i inspecció que et permet veure l'estat i la configuració interna de la partició. Per utilitzar aquesta ordre, has d'especificar el dispositiu (la partició) que vols inspeccionar. Per exemple: `tune2fs -l /dev/sda2`:

<img width="790" height="119" alt="image" src="https://github.com/user-attachments/assets/10c68533-189d-41a3-a588-120d23bec548" />

En la següent imatge podem veure com creem un fitxer de text amb contingut i a continuació comprovem la seva mida i la mida que ocupa al SO per la mida del bloc:

<img width="802" height="183" alt="image" src="https://github.com/user-attachments/assets/f860d2c5-0ead-4d6c-ab89-9dc99e329575" />

  
## 🧩 Fragmentació interna 
La fragmentació interna es produeix quan l'espai assignat a un fitxer és més gran que la mida real d'aquest fitxer, resultant en un malbaratament d'espai al disc.
  
## 🧩 Fragmentació externa 
És quan un arxiu no està guardat en blocs consecutius de la memòria i els seus accessos són més lents, i, per tant, baixa el rendiment. En Windows tenim una eina anomenada desfragmentador de discos que ens permet solucionar aquest problema, a Linux per norma general no fa falta, ja que el sistema de fitxers ext4 està més optimitzat. 
De totes maneres, si volem comprovar-ho podem fer servir la comanda `e4defrag`, amb els paràmetres -c fem un diagnòstic i l'indiquem la nostra carpeta a comprovar: 

<img width="933" height="565" alt="image" src="https://github.com/user-attachments/assets/2e614592-aee5-47e3-8abc-990f3dac8e30" />
  
## 💾 Tipus de formateig
* **Baix nivell:** Esborra tot, arixus, sistema de fitxers i intenta reparar sectors defectuosos, però es necessiten programes especifics, no es pot fer a travès del SO.
* **Mig nivell:** Formateig lent, no borra arxius però si es troba sectors dfectuosos els marca, però no els repara.
* **Alt nivell:** No es borren els arxius, només s'esborra el sistema de fitxers. Si troba sectors defectuosos els ignora totalment. 
    
## Gestio de particions
Una partició és un tros físic del disc dur i un volum és una capa d'abstracció que es posa damunt de les particions i/o discos. Amb l'eina GParted podem gestionar particions però no podem modificar la mida del bloc.

1. Preparació de l'equip: Afegim un disc de 10GB a la nostra màquina virtual Ubuntu:

<img width="862" height="535" alt="image" src="https://github.com/user-attachments/assets/a698f0b7-a1b7-4d38-8b06-e6aa9fdcebe9" />

2. Podem comprovar que el sistema detecta el nou disc amb `fdisk -l`:

<img width="819" height="298" alt="image" src="https://github.com/user-attachments/assets/7af12abd-f32e-49ca-b0e3-bba73c82b255" />

### GPARTED
Instal·lem el GParted amb la comanda `sudo apt install gparted`. Un cop fet l'iniciem i podrem veure el disc que hem afegit prèviament.

<img width="1107" height="420" alt="image" src="https://github.com/user-attachments/assets/515b2cc9-1b74-4bbd-bf11-09f5b93a6d10" />

### Comandes
Ara veurem les comandes per a dur a terme un procés d'inicialització i formatació de dues particions de disc diferents (/dev/sdb1 i /dev/sdb2) amb dos sistemes de fitxers completament diferents (Linux i Windows). Aquest procés prepara les particions per emmagatzemar dades d'una manera organitzada.

Primer crearem un sistema de fitxers ext4, formatant la partició i definint la mida del bloc a 2048 bytes per a evitar una possible fragmentació interna, optimitzant l'espai del disc tenint en compte que l'utilitzarem per a guardar molts fitxers petits. Ho farem amb la comanda `mkfs.ext4 -b 2048 /dev/sdb1`:

<img width="807" height="296" alt="image" src="https://github.com/user-attachments/assets/4a22fd1c-7a8f-4ff4-af92-043dd7ba202e" />

A continuació formatem la segona partició amb el sistema de fitxers de Windows NTFS amb la comanda `mkfs.ntfs /dev/sdb2`:

<img width="703" height="138" alt="image" src="https://github.com/user-attachments/assets/63bfee4f-9b74-4ff7-b769-c73e532d5b41" />

A la sgüent imatge podem veure com comprovar de dues maneres diferents la creació i formatació de les dues particions. Amb el terminal, fem servir la comanda `tune2fs - l /dev/sdb1 | grep Block` per a veure tota la informacióp del superbloc, on ens confirmen la mida del bloc i el nombre total de blocs. D'altra banda tenim l'eina GParted, on podem veure gràficament l'estructura, el tipus de sistema de fitxers i la mida.

<img width="771" height="445" alt="image" src="https://github.com/user-attachments/assets/b4a41272-e767-4659-8091-8a4efc4b7b90" />

El Sistema Operatiu Linux ofereix dues maneres principals de muntar particions, depenent de si el muntatge ha de sobreviure a un reinici o no.

| Característica | ⏱️ Muntatge Temporal (Amb `mount`) | ♾️ Muntatge Persistent (Amb `/etc/fstab`) |
| :--- | :--- | :--- |
| **Comanda** | S'utilitza l'ordre `mount` directament. | Es requereix editar el fitxer `/etc/fstab`. |
| **Durada** | Només dura fins que s'executa la comanda `umount` o el sistema es **reinicia**. | El muntatge es realitza **automàticament** cada vegada que el sistema operatiu s'inicia. |
| **Fitxer de Config.** | Cap fitxer modificat. L'acció es fa a l'instant. | S'afegeix una línia al fitxer **/etc/fstab** especificant la partició, el punt de muntatge i les opcions. |
| **Ús Típic** | Dispositius extraïbles (USB), CDs/DVDs, o fer proves ràpides a una partició nova. | Particions internes permanents (com `/home`, `swap`, o discs de dades secundaris). |

* Mode temporal
<img width="810" height="326" alt="image" src="https://github.com/user-attachments/assets/ef951cd5-da97-4b53-b7a9-7ae708eff851" />
<img width="806" height="374" alt="image" src="https://github.com/user-attachments/assets/78b11076-4645-4fa1-ba86-87f72803d544" />
<img width="804" height="261" alt="image" src="https://github.com/user-attachments/assets/826347b9-f4b4-478f-86ae-0daf385f2e04" />

* Mode definitiu
<img width="806" height="428" alt="image" src="https://github.com/user-attachments/assets/ad4372c2-f4f8-455c-9703-23a89a4850d7" />
<img width="607" height="140" alt="image" src="https://github.com/user-attachments/assets/79b5ab8e-a684-45cc-a825-c5ab37542140" />


## ⚙️ Gestió de processos
Un **procés** es defineix com la instància dinàmica resultant d'executar un codi o programa. És l'element bàsic de treball que el sistema operatiu ha de gestionar, planificar i monitoritzar constantment per garantir el funcionament fluid del sistema.

***

Per a la seva gestió eficient, el Sistema Operatiu (SO) atorga a cada procés dues identificacions crucials:

* **Identificador de Procés (PID):** Una matrícula numèrica **exclusiva** i temporal assignada al procés durant tota la seva vida útil.
* **Usuari vinculat:** El procés està lligat a l'usuari que el va iniciar, del qual **hereta automàticament tots els permisos i restriccions de seguretat**.

Durant la seva existència, un procés canvia constantment d'estat (per exemple, de **Actiu** a **En Espera** de recursos, o a **Zombi** després de finalitzar, a l'espera de ser netejat), sent el **SO l'àrbitre principal** (scheduler), encarregat d'administrar-ne la planificació i l'ús del temps de la CPU (CPU scheduling).

***

Per interactuar amb aquests processos des de la línia de comandes, disposem d'un conjunt d'utilitats classificades segons la seva finalitat:

| Acció | Comandes Essencials | Detalls i Finalitat |
| :--- | :--- | :--- |
| **Visualització** | `ps`, `top`, `htop` | Permeten monitoritzar l'estat actual, el consum de memòria i CPU, i la llista completa de tasques actives. |
| **Finalització** | `kill`, `pkill` | S'utilitzen per aturar processos específics (usant el PID) o grups de processos (usant el nom o l'usuari). |
| **Priorització** | `nice`, `renice` | Ajusten la prioritat d'accés a la CPU, permetent que uns processos tinguin més recursos que d'altres (valor "niceness"). |
| **Gestió de Serveis** | `systemctl`, `service` | Controlen els daemons (programes que s'executen en segon pla), com iniciar, aturar o reiniciar serveis del sistema. |

* **Permisos:** Un procés només pot accedir als recursos que li permet l'usuari sota el qual s'executa.
* **Tipus d'Execució:** Un procés pot funcionar com a part d'una sessió interactiva (procés de *foreground*) o com un servei de fons (*daemon*).

Aquests conceptes són la base per a una administració eficaç del sistema.


## 🔑 Gestió d'usuaris i grups i permisos
La **gestió d'usuaris, grups i permisos** és l'estructura fonamental que garanteix la seguretat i el control d'accés en els sistemes de tipus Linux. Aquest sistema defineix qui pot interactuar amb els recursos i de quina manera.

Els **usuaris** són les identitats individuals que tenen accés al sistema. Per administrar-los de manera eficient, s'organitzen en **grups**. Els grups faciliten l'aplicació de regles col·lectives a un conjunt de comptes.

La clau d'aquesta administració resideix en els **permisos**, que són les regles que defineixen si un usuari o un grup concret pot llegir, escriure o executar un fitxer o directori. Aquest control estricte és essencial per protegir la integritat i la confidencialitat de les dades del sistema.

Existeix una eina alternativa per a poder gestionar gràficament els usuaris i grups, tot i que no es pot aprofundir tant com amb les comandes i fitxers que veurem més endavant.
La podem instal·lar amb la comanda `sudo apt install gnome-system-tools`, i un cop oberta podrem veure un llistat dels usuaris, on podem afegir i suprimir-los, una secció per a la gestió dels grups i dins de cada usuari veurem el nom, el tipus de compte i la contrassenya.

<img width="806" height="457" alt="image" src="https://github.com/user-attachments/assets/38ab2536-8683-4ffd-90b1-9090856667a6" />

### Fitxers implicats
A continuació veurem una sèrie de fitxers que tenen una alta importància a l'hora de gestionar els usuaris, grups i permisos. 
* Comencem amb el fitxer **/etc/passwd**, que conté tots els usuaris del sistema. Veiem a la imatge que tenim seleccionat el nostre usuari i se'ns indiquen una sèrie de paràmetres, en ordre: nom d'usuari > contrasenya > UID > GID > GECOS > Directori personal > Intèrpret d'ordres:

<img width="918" height="810" alt="image" src="https://github.com/user-attachments/assets/acd4b78c-2ada-4740-90dd-0a7ba15a9f4f" />

* Seguim amb un altre fitxer de gran valor, és el **/etc/group**, on podem trobar tots els grups del sistema, juntament amb els usuaris que formen part del grup.

<img width="922" height="813" alt="image" src="https://github.com/user-attachments/assets/6554b7b7-806e-44f2-b20f-1e140bbf6aae" />

* A continnuació tenim el fitxer **/etc/shadow**, aqui trobem per a cada usuari el seu password encriptat i al final la caducitat de les contrasenyes.

<img width="915" height="796" alt="image" src="https://github.com/user-attachments/assets/f8e95762-2c61-449d-bc0e-c7465f7d3825" />

* Per últim tenim **/etc/gshadow** que conté passwords de grups i permet veure els usuaris que formen part del grup, la diferència amb l'arxiu /etc/group és que aqui es l'únic lloc on es pot veure l'usuari administrador del grup, que només pot haver un.

<img width="919" height="817" alt="image" src="https://github.com/user-attachments/assets/461443fe-6be7-411a-9aa4-7aa10d1c9b6b" />

### Comandes bàsiques

Les comandes de gestió d'usuaris són eines essencials per a l'administrador del sistema. Permeten controlar qui té accés al sistema i quins permisos bàsics se'ls assignen. A continuació veurem una sèrie d'ordres bàsiques per a la gestió.


Primer tenim la comanda `adduser [usuari]`, que crea un nou compte d'usuari de manera senzilla i interactiva, establint automàticament el seu directori personal i assignant la contrasenya.

<img width="883" height="660" alt="image" src="https://github.com/user-attachments/assets/1427e024-2afb-4aa8-9d6f-8cdce63d6990" />

En un principi no les veurem, però si iniciem sessió amb l'usuari nou podrem veure que ens apareixen les seves carpetes:

<img width="920" height="343" alt="image" src="https://github.com/user-attachments/assets/b7e64456-d5c8-41f7-b67c-bc0d1ff674a9" />


També tenim la comanda `useradd [usuari]`. Afegeix un nou compte d'usuari, creant la seva entrada a **/etc/passwd** i el seu directori personal. Amb la comanda `passwd [usuari]` establim la seva contrasenya:

<img width="926" height="745" alt="image" src="https://github.com/user-attachments/assets/1b2d6871-96fa-4a17-985f-e967ed5d7b94" />

Amb la comanda ` adduser [usuari] [grup]` podem afegir usuaris a un grup, i amb la comanda `deluser [usuari] [grup]` l'elimine. d'aquest. Podem veure com segons el grup al que pertanyen o deixen de pertànyer els usuaris tindrem o no permisos per realitzar certes accions com fer servir `sudo`.

<img width="929" height="880" alt="image" src="https://github.com/user-attachments/assets/ffbb3cd8-137c-43ca-bc48-a49521c998ba" />

Quan esborrem un usuari amb la comanda `deluser [usuari]` podem veure que no s'esborren les seves carpetes:

<img width="912" height="462" alt="image" src="https://github.com/user-attachments/assets/f9d523f6-2708-443d-81d7-c08085d5d4d8" />

En aquesta imatge veiem el procés de **bloqueig i desbloqueig temporal** d'un compte d'usuari (`gina`) mitjançant la modificació del seu registre al fitxer de contrasenyes xifrades (`/etc/shadow`).

1. Estat Inicial

* **Comanda:** `cat /etc/shadow | grep gina`
* **Observació:** L'entrada de l'usuari `gina` comença amb el *hash* normal de la contrasenya (`$`). Això indica que el compte està **desbloquejat**.

2. Bloqueig del Compte

* **Comanda:** `usermod -L gina`
* **Acció:** L'opció `-L` (Lock) de `usermod` bloqueja el compte.
* **Efecte al Fitxer:** Després de la comanda, el *hash* de la contrasenya a `/etc/shadow` és prefixat amb un **signe d'exclamació (`!`)** (`gina:!$y$j9T...`). La presència d'aquest caràcter impedeix qualsevol intent d'inici de sessió amb contrasenya.

3. Desbloqueig del Compte

* **Comanda:** `usermod -U gina`
* **Acció:** L'opció `-U` (Unlock) de `usermod` desbloqueja el compte.
* **Efecte al Fitxer:** El signe d'exclamació (`!`) és **eliminat** del registre de la contrasenya, tornant el compte a l'estat **desbloquejat** i permetent a l'usuari `gina` iniciar sessió de nou.

<img width="929" height="332" alt="image" src="https://github.com/user-attachments/assets/40d75fde-ba97-4db9-a705-02876333c0ac" />


Amb la comanda `groupmod -n` modifiquem el nom del grup i amb la comanda `groupdel` l'eliminem:
<img width="702" height="198" alt="image" src="https://github.com/user-attachments/assets/94ab1778-52b1-4f92-b6e5-c0d8b6d6fa08" />


Aquí podem veure tres maneres d'afegir un usuari a un grup: 
* Amb la comanda `adduser [usuari] [grup]`.
* Amb la comanda `gpasswd -a [usuari] [grup]`.
* Amb la comanda `usermod -a -G [grup] [usuari]`.

- Amb la comanda `gpasswd -A [usuari] [grup]` afegim a un usuari com a administrador del grup. 
A continuació comprovem que els quatre hagin funcionat correctament mirant l'arxiu /etc/group i filtrant pel nom del grup.
   
<img width="916" height="342" alt="image" src="https://github.com/user-attachments/assets/6dc79795-49f6-4b05-be56-c220d5094b6f" />

Si fem servir la comanda `usermod`amb el paràmetre `-g`  es modifica el grup principal d'un usuari però no s'afegeix al grup.

<img width="713" height="311" alt="image" src="https://github.com/user-attachments/assets/42ed80ed-6783-41a9-8fbb-37fe9bf6d49d" />

Primer comprovem quins han sigut els últims 4 usuaris creats i a continuació creem un nou grup i li canviem el nom:
<img width="751" height="225" alt="image" src="https://github.com/user-attachments/assets/ff2604db-c17c-4e05-90b8-bab5d6e5321b" />

Aquesta imatge mostra una demostració completa de **com afegir i eliminar usuaris d'un grup** (`parchis`) utilitzant diferents comandes disponibles a Linux.

### 1. Afegint Membres (3 Mètodes Diferents)

Es van afegir tres usuaris al grup `parchis`, demostrant diferents sintaxis:

| Usuari | Comanda Utilitzada | Funció |
| :--- | :--- | :--- |
| **roig** | `gpasswd -a roig parchis` | Utilitza `gpasswd` (gestió d'administració de grups) amb l'opció `-a` (add). |
| **verd** | `usermod -a -G parchis verd` | Utilitza `usermod` (modificació d'usuari) amb l'opció `-a -G` (append to group). |
| **groc** | `adduser groc parchis` | Utilitza la utilitat amigable `adduser` (opció senzilla). |
| **Verificació** | `cat /etc/group | grep parchis` | **Resultat:** Confirma que el grup conté: `roig,verd,groc`. |

### 2. Eliminant Membres (2 Mètodes Diferents)

Posteriorment, es van eliminar dos usuaris amb dos mètodes diferents:

| Usuari | Comanda Utilitzada | Funció |
| :--- | :--- | :--- |
| **roig** | `gpasswd -d roig parchis` | Ús de `gpasswd` amb l'opció `-d` (delete). |
| **verd** | `deluser verd parchis` | Utilitza la utilitat amigable `deluser` per suprimir l'usuari del grup. |

**Verificació Final:** La darrera comprovació (`cat /etc/group | grep parchis`) mostra que només queda l'usuari **`groc`** al grup `parchis`.

<img width="766" height="327" alt="image" src="https://github.com/user-attachments/assets/0987394c-b4db-4cb5-97dc-2350d39be1be" />

Amb aquesta comanda es modifica el grup principal de l'usuari. Un usuari nomé.s te un grup principal, però pot formar part de molts grups i el grup principal es pot establir de manera fixa (amb questa comanda que hem fet) o temporal.

<img width="789" height="152" alt="image" src="https://github.com/user-attachments/assets/b49fb1e6-38c5-49c8-8241-0d7fb1e20771" />

Sempre es pot eliminar un grup i als usuaris no els hi passa res, menys quan aquest és el grup principal de l'usuari, que no es pot esborrar:

<img width="729" height="83" alt="image" src="https://github.com/user-attachments/assets/cdc79ebc-1ac7-44b8-8b4a-1858c3068d97" />


### Personalitzacio de les comandes adduser i useradd

Aquesta imatge mostra com podem modificar el directori **/etc/skel** per establir una configuració per defecte per a tots els futurs usuaris del sistema.

1. Inspecció inicial

* **Acció:** L'usuari navega a `/etc/skel` i llista els fitxers existents (`.bashrc`, `.profile`, etc.).
* **Funció de `/etc/skel`:** Aquest directori actua com a **plantilla (skeleton)**. Quan es crea un nou usuari, tot el que conté `/etc/skel` es copia automàticament al nou directori personal de l'usuari.

2. Afegim els elements personalitzats

Es creen dos nous elements:

* **Comanda:** `mkdir prova`
* **Acció:** Es crea un nou subdirectori anomenat **`prova`**.
* **Comanda:** `touch hola`
* **Acció:** Es crea un fitxer buit anomenat **`hola`**.

3. Conseqüència de la modificació

* **Resultat:** Els elements `prova` i `hola` són ara part de la plantilla.

**En resum:** Qualsevol nou usuari que es creï a partir d'aquest moment tindrà automàticament el directori **`~/prova`** i el fitxer **`~/hola`** al seu directori personal.

<img width="704" height="490" alt="image" src="https://github.com/user-attachments/assets/48e5d3ed-f4fd-4063-a7df-57ec47fafa10" />

Modificant aquest arxiu també podem fer que el ID comenci per 3000:

<img width="458" height="175" alt="image" src="https://github.com/user-attachments/assets/fa40a4b8-b91a-46a8-9bdf-665e557bed1d" />

O que el /home estigui en altre lloc:

<img width="707" height="306" alt="image" src="https://github.com/user-attachments/assets/6ed68c61-cef2-49ec-b559-d5ba1978dfb4" />

També podem canviar paràmetres de la contraasenya:

<img width="822" height="202" alt="image" src="https://github.com/user-attachments/assets/a9066e1e-124b-4518-89e9-43416b5973fd" />

Ara comprovem que els canvis del fitxer han funcionat i comprovem la caducitat de les contrasenyes:

<img width="854" height="488" alt="image" src="https://github.com/user-attachments/assets/1d0f9093-9b94-4076-b1c1-91c0cd0df307" />

En l'arxiu `/etc/default/useradd` podem modificar paràmetres de la comanda `useradd` com la shell per defecte:

<img width="857" height="251" alt="image" src="https://github.com/user-attachments/assets/e27f5f0b-46d2-47a2-91c5-a32ca8bee7f2" />

Fem les comprovacions adients per veure els canvis:

<img width="856" height="217" alt="image" src="https://github.com/user-attachments/assets/a79fb683-72e8-4167-8c86-a756c25cc8d8" />


A l'arxiu /etc/skel/.profile podem canviar el lloc on estem a l'executar la comanda pwd:

<img width="862" height="413" alt="image" src="https://github.com/user-attachments/assets/843bdd45-e309-48ac-b6bf-b2a9848e70a1" />

A l'arxiu /etc/skel/.bashrc podem crear un alias per a executar una comanda utilitzant una paraula concreta.

<img width="860" height="261" alt="image" src="https://github.com/user-attachments/assets/7bb78bf0-6120-4185-b97e-2f7ac27f64da" />

A l'arxiu /etc/skel/.bashrc_logout podem modificar el comportament quan sortim del terminal:

<img width="852" height="227" alt="image" src="https://github.com/user-attachments/assets/2975631e-1a59-445a-a040-f53d44000e60" />

Ara accedim a l'usuari a travès del terminal i fem les comprovacions:

<img width="1109" height="732" alt="image" src="https://github.com/user-attachments/assets/04c3ef3c-18c0-4dee-8ea2-96509e63c8c3" />

<img width="1133" height="398" alt="image" src="https://github.com/user-attachments/assets/6eae412a-2ba1-4a99-8002-a52ab402cfb8" />

### Permisos

Amb les comandes `chown` i `chmod` podem canviar els permisos dels usuaris:

<img width="800" height="779" alt="image" src="https://github.com/user-attachments/assets/42361882-8222-4cef-82ca-486c54508d23" />

I comprovem que funcionen els permisos que hem donat abans:

<img width="805" height="679" alt="image" src="https://github.com/user-attachments/assets/7ab29fad-c0d1-4ce3-9487-e004c926cfd3" />

<img width="858" height="710" alt="image" src="https://github.com/user-attachments/assets/48693b2c-2059-44c8-adfd-3d65e4fc437d" />

### Permisos especials 
Aquí veiem el permís especial sticky, que fa que l'usuari només pugui esborrar lo seu, no lo dels altres. Es fa amb la comanda `chmod o+t`:

<img width="873" height="815" alt="image" src="https://github.com/user-attachments/assets/a6b40229-fb0e-45c8-bc88-4df36237012a" />

I amb aquesta comanda eliminem el permís:

<img width="641" height="151" alt="image" src="https://github.com/user-attachments/assets/cfbdd18c-fbd9-4d39-8e15-d34df5e4fee4" />

Ara veurem el permís especial SUID, que es dona amb la comanda `chmod u+s` i `chmod g+s`:

<img width="702" height="156" alt="image" src="https://github.com/user-attachments/assets/337b8223-553e-4add-95cd-2c177e7e56ad" />

---

## Còpies de seguretat i automatització de tasques

Primer es preparen els punts de muntatge i es connecten els dispositius d'origen i de destí al sistema de fitxers per assegurar-ne l'accés amb les comandes `mount -t ext4 /ruta/disc1 /ruta/destí` ,`mkdir clonació` i `mount -t ext4 /ruta/disc2 /ruta/destí`.
A continuació es realitza la clonació en cru utilitzant la comanda `dd if=/dev/sdc of=/dev/sdd bs=1M status=progress`, que transfereix la informació bloc a bloc des del disc /dev/sdc cap al /dev/sdd mostrant el progrés de l'operació. 
Finalment es verifica la integritat de les dades calculant el checksum MD5 d'ambdós discos amb la comanda `md5sum /dev/sdc /dev/sdd` i la coincidència exacta dels valors resultants confirma que la còpia és idèntica.
A part, s'observa un error d'accés al directori de destí, una conseqüència esperada per haver sobreescrit l'estructura de fitxers del disc /dev/sdd mentre aquest encara estava muntat pel sistema operatiu.

<img width="804" height="509" alt="image" src="https://github.com/user-attachments/assets/bd3bbf24-c22e-44d7-ba48-af2b4fbed83e" />

### Cron i anacron 

Son dos eines d'automatització que permeten executar tasques periòdiques. Tot i ser similars, tenen unes funcions diferents que les diferencien. Cron executa tasques programades en una data i una hora específiques. Si el sistema està apagat la tasca es perd. És ideal per a tasques en dates i hores concretes i per a accions específiques d'un usuari. 
D'altra banda, Anacron és ideal per a executar tasques periòdiques on no cal una data i una hora específiques. Normalment s'utilitza per a tasques de manteniment del sistema i no requereix que el sistema estigui obert, quan s'obre el sistema s'executa.

Aquesta imatge mostra el fitxer de configuració global del sistema per a l'automatització de tasques, ubicat a `/etc/crontab`. Tot lo que posem dins de `/etc/crontab` afecta a tots els usuaris.

<img width="862" height="617" alt="image" src="https://github.com/user-attachments/assets/8c3b3101-3119-4456-9f56-f001e355f081" />

Si volem programar una tasca per a un usuari especific podem fer servir la comanda `crontab -e-u [usuari]` per a accedir al fitxer de configuració i editar-lo com es pot veure a les imatges de sota.

<img width="604" height="270" alt="image" src="https://github.com/user-attachments/assets/a93f9233-22cb-47e1-b9d5-6cd90186b38e" />

<img width="861" height="651" alt="image" src="https://github.com/user-attachments/assets/f41ce5ed-8d96-4930-a8cd-aaa19de9521a" />

Aquí podem veure les carpetes predefinides de cron.`cron.daily, hourly, weekly, monthly, yearly`: Són carpetes. Qualsevol script que fiquis dins d'aquestes carpetes s'executarà automàticament un cop al dia, a l'hora, a la setmana, etc. És molt còmode perquè no cal escriure codi "cron", només moure el fitxer allà.

<img width="607" height="230" alt="image" src="https://github.com/user-attachments/assets/d8175ed6-94cd-45e8-b955-ca3fb5ff4012" />

`anacrontab`: És el fitxer de configuració d'Anacron. Serveix per a ordinadors que no estan encesos les 24 hores. Si una tasca s'havia de fer a les 3 del matí i l'ordinador estava apagat, Anacron s'assegura que s'executi tan bon punt l'engeguis.

<img width="866" height="381" alt="image" src="https://github.com/user-attachments/assets/36a19013-1c19-4c50-baa8-c480804a2b35" />

Aquí podem veure un exemple de script per a automatitzar una còpia de seguretat. 
* `#!/bin/bash`: Indica al sistema que aquest fitxer s'ha d'executar usant l'intèrpret d'ordres Bash.
* `TIMESTAMP=$(date + "%Y%m%d_%H%M%S")`: Crea una variable amb la data i hora actual (any, mes, dia, hora, minut i segon). Això serveix perquè cada còpia tingui un nom diferent i no se sobreescriguin.
* `tar -cvf ...`: Aquesta ordre empaqueta fitxers. Destí: Guarda el fitxer a l'escriptori d'en iker-espinosa amb el nom copies_[data].tar.gz. Origen: Agafa tot el contingut de la carpeta /home/iker-espinosa/Imatges.

<img width="1020" height="213" alt="image" src="https://github.com/user-attachments/assets/27053368-abb6-43e0-9155-9c75ce85c764" />

Li donem permisos d'execució i comprovem.

<img width="1081" height="413" alt="image" src="https://github.com/user-attachments/assets/be12da6d-6e3b-40b4-b0c7-f20ae82aee90" />

Creem dos imatges de prova per a fer la còpia de seguretat.

<img width="745" height="179" alt="image" src="https://github.com/user-attachments/assets/548ea2c7-e3bf-4fd6-bb9b-b637eba211b7" />

Anem a l'arxiu /etc/crontab i afegim la següent linia que serveix per programar l'execució automàtica de l'script de còpies que has preparat anteriorment. Indiquem la horal el minut, el dia, el mes els dies de la setmana, l'usuari que executarà l'ordre i la ruta de l'script.

<img width="1021" height="600" alt="image" src="https://github.com/user-attachments/assets/34f32c86-82ed-4137-b6b1-0b00ba80cef2" />

Un cop arribada l'hora podem veure com es crea una carpeta a l'escriptori amb els arxius.

<img width="1036" height="900" alt="image" src="https://github.com/user-attachments/assets/075303db-c8e2-465d-97ea-fbff2a48b71b" />

Ara copiem el nostre script a la carpeta de tasques diàries del sistema. D'aquesta manera, el sistema l'executarà un cop al dia de forma indefinida, sense haver de dependre d'una data fixa com el 9 de desembre.

<img width="816" height="118" alt="image" src="https://github.com/user-attachments/assets/5fc46ef8-db19-4f9e-94c8-c77097ff2a04" />

S'executa una vegada al dia i s'espera un minut per a fer-lo des de que s'inicia el sistema operatiu.

<img width="872" height="389" alt="image" src="https://github.com/user-attachments/assets/761925b6-183e-48bc-91b5-590c8289a4a7" />

<img width="866" height="693" alt="image" src="https://github.com/user-attachments/assets/574e09d3-95f8-4891-9e81-35111fb680b6" />

---

## Quotes d'usuari

Les quotes de disc (o quotes d'usuari) són una eina d'administració de sistemes operatius que serveix per limitar la quantitat d'espai de disc o el nombre de fitxers que un usuari o un grup pot crear.

Primer comrovem amb la comanda `fdisk -l` que tenim els nostres discos.

<img width="716" height="324" alt="image" src="https://github.com/user-attachments/assets/f7aefb57-5210-4457-ac59-6148b77f224c" />

Instal·lem  el programa quota per a treballar amb les quotes de disc amb la comanda `apt install quota`.

<img width="878" height="644" alt="image" src="https://github.com/user-attachments/assets/466fb575-b829-4e08-b77c-e38733c8620f" />

A continuació creem una carpeta a /mnt/ per a les dades dels usuaris.

<img width="616" height="143" alt="image" src="https://github.com/user-attachments/assets/6659ce86-5afa-4435-9d9e-2214fc72d81d" />

Editem l'arxiu /etc/fstab i li afegim la següent línia:
* **/dev/sdc1**: És el dispositiu físic (una partició del disc) que vols muntar.
* **/mnt/dades_usuaris**: És el punt de muntatge, la carpeta on podràs veure els fitxers d'aquest disc.
* **ext4**: El sistema de fitxers que utilitza aquesta partició.
* **defaults,usrquota,grpquota**: Aquesta és la part clau:
* **usrquota**: Activa el suport per a les quotes d'usuari en aquesta partició.
* **grpquota**: Activa el suport per a les quotes de grup.
* **0 0**: Són paràmetres tècnics per a les còpies de seguretat (dump) i la verificació de l'estat del disc (fsck) en iniciar.
  
<img width="873" height="457" alt="image" src="https://github.com/user-attachments/assets/3ac86c3e-3550-458d-83d5-877b19638252" />

Podem comprovar de les següents dos maneres que el muntatge està bé:

<img width="807" height="388" alt="image" src="https://github.com/user-attachments/assets/f87db7ef-7323-4039-9702-622ac8b8e45c" />

<img width="811" height="105" alt="image" src="https://github.com/user-attachments/assets/17dbd9cf-bb56-4511-9b50-7f42e271a079" />

1. **L'ordre `quotaoff /mnt/dades_usuaris`**

   **Què fa:**  
   Desactiva temporalment el control de quotes en el punt de muntatge especificat.

   **Per què s'usa:**  
   Normalment es fa abans de fer canvis importants o per “reiniciar” el comptador de quotes si s'han detectat errors o s'ha modificat la configuració manualment.

2. **L'ordre `quotaon /mnt/dades_usuaris`**

   **Què fa:**  
   Activa oficialment la vigilància de quotes d'usuari (`usrquota`) i de grup (`grpquota`) en aquesta partició.

   **Resultat:**  
   A partir d'aquest moment, el nucli del sistema Linux començarà a comptabilitzar quant d'espai gasta cada usuari dins de `/mnt/dades_usuaris` i aplicarà els límits que defineixis.

<img width="798" height="44" alt="image" src="https://github.com/user-attachments/assets/138dfc49-3f77-42a3-8630-8b47918cce0a" />

En aquesta imatge estem comprovant l'estat de les quotes que haviem activat prèviament per veure si s'estan aplicant correctament.

Aquí tenim l'explicació de les dues ordres que hem executat:

1. **Comprovació d'un usuari específic (`quota -u prova`)**

   **Ordre:**  
   `quota -u prova`

   **Què fa:**  
   Cerca si l'usuari anomenat *prova* té alguna restricció d'espai configurada.

   **Resultat:**  
   El sistema respon `none` (cap), la qual cosa significa que aquest usuari encara té permís per fer servir tot el disc sense límits.

2. **Informe resum del dispositiu (`repquota /dev/sdc1`)**

   **Ordre:**  
   `repquota /dev/sdc1`

   **Què fa:**  
   Genera un informe detallat de tots els usuaris que tenen fitxers dins de la partició `/dev/sdc1` (que és la que vam configurar a `/etc/fstab`).

   **Dades que ens dóna l'informe:**

   - **Temps de gràcia (Grace time):**  
     Està configurat en 7 dies tant per a l'espai (Blocks) com per al nombre de fitxers (Inodes). Aquest és el temps que tindria un usuari per esborrar dades si superés el seu *límit tou*.

   - **Estat de l'usuari `root`:**
     - **Block limits (Espai):**  
       Està utilitzant 20 unitats d'espai, però els límits *soft* (tou) i *hard* (dur) estan a 0, que vol dir “sense límit”.
     - **File limits (Fitxers):**  
       Té creats 2 fitxers, també sense cap límit definit.

<img width="788" height="282" alt="image" src="https://github.com/user-attachments/assets/cd6fc588-2797-4453-9d35-8ee8d357f865" />

En aquesta última imatge estem veient el moment precís en què assignem els límits reals de disc a l'usuari **prova** mitjançant l'editor de text.

Aquestes són les dades clau que hem configurat:

**Usuari i partició:**  
Estem editant les quotes de l'usuari *prova* (amb el codi d'identificació 3003) dins del disc o partició `/dev/sdc1`.

**Límits d'espai (Blocks):**

- **Ús actual:**  
  L'usuari encara no ha gastat res (0 blocks).

- **Límit tou (soft):**  
  Fixat en 1024, que equival aproximadament a 1 MB. Si l'usuari supera aquesta xifra, el sistema començarà a mostrar avisos.

- **Límit dur (hard):**  
  Fixat en 2048, aproximadament 2 MB. Aquest és el límit absolut; el sistema bloquejarà qualsevol escriptura que intenti superar-lo.

**Límits de fitxers (Inodes):**

- **Ús actual:**  
  L'usuari té 0 fitxers creats.

- **Configuració:**  
  Els límits *soft* i *hard* estan a 0, cosa que indica que no hi ha restricció en el nombre de fitxers que pot crear, sempre que no superi el límit total de 2 MB d'espai total.

<img width="867" height="318" alt="image" src="https://github.com/user-attachments/assets/417c71dd-2229-49bb-aa38-7576f36e7d40" />

Finalment, hem obert completament els permisos del directori amb `chmod 777` per permetre que qualsevol usuari, especialment *prova*, hi pugui escriure lliurement i així verificar que el sistema bloqueja l’escriptura quan se supera el límit dur de 2 MB.

<img width="761" height="289" alt="image" src="https://github.com/user-attachments/assets/537b6d4d-447f-4b95-a49d-1deb1bc89b86" />

Accedim amb l'usuari prova i creem un arxiu de 800MB.

<img width="863" height="268" alt="image" src="https://github.com/user-attachments/assets/277ff21c-febb-4d04-9e3f-d789d4f15d9a" />

Repetim i comprovem que hem ocupat els 1600MB.

<img width="847" height="566" alt="image" src="https://github.com/user-attachments/assets/7bb2818a-9ddc-4ac5-9f8d-c949c2b6b7fb" />

Ara creem un altre i podem veure com ens diu que hem excedit la quota, però es guarda l'arxiu incomplet.

<img width="860" height="377" alt="image" src="https://github.com/user-attachments/assets/37739453-1b96-4109-b152-7686e06e4359" />

<img width="855" height="431" alt="image" src="https://github.com/user-attachments/assets/6dee7bcf-bdb3-4609-b83f-c7bceed670fd" />

modificar periode de gracia, afecta a toto el disc i tots els usuaris
<img width="867" height="219" alt="image" src="https://github.com/user-attachments/assets/89ed2fca-cb51-49fa-8423-eb27baa8610f" />

si volem que només afecti a un usuari ho podem fer de la següent manera
<img width="865" height="328" alt="image" src="https://github.com/user-attachments/assets/bf08c4ec-e09e-41d7-b57f-0f30984f024d" />


---

### ACLs

Primer creem un directori i un arxiu per fer les proves i comprovem els permisos:

<img width="642" height="586" alt="image" src="https://github.com/user-attachments/assets/bbc48fe0-0d9d-4c1d-b1a6-095c83c6d436" /> 

A continuació modifiquem els permisos d'ambdos i ho comprovem amb la comanda `getfacl`:

<img width="749" height="521" alt="image" src="https://github.com/user-attachments/assets/fd3486b9-e761-4e09-92e5-bd45287e6185" />

Definim la llista i comrpovem el que passa: 

<img width="709" height="232" alt="image" src="https://github.com/user-attachments/assets/b68e5b78-332b-46f7-810d-f4ea6145603b" />

L'usuari blau no te permisos, per tant no ens deixa:

<img width="824" height="735" alt="image" src="https://github.com/user-attachments/assets/0dcf7363-d0da-49ee-ba54-9190be5d6bbd" />

Amb el roig ens deixa però no al directori var, però el missatge és diferent i pooriem:

<img width="831" height="739" alt="image" src="https://github.com/user-attachments/assets/1234cfb8-dd54-44f3-812b-2f7bd930aea3" />

Amb la comanda `setfacl -b` pdoem deixar els permisos com estaven per defecte:

<img width="713" height="484" alt="image" src="https://github.com/user-attachments/assets/de635c32-9066-46ff-8a52-de6653d80af1" />

També ens permet denegar l'accès a una carpeta a un usuari concret:

<img width="750" height="401" alt="image" src="https://github.com/user-attachments/assets/2f55aa96-3a3f-48dd-b548-35af1816c608" />

### UMASK

* Sistema de permisos i Umask (User Mask)

Aquest esquema resumeix la lògica interna de com Linux calcula els permisos per defecte quan es creen fitxers o directoris nous.

1. Els 4 Nivells de Gestió de Permisos

A l'esquerra de la imatge es defineixen les quatre capes de seguretat:

1.  **UGO (User, Group, Others):** El sistema estàndard de permisos (rwx) per a propietari, grup i la resta del món.
2.  **Permisos Especials:** Bits avançats com SUID, SGID i Sticky Bit.
3.  **ACLs (Access Control Lists):** Permisos granulars per a usuaris específics.
4.  **Màscara (Umask):** El filtre que determina els permisos inicials per defecte.

---

2. Taula de conversió: Octal a binari

Per entendre els càlculs, cal conèixer la relació entre els valors numèrics i els permisos:

| Octal | Binari | Text (Símbols) | Significat |
| :---: | :---: | :---: | :--- |
| **0** | `000` | `---` | Cap permís |
| **1** | `001` | `--x` | Execució |
| **2** | `010` | `-w-` | Escriptura |
| **3** | `011` | `-wx` | Escriptura + Execució |
| **4** | `100` | `r--` | Lectura |
| **5** | `101` | `r-x` | Lectura + Execució |
| **6** | `110` | `rw-` | Lectura + Escriptura |
| **7** | `111` | `rwx` | Lectura, Escriptura i Execució |

---

3. La Lògica del càlcul de la Umask

La **Umask** actua com una "resta" o filtre. El sistema comença amb uns permisos màxims (Base) i li "resta" el valor de la Umask.

* Permisos base (Punt de partida)
* **📂 Directoris:** `777` (`rwxrwxrwx`)
* **📄 Fitxers:** `666` (`rw-rw-rw-`) *(Nota: Els fitxers mai es creen amb execució per seguretat).*

#### Exemples de Càlcul (Segons la imatge)

**A. Usuari Root (Umask típica: 022)**
La màscara `022` prohibeix l'escriptura al grup i als altres.

* **Directori:** `777` (Base) - `022` (Mask) = **`755`** (`rwxr-xr-x`)
* **Fitxer:** `666` (Base) - `022` (Mask) = **`644`** (`rw-r--r--`)

**B. Usuaris Normals / Altres (Umask típica: 002)**
La màscara `002` permet l'escriptura al grup (útil per col·laborar), però la prohibeix als altres.

* **Directori:** `777` - `002` = **`775`** (`rwxrwxr-x`)
* **Fitxer:** `666` - `002` = **`664`** (`rw-rw-r--`)

<img width="1007" height="551" alt="image" src="https://github.com/user-attachments/assets/33ee3dac-a048-4ef3-86a4-bab61940e173" />

Amb la comanda `umask` podem veure la nostra màscara:

<img width="726" height="175" alt="image" src="https://github.com/user-attachments/assets/c0f7bfab-e431-4341-8600-8af866ad8496" />

Per a canviar la màscara de tots els usuaris ho podem fer des d'aquest arxiu **/etc/login.defs**:  

<img width="851" height="523" alt="image" src="https://github.com/user-attachments/assets/338f8021-59c5-4d48-a33f-c58e1b0c32e5" />

Per a canviar-lo nomes en un usuari editem l'arxiu .profile:

<img width="846" height="647" alt="image" src="https://github.com/user-attachments/assets/0cf71301-83e2-4540-8f29-61debef95c9d" />

Amb la comanda `umask [màscara]` podem canviar la màscara de manera temporal per  l'usuari actual:

<img width="764" height="257" alt="image" src="https://github.com/user-attachments/assets/24705d1d-d766-415d-a72a-2b9f0e2d8221" />

Per a fer-ho definitiu per a tots els usuaris modifiquem aquest arxiu **/etc/login.defs**:

<img width="840" height="506" alt="image" src="https://github.com/user-attachments/assets/b49cd404-9778-4e44-bf57-772391b52e99" />

Comprovem els canvis:

<img width="658" height="275" alt="image" src="https://github.com/user-attachments/assets/f142de3b-ec7a-4fea-959e-30d63b087078" />



## dia 2/12 Gestió de processos
CHECKLIST: Provar Ps tree, top, htop, btop, ps aux, kill -9 PID, diferència entre ctrl c, cntrl z, comanda jobs, comanda fg per a tornar a primer pla, renice, nice, 

Amb la comanda `pstree -p -h [usuari]`podem filtrar els processos per usuari:

<img width="926" height="948" alt="image" src="https://github.com/user-attachments/assets/b2836d1d-26b5-4cdf-801e-98509d05685c" />

Filtrem per a trobar els processos del terminal

<img width="928" height="292" alt="image" src="https://github.com/user-attachments/assets/75535bcc-c283-4550-8cf9-272fc58470a3" />

`ps aux` explicar cada columna
<img width="960" height="906" alt="image" src="https://github.com/user-attachments/assets/e4248d33-e963-400b-8a36-d212e4056f38" />

`ps aux` filtrado para ver el gnome-terminal de alumnat
<img width="946" height="198" alt="image" src="https://github.com/user-attachments/assets/cccda48b-7572-46c9-972c-20dd960a7225" />

Ara amb la comanda `kill -9 [PID]` podem "matar" a un procès

Entrem a top, Cntrl c matem, control z aturem i amb jobs podem veure els aturats, si volem tornar a executar-lo es `fg %[n.job]`
- buscar captura

`top &` el ampersand es per a executar processos en segon pla
<img width="596" height="134" alt="image" src="https://github.com/user-attachments/assets/a1976015-2d8c-40ed-83e6-02d0e436e297" />

renice per a modificar prioritat de processos que ja estan en start y nice llençar processos en una prioritat determinada.

<img width="944" height="697" alt="image" src="https://github.com/user-attachments/assets/91273615-bb81-4bc1-b106-e8404d5d11e4" />
<img width="934" height="416" alt="image" src="https://github.com/user-attachments/assets/38f8256c-ad8a-4c06-94e3-606becb4c5da" />




