
# 💧 ESP32 – Débitmètres Eau (Maison / Garage / Cumulus)

Suivi précis de la consommation d’eau avec un ESP32 et des débitmètres YF-B5 / YF-B6 / YF-S201.

## 📺 Tutoriel vidéo
> [Installer ESPHome sur Home Assistant et flasher un ESP32](https://youtu.be/3GbyYQHQvV8?si=5LLoGJLGmdWvFfUk)

## 🧩 Étapes d’installation
1. Copier `esphome/debitmetres-mgc.yaml` dans ESPHome.
2. Ajouter ton Wi‑Fi dans `secrets.yaml`.
3. Flasher l’ESP32.
4. Ajouter l’appareil détecté dans Home Assistant.
5. Ajouter les fichiers `utility_meter.yaml` dans ton include.

## ⚙️ Calibration
Faire couler 5 L d’eau mesurés et noter les impulsions.
```
pulses/L = total_pulses / volume_en_L
```
Exemple : 1565 pulses pour 5 L → 313 pulses/L.

## 📄 Structure
```
ESP32-Debimetres-Eau/
 ├── README.md
 ├── /esphome/debitmetres-mgc.yaml
 ├── /homeassistant/utility_meter.yaml
 ├── SECRETS_EXAMPLE.yaml
 └── LICENSE
```
