# Scripts

This is repository of my Archlinux scripts I use on daily basis.

## Installation

If you'd like to use this repository in your PATH keep in mind there are a few folders. In order to scrap all the script names from every folder I use `find`.

```sh
find $HOME/scripts -type d
```

This will generate bunch of weird folders we don't really need related to git, so we can ignore them like so

```sh
find $HOME/scripts -type d ! -iwholename "*git*" -printf %p:
```

This will scrap every folder and subfolder inside scripts directory and we can use it to add them as additional records in `PATH`. Directories in `PATH` are splited by colon sign hence addigional `-printf` flag. 

```sh 
scripts_dirs=$(find $HOME/scripts -type d ! -iwholename "*git*" -printf %p:)
export PATH=$PATH:/usr/local/games:/usr/local/bin:$HOME/.local/share/applications:$HOME/:$scripts_dirs
```

## Dependencies

Most of my scripts use: 

- `dmenu` or `fzf` for presenting options (I think the only one using `fzf` is `kcs` right now)
- gnutils such as `gawk`, `grep`, `tr`, `tail`, `head`, `echo`, `read` 
- monitor scripts are useful only in X11 so `xrandr` is required
- `xinput` used in `touchtog`
- `dunst` or another program for sending notifications via `notify-send`
- either `amixer` or `pactl` depending on what you're using for sound
- `mpc` and `ncmpcpp` for playing music
- `sxiv` to pick a wallpaper 
- `xrandr` to manage monitors and resolutions
- `ffmpeg`, `slop` and `maim` to record screen

## Variables

There are few scripts that expects you to have certain variables to be set in order to work.

|var|description|used by|
|-|-|-|
|SCRIPTS_DIR|self explainatory, your scripts directory|-|
|WALLPAPER_DIR|a file that supposed to be used as your wallpaper i.e. `$HOME/wallpaper.png`|setwall, swapwall|
|WALLPAPERS_DIR|directory with your wallpapers, i.e. `$HOME/Pictures/wallpapers`|setwall, swapwall|
|SCREENSHOT_DIR|directory with your screenshots, i.e. `$HOME/Pictures/screenshots`|screenshot|

## Description

I try to group scripts into folders for maintenance but they also have functional reasons. Here's short description of some of them. 

- aliases - a group of scripts that could have been aliases but I find it easier to maintain it there
	- [hibernate](https://github.com/smoorg/scripts/blob/main/aliases/hibernate) - systemd hibernation call
	- [music](https://github.com/smoorg/scripts/blob/main/aliases/music) - runs mpc update and ncmpcpp 
	- [pdf](https://github.com/smoorg/scripts/blob/main/aliases/pdf) - application for pdf, usually xreader
- sound - everything related to sound management, volume, mute status, switching sinks and so on
	- [currsink](https://github.com/smoorg/scripts/blob/main/sound/currsink) - returns default sink
	- [mute](https://github.com/smoorg/scripts/blob/main/sound/mute) - toggles mute status for sinkid or sink name
	- [muted](https://github.com/smoorg/scripts/blob/main/sound/muted) - returns mute status for sinkis or sink name
	- [pl](https://github.com/smoorg/scripts/blob/main/sound/pl) - lists sinks
	- [sds](https://github.com/smoorg/scripts/blob/main/sound/sds) - sets default sink
	- [sound](https://github.com/smoorg/scripts/blob/main/sound/sound) - increases and decreases volume
	- [switchsink](https://github.com/smoorg/scripts/blob/main/sound/switchsink) - changes default sink
	- [volume](https://github.com/smoorg/scripts/blob/main/sound/volume) - returns volume level
- screen - monitors, wallpapers, brightness, screenshots
	- [conmon](https://github.com/smoorg/scripts/blob/main/screen/conmon) - connect additional monitor (currently hardcoded to `right-of` so mostly for 2 monitors as of now)
	- [light](https://github.com/smoorg/scripts/blob/main/screen/light) - increases and decreases brightness
	- [night](https://github.com/smoorg/scripts/blob/main/screen/night) - runs redshift
	- [screenshot](https://github.com/smoorg/scripts/blob/main/screen/screenshot) - copies screenshots to $SCREENSHOT_DIR as well as to your xclip
	- [setwall](https://github.com/smoorg/scripts/blob/main/screen/setwall) - sets wallpaper
	- [showmonitors](https://github.com/smoorg/scripts/blob/main/screen/showmonitors) - lists monitors
	- [swapres](https://github.com/smoorg/scripts/blob/main/screen/swapres) - changes resolution and refresh rate
	- [swapwall](https://github.com/smoorg/scripts/blob/main/screen/swapwall) - replaces wallpaper file or runs sxiv to pick one and then calls setwall
- pacman - scripts related to pacman
	- [pacinst](https://github.com/smoorg/scripts/blob/main/pacman/pacinst) - copied from archlinux wiki; fzf based application installer
	- [pacupd](https://github.com/smoorg/scripts/blob/main/pacman/pacupd) - pacman update script which remembers to install archlinux-keyring first for me
- [statusbar](https://github.com/smoorg/scripts/blob/main/statusbar) - dwm bar status bar scripts to present cpu and ram usage, volume, date and time, nothing fancy there
- [emotes](https://github.com/smoorg/scripts/blob/main/emotes) - dumb script to present emotes and its tags and copy over needed one to the `xclip`
- [kcs](https://github.com/smoorg/scripts/blob/main/kcs) - Keepass + rclone sync to update/merge database.
- [marktime](https://github.com/smoorg/scripts/blob/main/marktime) - sets timestamp and adds it to a file. Then substracts it from previous one to count time period. Can be used to track time
- [record](https://github.com/smoorg/scripts/blob/main/record) - records screen area
- [recordws](https://github.com/smoorg/scripts/blob/main/recordws) - records whole screen in QHD resolution, can be modified to fHD easily
- [scan](https://github.com/smoorg/scripts/blob/main/scan) - uses plugged in scanner and tries to scan image
- [splitflac](https://github.com/smoorg/scripts/blob/main/splitflac) - splits flac file into pieces based on cue description
- [sshadd](https://github.com/smoorg/scripts/blob/main/sshadd) - picks ssh key from dmenu to use with ssh-agent
- [subdate](https://github.com/smoorg/scripts/blob/main/subdate) - subtracts two dates
- [touchtog](https://github.com/smoorg/scripts/blob/main/touchtog) - uses `xinput` to toggle provided device
- [webcam](https://github.com/smoorg/scripts/blob/main/webcam) - uses `mpv` to present webcam
- [ytrss](https://github.com/smoorg/scripts/blob/main/ytrss) - generates rss from youtube channel/playlist/user
