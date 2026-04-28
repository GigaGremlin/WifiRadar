# 📡 WifiRadar
### ESP8266 Wifi Radar – Vermeide ZigBee & Bluetooth Störungen

<div align="left">
  <img width="45%" alt="1" src="https://github.com/user-attachments/assets/d9080e12-7a63-424b-9f7a-cc5a621ae569" />
  <img width="45%" alt="2" src="https://github.com/user-attachments/assets/ccf34104-74bf-47b6-8397-aadeadea6add" />
</div>
  <p><em>Mein preiswerter, kleiner, offline Wifi-Präsenzmelder mit 3D-gedrucktem Halter.</em></p>
</div>

---

## 📖 Über dieses Projekt
Ich verwende einen **LD2410 Radarsensor** in Verbindung mit dem **ESP8266 D1 mini** (kompatibel mit fast allen ESP8266-Boards).

**Warum dieser Aufbau?**
* **Kein Funk-Chaos:** Ich verzichte bewusst auf zusätzliches **ZigBee** oder **Bluetooth**, um mein WLAN-Netz nicht weiter zu belasten. ❗
* **Lokale Kontrolle:** Kein „Onlinezwang“ zum Hersteller und keine Cloud-Verzögerung.
* **Speed:** Ich möchte nachts nicht die Treppe hinunterfallen, nur weil ein Cloud-Sensor 8 Sekunden zum Aufwachen braucht. Hier schaltet das Licht sofort! ⚡

> [!TIP]
> Die Bluetooth-Funktion des LD2410 kann nach dem Einschalten über Home Assistant aktiviert werden, um Firmware-Updates einzuspielen oder die Reichweiten-Einstellungen zu debuggen.

---

## 💻 Ressourcen & Hardware

### Downloads
* 📥 [**Firmware / Konfiguration**](Firmware/)
* 📥 [**3D-Druck Dateien**](3D-Files/)

### Hardware-Links
* 🖥️ [HLK-LD2450 Produktdetails](https://hlktech.net/index.php?id=1157)

---

## 🛠️ Installations-Checkliste

Stelle sicher, dass deine Hardware korrekt verkabelt ist:

* **Verdrahtung:** Der `OUT`-Pin des Radars geht an **D1 (GPIO5)**.
* **UART:** Wie im Skript hinterlegt: `TX` (Radar) ➔ `RX` (D1 Mini / GPIO3) und `RX` (Radar) ➔ `TX` (D1 Mini / GPIO1).
* **Stromversorgung:** Der LD2410 benötigt eine stabile Spannung. **VBUS/5V** ist meist am sichersten, da der ESP8266 beim Senden von WLAN-Daten Stromspitzen erzeugt.

### YAML-Anpassung
Falls der Sensor dauerhaft "Anwesend" anzeigt oder invertiert reagiert, kannst du die Logik im Code einfach umkehren:

```yaml
binary_sensor:
  - platform: gpio
    pin: 
      number: GPIO5
      inverted: false # Hier auf 'true' ändern, falls Logik falsch herum
      mode: INPUT_PULLUP
    name: "Anwesenheit via OUT-Pin"
    device_class: presence
```
</div></div>   
Viel Erfolg beim Löten! Wenn der Sensor erst mal stabil läuft, ist der LD2410 (besonders mit der Distanz-Auswertung über UART)<br>
ein echtes Upgrade für jedes Smart Home.

---

<div align="center">
<i>Zuletzt aktualisiert: April 2026</i>
</div>

</div></div>   
<div align="center">
   <a href="https://gigagremlin.de">
    <img src="https://img.shields.io/badge/Made%20by-GigaGremlin-blue?style=for-the-badge" alt="GigaGremlin Website" />
  </a>
</div>
