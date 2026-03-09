# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor
Aquesta part la fa Manu
## Directoris importants
Fer teoria rendiment
MOnitor del sistema fer captures i explicar

## Logs
En aquest directori podem trobar els principals logs del sistema, hi ha serveis que tenen els logs a les seves pròpies carpetes.
<img width="874" height="428" alt="image" src="https://github.com/user-attachments/assets/19e710a6-4696-4839-b9b7-ead2babbf5ae" />

Si fem un cat del syslog podem veure tots els registres.
<img width="896" height="840" alt="image" src="https://github.com/user-attachments/assets/d573461f-a614-4ce6-9f68-6587d14971f7" />

En aquest directori podem personalitzar la rotació de logs
<img width="880" height="161" alt="image" src="https://github.com/user-attachments/assets/39801082-04b9-40c3-99dd-7fcc368e5c30" />

Explicar això !!!
<img width="881" height="435" alt="image" src="https://github.com/user-attachments/assets/87a554f3-4145-479b-abaa-6c05d754900a" />

explicar 
<img width="879" height="793" alt="image" src="https://github.com/user-attachments/assets/318c3bd2-6c4d-4323-bc11-453c60551a91" />

<img width="897" height="551" alt="image" src="https://github.com/user-attachments/assets/9e9852a0-eb79-41b7-b23e-c5d7d9096ad4" />

Modifiquem l'arxiu
<img width="888" height="470" alt="image" src="https://github.com/user-attachments/assets/d9f2deea-8640-4640-8ec4-ffe80f901b8d" />

Reiniciem el servei syslog amb systemctl restart syslog
<img width="889" height="576" alt="image" src="https://github.com/user-attachments/assets/d0298008-cddb-4b83-acc8-8d1bec6bb506" />

<img width="895" height="835" alt="image" src="https://github.com/user-attachments/assets/c08acabb-b590-4315-8a31-bb8e3189f0f0" />

<img width="896" height="731" alt="image" src="https://github.com/user-attachments/assets/134a2b26-a034-4a3f-a734-73da900feec9" />

<img width="885" height="344" alt="image" src="https://github.com/user-attachments/assets/135ec7e2-2845-44e6-98b3-5fed5400f7c2" />

<img width="886" height="596" alt="image" src="https://github.com/user-attachments/assets/274c28a2-7377-40a6-902b-5a42b83bd913" />

<img width="882" height="353" alt="image" src="https://github.com/user-attachments/assets/6e280b6a-57ca-4d2e-a07d-fed651670bd9" />

<img width="884" height="586" alt="image" src="https://github.com/user-attachments/assets/23e84852-15c3-4d57-9de9-d32770eb7ec3" />

<img width="883" height="410" alt="image" src="https://github.com/user-attachments/assets/d2d46daf-b09e-4bea-92f5-7ecea96eb5a2" />

<img width="768" height="133" alt="image" src="https://github.com/user-attachments/assets/e9ed66b4-a465-4f0f-800b-7b5e4eb7a0e1" />

Fer exercici: dos maquines ubuntus i una ha de rebre els logs de l'altre, a part de que s'envii a la propia maquina


## Servidor d'actualitzacions
Explicar lo que es

Primer instal·lem el paquet apache2 a la nostra màquina servidor.
<img width="646" height="24" alt="image" src="https://github.com/user-attachments/assets/81c1fb4d-8bf8-460c-aa5e-30cad856b13c" />

A continuació instal·lem apt-mirror.
<img width="662" height="26" alt="image" src="https://github.com/user-attachments/assets/8053f08e-babb-4235-a502-80da1a927529" />

Desprès modifiquem l'arxiu /etc/apt/mirror.list per a afegir els repositoris que anem a descarregar. Primer comentem els repositoris que tenen i afegim una línia nova amb el repositori de Google Chrome.
<img width="695" height="25" alt="image" src="https://github.com/user-attachments/assets/117158fd-1b9b-4a73-809d-ad6b9d463df9" />
<img width="867" height="500" alt="image" src="https://github.com/user-attachments/assets/318b6581-7003-4798-b531-a751f0a2696d" />

Ara executem la comanda apt-mirror.
<img width="885" height="788" alt="image" src="https://github.com/user-attachments/assets/1bb836ea-89cc-466c-b085-dd09852b3325" />

Anem a configurar apache per a poder compartir-lo amb el client. Accedim a la següent ruta:
<img width="880" height="37" alt="image" src="https://github.com/user-attachments/assets/b9c3fd89-d377-4277-8f12-307cfd095ecc" />

I fem un soft link.
<img width="882" height="41" alt="image" src="https://github.com/user-attachments/assets/d598d4ec-f44b-4bce-93d5-1770ee739855" />
<img width="880" height="69" alt="image" src="https://github.com/user-attachments/assets/b2fc8b14-fe73-4f85-be23-450755f5e3bb" />


Anem a configurar el client, primer editem l'arxiu /etc/apt/sources.list i afegim una línia indicant la IP del nostre servidor i el paquet.
<img width="779" height="78" alt="image" src="https://github.com/user-attachments/assets/37ecd592-e497-4156-8d13-d17149c75b01" />

Afegim una clau.
<img width="885" height="110" alt="image" src="https://github.com/user-attachments/assets/cad6b92f-871d-4d0c-aedd-74b13c483fcd" />

Fem un apt update i podem comprovar que agafa el paquet del servidor.
<img width="884" height="339" alt="image" src="https://github.com/user-attachments/assets/1a4ef806-043a-4fc8-82ef-9fbeb75329b4" />

Instal·lem chrome i comprovem que es descarrega des del servidor.
<img width="885" height="328" alt="image" src="https://github.com/user-attachments/assets/21c63d84-fce4-4e84-b643-6e06f259d7d7" />
<img width="799" height="263" alt="image" src="https://github.com/user-attachments/assets/1a284bd5-9a30-4d3b-a381-9dbad1238605" />


Ara repetim el procès amb un altre paquet. En aquest cas VSCode. EL primer pas serà obtenir la clau amb aquesta comanda:
<img width="875" height="65" alt="image" src="https://github.com/user-attachments/assets/f13804ee-c090-47f7-8c47-002da762084c" />

Afegim al servidor la línia indicant on es troba el paqeut per a descarregar.
<img width="1374" height="401" alt="image" src="https://github.com/user-attachments/assets/b9e80368-ae3b-4230-af30-fadd3bcd1b84" />

Fem un apt-mirror de nou amb el repsoitori ja afegit:
<img width="878" height="662" alt="image" src="https://github.com/user-attachments/assets/470ed1a0-124b-4a7d-8abc-4040606efcf2" />

Anem al client i afegim una nova línia com la que hem fet abans a /etc/apt/sources.list indicant la IP del servidor i on es troba el paquet.
<img width="789" height="137" alt="image" src="https://github.com/user-attachments/assets/eb7ac970-3f4a-44e4-a48b-db355c740763" />

