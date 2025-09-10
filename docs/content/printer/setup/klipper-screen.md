# Klipper Screen

THe screen included with the LDO Voron 2.4 RevD kit is the BigTreeTech 4.3" LCD
To get this to work we'll need to use klipper screen

  * https://klipperscreen.readthedocs.io/en/latest/

## Setup

Launch kiauth
```sh
./kiauh/kiauh.sh
```

  * Select 1 install
  * Select 7 for KlipperScreen
  * Default Yes (Standalone)
  * Default X (Xserver)
  * Default Y to Network Manager for network panel

Note the network will drop out part way through due to the network manager change
set the wifi backup at the touch screen


## Themes

To install some themes

  * https://bumbeng.github.io/mainsail-themes.github.io/

```sh
mkdir ~/temp1
cd ~/temp1/

# blurry Theme
wget -c https://github.com/bumbeng/Klipperscreen_blurry_theme/archive/refs/heads/main.zip -O blurry.zip
unzip blurry.zip
cp -a Klipperscreen_blurry_theme-main/blurry ~/KlipperScreen/styles/
cp -a Klipperscreen_blurry_theme-main/blurry2 ~/KlipperScreen/styles/
cp -a Klipperscreen_blurry_theme-main/simple ~/KlipperScreen/styles/

# mainsail theme
wget -c https://github.com/bumbeng/Klipperscreen-theme-mainsail/archive/refs/heads/main.zip -O mainsail.zip
unzip mainsail.zip
cp -a Klipperscreen-theme-mainsail-main/mainsail ~/KlipperScreen/styles/

# Bubbles theme
wget -c https://github.com/bumbeng/klipperscreen-theme-bubbles/archive/refs/heads/main.zip -O bubbles.zip
unzip bubbles.zip
cp -a klipperscreen-theme-bubbles-main/bubbles ~/KlipperScreen/styles/

# ocean theme
wget -c https://github.com/bumbeng/KlipperScreen-theme-ocean/archive/refs/heads/main.zip -O ocean.zip
unzip ocean.zip
cp -a KlipperScreen-theme-ocean-main/ocean ~/KlipperScreen/styles/

# restart klipper screen
sudo service KlipperScreen restart
```
