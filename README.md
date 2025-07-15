# Arduino GPS + GSM Location Tracker

This project uses a GPS module to read live location coordinates and a GSM module to send these as SMS updates to a predefined mobile number. It is ideal for building simple GPS tracking systems, asset monitoring, or personal safety devices.

---

## 📝 How it Works
- The Arduino reads NMEA data from the GPS module using `TinyGPS++` to decode it into decimal latitude and longitude.
- Once valid coordinates are obtained, the Arduino sends an SMS with the location details via the GSM module using AT commands.

---

## ⚙️ Hardware Components
- Arduino Uno
- NEO-6M GPS Module
- SIM800L GSM Module (or similar)
- Power supply (recommended >= 2A for stable GSM operation)
- Jumper wires

---

## 🔌 Arduino Pin Connections
| Module | Pin | Arduino Pin |
|--------|-----|-------------|
| **GPS** | TX  | 4 |
|         | RX  | 3 |
| **GSM** | TX  | 7 |
|         | RX  | 8 |

*(Using SoftwareSerial to create two UART ports.)*

---

## ⚡ Important Notes on Power
- **SIM800L requires stable 3.7V-4.2V at ~2A peak current.**  
  Use a LiPo battery or a dedicated buck converter (not USB alone).  
- If GSM module resets often, it means insufficient current.  
- GPS draws less (~20mA) and can run on Arduino 5V.

---

## 📚 Libraries Used
- [`TinyGPS++`](https://github.com/mikalhart/TinyGPSPlus) for decoding GPS NMEA strings.

To install:
1. Open Arduino IDE
2. Go to **Sketch > Include Library > Manage Libraries**
3. Search `TinyGPS++` and install.

---

## 🚀 Usage
1. Update the phone number inside `sendSMS()` in your sketch:
   ```cpp
   gsmSerial.println("AT+CMGS=\"+91XXXXXXXXXX\"");
