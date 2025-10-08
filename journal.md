For grub bootloader, i just need to '# grub-install --target=x86_64-efi --efi-directory=esp --bootloader-id=GRUB' with "esp" being /mnt/boot before chrooting into it. After that just '# grub-mkconfig -o /boot/grub/grub.cfg' to generate default grub.cfg.

Freshinstall installed iwd instead of networkmanager. Ends up configuring /etc/resolv.conf; /etc/iwd/main.conf; /etc/systemd/network/* using only cat and echo because I 'pacman -Rs vi' wanted to change it to vim, problem with dhcp of ipv4. Regular stuff of freshinstall arch, enabling bunch of systemd services (e.g iwd.services, systemd-resolved, and systemd.networkd.service). Note: vi and w3m/lynx are important.

Added new user put on wheel group. Configured /etc/systemd/resolved.conf.d/*. Use '$ systemctl edit getty@tty1.service --drop-in=autologin.conf' to add getty@tty1.service.d/autologin.conf for autologin without login manager (should not be added manually.  Configured ~/.xinitrc to have setxkbmap -variant dvorak; xset r66; xset r rate 191; xset s off -dpms. Added .bash_alias

Compiled dwm, st, and surf all with gruvbox patch one way or another. Here's what I've learnt, 'makepkg' to run modified arch user
repo build and 'make' to compile C programs. Checked and modified /etc/hosts when ethernet is botched. Gives up on compiling browser and instead stick with bin version of it. Got problems with public gpg key, it turns out aur use user key and not the one on pacman, I still need to learn more of it.

Default layout configured with 'loadkeys' overridden when xorg is installed. Turns out it loads different config and can be manually configured by modifying /etc/X11/xorg.conf.d/00-keyboard.conf or using 'localectl' (e.g localectl --no-convert set-x11-keymap us pc105 ,dvorak) doing the latter overwrite the former config file.

Added audio and brightness capabiltity to dwm config.h. Before I can use them properly I need to install pipewere-pulse and brightnessctl respectively. Reminds me to remove linux account timeout lock. Add $HOME/user-dirs.dirs to set default directory for common user directory. When updating grub with pacman don't forget to 'grub-install' again and 'grub-mkconfig -o /boot/grub/grub.cfg'. To allow non-latin font and emoji rendering on browser or any other graphical software you need to download them manually (e.g ttf-ancient-fonts for ancient language unicode rendering). Install libnotify to allow utilizing  'notify-send'.

There are plenty of things I need to patch if I want to use st conveniently. Like columnredraw, w3m support, kitty like render, delkey, expected anysize, blinking cursor, scrollback, etc.

Added EDITOR=vim in /etc/environment and run 'xdg-mime default vim.desktop text/plain' recently so that it default to vim when editing plain text file.

Added ufw as a frontend to iptables with common configuration for a light sprinkle of security. Added ntfs-3g package so that I can mount ntfs partition. Installed ueberzug as backend to display images on terminal.

CUPS is for printers and SANE is for scanners. Install toolbox for large dependent software like texlive.

I've followed silent boot instruction. Managed to silence startx, udev hook for fsck and systemd bootlog. For grub init, it needs customized grub package from aur, which needs /boot reconfiguration, which in turn is a hassle. Mess around with plymouth and found out 'i915' module need to be placed in /etc/mkinitcpio.conf for it to run on boot for intel GPU.

I'm still confused with fonts, plenty of unicodes and glyphs don't render completely. Just installed custor compiled cursor, placed on .icons (user) and /usr/share/icons/ (system-wide). Remember to update .config/gtk-3.0 and also add index.theme in .icons/default/ and /usr/share/icons/default/.

Installed 'lf' with previous config, just need to chmod to some, preview for images works with small configuration in /.local/bin/ and installation of ueberzug (or at leaast the equivalent of it as ueberzug is unmaintained now). The headscratcher is icons because some glyphs are missing.
