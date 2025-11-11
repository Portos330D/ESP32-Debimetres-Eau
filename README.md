
# 💧 ESP32 – Débitmètres Eau (Maison / Garage / Cumulus)

Suivi précis de la consommation d’eau avec un ESP32 et des débitmètres YF-B5 / YF-B6 / YF-S201.

## 📺 Tutoriel vidéo
> [Installer ESPHome sur Home Assistant et flasher un ESP32](https://youtu.be/3GbyYQHQvV8?si=5LLoGJLGmdWvFfUk)
>
## 🧰 Matériel utilisé (Hardware)

Voici la liste complète des composants utilisés pour reproduire le projet **Débitmètres Eau ESP32 – Maison / Garage / Cumulus**.

| Élément | Description | Lien |
|----------|--------------|------|
| 🧠 **ESP32 DevKit v1 (38 broches)** | Carte microcontrôleur utilisée pour le traitement et la communication avec Home Assistant via ESPHome | [AliExpress](https://a.aliexpress.com/_EJcmddO) |
| 💧 **Débitmètre YF-B5 / YF-B6 / YF-S201** | Capteurs à effet Hall mesurant le débit d’eau par impulsions. Un capteur par zone (Maison, Garage, Cumulus) | [AliExpress](https://a.aliexpress.com/_Exk3gqM) |
| 🔌 **Connecteurs / câbles Dupont + alimentation 5V stable** | Pour relier les débitmètres à l’ESP32 (alimentation + signal) | [AliExpress](https://a.aliexpress.com/_EuTxiIc) |
| 🧱 **Boîtier 3D ESP32 – 38 pin Snap Fit Case** | Boîtier imprimé en 3D (version testée par Jérémy). Permet une installation propre et sécurisée de l’ESP32 | [Printables.com – ESP32 38 Pin Breakout Case](https://www.printables.com/model/739842-esp32-38-pin-breakout-board-case-snap-fit-lid) |

> ⚙️ **Astuce :**  
> - Le VCC des débitmètres est branché sur le **5V (VIN)** de l’ESP32.  
> - Le GND est commun.  
> - Les signaux sont reliés aux **GPIO13**, **GPIO14** et **GPIO19**, avec `mode: INPUT_PULLUP` activé dans le code ESPHome.

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

## 📸 Illustrations & Montage

Quelques photos du montage final pour aider à la reproduction du projet :

| Illustration | Description |
|---------------|-------------|
| ![ESP32 dans son boîtier](images/boitier_esp32.jpg) | L’ESP32 DevKit v1 installé dans le boîtier 3D (Printables). Connexions via borniers latéraux, alimentation 5V et câbles Dupont. |
| ![Câbles connecteurs](images/cable_dupont_1.jpg) | Exemple de câbles Dupont 4 fils utilisés pour raccorder les débitmètres. |
| ![Connecteurs rapides](images/cable_dupont_2.jpg) | Connecteurs rapides avec détrompeur pour éviter les inversions de polarité. |

## 📊 Aperçu du tableau de bord Home Assistant

Voici un aperçu du tableau de bord complet permettant de suivre en temps réel les débits et consommations d’eau (Maison, Garage, Cumulus).

| Capture | Description |
|----------|--------------|
| ![Aperçu Home Assistant - Partie 1](images/apercu_1.png) | Affichage des débits instantanés, de la consommation journalière et du suivi hebdomadaire/mensuel/annuel avec indicateurs colorés et graphiques. |
| ![Aperçu Home Assistant - Partie 2](images/apercu_2.jpg) | Vue complémentaire avec graphique des 7 derniers jours, récapitulatif Utility Meters et estimation automatique des coûts journaliers/mensuels/annuels. |

> 🧩 Ces cartes utilisent uniquement des cartes standard de Home Assistant :  
> `gauge`, `entities`, `history-graph`, et `apexcharts-card` (facultatif).  
> Aucun module HACS requis.

## 📁 Structure du projet

L’organisation du dépôt permet une intégration rapide dans Home Assistant et ESPHome.

ESP32-Debimetres-Eau/
├── README.md # Documentation complète du projet
├── LICENSE # Licence MIT (libre et ouverte)
├── SECRETS_EXAMPLE.yaml # Exemple de fichier secrets.yaml
├── /esphome/ # Code ESPHome à flasher sur l’ESP32
│ └── debitmetres-mgc.yaml
├── /homeassistant/ # Fichiers à intégrer dans Home Assistant
│ └── utility_meter.yaml
└── /images/ # Illustrations du montage et aperçus HA
├── boitier_esp32.jpg
├── cable_dupont_1.jpg
├── cable_dupont_2.jpg
├── apercu_1.png
└── apercu_2.jpg

yaml
Copier le code

> 🧩 **Conseil :**  
> - Copie le fichier `debitmetres-mgc.yaml` dans ton répertoire ESPHome.  
> - Adapte ton `secrets.yaml` avec ton Wi-Fi.  
> - Ajoute `utility_meter.yaml` dans ton dossier Home Assistant.  
> - Puis redémarre Home Assistant pour voir les capteurs apparaître.
```
