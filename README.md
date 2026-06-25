# HA-Smart-Box
Home Assistant ESP32-S3 Smart Box Project

[Magyar verzió](README_HU.md)

<img width="330" height="240" alt="image" src="https://github.com/user-attachments/assets/e1502775-6c5c-41b7-819a-0000c0a53b1c" />
<img width="280" height="240" alt="image" src="https://github.com/user-attachments/assets/86511280-9d4d-4f5f-abb2-ae7e0704b7e7" />
<img width="300" height="240" alt="image" src="https://github.com/user-attachments/assets/24915971-5e9f-4c95-a921-19c18bd15e09" /> </br>

[Video Demo](https://youtu.be/4N20afO6rvo)

## Assembly & Wiring
<img width="200" height="140" alt="IMG_0558" src="https://github.com/user-attachments/assets/5678da20-636b-45ee-b42a-9772d9ffb282" />
<img width="200" height="140" alt="IMG_0555" src="https://github.com/user-attachments/assets/b9324f1d-b1c2-4816-ba04-e596cb3c0fa3" />
<img width="200" height="140" alt="IMG_0556" src="https://github.com/user-attachments/assets/7952407e-6317-4b44-b89a-fabd035f7f74" />
<img width="200" height="140" alt="IMG_0562" src="https://github.com/user-attachments/assets/e2fb0770-5d45-463a-872d-58cad6982f41" /> </br>
<img width="120" height="200" alt="image" src="https://github.com/user-attachments/assets/6e8c5773-0a98-401b-8740-5421e1b2bf2d" />
<img width="200" height="140" alt="image" src="https://github.com/user-attachments/assets/c8a1d3e9-ca85-4145-a31b-2d3d384906c5" />

## Home Assistant Dashboard
<img width="230" height="318" alt="image" src="https://github.com/user-attachments/assets/0941120d-035a-4852-a6d4-420fa043747e" />
<img width="245" height="356" alt="image" src="https://github.com/user-attachments/assets/0eb5fc13-57e6-48d5-9ce0-7a63f8d79572" />
<img width="330" height="180" alt="image" src="https://github.com/user-attachments/assets/4a06f154-ce8a-4eb5-8867-de696cf36622" />

## Hardware Components (BOM)
- ESP32-S3 N16R8
- Temperature & Humidity Sensor: DHT22
- Speaker: 3W 4Ω 3525/2535
- Amplifier: MAX98357A
- Display: 1.3" OLED I2C SH1106 128X64
- Push Buttons: 5 pcs
- LED Indicators: 5 pcs (3-6V) with series ballast resistors!
- Rotary Encoder Module with Push Button: 1 pc
- Project Box / Enclosure: 115x90x55 mm 
- Panel Mount USB-C Female Connector --> *Note: only works with USB-A to USB-C cable*
- Programmed via ESPHome

## Features

### 1. LED Indicators
- **Green**  
  *Solid:* If any door or window is open in the house.  
  *Flashing:* The main entrance door is open.  
  *Off:* All doors and windows are closed.
- **Blue**  
  *Solid:* If any light is turned on in the house.  
  *Off:* All lights are turned off.
- **White**  
  *Solid:* Active audio playback is in progress.  
  *Off:* No audio playback.
- **Yellow**  
  *Solid:* Custom system warning/alert is active. Currently monitored conditions:  
  - Proxmox node CPU usage is above 20%  
  - Number of running VMs is below X (set to 3)  
  - Number of running LXCs is below X (set to 5)  
  - Proxmox node updates are available  
  - Any battery-powered sensor's level drops below 20%  
  *Off:* No active system warnings.
- **Red**  
  *Solid:* A tracked person is inside a designated Home Assistant zone (other than "Home").  
  *Flashing:* The tracked person has left a known zone and is currently commuting.  
  *Off:* The tracked person is at home.

### 2. Physical Buttons
- **Green Button:** TTS announcement of exactly which doors and/or windows are open (or confirms everything is closed).  
- **Blue Button:** TTS announcement of exactly which rooms have lights on (or confirms all lights are off).  
- **White Button:** Starts the pre-set radio station and automatically switches the screen to the Radio tab.  
- **Yellow Button:** TTS announcement of active system warnings/alerts (or confirms no alerts).  
- **Red Button:** TTS announcement of the tracked person's current status (current zone, commuting, or at home).
- **Rotary Encoder:** Turn left/right to navigate the menu or adjust values. Press to enter a menu or select an option (detailed in the Display section).

### 3. Display Interface
The OLED display menu is divided into 5 screens. Use the rotary encoder to navigate left or right. Each page displays the current Wi-Fi signal strength icon in the top right corner.

📌 **Main Screen**  
Displays the current time and date. The bottom row shows the temperature and humidity readings from the built-in DHT22 sensor.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/a864b98b-7922-43bc-96e5-c57c9583c986" />

📌 **Volume Control**  
Adjusts the volume of the built-in I2S media player. It stays synchronized with the volume level in Home Assistant and also works offline. Press the rotary encoder button to enter/exit adjustment mode, where a graphical slider shows the current volume level.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/e9f787e0-bd04-4d34-a85b-cd14208456d2" />
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/947713a8-703f-438e-a53e-5f73181046fb" />

📌 **Radio**  
Press the rotary encoder button to play the radio station shown on the screen. Long press to open the station selection menu. To exit the selection menu, long press again or wait for 5 seconds of inactivity.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/79a18749-8b2b-417c-8d52-c7019b72e1de" />
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/c6c8f841-61b7-4e8a-87bc-c701e692d06a" />
<img width="38dfe362-c181-48f4-ad65-35c618cdf4db" />

📌 **Temperature**  
Displays the temperature from the built-in DHT22 sensor alongside an external Zigbee sensor integrated through Home Assistant.  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/eb98657e-2ad8-4e7c-835d-87aab74443f2" />

📌 **System Status**  
- Home Assistant system uptime  
- Proxmox Node CPU usage  
- Number of available Proxmox updates  
- Number of running VMs / LXC containers  
<img width="200" height="100" alt="image" src="https://github.com/user-attachments/assets/1d0992dd-f408-49b8-a314-e087b6b3cf85" />
