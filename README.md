# Home-Assistant-Linky-Teleinfomation
 Linky Téléinformation pour Home Assistant avec ESPHOME

 Pour pouvoir ajouter simplement des modules complémentaires, prennez image contenant:
 - HA Operating System
 - Home Assitant
 - Supervisor
 
# Environnement matériel (configuration minimale)
- Boitier X820-C6 : Metal Case Kit
- Raspberry 3B
- X820 V3.0 2.5" SATA HDD/SSD Shield
- Disque SSD 120GB 
- Une carte SD 32 giga
- Un adaptateur SD USB
- Un écran HDMI à connecter sur la Raspberry 3B
- Un clavier USB à connecter sur la Rasberry 3B
- Un cable réseau pour connecter la Rasberry 3B sur votre réseau local

# Environnement logiciel de test
- Raspberry OS Lite 64 bits
- Home Assitant  V16.2 : haos_rpi3-64-16.2.img.xz
  - https://github.com/home-assistant/operating-system/releases/download/16.2/haos_rpi3-64-16.2.img.xz

# Outils nécessaires
- Ordinateur personnel connecté sur votre réseau local
  - Pour graver l'image haos_rpi3-64-16.2.img.xz sur le SSD
  - Pour accéder à l'interface Web de Home Assistant
  - Pour accéder à l'interface web de votre module ESPHOME
  - Test fait avec Linux Mint V22
- Interface SATA USB pour connecter le SSD sur l'ordinateur
- Logiciel pour transférer l'image : Balena Etcher

# Matériel 1 : ESP32 dev kit
- Vous pouvez utiliser un autre modèle mais il faudra changer la déclaration esp32-linky.yaml
  - esp32:
    - board: xxxx
- Type WROOM 32 avec 4 Mo de flash (30 broches)
![esp32 cp2102](docs/ESP32S-30P-CP2102-MicroUSB.png) 
![esp32 gpio](docs/ESP32-dev-kit-30pins-pinout.png)

# Matériel 2 : Linky Interface
![interface linky](docs/schema-interface-linky.png)
Attention, les BS170 que j'ai reçu avait un brochage inversé S-G-D (au lieu de D-G-S) ça ne fonctionnait pas !!!
- C'est reconnaissable, la tension entre Drain et Source était de 0,6V alors que la grille était à zéro.

Pour un linky en mode <b>standard</b>, il faut peut être passer la valeur de la résistance <B>R1 à 1k</b>.

ESP (ESP8266 or ESP32) Input specifications (Entrée Teleinfo):
- Niveau bas : Tension inférieure à Vil (max) = 0.25 * 3.3 = 0.825V
- Niveau Haut : Tension supérieure à Vih (min) = 0.75 * 3.3 = 2.475V

Test de l'interface:
- La LED TIC doit être éteinte (Tension en Drain et Source environ 3.3 Volts)
- En reliant l'entrée 1 à GND et 2 à 3.3V la LED TIC doit s'allumer (Tension en Drain et Source environ 0 Volt)
- Avec une tension variant entre 0V et 3.3V on respecte bien les spécifications ESP

Connexions au compteur Linky (il n'y a pas de sens, on peut inverser)
- Connecter Teleinfo 1 et sur I1 du compteur
- Connecter Teleinfo 2 et sur I2 du compteur

Connexions à Serial2 de ESP32 WROOM
- GND : GND de ESP (GND) 
- +V  : 3V  de ESP (3.3V)
- RXD : Entrée Teleinfo de l'ESP (esp32-linky.yaml uart_pin: GPIO16)

# Etape 1 : Installation de Home Assistant V16.2
- 1 Positionner le flag boot from USB de la Raspberry 3B
- 2 Graver l'image de haos sur le disque SSD
- 3 Retirer la carte SD de la Raspberry 3B
- 4 Connecter le disque SSD sur la Raspberry 3B
- 5 Mettez sous tension : ça boote directement sur haos
  - Les logs de boot s'affichent sur l'écran connecté à la Raspberry 

# Etape 2 : Configurer Home Assistant
- Depuis http://homeassistant.local:8123
