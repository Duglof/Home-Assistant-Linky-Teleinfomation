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

# Etape 1 : Installation de Home Assistant V16.2
- 1 Positionner le flag boot from USB de la Raspberry 3B
- 2 Graver l'image de haos sur le disque SSD
- 3 Retirer la carte SD de la Raspberry 3B
- 4 Connecter le disque SSD sur la Raspberry 3B
- 5 Mettez sous tension : ça boote directement sur haos
  - Les logs de boot s'affichent sur l'écran connecté à la Raspberry 

# Etape 2 : Configurer Home Assistant
- Depuis http://homeassistant.local:8123
