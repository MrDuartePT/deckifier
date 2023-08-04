<p align="center">
 
[//]: <> (site para ícones: https://shields.io/ )
 
<img alt="Maintained" src="https://img.shields.io/badge/Maintained%3F-Yes-green">
<img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/MrDuartePT/deckifier-hyprland">
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/MrDuartePT/deckifier-hyprland">
<img alt="Bitbucket open issues" src="https://img.shields.io/bitbucket/issues/MrDuartePT/deckifier-hyprland">
<img alt="GitHub commit activity (branch)" src="https://img.shields.io/github/commit-activity/y/MrDuartePT/deckifier-hyprland">

<hr>

# Deck-ifier

***SteamOS session on any Arch-based distro!***

This repository aims to add required SteamDeck's binaries for Gamescope Wayland session with full "Switch to Desktop", "Game Mode" support and other required components to Arch Linux.

This adds almost all of the required SteamOS dependencies, as well as FPS limiting, flyouts, performance overlay and so on.

<hr>

# IMPORTANT
This only works for ArchLinux running Hyprland and Greetd as display manager. The files named as ```jupiter-biosupdate``` and ```steamos-update``` are just dummy files for Gamescope Session to work. I'm working on an automated installation script but just wanted to share this as soon as i got it working.

<hr>

# Pre-requisites
Before installing, make sure the `multilib` repository is enabled in /etc/pacman.conf and `nano`, `mangohud`, `lib32-mangohud` and `mangoapp` installed.

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
## 3. Reboot and enjoy SteamOS!
```
reboot
```

# Credits:

To [Joaquín Ignacio Aramendía](https://github.com/Samsagax) and [ChimeraOS](https://github.com/ChimeraOS)'s Team.
To [Adam Jafarov](https://github.com/theVakhovskeIsTaken).
To Gamescope, Valve and Steam developers.
To everyone involved on these amazing projects.
