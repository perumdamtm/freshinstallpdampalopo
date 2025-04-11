Freshinstall installed iwd instead of networkmanager.Ends up configuring /etc/resolv.conf; /etc/iwd/main.conf; /etc/systemd/network/* using only cat and echo because I 'pacman -Rs vi' wanted to change it to vim, problem with dhcp of ipv4. Regular stuff of freshinstall arch, enabling bunch of systemd services (e.g iwd.services, systemd-resolved, and systemd.networkd.service). Note: vi and w3m/lynx are important.

Added new user put on wheel group. Configured /etc/systemd/resolved.conf.d/*. Use '$ systemctl edit getty@tty1.service --drop-in=autologin.conf to add getty@tty1.service.d/autologin.conf for autologin without login manager (should not be added manually.  Configured ~/.xinitrc to have setxkbmap -variant colemak; xset r66; xset r rate 191; xset s off -dpms. Added .bash_alias

Compiled dwm, st, and surf all with gruvbox patch one way or another. Here's what I've learnt, 'makepkg' to run modified arch user
repo build and 'make' to compile C programs. Checked and modified /etc/hosts when ethernet is bothced. Gives up on compiling browser and instead stick with bin version of it. Got problems with public gpg key, it turns out aur use user key and not the one on pacman, I still need to learn more of it.

Default layout configured with 'loadkeys' overridden when xorg is installed. Turns out it loads different config and can be manually configured by modifying /etc/X11/xorg.conf.d/00-keyboard.conf or using 'localectl' (e.g localectl --no-convert set-x11-keymap us pc105 ,dvorak) doing the latter overwrite the former config file.

Added audio and brightness capabiltity to dwm config.h. Before I can use them properly I need to install pipewere-pulse and brightnessctl respectively. Reminds me to remove linux account timeout lock. Add $HOME/user-dirs.dirs to set default directory for common user directory. When updating grub with pacman don't forget to 'grub-install' again and 'grub-mkconfig -o /boot/grub/grub.cfg'. To allow non-latin font and emoji rendering on browser or any other graphical software you need to download them manually (e.g ttf-ancient-fonts for ancient language unicode rendering). Install libnotify to allow utilizing  'notify-send'.

There are plenty of things I need to patch if I want to use st conveniently.

Added EDITOR=vim in /etc/environment and run 'xdg-mime default vim.desktop text/plain' recently so that it default to vim when editing plain text file.
