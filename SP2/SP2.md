# 🚀 Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers

# Sistemes de fitxers i particions

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
És la unitat mínima física on se guarden les dades en un disc. Per defecte la mida són 512 bytes i no es pot modificar.

<img width="784" height="485" alt="image" src="https://github.com/user-attachments/assets/488e91cf-9b35-4619-9790-72821b9c2cd7" />

*/  <img width="834" height="427" alt="image" src="https://github.com/user-attachments/assets/5627f21c-b230-49bf-8ccb-67c99ea04e3b" />

*/ <img width="862" height="535" alt="image" src="https://github.com/user-attachments/assets/a698f0b7-a1b7-4d38-8b06-e6aa9fdcebe9" />
## Mida block 
També es pot dir clúster, la seva mida és la unitat mínima lògica on es guarden les dades a nivell de sistema operatiu. Per defecte són 4096 bytes (8 sectors) i aquesta mida sí que la podem modificar quan es formateja la partició. Cada partició del disc pot tenir una mida de bloc i un sistema de fitxers diferent.

La comanda `tune2fs -l` s'utilitza per llistar o mostrar tota la informació detallada del superbloc d'un sistema de fitxers de tipus ext2, ext3 o ext4 a Linux. És una eina de diagnòstic i inspecció que et permet veure l'estat i la configuració interna de la partició. Per utilitzar aquesta ordre, has d'especificar el dispositiu (la partició) que vols inspeccionar. Per exemple: `tune2fs -l /dev/sda2`:

<img width="790" height="119" alt="image" src="https://github.com/user-attachments/assets/10c68533-189d-41a3-a588-120d23bec548" />

En la següent imatge podem veure com creem un fitxer de text amb contingut i a continuació comprovem la seva mida i la mida que ocupa al SO per la mida del bloc:

<img width="802" height="183" alt="image" src="https://github.com/user-attachments/assets/f860d2c5-0ead-4d6c-ab89-9dc99e329575" />

  
## Fragmentació interna 
La fragmentació interna es produeix quan l'espai assignat a un fitxer és més gran que la mida real d'aquest fitxer, resultant en un malbaratament d'espai al disc.
  
## Fragmentació externa 
És quan un arxiu no està guardat en blocs consecutius de la memòria i els seus accessos són més lents, i, per tant, baixa el rendiment. En Windows tenim una eina anomenada desfragmentador de discos que ens permet solucionar aquest problema, a Linux per norma general no fa falta, ja que el sistema de fitxers ext4 està més optimitzat. 
De totes maneres, si volem comprovar-ho podem fer servir la comanda `e4defrag`, amb els paràmetres -c fem un diagnòstic i l'indiquem la nostra carpeta a comprovar: 

<img width="933" height="565" alt="image" src="https://github.com/user-attachments/assets/2e614592-aee5-47e3-8abc-990f3dac8e30" />
  
## Tipus de formateig
  
### Baix nivell (Esborra tot, arixus, sistema de fitxers i intenta reparar sectors defectuosos però es necessiten programes especifics, no e spot fer a travès del SO.)
    
### Mig nivell (Format lento, no borra arxius però si es troba sectors dfectuosos els marca, però no els repara.)
    
### Alt nivell (No es borren els arxius, només s'esborra el sistema de fitxers. Si troba sectors defectuosos els ignora totalment.)


    
  ### Gestio de particions
  Particions: una partició és un tros físic del disc dur i amb el gparted podem gestionar particions però no podem modificar la mida del bloc.
  Volum: un volum és una capa d'abstracció que es posa damunt de les particions i/o discos.


  
    #### GPARTED
    <img width="1107" height="420" alt="image" src="https://github.com/user-attachments/assets/515b2cc9-1b74-4bbd-bf11-09f5b93a6d10" />
    esto para gparted
<img width="1107" height="420" alt="image" src="https://github.com/user-attachments/assets/515b2cc9-1b74-4bbd-bf11-09f5b93a6d10" />

    #### Comandes

esto para comandes
<img width="819" height="298" alt="image" src="https://github.com/user-attachments/assets/7af12abd-f32e-49ca-b0e3-bba73c82b255" />
<img width="807" height="296" alt="image" src="https://github.com/user-attachments/assets/4a22fd1c-7a8f-4ff4-af92-043dd7ba202e" />
<img width="703" height="138" alt="image" src="https://github.com/user-attachments/assets/63bfee4f-9b74-4ff7-b769-c73e532d5b41" />
<img width="771" height="445" alt="image" src="https://github.com/user-attachments/assets/b4a41272-e767-4659-8091-8a4efc4b7b90" />
    
## Gestió de processos



## Gestió d'usuaris i grups i permisos

# dia 4/11 Usuaris, grups, permisos
Eina ALternativa per a poder gestionar graficament usuaris i grups
<img width="806" height="457" alt="image" src="https://github.com/user-attachments/assets/38ab2536-8683-4ffd-90b1-9090856667a6" />

# Fitxers implicats
Aquest fitxer té tots els usuaris del sistema, seleccionar usuari i explicar 
/etc/passwd <img width="918" height="810" alt="image" src="https://github.com/user-attachments/assets/acd4b78c-2ada-4740-90dd-0a7ba15a9f4f" />

/etc/group
Té tots els grups del sistema i els usuaris que formen part del grup
<img width="922" height="813" alt="image" src="https://github.com/user-attachments/assets/6554b7b7-806e-44f2-b20f-1e140bbf6aae" />

/etc/shadow
Aqui trobem per a cada usuari el seu password encriptat i al final la caducitat de les contraseyes 
<img width="915" height="796" alt="image" src="https://github.com/user-attachments/assets/f8e95762-2c61-449d-bc0e-c7465f7d3825" />

/etc/gshadow
Passwords de grups i permet veure els usuaris que formen part del grup, la diferencia amb el group es que aqui es l'unic lloc on es pot veure l'usuari administrador del grup, que només pot haver un.
<img width="919" height="817" alt="image" src="https://github.com/user-attachments/assets/461443fe-6be7-411a-9aa4-7aa10d1c9b6b" />

# Comandes bàsiques
afegir usuari adduser
<img width="883" height="660" alt="image" src="https://github.com/user-attachments/assets/1427e024-2afb-4aa8-9d6f-8cdce63d6990" />

Les carpetes apareixen un cop hem iniciat sessió amb l'usuari que hem creat.
<img width="920" height="343" alt="image" src="https://github.com/user-attachments/assets/b7e64456-d5c8-41f7-b67c-bc0d1ff674a9" />

afegir usuari useradd
<img width="926" height="745" alt="image" src="https://github.com/user-attachments/assets/1b2d6871-96fa-4a17-985f-e967ed5d7b94" />

grupos
<img width="929" height="880" alt="image" src="https://github.com/user-attachments/assets/ffbb3cd8-137c-43ca-bc48-a49521c998ba" />

al borrar el usuario no se borra el home, hay que hacerlo de otra manera
<img width="912" height="462" alt="image" src="https://github.com/user-attachments/assets/f9d523f6-2708-443d-81d7-c08085d5d4d8" />

bloquejar i desbloquejar un usuari
<img width="929" height="332" alt="image" src="https://github.com/user-attachments/assets/40d75fde-ba97-4db9-a705-02876333c0ac" />


creem el grup asixb i tres usuaris ivan pau iker aaron
modifiquem el nom del grup i l'eliminem
<img width="702" height="198" alt="image" src="https://github.com/user-attachments/assets/94ab1778-52b1-4f92-b6e5-c0d8b6d6fa08" />


tres maneres d'afegir un usuari a un grup
<img width="717" height="240" alt="image" src="https://github.com/user-attachments/assets/a9954f93-1a7a-4bd1-9621-00af319b8e9f" />

amb la segona comanda i el parametre -A en majuscula es el admin del grup

<img width="916" height="342" alt="image" src="https://github.com/user-attachments/assets/6dc79795-49f6-4b05-be56-c220d5094b6f" />

amb la -g minuscula es modifica el grup principal d'un usuari però no s'afegeix al grup
<img width="713" height="311" alt="image" src="https://github.com/user-attachments/assets/42ed80ed-6783-41a9-8fbb-37fe9bf6d49d" />

# dia 17/11

creacio 4 usuaris i modificacio nom de grup
<img width="751" height="225" alt="image" src="https://github.com/user-attachments/assets/ff2604db-c17c-4e05-90b8-bab5d6e5321b" />

3 maneres d'afegir un usuari a un grup i dos maneres d'eliminarlo
<img width="766" height="327" alt="image" src="https://github.com/user-attachments/assets/0987394c-b4db-4cb5-97dc-2350d39be1be" />

amb aquesta comanda es modifica el grup principal de l'usuari i un usuari nomes te un grup principal, pero pot formar part de molts grups i el grup principal es pot establir de manera fixa (amb questa comanda que hem fet) o temporal
<img width="789" height="152" alt="image" src="https://github.com/user-attachments/assets/b49fb1e6-38c5-49c8-8241-0d7fb1e20771" />

sempre es pot borrar un grup i als usuaris no els hi passa res, menys quan aquest és el grup principal de l'usuari, que no es pot esborrar
<img width="729" height="83" alt="image" src="https://github.com/user-attachments/assets/cdc79ebc-1ac7-44b8-8b4a-1858c3068d97" />

crar arxiu i carpeta, tot lo que hi hagi en aquest directori es copia al home del usuarinutilitzant la comanda adduser
<img width="704" height="490" alt="image" src="https://github.com/user-attachments/assets/48e5d3ed-f4fd-4063-a7df-57ec47fafa10" />

que el id comenci per 3000
<img width="458" height="175" alt="image" src="https://github.com/user-attachments/assets/fa40a4b8-b91a-46a8-9bdf-665e557bed1d" />

que el home estigui en altre lloc 
<img width="707" height="306" alt="image" src="https://github.com/user-attachments/assets/6ed68c61-cef2-49ec-b559-d5ba1978dfb4" />

canvair coses de passwd
<img width="822" height="202" alt="image" src="https://github.com/user-attachments/assets/a9066e1e-124b-4518-89e9-43416b5973fd" />

comprovem que els canvis del fitxer adduser han funcionat i comprovem la caducitat de les passwd i que l'usuari se li ha creat lo del skel
<img width="854" height="488" alt="image" src="https://github.com/user-attachments/assets/1d0f9093-9b94-4076-b1c1-91c0cd0df307" />

ara amb els arxius que modifiquen useradd
canviar shell per defecte
<img width="857" height="251" alt="image" src="https://github.com/user-attachments/assets/e27f5f0b-46d2-47a2-91c5-a32ca8bee7f2" />

fem les comprovacions
<img width="856" height="217" alt="image" src="https://github.com/user-attachments/assets/a79fb683-72e8-4167-8c86-a756c25cc8d8" />

TITULO DE TODO ESTO personalitzacio de les comandes adduser i useradd, debajo de comandes basiques

canviar el lloc on estem al fer la comanda pwd
<img width="862" height="413" alt="image" src="https://github.com/user-attachments/assets/843bdd45-e309-48ac-b6bf-b2a9848e70a1" />

crear alias para ejecutar un comando usando una palabra
<img width="860" height="261" alt="image" src="https://github.com/user-attachments/assets/7bb78bf0-6120-4185-b97e-2f7ac27f64da" />


<img width="852" height="227" alt="image" src="https://github.com/user-attachments/assets/2975631e-1a59-445a-a040-f53d44000e60" />

accedim a l'usuari a traves del terminal i fem les comprovacions
<img width="1109" height="732" alt="image" src="https://github.com/user-attachments/assets/04c3ef3c-18c0-4dee-8ea2-96509e63c8c3" />
<img width="1133" height="398" alt="image" src="https://github.com/user-attachments/assets/6eae412a-2ba1-4a99-8002-a52ab402cfb8" />


!!! EXERCICI crear personalitzacio al bashrc bashlogout i profile un nou usuari amb modificacions

# dia 18/11

canviar permisos, dos maneres una amb dos comandes i una altra amb una
<img width="800" height="779" alt="image" src="https://github.com/user-attachments/assets/42361882-8222-4cef-82ca-486c54508d23" />

proves de que funcionen els permisos que hem donat abans
<img width="805" height="679" alt="image" src="https://github.com/user-attachments/assets/7ab29fad-c0d1-4ce3-9487-e004c926cfd3" />

<img width="858" height="710" alt="image" src="https://github.com/user-attachments/assets/48693b2c-2059-44c8-adfd-3d65e4fc437d" />

permisos especials 
(sticky) - nomes pot esborrar lo seu, no lo dels altres
<img width="873" height="815" alt="image" src="https://github.com/user-attachments/assets/a6b40229-fb0e-45c8-bc88-4df36237012a" />
<img width="641" height="151" alt="image" src="https://github.com/user-attachments/assets/cfbdd18c-fbd9-4d39-8e15-d34df5e4fee4" />

(suid)
<img width="702" height="156" alt="image" src="https://github.com/user-attachments/assets/337b8223-553e-4add-95cd-2c177e7e56ad" />
exemple al moodle per fer el pas a pas d'exemple SUID


## Còpies de seguretat i automatització de tasques



## Quotes d'usuari







mode temporal
<img width="810" height="326" alt="image" src="https://github.com/user-attachments/assets/ef951cd5-da97-4b53-b7a9-7ae708eff851" />
<img width="806" height="374" alt="image" src="https://github.com/user-attachments/assets/78b11076-4645-4fa1-ba86-87f72803d544" />
<img width="804" height="261" alt="image" src="https://github.com/user-attachments/assets/826347b9-f4b4-478f-86ae-0daf385f2e04" />

mode definitiu
<img width="806" height="428" alt="image" src="https://github.com/user-attachments/assets/ad4372c2-f4f8-455c-9703-23a89a4850d7" />
<img width="607" height="140" alt="image" src="https://github.com/user-attachments/assets/79b5ab8e-a684-45cc-a825-c5ab37542140" />



# dia 24-11
ACLs (gestió d'usuaris, permisos, etc)
<img width="642" height="586" alt="image" src="https://github.com/user-attachments/assets/bbc48fe0-0d9d-4c1d-b1a6-095c83c6d436" /> (el ls- l sin el grep sobra)

<img width="749" height="521" alt="image" src="https://github.com/user-attachments/assets/fd3486b9-e761-4e09-92e5-bd45287e6185" />

Definim la llista i comrpovem el que passa
<img width="709" height="232" alt="image" src="https://github.com/user-attachments/assets/b68e5b78-332b-46f7-810d-f4ea6145603b" />

l'usuari blau no te permisos, per tant no ens deixa
<img width="824" height="735" alt="image" src="https://github.com/user-attachments/assets/0dcf7363-d0da-49ee-ba54-9190be5d6bbd" />

amb el roig ens deixa però no al directori var, però el missatge és diferent i pdoriem
<img width="831" height="739" alt="image" src="https://github.com/user-attachments/assets/1234cfb8-dd54-44f3-812b-2f7bd930aea3" />

deixar els permisos com estaven al principi amb una comanda
<img width="713" height="484" alt="image" src="https://github.com/user-attachments/assets/de635c32-9066-46ff-8a52-de6653d80af1" />

denegar l'accès a la carpeta
<img width="750" height="401" alt="image" src="https://github.com/user-attachments/assets/2f55aa96-3a3f-48dd-b548-35af1816c608" />

# dia 25-11
UMASK
explicar teoria foto movil

<img width="726" height="175" alt="image" src="https://github.com/user-attachments/assets/c0f7bfab-e431-4341-8600-8af866ad8496" />

per a canviar la màscara de tots els usuaris ho podem fer des d'aquest arxiu 
<img width="851" height="523" alt="image" src="https://github.com/user-attachments/assets/338f8021-59c5-4d48-a33f-c58e1b0c32e5" />

per a canviar-lo nomes en un usuari editem l'arxiu .profile
<img width="846" height="647" alt="image" src="https://github.com/user-attachments/assets/0cf71301-83e2-4540-8f29-61debef95c9d" />

amb la comanda umask podem canviar la màscara de manera temporal per  l'usuari actual
<img width="764" height="257" alt="image" src="https://github.com/user-attachments/assets/24705d1d-d766-415d-a72a-2b9f0e2d8221" />


per a fer-ho definitiu per a tots els usuaris modifiquem aquest arxiu
<img width="840" height="506" alt="image" src="https://github.com/user-attachments/assets/b49cd404-9778-4e44-bf57-772391b52e99" />

comprovem els canvis
<img width="658" height="275" alt="image" src="https://github.com/user-attachments/assets/f142de3b-ec7a-4fea-959e-30d63b087078" />

