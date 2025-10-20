# Proiect Statia Meteo - Stagiile de practica SciFabLab

![first](/images/first.png)

### Ce este statia meteo in miniatura?

Este un proiect DIY educativ, construit integral din piese printate 3D si senzori electronici usor de gasit. Conceputa pentru demonstrartii practice cu elevi de gimnaziu si liceu, aceasta statie reuneste patru module de masurare a conditiilor atmosferice, fiecare ales pentru a evidentia un principiu fizic diferit. **Scopul** sau este de a oferi o experienta interactiva prin care participantii pot explora direct functionarea senzorilor, procesul de colectare a datelor si legatura dintre masuratori si fenomenele meteorologice.

---

## Introducere si descriere generala
#### Statia meteo este alcatuita din patru module de senzori conectate la o unitate centrala:
* **anemometru de viteza vantului**
* **anemometru de directia vantului**
* **termometru si barometru**
* **pluviometru**

![Structura](/images/Structură.png)

---   
   
### Printarea 3D
Statia este aproape in intregime alcatuita din elemente printate 3D. Recomandam printarea in **PETG** pentru echilibrul intre duritatea si rezistenta produsului final si usurinta de printare. Culoarea aleasa a fost **alb** pentru a proteja statia de radiatia solara.  
Fisierele pentru elementele printate 3D se pot gasi in folderul [*STL*](STL).
Fisierul [*Requirements.md*](Requirements.md) contine si o lista de alte materiale necesare pentru completarea asamblarii statiei.

---

## Descrierea elementelor 
### 1. Anemometru de viteza vantului
Este un modul ce foloseste un **magnet** incapsulat intr-o componenta mobila, a carui miscare o detectam cu un senzor de efect Hall.
Astfel, putem numara de cate ori pe minut se roteste elementul cu cele trei cupe ce "prind" vantul.
![windspeed](/images/windspeed.png)   
Fisierele 3D necesare acestui element din statie pot fi gasite in folderul [*STL/Wind Speed*](STL/Wind%20Speed/).

<br/>

### 2. Anemometru de directia vantului
Este un senzor ce foloseste 4 senzori de efect Hall si 4 magneti pentru a detecta pozitia in care este impins elementul senzorului cu forma unei sageti.
![winddirection](/images/winddirection.png)
Fisierele 3D necesare acestui element din statie pot fi gasite in folderul [*STL/Wind Direction*](/STL/Wind%20Direction/).

<br/>

### 3. Pluviometrul
Este palnia ce colecteaza apa provenita de la precipitatii, care produce o oscilatie a unui element mobil ce prezinta un magnet, a carui miscare o inregistram tot cu un senzor de efect Hall.
![pluviometru1](/images/Pluvi1.png)
![pluviometru2](/images/Pluvi2.png)
Fisierele 3D necesare acestui element din statie pot fi gasite in folderul [*STL/Pluvio*](STL/Pluvio/).

<br/>

### 4. Termometru si Barometru 
In interiorul protectiei de tip Stevenson Screen avem doi senzori. Un DHT22 (temperatura si umiditate) si un BMP180 (presiunea aerului si temperatura).
Acesti senzori vor fi lipiti de o extruzie a capacului unitatii centrale, dupa care protectia de tip Stevenson Screen va fi plasata deasupra acestora.
![stevenson](/images/Stevenson.png)

---

## Introducerea unitatii centrale

*"Creierul"* statiei meteo are doua componente principale:
* un RaspberryPi5 de 2 GB ram (alte versiuni sunt de asemenea compatibile. Pentru cerinta verificati [*HomeAssistant*](https://www.home-assistant.io/installation/) )
* Un ESP32

<br/>

RaspberryPi-ul ruleaza un sistem de operare dedicat pentru aplicatii cu senzorii IoT (in special pentru Smart-Home, dar nu si in cazul nostru), numit [HomeAssistant](https://www.home-assistant.io/).
Acesta, dupa instalarea de [ESPHome](https://esphome.io), reuseste sa comunice prin WiFi cu un microcontroller ESP32, care reuseste sa citeasca datele de la fiercare senzor in parte.

<br/>

Cu ajutorul circuitelor a caror structura si asamblare o vom descrie mai jos, aceste doua componente impreuna cu platformele software descrie reusesc sa preia datele de la senzorii statiei si sa ii ofere intr-o interfata grafica accesibila de pe orice dispozitiv cu un browser modern conectat la o retea de internet locala.
