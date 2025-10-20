# ⚡ Sprint 1: Instal·lació i Configuració Inicial


## Virtualització i instal·lació del SO Ubuntu
Primer obrim VirtualBox i creem una nova màquina virtual. Seleccionem la ISO d'Ubuntu24 i configurem els paràmetres com la RAM,la xarxa i l'emmagatzematge.

<img width="957" height="696" alt="Captura1" src="https://github.com/user-attachments/assets/6658d8b2-87fc-4070-9b7c-b79c3859e72a" />


Obrim la MV i continuem amb la instal·lació del SO Ubuntu de manera gràfica.

A continuació procedim amb l'instal·lació fins arribar al punt on hem de configurar el disc i escollim fer les particions manuals. Seleccionem el nostre disc.

<img width="798" height="655" alt="Captura2" src="https://github.com/user-attachments/assets/3539bd99-9c83-41ff-afe1-450bf666cfec" />


<img width="796" height="649" alt="Captura3" src="https://github.com/user-attachments/assets/63f66803-b837-4edf-93b4-7c6cc2ec57b1" />


Fem les particions adients, en aquest cas /home, /boot, /boot/efi, / i swap.

<img width="796" height="649" alt="Captura4" src="https://github.com/user-attachments/assets/8fcb63b3-2a9f-4fa3-ac6b-7271563ec9b2" />

Un cop fet, creem el nostre usuari.

<img width="796" height="649" alt="image" src="https://github.com/user-attachments/assets/f821b02d-7c27-4c66-810b-01474cd75422" />

Continuem amb el procès habitual de la instal·lació i esperem a que termini. Reiniciem el sistema i ja tindriem l'instal·lació realitzada.

<img width="796" height="649" alt="image" src="https://github.com/user-attachments/assets/24abf174-2785-45b0-acd4-6434d11f700a" />

<img width="1285" height="856" alt="image" src="https://github.com/user-attachments/assets/b7edc55c-f58a-475f-be62-9966115d2944" />

## Llicenciament

Saber on és la llicencia y dcoumentar les que te el ubuntu y pe que  tal tal

Ubuntu és una distribució basada en Debian que inclou principalment programari amb llicències lliures i de codi obert. Cada paquet instal·lat a Ubuntu té un fitxer amb la llicència i els drets d'autor que es troba a /usr/share/doc/paquet/copyright.

Podem trobar les següents llicències que són les més habituals:
- GPL (General Public License): obliga a distriubir el codi font i les modificacions.
- LGPL: semblant però més flexible per a biblioteques compartides.
- MIT/BSD/Apache: llicències permissives, permeten ús comercial i redistribució amb algunes restriccions.
- Privatives (EULA): aplicades a alguns components com els controladors.

Legalment el sistema base es troba sota llicències lliures, les aplicacions de tercers poden variar segons el repositori d'origen i la documentació està sota llicències com la Creative Commons.

Els repositoris es poden dividir segons el tipus:
- Main: programari lliure.
- Restricted: controladors privatius.
- Universe: programari lliure mantingut per la comunitat.
- Multiverse: programari amb problemes de llicència o restriccions legals.
  
## Gestors d'arrencada per a instal·acions DUALS
Volem instal·lar Windows en mode DUAL en la nostra màquina virtual amb Ubuntu que hem creat anteriorment. Veurem dos escenaris diferents segons l'ordre d'instal·lació i l'ubicació de la misma. Per fer-ho, primer ens hem de descarregar la ISO de Windows y obrir el VirtualBox.

### Instal·lar Windows en DUAL desprès d'Ubuntu

Primer hem de preparar amb la nostra màquina Ubuntu tot lo necessari per a fer la instal·lació DUAL. Inserim la ISO de W10 Enterprise

<img width="951" height="463" alt="image" src="https://github.com/user-attachments/assets/8f10a503-4758-491c-bd81-1db90af77031" />

Procedim amb la instal·lació fins a arribar a les particions, on haurem de seleccionar l'espai buit que hem deixat abans i fer clic a Nou. 

<img width="852" height="821" alt="image" src="https://github.com/user-attachments/assets/111f7c0c-7bd1-483b-8d0f-177d7d174fb4" />

Seleccionem tot l'espai disponible i fem clic a següent per a acabar de fer la instal·lació. Quan acabi es reiniciarà la màquina i s'obrirà el Windows. Creem un compte i continuem amb la instal·lació fins a que se'ns obri Windows 10.
  
<img width="954" height="886" alt="image" src="https://github.com/user-attachments/assets/a580aada-c05e-410f-b149-c0700f4e0957" />

Ara quan tornem a iniciar la màquina veurem que s'obre Windows directament sense deixar-nos escollir el sistema que volem fer sevrir. Per solucionar-lo utilitzarem l'eina SuperGrub. El primer pas serà afegir la ISO del SuperGrub.

<img width="870" height="538" alt="image" src="https://github.com/user-attachments/assets/20a5c36c-551e-44e2-a575-964a02c8fe58" />

Un cop fet iniciem la màquina i mitjançant el boot manager obrim el SuperGrub.

<img width="628" height="531" alt="image" src="https://github.com/user-attachments/assets/026e6835-7f06-492a-9120-625cb1428057" />

Obrim el SuperGrub i seleccionem la segona opció que diu "Detect and show boot methods"

<img width="638" height="475" alt="image" src="https://github.com/user-attachments/assets/8d52805c-5974-4ee7-aaab-303fc8d79a5e" />

Trobem el linux que hem instal·lat i l'iniciem.

<img width="638" height="489" alt="image" src="https://github.com/user-attachments/assets/abb1826a-1b19-44a4-b95f-3dd5bcf17eae" />

Se'ns obrirà l'Ubuntu i haurem d'accedir a la terminal per a acabar de configurar el GRUB. Accedim al mode d'administrador amb la comanda "sudo su". EL primer que haurem de fer és reinstal·lar el grub amb la comanda "apt install --reinstall grub-pc".

<img width="857" height="543" alt="image" src="https://github.com/user-attachments/assets/69913466-32a8-4c5e-ae81-e3a75704bb70" />

A continuació executem la comanda "grub-install /dev/sda".

<img width="655" height="92" alt="image" src="https://github.com/user-attachments/assets/0666dc40-bf6d-4f09-a241-ea59d1564c6d" />

Anem a la carpeta /boot i mirem si tenim una subcarpeta anomenada /efi, si no la tenim la creem amb la comanda "mkdir efi".

<img width="818" height="378" alt="image" src="https://github.com/user-attachments/assets/97d7cad1-ca52-46cc-a30e-dc747041b47a" />

Anem a la carpeta que acabem de crear i executem la comanda "fdisk -l".

<img width="842" height="674" alt="image" src="https://github.com/user-attachments/assets/2e98f166-b03e-4b69-aa1e-bc90cf9f1854" />

Aquí hem de trobar la partició del Sistema EFI.

<img width="798" height="257" alt="image" src="https://github.com/user-attachments/assets/b2f29e03-136a-466d-b8b2-aa1b268dd18c" />

Amb aquesta informació executem la comanda "mount /dev/sda6 /boot/efi".

<img width="607" height="20" alt="image" src="https://github.com/user-attachments/assets/2a4c4067-b280-46a2-8f9b-5935cb187da1" />

Desprès executem aquesta comanda "grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu".

<img width="832" height="113" alt="image" src="https://github.com/user-attachments/assets/ce00727d-3ecb-4e93-b210-47fe365e4f86" />

Ara executem la comanda update-grub i podem trobar el Linux i el Windows.

<img width="838" height="294" alt="image" src="https://github.com/user-attachments/assets/07730bd5-0a7b-48e6-9664-29e78aa5c1bf" />

Ara instal·larem el gestor d'arrencada amb la comanda "apt install efibootmgr".

<img width="815" height="244" alt="image" src="https://github.com/user-attachments/assets/395de237-2e29-45fc-a277-cb2ad971d270" />

L'executem amb la comanda "efibootmgr" per a veure l'ordre d'arrencada, ens hem d'assegurar de que estigui primer el Ubuntu, si no és així es pot modificar amb la comanda "efibootmgr -o [ordre]".

<img width="839" height="576" alt="image" src="https://github.com/user-attachments/assets/cae04489-9815-4bc9-84b1-d28a6699fc92" />

Ara hem de modificar l'arxiu del grub amb la comanda "nano /etc/default/grub". Els paràmetres GRUB_TIMEOUT_STYLE=hidden i GRUB_TIMEOUT=0  han d'estar coments i el paràmetre GRUB_DISABLE_OS_PROBER=false sense comentar.

<img width="843" height="284" alt="image" src="https://github.com/user-attachments/assets/e1e59fbf-86ea-468f-b358-7f469f587d5c" />

Guardem l'arxiu i ja podem apagar la màquina i treiem la ISO de W10 per a iniciar-la i comprovar que podem accedir a ambdos sistemes operatius.

<img width="849" height="374" alt="image" src="https://github.com/user-attachments/assets/500e3534-0172-4c87-80c5-e1c773eb1e81" />



## Punts de restauració

Obrim la màquina virtual i li configurem un nou disc de 15GB.

<img width="858" height="456" alt="image" src="https://github.com/user-attachments/assets/82e85bf3-f444-4c43-9df3-63bb80207024" />




## Configuració de xarxa

## Comandes generals i instal·lacions

# APUNTES BORRAR!!!!!
dia 1
Ubuntu altres 40gb instalar w10 enterprise (meter windows en emmagatzematge) de instalacion solo pantalla particiones, cuenta local unirse a un dominio
si nuevo aplicar no deja instalar es porque no esta activada la efi en los ajustes de vbox 


1 maquina virtual que solo se enciende windows > emmagatz. parametres solo iso supergrub esc > boot > supergrub. segona opcio detect > trobar el linux (el primer) y ya per a iniciar el sistema 
- descargar iso supergrub ftp

sudo su
apt install --reinstall grub-pc (captura)
grub-install /dev/sda (captura)
da error efi
cd /boot
cd efi/ (si no esta mkdir efi)
ls
fdisk -l 
buscar particion sistema efi  por ejemplo /dev/sda6 (captura)
mount /dev/sda6 /boot/efi (captura)
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu (captura)
update-grub  > trobar windows y linux (captura)
apt install efibootmgr
efibootmgr > ves el orden de arranque y si el primero es el windows hay que cambiarlo por el ubuntu (efibootmgr -o 0004,0002 (el orden que sea))
nano etc default grub
  GRUB_TIMEOUT_STYLE=hidden comentada
  GRUB_TIMEOUT=0 comentada 
  descomentada GRUB_DISABLE_OS_PROBER=false
apagamos y quitamos la iso
tiene que salir el grub y probar que funcionen los dos



dia 2 ## Punts de restauració y Configuració de xarxa
abrir maquina virtual ubuntu con adaptador puente
emmagatzematge > controlador sata > afegir disc (crea) 15gb 
iniciem maquina > terminal sudo su
apt install timeshift <img width="879" height="452" alt="image" src="https://github.com/user-attachments/assets/0444a6bb-382d-48d1-a9cf-fb4981e4851c" />

fdisk -l localizar el disco /dev/sdb
crear particion del disco fdisk /dev/sdb intro <img width="690" height="230" alt="image" src="https://github.com/user-attachments/assets/18a3564a-81c3-4d3a-aade-a8e3a8a78d92" />

n per a nova particio > todo intro <img width="884" height="582" alt="image" src="https://github.com/user-attachments/assets/d5f8f458-c954-4e33-b59b-dcf4a33ba197" />
fdisk -l y captura del disco ahora <img width="625" height="256" alt="image" src="https://github.com/user-attachments/assets/c0c33db9-bfb8-4732-a106-3135a20f6062" />

mkfs.ext4 /dev/sdb1 ahora es el formato de la particion <img width="876" height="278" alt="image" src="https://github.com/user-attachments/assets/44c17985-f551-4948-913f-dff29490d169" />

ls
touch hola 
mkdir adeu
ls <img width="860" height="200" alt="image" src="https://github.com/user-attachments/assets/6951cf4c-3c9b-469a-ae15-c3356262ecc6" />

abrir timeshift desde apps
captura rsync <img width="742" height="808" alt="image" src="https://github.com/user-attachments/assets/de2400fe-e11a-4cd9-a479-8883e073999c" />

seleccionar sdb1 (disco q hemos creado para las copias de seg) y captura <img width="750" height="548" alt="image" src="https://github.com/user-attachments/assets/8814fb64-6455-4241-a7d3-f7218d7be9f1" />

marcar arrencada solo y captura <img width="825" height="805" alt="image" src="https://github.com/user-attachments/assets/94db82b3-01de-48b1-bb87-72493f64d966" />

marcar inclou tots del usuari <img width="880" height="528" alt="image" src="https://github.com/user-attachments/assets/7258935a-8777-47aa-8b8f-840f9f67c9fe" />

ahora reiniciamos para ver si va (se crean 10 min despues de iniciar)

creamos una instantanea con timeshift y captura  <img width="849" height="846" alt="image" src="https://github.com/user-attachments/assets/b3471ccc-4d4f-436d-99be-80582ba391d0" />

y otra cap cuando acabe <img width="814" height="838" alt="image" src="https://github.com/user-attachments/assets/6a6f5403-0f01-4479-88c1-c27cbf2d4254" />



cuando este sudo su
ls
rm hola
rm -r adeu
ls

abrir timeshift
seleccionamos y restaura <img width="848" height="751" alt="image" src="https://github.com/user-attachments/assets/1633fc0c-189e-4010-88fd-38f5fd8acb0a" />


ls y deberiamos tener los archivos hola y adeu <img width="764" height="348" alt="image" src="https://github.com/user-attachments/assets/50ee6598-9d90-4d0e-84bd-2a32ba62859e" />


ip A
192.168.203.153

GRAFICAMENTE CAMBIAR Ip <img width="889" height="726" alt="image" src="https://github.com/user-attachments/assets/0453adb8-416c-43cf-b7d2-a646a86000ef" />

ping dns y captura <img width="693" height="241" alt="image" src="https://github.com/user-attachments/assets/fbbb115d-1e92-4b0b-b9b1-910c17ad3721" />

<img width="801" height="306" alt="image" src="https://github.com/user-attachments/assets/35228cfd-8c1e-4884-99ab-3726755ba8f5" />

cd /etc/netplan > ls

modificar 01-network-manager-all.yaml CON NANO
 Y TIENE que quedar asi <img width="589" height="402" alt="image" src="https://github.com/user-attachments/assets/ee34c790-b4e0-4fd7-9516-e0b2c67f098f" />

netplan apply para ver si esta bien <img width="875" height="641" alt="image" src="https://github.com/user-attachments/assets/2ca7d157-6b2f-4efb-a951-ed76a90ca921" />





instalacions
fer video instalacio dun paquet a traves de 


sudo su
apt-cache policy audacity
veiem que no el tenim y nos dice el candidato que nos instalara
queremos una version anterior

cd /etc/apt/preferences
crear nou fitxer y exemple pinning packet moodle
 en el video apt policie tiene que salir la que hemos puesto nosotros



20/10/25

sudo su
apt-cache policy audacity
nos dice que no esta instalado y si hacemos apt istall nos instaka esa version porque hay un candidato
exemple pinning packet moodle
a
apt-cache policy paquet
crear al dkirectori etc apt preferences.d nou arxiu establint altres prioritats
repetimos el apt y comprobamos que hemos cambiado el candidato
- apt install paquet  y veure como se instala el que hemos decidido (4 capturas)

 pinning packet
 

 



 












