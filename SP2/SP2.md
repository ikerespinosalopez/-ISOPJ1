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
