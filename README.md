## ATTENTION

A lire attentivement : https://docs.google.com/document/d/1IeKgfE2WIDjqH1fx5Yg7n1FOHVwhDFmDlZ-7QMlOEV0/edit?fbclid=IwAR3gCoyRlxSNaZfyHNV_BgGn1apJKmvagmzduOfGGYjY7I8kDBUVAuLyIi4

Si vous aimez mon travail, n'hésitez pas à me soutenir en me payant une 🍺 ou un ☕. Merci 🙂

 [ ![Download](https://user-images.githubusercontent.com/12702322/115148445-e5a40100-a05f-11eb-8552-c1f5d4355987.png) ](https://www.paypal.me/CyrilGuislain)


![GitHub](https://img.shields.io/github/license/marlinfirmware/marlin.svg)
[![Build Status](https://github.com/MarlinFirmware/Marlin/workflows/CI/badge.svg?branch=bugfix-2.0.x)](https://github.com/MarlinFirmware/Marlin/actions)

<img align="left" width=600 src="https://user-images.githubusercontent.com/12702322/116473468-7b693880-a877-11eb-8783-5eccf0b5fbc0.jpg" />
<img align="right" width=175 src="buildroot/share/pixmaps/logo/marlin-250.png" />

<br /><br /><br /><br /><br /><br /><br /><br />

**Firmware Marlin 2.0.9.1 bugfix configuré pour FLSUN Super Racer avec carte mère BigTreeTech SRK 2.0 Rev B.**

Le firmware pour écran BigTreeTech TFT70 3.0 est disponible [ici](https://github.com/Guilouz/BTT-TFT70-SuperRacer).

<br />

Les fichiers STL nécessaires sont disponibles dans le dossier "_STL" [ici](https://github.com/Guilouz/Marlin-SuperRacer-SKR2.0-LGX/tree/main/_STL).

<br />

## Schema de câblage :

![FLSUN SuperRacer SKR2](https://user-images.githubusercontent.com/12702322/128229118-0e99d567-2a6f-4fc2-8bfe-600c4e845f50.png)

## Principales fonctionnalités configurées :

- Support carte mère BigTreeTech SKR 2.0 Rev B
- Support extrudeur Bondtech LGX
  - Si extrudeur stock, définissez ces valeurs :
  - Dans Configuration.h : `#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 80, 415 }`
  - Dans Configuration.h : `#define INVERT_E0_DIR`
  - Dans Configuration_adv.h : `#define E0_CURRENT      950`
- Support drivers TMC2209/TMC2226 UART
- Support écrans BigTreeTech
- Support Bed Leveling Bilinear 9 x 9 points
- Support M600 & Nozzle Park / Advanced Pause
- Support Babystepping
- Support du contrôle du ventilateur de la carte mère
- Support Neopixels (j'utilise cet anneau de LED : [ici](https://fr.aliexpress.com/item/1005002090765807.html?spm=a2g0s.9042311.0.0.56d46c37lqhfaf))
- Support EEPROM
- Support PID Buse & Plateau
- Support protection thermique contre l'emballement
- Support S-Curve Acceleration
- Support de la compensation d'inclinaison du plateau (https://www.thingiverse.com/thing:2563185)
- Support G26 - Mesh Validation Pattern
- Support G33 - Delta Auto Calibration
- Support du transfert de fichier binaire (transfert du fichier firmware à distance via Octoprint)
- Support de l'extinction de la chauffe après 15 minutes d'inactivité de la hotend
- support des commandes d'action de l'hôte
- Activation du ventilateur de la hotend uniquement quand la chauffe dépasse 50°C
- Prise en charge de plusieurs volumes (microSD & USB)
- Prise en charge du partage multimédia USB
- Optimisation du buffer pour Octoprint
- Marlin en français

## Procédure d'installation :

- Effectuez un reset EEPROM avant flash du nouveau firmware (commande M502 suivi de la commande M500 ou via l'écran TFT).
- Copiez le fichier `firmware.bin` à la racine de la carte microSD (capacité max de 32Go, formatée en FAT32, taille d'unité d'allocation 4096).
- Imprimante éteinte, insérez la carte microSD dans le port dédié sur la carte mère et allumez l'imprimante.
- La procédure de flash démarre (sans rien afficher à l'écran) et dure quelques secondes.
- Vérifiez le contenu de la carte microSD, le fichier `firmware.bin` a été renommé en `FIRMWARE.CUR` ce qui indique que le flash s'est bien déroulé.
- Effectuez de nouveau un reset EEPROM (commande M502 suivi de la commande M500 ou via l'écran TFT).
- Lancez un PID Buse & Plateau depuis les paramètres de l'écran.
- Lancez une calibration de l'extrudeur depuis les paramètres de l'écran.
- Lancez une calibration Delta depuis les menus de l'écran.
- Lancez un auto-nivellement depuis les menus de l'écran.

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
