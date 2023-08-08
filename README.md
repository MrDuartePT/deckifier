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
This only works on distros running Hyprland and Greetd as display manager. The files named as ```jupiter-biosupdate``` and ```steamos-update``` are just dummy files for Gamescope Session to work. I'm working on an automated installation script but just wanted to share this as soon as i got it working.

<hr>

# Pre-requisites
Before installing, make sure you have mangohud install (both 64 and 32 bits).

# Gentoo Ebuild

The Gentoo Ebuild link is hosted [here](https://github.com/MrDuartePT/mrduarte-ebuilds)

[Ebuild file](https://github.com/MrDuartePT/mrduarte-ebuilds/blob/f5785e150017b9c7bcb734b8a55cfa0ce083215b/games-util/gamescope-session-hyprland/gamescope-session-hyprland-9999.ebuild)

# Steps:

## 1. Cloning this repo and copy files with proper permissions
```
git clone https://github.com/MrDuartePT/deckifier-hyprland.git && cd deckifier-hyprland
```
```
cp -rf rootfs/usr/* /usr
cp -rf rootfs/etc/* /etc
chmod 777 /usr/bin/jupiter-biosupdate
chmod 777 /usr/bin/steamos-update
chmod 777 /usr/bin/steamos-session-select
gio set /usr/share/applications/org.valve.gamescope.desktop metadata::trusted true
chmod a+x /usr/share/applications/org.valve.gamescope.desktop

Note: No greetd and/or hyprland user pls run: ```rm -rf /etc/greetd```

```

## 2. Go inside polkits folder and replace with your username SteamVR's Policy 
```
cd /usr/share/polkit-1/actions && nano org.valve.steamvr.policy
```
```
At line 14 replace /home/mrduarte with your username
ctrl+O and Enter to Save
ctrl+X to exit
```

## 3. Hyprland and greetd user

Not forget to edit the user in /etc/greetd/config-desktop-mode.toml 
If you use sway or other DE with greetd you can edit the DE of choice in there and copy your current /etc/greetd/config.toml to /etc/greetd/config-desktop-mode.toml

## 4. Reboot and enjoy SteamOS!
```
reboot
```

## NOTE:
Not using Hyprland: just run ```rm -rf /etc/greetd``` and by defaut 'Switch to Desktop Mode' will restart your display manager

Using Nvidia Laptop
After adding DRI_PRIME=1 %command% to launch option games launch fine
1st Note: Dont do nested gamescipe on SteamOS session the game will crash on lauch, but you can use mangohud or other option
2st Note: If you laptop have the hdmi conneted to the dGPU you looose that output

Using Laptop in dGPU Mode[MUX] or Nvidia GPU on desktop (Need testers):
[I will alsume the result will be the same on Desktop PC but I only have a laptop to test]

# Credits:

To [Joaquín Ignacio Aramendía](https://github.com/Samsagax) and [ChimeraOS](https://github.com/ChimeraOS)'s Team.
To [Adam Jafarov](https://github.com/theVakhovskeIsTaken).
To Gamescope, Valve and Steam developers.
To everyone involved on these amazing projects.
