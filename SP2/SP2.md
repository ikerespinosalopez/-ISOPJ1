# 🚀 Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers
## Sistemes de fitxers i particions
  ### Mida sector (és la unitat mínima física on se guarden les dades en un disc, per defecte la mida són 512 bytes i no es pot modificar.)
  ### Mida block (També es pot dir clúster, la seva mida és la unitat mínima lògica on se guarden les dades a nivell de sistema operatiu, per defecte són 4096 bytes [8 sectors] i aquesta mida sí que la podem canviar quan es formateja la partició, i cada partició del disc pot tenir una mida de bloc i un sistema de fitxers diferent.)
  ### Fragmentació interna (és quan els blocs són massa grans per a lo que es vol guardar i es desaprofita espai al disc)
  ### Fragmentació externa (és quan un arxiu no està guardaten blocs consecutius de la memòria i els seus accesos són més lents, i per tant, baixa el rendiment)
  El sistema de fitxers condiciona moltes coses, hi ha molts tipus i cada sistema està optimitzat  per fer unes tasques o altres i cadascun té unes limitacions. Windows -- NTFS/FAT32 Ubuntu -- ext4
  ### Tipus de formateig
    #### Baix nivell (Esborra tot, arixus, sistema de fitxers i intenta reparar sectors defectuosos però es necessiten programes especifics, no e spot fer a travès del SO.)
    #### Mig nivell (Format lento, no borra arxius però si es troba sectors dfectuosos els marca, però no els repara.)
    #### Alt nivell (No es borren els arxius, només s'esborra el sistema de fitxers. Si troba sectors defectuosos els ignora totalment.)
  ### Gestio de particions
  Particions: una partició és un tros físic del disc dur i amb el gparted podem gestionar particions però no podem modificar la mida del bloc.
  Volum: un volum és una capa d'abstracció que es posa damunt de les particions i/o discos.
    #### GPARTED
    <img width="1107" height="420" alt="image" src="https://github.com/user-attachments/assets/515b2cc9-1b74-4bbd-bf11-09f5b93a6d10" />

    #### Comandes
## Gestió de processos
## Gestió d'usuaris i grups i permisos
## Còpies de seguretat i automatització de tasques
## Quotes d'usuari

<img width="834" height="427" alt="image" src="https://github.com/user-attachments/assets/5627f21c-b230-49bf-8ccb-67c99ea04e3b" />

<img width="862" height="535" alt="image" src="https://github.com/user-attachments/assets/a698f0b7-a1b7-4d38-8b06-e6aa9fdcebe9" />

<img width="784" height="485" alt="image" src="https://github.com/user-attachments/assets/488e91cf-9b35-4619-9790-72821b9c2cd7" />
esto de arriba es para sector

lo de abajo es para bloc
<img width="790" height="119" alt="image" src="https://github.com/user-attachments/assets/10c68533-189d-41a3-a588-120d23bec548" />
<img width="802" height="183" alt="image" src="https://github.com/user-attachments/assets/f860d2c5-0ead-4d6c-ab89-9dc99e329575" />

esto para sistema de fitxers 
<img width="803" height="250" alt="image" src="https://github.com/user-attachments/assets/5da20936-6585-4d0f-aacb-efed6d4f92e2" />

esto para gparted
<img width="1107" height="420" alt="image" src="https://github.com/user-attachments/assets/515b2cc9-1b74-4bbd-bf11-09f5b93a6d10" />

esto para comandes
<img width="819" height="298" alt="image" src="https://github.com/user-attachments/assets/7af12abd-f32e-49ca-b0e3-bba73c82b255" />
<img width="807" height="296" alt="image" src="https://github.com/user-attachments/assets/4a22fd1c-7a8f-4ff4-af92-043dd7ba202e" />
<img width="703" height="138" alt="image" src="https://github.com/user-attachments/assets/63bfee4f-9b74-4ff7-b769-c73e532d5b41" />
<img width="771" height="445" alt="image" src="https://github.com/user-attachments/assets/b4a41272-e767-4659-8091-8a4efc4b7b90" />

mode temporal
<img width="810" height="326" alt="image" src="https://github.com/user-attachments/assets/ef951cd5-da97-4b53-b7a9-7ae708eff851" />
<img width="806" height="374" alt="image" src="https://github.com/user-attachments/assets/78b11076-4645-4fa1-ba86-87f72803d544" />
<img width="804" height="261" alt="image" src="https://github.com/user-attachments/assets/826347b9-f4b4-478f-86ae-0daf385f2e04" />

mode definitiu
<img width="806" height="428" alt="image" src="https://github.com/user-attachments/assets/ad4372c2-f4f8-455c-9703-23a89a4850d7" />
<img width="607" height="140" alt="image" src="https://github.com/user-attachments/assets/79b5ab8e-a684-45cc-a825-c5ab37542140" />

fragmentacio externa
<img width="933" height="565" alt="image" src="https://github.com/user-attachments/assets/2e614592-aee5-47e3-8abc-990f3dac8e30" />


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








