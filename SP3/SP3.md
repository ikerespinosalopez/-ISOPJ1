# Sprint 3: Administració de Dominis i Seguretat
## Instal·lació del domini LDAP i unir client al domini
FER explicacions: Que es un domini, objectes del domini, necessita una ip fixa, bosc arbre, brancas de l'arbre

Configurem una IP fixa al servidor.

<img width="819" height="592" alt="image" src="https://github.com/user-attachments/assets/7381067e-09a0-40e6-8c1c-79319091ec2d" />

Anem a l'arxiu /etc/hostname i establim un nou nom. En aquest cas `ikerserver`.

<img width="613" height="178" alt="image" src="https://github.com/user-attachments/assets/be54896e-4f23-452c-932e-e9cf8b256186" />

Ara anem a l'arxiu /etc/hosts i canviem el hostname que hi havia abans per el nou, desprès afegim una nova línia a sota on indicarem la nostra IP i el nom del domini juntament amb el hostname.

<img width="651" height="314" alt="image" src="https://github.com/user-attachments/assets/280e9703-5ea3-4fd3-83ad-75c59d1a5c56" />

Instal·lem sldap

<img width="750" height="29" alt="image" src="https://github.com/user-attachments/assets/1783adc4-85d0-4425-91da-8c0c8683a41d" />

Amb la comanda slapcat podem veure tots els objectes del domini.

<img width="524" height="319" alt="image" src="https://github.com/user-attachments/assets/1e482715-2d2f-4f6e-b219-8dd97710cea8" />

Descomprimim els arxius que ens hem descarregat abans.

<img width="722" height="263" alt="image" src="https://github.com/user-attachments/assets/edd57613-7f25-40e4-8752-7e1fce34ebce" />

Ara amb la comandadpkg-reconfigure slapd anem a tornar a configurar slapd.

<img width="770" height="28" alt="image" src="https://github.com/user-attachments/assets/48ca01c9-447a-49ab-bd9e-3709f0e55884" />

Se'ns obrirà una finestra per a configurar el paquet, hem de seleccionar NO per a continuar amb la configuració.

<img width="822" height="289" alt="image" src="https://github.com/user-attachments/assets/92991b10-c69f-47cc-8a96-f37ffadd2896" />

En la següent finestra hem d'escriure el nom del domini que hem creat abans, en aquest cas iso.cat.

<img width="855" height="315" alt="image" src="https://github.com/user-attachments/assets/3cd4cf48-2d41-47cb-9564-0d6b23054099" />

A continuació escriurem el nom de l'organització que desitjem.

<img width="854" height="299" alt="image" src="https://github.com/user-attachments/assets/da340a68-e04c-4843-8fc2-776e3c464adc" />

I ens demanarà una contrasenya per a l'usuari administrador.

<img width="837" height="304" alt="image" src="https://github.com/user-attachments/assets/66d9a04b-b51d-43e2-9f3b-4b081b974faa" />

Ara seleccionem que no volem eliminar la base de dades i continuem.

<img width="756" height="262" alt="image" src="https://github.com/user-attachments/assets/6e5d24c0-ffaf-4c13-b9fb-a817e49dea25" />

Seleccionem que volem moure la base de dades anterior i finalitzem el procès de configuració.

<img width="854" height="307" alt="image" src="https://github.com/user-attachments/assets/d553c462-6ef1-401a-bc52-389a6fc608ca" />

Tornem a executar la comanda slapcat i podem veure els canvis respecte abans

<img width="630" height="304" alt="image" src="https://github.com/user-attachments/assets/84b8b07e-6ca3-45f3-8faf-cbb5c4dfcd86" />

Anem a l'arxiu uo.ldif i modifiquem per a canviar el que ve per defecte per el nostre domini.

<img width="597" height="144" alt="image" src="https://github.com/user-attachments/assets/f0f464e5-838a-4c04-9852-f104e5a5d291" />

Repetim amb l'arxiu grup.ldif.

<img width="602" height="197" alt="image" src="https://github.com/user-attachments/assets/33f925b7-e16d-4150-ada7-00d6189e6dc0" />

I tornem a repetir amb l'arxiu usu.ldif.

<img width="587" height="470" alt="image" src="https://github.com/user-attachments/assets/fa5fe846-a2d9-4bcc-a35f-bb5da502662b" />

Amb la comanda `ldapadd -c -x -D "cn=admin,dc=iso,dc=cat" -W -f [nom_de_arxiu]` afegim els objectes que hem creat. Repetim el procès amb els tres arixus. Els paràmetres fan lo següent: -c per a que no s'aturi en cas d'error, -x fa servir l'autenticació simple, -D indica l'usuari que fa l'acció, -W et demana la contrasenya de forma segura per pantalla i -f indica el fitxer que volem carregar.

<img width="863" height="326" alt="image" src="https://github.com/user-attachments/assets/832430e8-b7d3-4dd8-b6be-2fdc9c2155d6" />

Ara anem al client, comprovem que tenim connexió amb el servidor i instal·lem els tres paquets següents:

<img width="870" height="29" alt="image" src="https://github.com/user-attachments/assets/6b614ac7-8b1c-4cb8-901b-3478652d5d2a" />

Primer hem de configurar l'adreça IP del servidor al qual ens volem connectar, és important esborrar la i de "ldapi" i una de les tres /// que ens apareixen per defecte.

<img width="858" height="385" alt="image" src="https://github.com/user-attachments/assets/dc0214bd-499f-4278-b74f-6f5a56165cfe" />

A continuació configurem el nom del domini que hem establert abans.

<img width="856" height="340" alt="image" src="https://github.com/user-attachments/assets/e6073ef9-8f13-4259-9f2c-f467f73006b6" />

Seleccionem la versió que volem utilitzar.

<img width="853" height="338" alt="image" src="https://github.com/user-attachments/assets/43dfd452-7420-48e8-87ab-dd1ed3a27a87" />

Escollim que sí.

<img width="860" height="402" alt="image" src="https://github.com/user-attachments/assets/c628ff1e-1720-4ab7-8050-1f19594d8e5b" />

Seleccionem que si per a que ens demani l'usuari i contrasneya per a accedir.

<img width="848" height="321" alt="image" src="https://github.com/user-attachments/assets/b5325f67-b442-46f5-8aab-24188fcd6da4" />

Establim el compte que volem fer servir amb privilegis d'administrador.

<img width="667" height="363" alt="image" src="https://github.com/user-attachments/assets/1d54b8f9-0851-4780-9a45-d355cabecbb2" />

Escollim la contrasenya.

<img width="855" height="413" alt="image" src="https://github.com/user-attachments/assets/e23c3d30-501a-486e-a572-7fab18fb9c5a" />

Ara seleccionem l'usuari que volem fer servir sense privilegis.

<img width="856" height="358" alt="image" src="https://github.com/user-attachments/assets/54256f8e-a588-4bee-a60f-fcd215834363" />

I l'establim una altra contrasenya per a finalitzar el procès.

<img width="842" height="288" alt="image" src="https://github.com/user-attachments/assets/2c25fc5a-98a3-422e-bbb8-955f4e80ca87" />

Executem la comanda `dpkf-reconfigure ldap-auth-config` per a repetir el procès i confirmem tot els passos per a veure un de nou a final que ens pregunta com volem encriptar la contrasenya.

<img width="803" height="20" alt="image" src="https://github.com/user-attachments/assets/6cd8bd58-7c1b-4603-8ffa-25f187f52416" />

<img width="834" height="701" alt="image" src="https://github.com/user-attachments/assets/5545f453-1e6f-4ee6-bbf8-450c1c3d03b1" />

Modifiquem l'arxiu nsswitch.conf per a que el sistema busqui primer al ldap.

<img width="715" height="509" alt="image" src="https://github.com/user-attachments/assets/9a5fc62b-a356-45ec-a05f-a8f73c7e95ce" />

A continuació modifiquem l'arxiu /etc/pam.d/common-session.

<img width="837" height="756" alt="image" src="https://github.com/user-attachments/assets/102e4428-3a6f-4c24-b71f-36985434044c" />

Ara modifiquem l'arxiu /etc/pam.d/common-password i eliminem la part de authtok.

<img width="871" height="735" alt="image" src="https://github.com/user-attachments/assets/0bcee416-922b-4408-8ea3-0e8725682cef" />

Per a iniciar sessió gràficament modifiquem l'arxiu /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf.

<img width="761" height="113" alt="image" src="https://github.com/user-attachments/assets/e4b7a9b4-c576-48dc-9c64-9979237481b3" />

Comprovem que funciona.

<img width="728" height="112" alt="image" src="https://github.com/user-attachments/assets/e8ebcc61-a10b-495e-8fa1-ce920d952d15" />

Iniciem sessió amb l'usuari que tenim i comprovem que funcioni correctament.

<img width="599" height="367" alt="image" src="https://github.com/user-attachments/assets/c0d8ca8d-b26e-420d-b3fa-bfb8a93bfe59" />

## Instal·lació de Apache Directory Studio
El primer pas abans d'instal·lar el paquet serà actualiztar els repositoris, un cop fet haurem d'instal·lar Java, ja que és necessari per a fer servir ADS.

Per fer-ho utilitzarem la següent comanda:

<img width="700" height="25" alt="image" src="https://github.com/user-attachments/assets/365e6c17-4b2d-4c63-9b46-73306110be80" />

Podem comprovar si 'sha instal·lat correctament amb la comanda `java -version`

<img width="517" height="25" alt="image" src="https://github.com/user-attachments/assets/d1e4771c-ccf4-4488-b192-720eb5cdccdc" />

Un cop instal·lat haurem de baixar-nos l'ADS des de la seva pàgina oficial, on trobarem un arxiu .gz. El descomprimim i el copiem a /opt.

I donem permisos al nostre usuari amb aquesta comanda:

<img width="881" height="23" alt="image" src="https://github.com/user-attachments/assets/9b6b9596-d2e1-4610-b229-a2e0f8abd836" />

Trobem la ruta de java amb la comanda `readlink -f $(which java)` i editem l'arxiu Apachedirectoryestudio.ini i introduim aquestes línies:

<img width="868" height="613" alt="image" src="https://github.com/user-attachments/assets/feab7a29-a9b7-48fb-8ff8-f506beb02579" />

Un cop fet creem un arxiu .desktop anomenat apachedirectorystudio i afegim dins aquest contingut:

<img width="771" height="280" alt="image" src="https://github.com/user-attachments/assets/2cf36dd0-9f43-4a51-b08f-eae9f2348f08" />

Guardem els canvis i ara ja podrem obrir ADS:

<img width="892" height="181" alt="image" src="https://github.com/user-attachments/assets/ffc4d9d3-f3a6-4cb7-982c-8b4085b37d47" />

Un cop dins haurem d'obrir el panel de Connections i establir una nova connexió amb el server on haurem d'indicar la IP, el nom del domini i la password. Un cop fet se'ns obrirà el panell del nostre servidor LDAP:

<img width="221" height="320" alt="image" src="https://github.com/user-attachments/assets/cf7007d1-6ee2-4588-90ee-7fa8ecb999e9" />

Ara anem a crear una UO. Fem click dret al domini i seleccionem una nova entrada:

<img width="792" height="698" alt="image" src="https://github.com/user-attachments/assets/4639655f-fa24-467a-b601-f4d3027f05fb" />

Escollim Create entry from scratch:

<img width="605" height="233" alt="image" src="https://github.com/user-attachments/assets/adab951e-921e-443c-a781-17f4dbd6f79f" />

Escollim l'objecte UO:

<img width="611" height="475" alt="image" src="https://github.com/user-attachments/assets/54d0f431-10d4-49fd-89d8-9f13c5e2510e" />

I a l'apartat RDN escrivim ou=[nom_OU].

<img width="612" height="275" alt="image" src="https://github.com/user-attachments/assets/92a10f0f-19b3-43fa-baed-84e78869ccab" />

I podem veure com s'ha creat la UO:

<img width="223" height="380" alt="image" src="https://github.com/user-attachments/assets/6be24928-bbd2-4ca0-b5d5-5d01d22a79f2" />

Per a crear l'usuari repetim el procès però des de la nova UO i seleccionant el tipus d'objecte inetOrgPerson:

<img width="615" height="512" alt="image" src="https://github.com/user-attachments/assets/f3d202ed-56e6-4bdb-8989-24770280b6a6" />

A RDN escrivim uid=[nom_usuari] i a continuació escrivim els atributs com el cognom:

<img width="610" height="397" alt="image" src="https://github.com/user-attachments/assets/9df7ba76-00b6-489a-bd23-0fb7db1ec065" />

Aprofitem per a afegir una contrasenya, fem clic dret i escollim New Attribute, escollim el tipus userPassword:

<img width="606" height="429" alt="image" src="https://github.com/user-attachments/assets/c8928715-0cf7-4e56-a42e-6e9a6905cc24" />

S'obrirà una finestra per a introduir la contrasenya de manera segura.

<img width="768" height="405" alt="image" src="https://github.com/user-attachments/assets/3ef8d8f2-6ddc-4eac-af10-43176af9aaff" />

I ja tenim l'usuari dins la OU:

<img width="219" height="405" alt="image" src="https://github.com/user-attachments/assets/e673f8b5-66a0-4e39-bafc-700a7e1879bb" />

Ara hem de comprovar que sigui accessible des del client.




- Crear UO
- Crear usuari
- Client accedir amb l'usuari creat


dades pt10 fer lo del paper 

## Servidor SAMBA
Un servidor samba serveix per a compartir fitxers, impresores, carpetes a travès d'una autenticació a nivell usuari, ja sigui de SAMBA o de LDAP. Funciona tant en WIndows com en Ubuntu.

### Server
Instal·lem SAMBA al servidor amb la comanda `apt install samba`:

<img width="576" height="32" alt="image" src="https://github.com/user-attachments/assets/592caf50-3ae9-49c1-9410-f0aa359188cd" />

Anem al directori arrel, creem la carpeta proves i li donem permisos. Li canviem el grup, creem un arxiu dins i comprovem que els permisos són correctes.

<img width="683" height="376" alt="image" src="https://github.com/user-attachments/assets/06b56742-c3c6-4992-814a-addbb2dca97a" />

<img width="637" height="112" alt="image" src="https://github.com/user-attachments/assets/ef20407d-4eb9-4250-a3cc-a45065bb8f67" />

Creem els usuaris per a samba amb la comanda useradd, no son vàlids per al sistema. Els afegim a un nou grup que hem creat i comprovem que s'hagin fet correctament.

<img width="716" height="397" alt="image" src="https://github.com/user-attachments/assets/20bf0e2f-bd8c-41bf-a397-30e962fd2e16" />

Ara li assignem una contrasenya a cada usuari que hem creat abans.

<img width="510" height="265" alt="image" src="https://github.com/user-attachments/assets/a7b2a82c-cc91-41f0-a324-1c569b087ad6" />

Ara modifiquem la configuració editant l'arxiu /etc/samba/smb.conf i afegim una sèrie de línies.

#### Explicació dels paràmetres

| Paràmetre | Valor | Descripció |
| :--- | :--- | :--- |
| **`[proves]`** | - | **Nom del recurs**. Aquest és el nom visible a la xarxa (ex: `\\servidor\proves`). |
| **`path`** | `/proves` | **Ruta del sistema**. Indica el directori físic al servidor on s'emmagatzemen realment les dades. |
| **`guest ok`** | `yes` | **Convidats**. Permet l'accés sense autenticació (encara que pot ser limitat per altres regles). |
| **`directory mask`** | `0755` | **Permís carpetes**. Les carpetes noves es creen amb permisos `755`: Propietari (RWX), Grup (RX), Altres (RX). |
| **`create mask`** | `0644` | **Permís fitxers**. Els fitxers nous es creen amb permisos `644`: Propietari (RW), Grup (R), Altres (R). |
| **`browseable`** | `yes` | **Visibilitat**. La carpeta apareix llistada quan s'explora el servidor per la xarxa. |
| **`read list`** | `blau, @color` | **Llista de lectura**. Defineix qui pot llegir:<br>• `blau`: L'usuari "blau".<br>• `@color`: El grup d'usuaris "color" (l'arrova indica grup). |
| **`write list`** | `blau` | **Llista d'escriptura**. Defineix qui pot modificar/esborrar:<br>• Només l'usuari `blau` té permisos d'escriptura explícits. |
| **`invalid users`** | `roig` | **Bloquejat**. L'usuari `roig` té l'accés denegat explícitament. |

<img width="884" height="746" alt="image" src="https://github.com/user-attachments/assets/8c5ee0b3-9807-45f5-807b-aa062bfe49f4" />

És important desprès de fer els canvis reiniciar els serveis smbd nmbd.

<img width="552" height="45" alt="image" src="https://github.com/user-attachments/assets/afaf139c-b162-42e9-88bc-bfd3c27ba527" />


### Client



## Servidor NFS



