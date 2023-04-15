# Arch Linux Notes

## Anarchy Installerc
[Anarchy Installer](https://anarchyinstaller.gitlab.io/)

Its a bit buggy aka if it fails you need to go thru all the settings again. Still faster than a normal arch install.

## Theming

GTK theme is separate from system theme setting e.g. for firefox's right click menus or discord's save image as menu.

Install and use the lxappearance command 

```bash
yay -S lxappearance && lxappearance
```


## Fonts & Emoji
Default font used by arch is Noto
```bash
yay -S noto-fonts-extra noto-fonts-emoji-flags noto-fonts-emoji
```

## Audio & Sidetone
Alsamixer CLI app for adjusting setting
```bash
alsamixer
```
Save settings with 
```bash
sudo alsactl store
```


## Steam & Gaming

#### Enable Multilib
Uncomment the `[multilib]` section in `/etc/pacman.conf`

```bash
[multilib]
Include = /etc/pacman.d/mirrorlist
```

#### Enable Proton
You can enable Proton in the Steam Client in `Steam > Settings > Steam Play`
To force enable Proton, right click on the game, `Properties > General > Force the use of a specific Steam Play compatibility tool`

When reusing existing home directories, to get steam to work after installing it from pacman/yay, delete the compatdata in `SteamLibrary/steamapps/` so that steam regenerates them and installs the proton properly.


## GRUB
### Disable boot delay

Edit the grub config:
```bash
sudo nano /etc/default/grub
```
Add the following line
```
# achieve the fastest possible boot:
GRUB_FORCE_HIDDEN_MENU="true"
```
Copy text from https://goo.gl/nac6Kp to  
```bash
sudo nano /etc/grub.d/31_hold_shift
```

Make it executable, and regenerate the grub configuration:
```bash
sudo chmod a+x /etc/grub.d/31_hold_shift
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## Apps

Utilities
```bash
yay -S syncthing flameshot bitwarden
```

Development
```bash
yay -S visual-studio-code-bin thefuck
```

Communication
```bash
yay -S signal-desktop tutanota-desktop-bin
```

Gaming related
```bash
yay -S discover-overlay minecraft-launcher mirage syncthing
```
> discover-overlay: Discord overlay
> mirage: Image viewer, alternative to gwenview


### Remove orphans
```bash
sudo pacman -Rns $(pacman -Qtdq)
```

### Webp support for gwenview
```bash
yay -S qt5-imageformats
```


---

### TODO
#todo look into keyring on linux
