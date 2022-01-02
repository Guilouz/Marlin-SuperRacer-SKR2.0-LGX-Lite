
Si vous aimez mon travail, n'hésitez pas à me soutenir en me payant une 🍺 ou un ☕. Merci 🙂

 [ ![Download](https://user-images.githubusercontent.com/12702322/115148445-e5a40100-a05f-11eb-8552-c1f5d4355987.png) ](https://www.paypal.me/CyrilGuislain)

**Firmware Marlin configuré pour FLSUN Super Racer avec carte mère BigTreeTech SRK 2.0 et extrudeur Direct Drive Bondtech LGX Lite**

<img align="center" width="600" src="https://user-images.githubusercontent.com/12702322/147616087-0f469071-5b6e-46a0-80cc-16946128bd5a.png" />


<br />

<img align="center" width="600" src="https://user-images.githubusercontent.com/12702322/147516889-67b58b86-4929-4c54-921e-f4cf3d9b31af.png" />

<br />

Le firmware pour écran BigTreeTech TFT70 3.0 est disponible [ici](https://github.com/Guilouz/BTT-TFT70-SuperRacer).

<br />

<img align="center" width="600" src="https://user-images.githubusercontent.com/12702322/147615822-f4e13a89-36a5-49a1-b28a-3e4100890941.jpg" />

<br />

## ATTENTION

Lire attentivement ceci pour [SKR 2.0 Rev. A et Rev. B](https://docs.google.com/document/d/1IeKgfE2WIDjqH1fx5Yg7n1FOHVwhDFmDlZ-7QMlOEV0/edit?fbclid=IwAR3gCoyRlxSNaZfyHNV_BgGn1apJKmvagmzduOfGGYjY7I8kDBUVAuLyIi4).

EDIT 06/12/2021 : En raison de la pénurie de composants, BigTreeTech utilise désormait une autre version de processeur `STM32F429VGT6` à la place du `STM32F407VGT6`. Il est donc nécessaire de changer l'environnement dans le fichier `platformio.ini` pour la compilation. Le firmware terminant par `F429` fourni dans la partie <a href="https://github.com/Guilouz/Marlin-SuperRacer-SKR2.0-LGX-Lite/releases">releases</a> est compatible avec cette nouvelle version.

- `default_envs = BIGTREE_SKR_2` <br/>
<img src="https://user-images.githubusercontent.com/12702322/144914479-673edf80-81ff-497d-a279-61d9cbf0199f.jpeg" width="400" /><br/>

- `default_envs = BIGTREE_SKR_2_F429` <br/>
<img src="https://user-images.githubusercontent.com/12702322/144914613-1f89739c-371e-442d-b07d-eaeff1332e45.jpeg" width="400" /><br/>

## Schema de câblage :

![FLSUN SuperRacer SKR2](https://user-images.githubusercontent.com/12702322/128229118-0e99d567-2a6f-4fc2-8bfe-600c4e845f50.png)

![Capture d’écran 2021-12-08 à 00 44 42](https://user-images.githubusercontent.com/12702322/145123450-537eda9a-34b1-428f-9799-957fa6c3db11.jpg)

## Principales fonctionnalités configurées :

- Support carte mère BigTreeTech SKR 2.0
- Support extrudeur Direct Drive Bondtech LGX Lite
- Support drivers TMC2209/TMC2226 UART
- Support écrans BigTreeTech
- Support Bed Leveling Bilinear 9 x 9 points
- Support M600 & Nozzle Park / Advanced Pause
- Support Babystepping
- Support Neopixels (j'utilise cet anneau de LED : [ici](https://fr.aliexpress.com/item/1005002090765807.html?spm=a2g0s.9042311.0.0.56d46c37lqhfaf))
- Support EEPROM
- Support PID Buse & Plateau
- Support protection thermique contre l'emballement
- Support S-Curve Acceleration
- Support de la compensation d'inclinaison du plateau (https://www.thingiverse.com/thing:2563185)
- Support G26 - Mesh Validation Pattern
- Support G33 - Delta Auto Calibration
- Support du transfert de fichier binaire (transfert du fichier firmware à distance via Octoprint)
- Support des commandes d'action de l'hôte
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

## Fichiers STL nécessaires :

<img align="left" width="200" src="https://user-images.githubusercontent.com/12702322/147863957-b25b46d0-1ad6-4ef2-b6ff-d6f69259bd86.png" />[TFT70 Case.zip](https://github.com/Guilouz/Marlin-SuperRacer-SKR2.0-LGX-Lite/files/7798453/TFT70.Case.zip)

<img align="left" width="200" src="https://user-images.githubusercontent.com/12702322/147863965-d4a2b271-5ff7-4fcc-bd89-1e59acba76e0.png" />[Spool Holder.zip](https://github.com/Guilouz/Marlin-SuperRacer-SKR2.0-LGX-Lite/files/7798455/Spool.Holder.zip)

## Réglages slicers recommandés :

**G-Code de démarrage :**

`G21 ; Unités en millimètres`<br />
`G90 ; Positionnement absolu`<br />
`M82 ; Axe E en mode absolu`<br />
`M140 S{material_bed_temperature} ; Température du plateau` (pour Cura)<br />
`M104 S{material_print_temperature} ; Température de la buse` (pour Cura)<br />
`M190 S{material_bed_temperature} ; Attente la température du plateau` (pour Cura)<br />
`M109 S{material_print_temperature} ; Attente de la température de la buse` (pour Cura)<br />
`G28 ; Origines des axes`<br />
`M420 S1 ; Activation du maillage`<br />
`; Descente de la Hotend et passage à la position de départ`<br />
`G1 Z150`<br />
`G1 X-130 Y0 Z0.4 F3000`<br />
`; Extrude environ 40mm en imprimant un arc de 90 degrés`<br />
`G3 X0 Y-130 I130 Z0.3 E40 F2700`<br />
`; Rétraction et déplacement de la hotend vers le haut`<br />
`G92 E0`<br />
`G1 E-1.5 F1800`<br />
`G0 Z0.5`<br />
`G1 E0 F300`

**G-Code de fin :**

`G91 ; Positionnement relatif`<br />
`G1 E-1 F300 ; Rétraction avant déplacement de la hotend vers le haut`<br />
`G1 Z+5 E-5 F6000 ; Déplacement de la hotend vers le haut`<br />
`G28 X0 Y0 ; Origines des axes`<br />
`G90 ; Positionnement absolu`<br />
`G92 E0 ; Réinitialisation de l'extrudeur`<br />
`M104 S0 ; Arrêt de la chauffe de la buse`<br />
`M140 S0 ; Arrêt de la chauffe du plateau`<br />
`M107 ; Arrêt des ventilateurs`<br />
`M84 ; Désactivation des moteurs`

**Rétraction :**

- Distance : `1.2 mm`
- Vitesse : `35 mm/s`

## Changements éventuels :

Ce firmware est configuré pour une carte mère BigTreeTech SKR 2.0 Rev. B avec MCU STM32F407VGT6 et extrudeur Bondtech LGX. Certains changements peuvent être effectués si vous disposez d'autres équipements.

  - Pour changer la langue de Marlin en anglais, définissez cette valeur :
    - Dans Configuration.h : `#define LCD_LANGUAGE en`

  - Si vous voulez utiliser le port `microSD`, définissez ces valeurs :
    - Dans Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT`
    - Dans Configuration_adv.h : `//#define USE_OTG_USB_HOST`

  - Si vous voulez utiliser le port `USB`, définissez ces valeurs :
    - Dans Configuration_adv.h : `#define USB_FLASH_DRIVE_SUPPORT`
    - Dans Configuration_adv.h : `#define USE_OTG_USB_HOST`

  - Si `EXTRUDEUR FLSUN STOCK / BONDTECH BMG (BOWDEN)`, définissez ces valeurs :
    - Dans Configuration.h : `#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 80, 415 }`
    - Dans Configuration.h : `#define INVERT_E0_DIR true`
    - Dans Configuration_adv.h : `#define E0_CURRENT      1050`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_UNLOAD_LENGTH      350`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_FAST_LOAD_LENGTH     350`

  - Si `EXTRUDEUR OMG-V2-S (BOWDEN)`, définissez ces valeurs :
    - Dans Configuration.h : `#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 80, 385 }`
    - Dans Configuration.h : `#define INVERT_E0_DIR true`
    - Dans Configuration_adv.h : `#define E0_CURRENT      1050`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_UNLOAD_LENGTH      350`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_FAST_LOAD_LENGTH     350`

  - Si `EXTRUDEUR BONDTECH LGX (BOWDEN)`, définissez ces valeurs :
    - Dans Configuration.h : `#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 80, 400 }`
    - Dans Configuration.h : `#define INVERT_E0_DIR false`
    - Dans Configuration_adv.h : `#define E0_CURRENT      650`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_UNLOAD_LENGTH      350`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_FAST_LOAD_LENGTH     350`

  - Si `EXTRUDEUR BONDTECH LGX LITE (DIRECT DRIVE)`, définissez ces valeurs :
    - Dans Configuration.h : `#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 80, 562 }`
    - Dans Configuration.h : `#define INVERT_E0_DIR false`
    - Dans Configuration_adv.h : `#define E0_CURRENT      650`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_UNLOAD_LENGTH      70`
    - Dans Configuration_adv.h : `#define FILAMENT_CHANGE_FAST_LOAD_LENGTH     70`

  - Si `MKS ROBIN NANO V3`, définissez ces valeurs :
    - Dans platformio.ini : `default_envs = mks_robin_nano_v3_usb_flash_drive_msc`
    - Dans Configuration.h : `#define MOTHERBOARD BOARD_MKS_ROBIN_NANO_V3`
    - Dans Configuration.h : `#define SERIAL_PORT -1`
    - Dans Configuration.h : `#define SERIAL_PORT_2 3`
    - Dans Configuration.h : `#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`
    - Dans Configuration.h : `//#define Z_MIN_PROBE_PIN PA0`
    - Dans Configuration.h : `//#define NEOPIXEL_LED`
    - Dans Configuration_adv.h : `#define E0_AUTO_FAN_PIN PB0`
    - Dans Configuration_adv.h : `//#define LED_CONTROL_MENU`
    - Dans Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT` pour utiliser le port microSD
    - Dans Configuration_adv.h : `#define USB_FLASH_DRIVE_SUPPORT` pour utiliser le port USB
    - Dans Configuration_adv.h : `#define DISABLE_DRIVER_SAFE_POWER_PROTECT`
    
  - Si `SKR 1.3`, définissez ces valeurs :
    - Dans platformio.ini : `default_envs = LPC1768`
    - Dans Configuration.h : `#define MOTHERBOARD BOARD_BTT_SKR_V1_3`
    - Dans Configuration.h : `#define SERIAL_PORT -1`
    - Dans Configuration.h : `#define SERIAL_PORT_2 0`
    - Dans Configuration.h : `#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`
    - Dans Configuration.h : `//#define Z_MIN_PROBE_PIN PA0`
    - Dans Configuration.h : `//#define NEOPIXEL_LED`
    - Dans Configuration_adv.h : `#define E0_AUTO_FAN_PIN P2_04`
    - Dans Configuration_adv.h : `//#define LED_CONTROL_MENU`
    - Dans Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT`
    - Dans Configuration_adv.h : `#define DISABLE_DRIVER_SAFE_POWER_PROTECT`
    
  - Si `SKR 1.4`, définissez ces valeurs :
    - Dans platformio.ini : `default_envs = LPC1768`
    - Dans Configuration.h : `#define MOTHERBOARD BOARD_BTT_SKR_V1_4`
    - Dans Configuration.h : `#define SERIAL_PORT -1`
    - Dans Configuration.h : `#define SERIAL_PORT_2 0`
    - Dans Configuration.h : `#define Z_MIN_PROBE_PIN P1_25` Le palpeur doit être branché sur le port E1DET
    - Dans Configuration.h : `//#define NEOPIXEL_LED`
    - Dans Configuration_adv.h : `#define E0_AUTO_FAN_PIN P2_04`
    - Dans Configuration_adv.h : `//#define LED_CONTROL_MENU`
    - Dans Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT`
    - Dans Configuration_adv.h : `#define DISABLE_DRIVER_SAFE_POWER_PROTECT`
    
  - Si `SKR 1.4 Turbo`, définissez ces valeurs :
    - Dans platformio.ini : `default_envs = LPC1769`
    - Dans Configuration.h : `#define MOTHERBOARD BOARD_BTT_SKR_V1_4_TURBO`
    - Dans Configuration.h : `#define SERIAL_PORT -1`
    - Dans Configuration.h : `#define SERIAL_PORT_2 0`
    - Dans Configuration.h : `#define Z_MIN_PROBE_PIN P1_25` Le palpeur doit être branché sur le port E1DET
    - Dans Configuration_adv.h : `#define E0_AUTO_FAN_PIN P2_04`
    - Dans Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT`
    - Dans Configuration_adv.h : `#define DISABLE_DRIVER_SAFE_POWER_PROTECT`
    
  - Si `SKR 2.0 Rev. A`, définissez ces valeurs :
    - Dans Configuration.h : `#define MOTHERBOARD BOARD_BTT_SKR_V2_0_REV_A`
    - Dans Configuration_adv.h : `#define DISABLE_DRIVER_SAFE_POWER_PROTECT` en vous assurant d'avoir vérifier ceci : [SKR 2.0 Rev. A et Rev. B](https://docs.google.com/document/d/1IeKgfE2WIDjqH1fx5Yg7n1FOHVwhDFmDlZ-7QMlOEV0/edit?fbclid=IwAR3gCoyRlxSNaZfyHNV_BgGn1apJKmvagmzduOfGGYjY7I8kDBUVAuLyIi4).

  - Si `SKR 2.0 avec MCU STM32F429VGT6`, définissez ces valeurs :
    - Dans platformio.ini : `default_envs = BIGTREE_SKR_2_F429`
  
Recompilez ensuite le firmware à l'aide de VSCode et PlatformIO (voir [ici](https://marlinfw.org/docs/basics/install_platformio_vscode.html)).
