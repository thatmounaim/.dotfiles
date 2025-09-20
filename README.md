# Work in Progress

## Step 1 - Install Fedora Sway Flavour

## Step 2 - Post install 

Note: These commands were taken from bash history after a fresh install, if i missed anything that's needed please let me know until i test it in this order on a fresh install.
```bash
# Update
sudo dnf update
# Add RPM Fusin Repos
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# AppImage Support
sudo dnf in fuse fuse3

# Multimedia and Graphics
sudo dnf group install multimedia
sudo dnf swap 'ffmpeg-free' 'ffmpeg' --allowerasing
sudo dnf upgrade @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
sudo dnf group install sound-and-video
sudo dnf install ffmpeg-libs libva libva-utils
# AMD Drivers
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld

# More Multimedia and Graphics
sudo dnf install openh264 gstreamer1-plugin-openh264 mozilla-openh264
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1

# Misc Needed
sudo dnf install git unzip p7zip p7zip-plugins unrar go ripgrep luajit playerctl fastfetch

# Replace Greeter with TUI Based Greeter
sudo dnf install greetd greetd-gtkgreet tuigreet 

# Virtualisation
sudo dnf install @virtualization
sudo dnf group install --with-optional virtualization

# Brave Browser
sudo dnf install dnf-plugins-core
sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
sudo dnf install brave-browser

# User Packages (Optional)
sudo dnf install vim nvim gimp inkscape tmux thunderbird wdisplays go-task

# Jetbrains Toolbox - Download using default browser
xdg-open "https://www.jetbrains.com/toolbox-app/download/download-thanks.html?platform=linux"
# After Download
cd Downloads
tar -xzvf jetbrains-toolbox-*
mkdir -p ~/Apps/jetbrains-toolbox
rm jetbrains-toolbox-*.*
mv -r jetbrains-toolbox-* ~/Apps/jetbrains-toolbox
cd
```
#### Only on Personal PC
```bash
sudo dnf install blender godot nebula steam
```

### App Themes - Catppuccin Macchiato
[Firefox](https://color.firefox.com/?theme=XQAAAAJLBAAAAAAAAABBqYhm849SCicxcUcPX38oKRicm6da8pG5gi-DrbS7fiEFLUzDsWXWyUHMSkHZ2PpRK_LvZGTF44fp7VjbASbxkoZAmYAwEJIoRnjw8xrOTGV_TjmyI1jBzmpM9P7ysk1XcU5Vim_Fm-lEdd2D1sQPsVLwIxVk1FLPo7F1GlxDxEbvzz2oyPkXJKwznKedTeki8Ni5-1N2IG5ILU0xTLPxbSOgMlp8Gtpz2UTBtY7mDjgmnzg5f1dFvM3U6Zb_USTJm_VEifPtctzp32FCuv1Hj3ajaJnmmzgKTtWRnVdej9xjhRuEmO3_HRE8-dC6LZZeEC5zr0Sfj2a8OyJl85HG_XpX_gR1-_j9NUkb89NePlNVCxI2Lr4m8v27wIwRH9Rtuv2UdsFuGrc5YKmTvvpH4PdqwGnrH0mdOs-PNQ6bXLtqr7dQQxzC5NPvCckRYd5Pu7YuuWBTmXqQ2S1kKg53z2OaX1kXcZwbiUzDQHO13vQMdvQUBzWXhXZrnQA77vOAc9X-rHTSdW9Y6esghRmoHbHbnFFK202RUtGdF6AbYyNtwP_d_RD-)
[Brave/Chromium Based](https://chromewebstore.google.com/detail/catppuccin-chrome-theme-m/cmpdlhmnmjhihmcfnigoememnffkimlk) 
[Thunderbird](https://github.com/catppuccin/thunderbird/raw/refs/heads/main/themes/macchiato/macchiato-lavender.xpi)
[Godot Text Editor](https://raw.githubusercontent.com/godotengine/godot-syntax-themes/refs/heads/master/Catppuccin-Macchiato.tet)
**Godot Editor:**
1.  In Godot, go to Editor → Editor Settings → Interface → Theme
2.  Use the following settings:
    -   Base Color: `#24273a`
    -   Accent:  `#9ea7f7`
    -   Contrast:  `0.2`
    -   Icon Saturation:  `0.6`

## Step 3 - Configuring Look and Feel

```bash
# Clone Dotfiles
git clone https://github.com/thatmounaim/.dotfiles

# Sway, Waybar, Swaylock, Rofi
cp -r ~/.dotfiles/home/moon/.config/* ~/.config/

# Greetd & Tuigreet
sudo cp ~/.dotfiles/etc/greetd/config.toml /etc/greetd/config.toml 

# GTK Theme & Cursors
cp -r ~/.dotfiles/home/moon/.themes ~/.themes
cp -r ~/.dotfiles/home/moon/.icons ~/.icons

# OhMyBash - Install
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"

# Aliases & Bash Profile/RC ( Change as needed )

cp ~/.dotfiles/home/moon/.bashcommon ~/
cp ~/.dotfiles/home/moon/.bash_profile ~/
cp ~/.dotfiles/home/moon/.profile ~/
cp ~/.dotfiles/home/moon/.bashrc ~/
```

