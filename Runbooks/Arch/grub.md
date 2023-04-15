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
