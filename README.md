# personal-guide-fedora

This repository aims to keep track of every installation/process I make in my fedora setup. This way, I can always come here and check how I did something.

## General commands

### Set pcmanfm as default file manager:
```
xdg-mime default pcmanfm.desktop inode/directory application/x-gnome-saved-search
```

### Mount partition

The command ```fdisk -l``` lists all disk partitions available. When desired partition is chosen, e.g. /dev/sdb2, create directory where it will be mounted: ```sudo mkdir /mnt/disk1```; then mount it with ```sudo mount -t auto -v /dev/sdb2 /mnt/disk1/```.

Unmount it with ```sudo umount /dev/sdb2 -l```

### Create symbolic link of all files in a directory (if you're in the actual directory):

Update `ln -s -r * ~/.local/bin/`

This will link all files in directory to the path ~/.local/bin.

### Install ueberzug to preview images in ranger:

Install dependencies: `sudo dnf install python3-devel libXxf86vm-devel`

Install ueberzug: `pip install ueberzug`

Now that it is unmaintained, this is how to install it:
```bash
sudo apt install libxext-dev libx11-dev -y
git clone --depth 1 --branch 18.1.9 https://github.com/seebye/ueberzug.git
cd ueberzug
sudo python3 setup.py install
```

### Qalculate use period (.) instead of comma (,):

In file `~/.config/qalculate/qalc.cfg`, write `decimal_comma=0`. Set it to `-1` to ignore setting (use system's locale) or to `1` (to enable .).

### Rename Enter key

Enter key was named `KP_Enter`, instead of `Return`, so with command (requires xmodmap)
```
xmodmap -e "keysym KP_Enter = Return"
```
it's now solved. 

### Wayland

#### Waybar

To install waybar git version, `git clone` waybar repository, `meson build -Dexperimental=true` and `ninja build` +  install`.  

## Arch Linux

### Update pacman mirrors

```
sudo reflector --country 'Spain' --latest 5 --age 2 --fastest 5 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
```
