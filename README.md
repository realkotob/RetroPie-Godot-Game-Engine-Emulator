# RetroPie Godot Game Engine "Emulator"

A Godot "emulator" for RetroPie.

Thanks to [@efornara](https://github.com/efornara) (for creating [FRT - A Godot "platform" targeting single board computers](https://github.com/efornara/frt)) you can now play* games made with [Godot](https://godotengine.org/) on your Raspberry Pi (and other single board cumputers) using [RetroPie](https://retropie.org.uk/).

If you are running RetroPie on an `x86` PC, the Godot "emulator" uses the **Linux/X11-32bits** template instead of **FRT**, so most games should work fine.

**\*Games that (would) work on a Raspberry Pi must be created with Godot 3.1 using GLES2 (or maybe Godot 2.x) and not using any 'fancy VFX' like particles and other CPU/GPU demanding stuff.**

## Setup

```
cd /home/pi/
curl "https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/install-godot-engine-scriptmodule.sh" -o "install-godot-engine-scriptmodule.sh"
curl "https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/uninstall-godot-engine-scriptmodule.sh" -o "uninstall-godot-engine-scriptmodule.sh"
curl "https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/update-godot-engine-scriptmodule.sh" -o update-godot-engine-scriptmodule.sh
sudo chmod +x install-godot-engine-scriptmodule.sh
sudo chmod +x uninstall-godot-engine-scriptmodule.sh
sudo chmod +x update-godot-engine-scriptmodule.sh
```

## Install the scriptmodule

```
cd /home/pi/
./install-godot-engine-scriptmodule.sh
```

## Uninstall the scriptmodule

```
cd /home/pi/
./uninstall-godot-engine-scriptmodule.sh
```

## Update the scriptmodule

```
cd /home/pi/
./update-godot-engine-scriptmodule.sh
```

These scripts assume that you are running them on a Raspberry Pi with the `RetroPie-Setup` folder being stored in `/home/pi/RetroPie-Setup`. If your setup differs, you can pass the path where your `RetroPie-Setup` folder is stored as a parameter, like this:

```
./install-godot-engine-scriptmodule.sh "/path/to/your/RetroPie-Setup"
./uninstall-godot-engine-scriptmodule.sh "/path/to/your/RetroPie-Setup"
./update-godot-engine-scriptmodule.sh "/path/to/your/RetroPie-Setup"
```
## Install the Godot "emulator" from RetroPie-Setup

Once you've [successfully installed](#install-the-scriptmodule) the scriptmodule, run `sudo /home/pi/RetroPie-Setup/retropie_setup.sh`  and then go to:

* Manage packages
* Manage optional packages
* godot-engine
* Install from source

A new `godot-engine` folder will be created in `/home/pi/RetroPie/roms/`, where you can put your games using `.pck` and `zip` extensions.

If you are using an `x86` PC, two different emulators will be installed:

* `godot-engine-3.0` 
* `godot-engine-3.1 (default)`

If the game you are trying to play doesn't work, try changing the "emulator" in the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand).

For the Raspberry Pi, the script will auto-detect if you are using a `0/1` or a `2/3` and it will install the proper "emulator". Same for any `arm64` single computer board.

In this case, only one "emulator" will be installed, so if the game you are trying to play isn't working... Sorry.
 
## How to create a new theme system for Godot

As there is no way to create a script to automate this, because themes don't have the same structure,the best way is to manually create a new system in your preferred theme.

* [Download](https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/system.svg) the Godot `system.svg`.
* [Download](https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/controller.svg) the Godot `controller.svg`.
* Copy any system folder in your theme (e.g. `/etc/emulationstation/themes/[THEME]/nes`).
* Rename it as `godot-engine`.
* Move the Godot logo and controller to the `godot-engine/art` folder.

**Note**

The folder structure in the theme you are using might differ. Take a look at how this particular theme works to create the `godot-engine` folder accordingly. You might need to delete extra icons that are not needed.

## Example using the default Carbon theme

```
cd /home/pi/
wget "https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/system.svg"
wget "https://raw.githubusercontent.com/hiulit/RetroPie-Godot-Game-Engine-Emulator/master/controller.svg"
sudo cp -R "/etc/emulationstation/themes/carbon/nes" "/etc/emulationstation/themes/carbon/godot-engine"
sudo mv "/home/pi/system.svg" "/etc/emulationstation/themes/carbon/godot-engine/art"
sudo mv "/home/pi/controller.svg" "/etc/emulationstation/themes/carbon/godot-engine/art"
```

![Godot system for RetroPie's Carbon theme](/example-images/godot-engine-carbon-theme.jpg)

## Changelog

See [CHANGELOG](/CHANGELOG.md).

## Authors

Me 😛 [@hiulit](https://github.com/hiulit).


## Credits

Thanks to:

- Emanuele Fornara [@efornara](https://github.com/efornara) - For creating [FRT - A Godot "platform" targeting single board computers](https://github.com/efornara/frt).
- Andrea Calabró - For creating the **Godot logo**. Changes made to it:
  - Created an outline version.
- Alícia Folgarona Ribot (Alfórium Studios) [@alforiumstudios](https://twitter.com/alforiumstudios) - For creating the **Pixel Godot logo**. Changes made to it:
  - New colors.
  - Added white outline.

## LICENSE

- Source code: [MIT License](/LICENSE).
- Godot logo: [CC BY](https://creativecommons.org/licenses/by/3.0/).
- Pixel Godot logo: [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/).


