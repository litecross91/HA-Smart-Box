
# HA-Smart-Box
Home Assistant ESP32-S3 Smart Box Project

<img width="330" height="240" alt="image" src="https://github.com/user-attachments/assets/e1502775-6c5c-41b7-819a-0000c0a53b1c" />
<img width="280" height="240" alt="image" src="https://github.com/user-attachments/assets/86511280-9d4d-4f5f-abb2-ae7e0704b7e7" />
<img width="300" height="240" alt="image" src="https://github.com/user-attachments/assets/24915971-5e9f-4c95-a921-19c18bd15e09" /> </br>
[Videó](https://youtu.be/4N20afO6rvo)


## Szerelés
<img width="200" height="140" alt="IMG_0558" src="https://github.com/user-attachments/assets/5678da20-636b-45ee-b42a-9772d9ffb282" />
<img width="200" height="140" alt="IMG_0555" src="https://github.com/user-attachments/assets/b9324f1d-b1c2-4816-ba04-e596cb3c0fa3" />
<img width="200" height="140" alt="IMG_0556" src="https://github.com/user-attachments/assets/7952407e-6317-4b44-b89a-fabd035f7f74" />
<img width="200" height="140" alt="IMG_0562" src="https://github.com/user-attachments/assets/e2fb0770-5d45-463a-872d-58cad6982f41" /> </br>
<img width="120" height="200" alt="image" src="https://github.com/user-attachments/assets/6e8c5773-0a98-401b-8740-5421e1b2bf2d" />
<img width="200" height="140" alt="image" src="https://github.com/user-attachments/assets/c8a1d3e9-ca85-4145-a31b-2d3d384906c5" />

## Home Assistant
<img width="230" height="318" alt="image" src="https://github.com/user-attachments/assets/0941120d-035a-4852-a6d4-420fa043747e" />
<img width="245" height="356" alt="image" src="https://github.com/user-attachments/assets/0eb5fc13-57e6-48d5-9ce0-7a63f8d79572" />


## Felépítés
- ESP32-S3 N16R8
- Hőmérséklet/páratartalom szenzor: DHT22
- Hangszóró: 3W 4Ω 3525/2535
- Amp: MAX98357A
- Kijelző: 1,3" OLED I2C SH1106 128X64
- Nyomógomb: 5 db
- LED visszajelző: 5 db (3-6V) előtét ellenállással!
- Nyomógombos rotary enkóder modul: 1 db
- Műszerdoboz: 115x90x55 mm 
- USB-C beépíthető anya csatlakozó --> csak USB-A/USB-C kábellel működik
- Programozás ESPHome-on keresztül

## Funkciók
### 1. LED-ek
- **Zöld**  
  *Világít:* Ha a lakásban nyitva van egy ajtó vagy ablak.  
  *Villog:* Bejárati ajtó nyitva van.
  *Kialszik:* Nincs nyitva se ajtó, se ablak
- **Kék**  
  *Világít:* Ha a lakásban világít egy lámpa.
  *Kialszik:* Nem világít lámpa
- **Fehér**  
  *Világít:* Ha a bármilyen hang lejátszás folyamatban van.
  *Kialszik:* Nincs lejátszás folyamatban
- **Sárga**  
  *Világít:* Ha egy rendszer hibajelzés aktív. Ezeket én definiáltam.  
  - Proxmox node CPU használat 20% fölött  
  - Futó VM-ek száma X (nekem 3) alatt van  
  - Futó LXC-k száma X (nekem 5) alatt van  
  - Node frissítés érhető el  
  - Bármelyik elemes szenzorban az elem állapota 20% alatt van

  *Kialszik:* Nincs aktív hibajelzés.
- **Piros**  
  *Világít:*  Ha egy beállított személy, egy HA-ban megadott zónán belül van, ami nem az otthon.  
  *Villog:* Ha az adott személy elhagyja az ismert zónát.  
  *Kialszik:* Otthon van az adott személy

  
### 2. Gombok
- **Zöld:** Felolvassa, hogy pontosan melyik ajtó és/vagy ablak van nyitva VAGY nincs nyitva semmi.  
- **Kék:** Felolvassa, hogy pontosan melyik helyiségben világít lámpa VAGY nem világít semmi.  
- **Fehér:** Elindítja az előre beállított rádiót és a kijelző a Rádió lapra ugrik.  
- **Sárga:** Felolvassa, hogy pontosan milyen aktív rendszer riasztás van VAGY nincs aktív riasztás.  
- **Piros:** Felolvassa, hogy a beállított személy éppen melyik zónában van VAGY úton van VAGY otthon van.
- **Rotary Enkóder:** Jobbra/balra tekerésre lépkedés a menüben vagy beállítás/érték módosítás. Nyomásra menüben mélyebbre lépés. Kijelzőnél részletezem.

  
### 3. Kijelző
A kijelző menüjét jelenleg 5 lapra osztottam. A rotary enkóder segítségével lehet balra vagy jobbra váltani az oldalakat. 
Jobb felül minden lapon mutatja a wifi jelet, annak erősségének megfelelő vonalakkal.  

**Fő képernyő**  
Óra és dátum kijelzés. Alul pedig a DHT szenzor hőmérséklet és páratartalom kijelzése.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/a864b98b-7922-43bc-96e5-c57c9583c986" />

**Hangerő**  
A beépített I2S media lejátszó hangerejét szabályozhatjuk. Szinkronban üzemel a HA-ban látott értékkel. Offline is működik.  
Rotary gombnyomásra léphetünk be/ki az állítás módba, ahol grafikus csúszka is mutatja a hangerő állását.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/e9f787e0-bd04-4d34-a85b-cd14208456d2" />
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/947713a8-703f-438e-a53e-5f73181046fb" />

**Rádió**  
Rotary gombnyomásra elindítja a kijelzőn látható rádiót. Hosszú nyomásra lehet kiválasztani az állomást. Ebből a választó menüből hosszú nyomásra kilép vagy 5 másodperc tétlenség után.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/79a18749-8b2b-417c-8d52-c7019b72e1de" />
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/c6c8f841-61b7-4e8a-87bc-c701e692d06a" />
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/38dfe362-c181-48f4-ad65-35c618cdf4db" />

**Hőmérséklet**  
Mutatja a DHT22 szenzor értékét (beépített) és egy HA-ben lévő zigbee-s szenzor (külső) értékét.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/eb98657e-2ad8-4e7c-835d-87aab74443f2" />

**Rendszer**  
- HA rendszer futási ideje  
- Proxmox Node CPU használata  
- Proxmox frissítések száma  
- Futó VM-ek/LXC-k száma  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/1d0992dd-f408-49b8-a314-e087b6b3cf85" />



