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
    #### GPARTED
    #### Comandes
## Gestió de processos
## Gestió d'usuaris i grups i permisos
## Còpies de seguretat i automatització de tasques
## Quotes d'usuari

<img width="834" height="427" alt="image" src="https://github.com/user-attachments/assets/5627f21c-b230-49bf-8ccb-67c99ea04e3b" />
