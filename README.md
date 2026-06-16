
# HA-Smart-Box
Home Assistant ESP32-S3 Smart Box Project

<img width="400" height="280" alt="IMG_0562" src="https://github.com/user-attachments/assets/e2fb0770-5d45-463a-872d-58cad6982f41" />  </br>
<img width="200" height="140" alt="IMG_0558" src="https://github.com/user-attachments/assets/5678da20-636b-45ee-b42a-9772d9ffb282" />
<img width="200" height="140" alt="IMG_0555" src="https://github.com/user-attachments/assets/b9324f1d-b1c2-4816-ba04-e596cb3c0fa3" />
<img width="200" height="140" alt="IMG_0556" src="https://github.com/user-attachments/assets/7952407e-6317-4b44-b89a-fabd035f7f74" />



## Felépítés
- Hőmérséklet/páratartalom: DHT22
- Hangszóró: 3W 4Ω
- Amp: MAX98357A
- Kijelző: 1,3" OLED I2C
- Nyomógomb: 5 db
- LED visszajelző: 5 db
- Nyomógombos rotary enkóder modul: 1 db
- Box: 115x90x55 mm

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
  
