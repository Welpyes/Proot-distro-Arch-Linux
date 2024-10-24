# Proot distro Arch Linux install
<br><img width="300-" align="center" src="https://github.com/Welpyes/dotfiles-windows/blob/18d130b89831024092f5a6c05cc556dd70efd60f/wallpapers/20241018_195232.png">

## Applications Download

- **Termux**: A terminal emulator for Android that allows you to run Linux commands on your device.  
  [![Download Termux](https://img.shields.io/badge/Download-Termux-brightgreen?style=for-the-badge&logo=android)](https://f-droid.org/repo/com.termux_118.apk) - click to download

- **Termux-X11 (Xserver)**: Required for running graphical applications within Termux, providing a graphical user interface.  
  [![Download Termux-X11](https://img.shields.io/badge/Download-Termux--X11-blue?style=for-the-badge&logo=linux)](https://github.com/ahmad1abbadi/extra/releases/download/apps/termux-x11.apk) - click to download 
# 

### Requirements
* **Android Version**: `10 and above`
* **Processor**: `Snapdragon 665 is recommended`
* **Ram** : `3gb and above`
* **Storage**: `5gb minimum, 8gb recommended`
# 
<details>
<summary><b>Termux-x11(Xserver) Preferences</b></summary>

#### Output  
- Display resolution mode  - Exact 
- Display resolution  - 1920x1080(minimum is 1280x720)
- Stretch to fit display  - Off
- Reseed screen while soft keyboard is open  - Off
- PIP mode  - Off
- Fullscreen on device display  - On
- Force landscape orientation  - On
- Hide display cutout (if any)  - Optional
- Keep Screen On - On

### Pointer
- Touchscreen input mode  - Trackpad  
- Show stylus click options  - Off
- Show mouse click helper overlay  - On
- Capture external mouse when possible  - On
- Transform captured pointer movements  - On  
- Enable tap-to-move for touchpads - Off

### Keyboard
Toggle Keyboard using back key - On
**Everything else is optional**

</details>

<details>
<summary><b>Termux Setup</b></summary>
<br> 
First off all use this to update repos and check for bad ones

```sh
termux-change-repo && pkg upgrade -y
```
![termux-change-repo1](https://github.com/Welpyes/Proot-distro-Arch-Linux/blob/a329f2be169ed71e6e812f926df9d911310c5c81/.Readme-Resources/termux-repos1.jpg)
![termux-change-repo2](https://github.com/Welpyes/Proot-distro-Arch-Linux/blob/a329f2be169ed71e6e812f926df9d911310c5c81/.Readme-Resources/termux-repos2.jpg)


<br> 
Installing additional repos

```sh
pkg install root-repo x11-repo tur-repo -y
```
<br>
Install proot-distro and necessary packages

```sh
pkg install termux-x11-nightly pulseaudio proot-distro wget -y
```
now thats finished lets move on to **Arch Setup**

</details>

## 

### Arch Installation 

**NOTE** Before you proceed make sure you have done the pre installation procedures up above

Install Archlinux by using this command
```bash
pd i archlinux
```
then log in to arch by using
```bash
pd sh archlinux
```

<details>
<summary><b>Mirror Setup</b></summary>

First of all we have to enable mirrors based on your region to achieve fast download speeds
```bash
nano /etc/pacman.d/mirrorlist
```
After executing that command, disable the Geo-ip server by adding a comment (#) in front of `server` entry <br>
example: **DONT COPY THIS**
```bash
## Geo-IP based mirror selection and load balancing
   Server = http://mirror.archlinuxarm.org/$arch/$repo`
/\
 L add # Here
```
after that just remove the comment on the servers you want based on your region
```bash
### Japan
## Tokyo
 # Server = http://jp.mirror.archlinuxarm.org/$arch/$repo
 /\
  L remove the # here
 ```
 then save the file by clicking `ctrl` then O<br>
 and closing nano by `ctrl` then X
 
</details>


<details>
<summary><b>Arch Linux Main Setup</b></summary>

Do a full system upgrade
```bash
pacman -Syyyyyyyyyyu
```
install sudo and xfce4 
```bash
pacman -S sudo xfce4 --noconfirm
```
add user (add your username) **NOTE** dont forget that your username is case sensitive 
```bash
useradd -m -G wheel {Username}
```
Add a password to your user
```bash
passwd Welpyes
```
open the sudoers file using this command 
```bash
nano /etc/sudoers
```
now scroll down and find `User Privilege Specification` one line under `root` add:
```bash
{Username} ALL=(ALL) ALL
```
then save the file<br>
<br>
now we're gonna select your timezone using
```bash
tzselect
```
Choose your region and country and copy the `export` command it outputs<br>
eg. `export tz={timezone}` then execute it to save

exit archlinux by typing `exit` to return to termux

### Launching Archlinux
inside termux 
import the script using 
```bash
wget https://raw.githubusercontent.com/Welpyes/dotfiles-resource/refs/heads/main/startxfce4_arch.sh
```
Now if you changed the username open the script by using nano
```bash
nano startxfce4_arch.sh
```
and in line 25 change `Welpyes` to your username of choice<br>

now to launch arch linux just use this command
```bash
bash startxfce4_arch.sh
```
If You're getting `"[Process completed (signal 9) - press Enter]"` Termux error see this [github repo](https://github.com/agnostic-apollo/Android-Docs/blob/master/en/docs/apps/processes/phantom-cached-and-empty-processes.md#commands-to-disable-phantom-process-killing-and-tldr) and [reddit post](https://www.reddit.com/r/termux/comments/w0ixkp/comment/ighshu6/?utm_source=share&utm_medium=mweb3x&utm_name=mweb3xcss&utm_term=1&utm_content=share_button)

</details>
