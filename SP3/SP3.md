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
 


- Crear UO
- Crear usuari
- Client accedir amb l'usuari creat

