<p align="center">
 
[//]: <> (site para ícones: https://shields.io/ )
 
<img alt="Maintained" src="https://img.shields.io/badge/Maintained%3F-Yes-green">
<img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/MrDuartePT/deckifier-hyprland">
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/MrDuartePT/deckifier-hyprland">
<img alt="Bitbucket open issues" src="https://img.shields.io/bitbucket/issues/MrDuartePT/deckifier-hyprland">
<img alt="GitHub commit activity (branch)" src="https://img.shields.io/github/commit-activity/y/MrDuartePT/deckifier-hyprland">

<hr>

# Deck-ifier

***SteamOS session on any distro!***

This repository aims to add required SteamDeck's binaries for Gamescope Wayland session with full "Switch to Desktop", "Game Mode" support and other required components on any distro.

This adds almost all of the required SteamOS dependencies, as well as FPS limiting, flyouts, performance overlay and so on.

<hr>

# IMPORTANT
This works on distros running Hyprland and SDDM as display manager. But can be edit to work with other DE/WM (explain bellow)

It also available a [kde](https://github.com/MrDuartePT/deckifier/tree/kde) branch that use the plasma desktop

For lightdm user use the [lightdm](https://github.com/MrDuartePT/deckifier/tree/kde) branch (not forget to change the DE/WM if needed)

For greetd user use the [Hyprland-greetd](https://github.com/MrDuartePT/deckifier/tree/kde) branch (not forget to change the DE/WM if needed)

TODO: An [gbm](https://github.com/MrDuartePT/deckifier/tree/gbm)  branch (If someone what to do a PR also welcome)

<hr>

# Pre-requisites
Before installing, make sure you have mangohud install (both 64 and 32 bits), ChimeraOS gamescope fork and steam.

# Gentoo Ebuild

The Gentoo Ebuild link is hosted [here](https://github.com/MrDuartePT/mrduarte-ebuilds)

[Ebuild file](https://github.com/MrDuartePT/mrduarte-ebuilds/blob/f5785e150017b9c7bcb734b8a55cfa0ce083215b/games-util/gamescope-session-hyprland/gamescope-session-hyprland-9999.ebuild)

If you are using kde pls use the [kde](https://github.com/MrDuartePT/deckifier/tree/kde) branch, if you are using other DE/WM fork the project and create a patch in the `rootfs/usr/lib/os-session-select` file (by changing the session_launcher names)

# Manual install:

## 1. Cloning this repo and copy files with proper permissions
```
git clone https://github.com/MrDuartePT/deckifier-hyprland.git && cd deckifier-hyprland
```
```
cp -rf rootfs/usr/* /usr
cp -rf rootfs/etc/* /etc
chmod 777 /usr/bin/steamos-session-select
gio set /usr/share/applications/org.valve.gamescope.desktop metadata::trusted true
chmod a+x /usr/share/applications/org.valve.gamescope.desktop
systemctl --user enable steam-powerbutton.service
```

## 2. Go to /usr/lib/os-session-select and replace session_launcher if needed 
```
nano /usr/lib/os-session-select
```
```
At line 50-66 replace session_launcher what is needed
At line 94 replace mrduarte with your username
ctrl+O and Enter to Save
ctrl+X to exit
```

## 4. Reboot and enjoy SteamOS!
```
reboot
```

## NOTE:
Using Nvidia Laptop
My need to add DRI_PRIME=1 %command% to launch the game with NVIDIA dGPU (I don't need on my laptop pls tested)
1st Note: Dont do nested gamescope on SteamOS session the game will crash on launch.
2st Note: If you laptop have the hdmi conneted to the dGPU you loose that output

Using Laptop in dGPU Mode[MUX] or Nvidia GPU on desktop my cause graphical glitches

Pls double check [/usr/lib/os-session-select](https://github.com/MrDuartePT/deckifier-hyprland/blob/main/rootfs/usr/lib/os-session-select) you my need to edit things

# Credits:

To [Joaquín Ignacio Aramendía](https://github.com/Samsagax) and [ChimeraOS](https://github.com/ChimeraOS)'s Team.
To [Adam Jafarov](https://github.com/theVakhovskeIsTaken).
To Gamescope, Valve and Steam developers.
To everyone involved on these amazing projects.
