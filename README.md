1. Add "chaotic-aur" repo:

sudo pacman-key --recv-key 3056513887B78AEB --keyserver keyserver.ubuntu.com
sudo pacman-key --lsign-key 3056513887B78AEB
sudo pacman -U 'https://cdn-mirror.chaotic.cx/chaotic-aur/chaotic-keyring.pkg.tar.zst'
sudo pacman -U 'https://cdn-mirror.chaotic.cx/chaotic-aur/chaotic-mirrorlist.pkg.tar.zst'
micro /etc/pacman.conf 
# Append this:
# [chaotic-aur]
# Include = /etc/pacman.d/chaotic-mirrorlist

1. Setup reflector:

Edit last line of "/etc/xdg/reflector/reflector.conf", replace `age` with `rate`
sudo systemctl start reflector.service
sudo systemctl enable reflector.timer

1. Install dependencies:

sudo pacman -Syu
sudo pacman -S pamac-aur
pamac install fd zsh zsh-completions starship ripgrep eza chezmoi ttf-fantasque-nerd linux-cachyos linux-cachyos-headers trash-cli
pamac install forkgram docker docker-compose docker-buildx code brave btop inxi

1. Change default shell

chsh -s /usr/bin/zsh
sudo chsh -s /usr/bin/zsh

1. To run gnome using wayland:

XDG_SESSION_TYPE=wayland dbus-run-session gnome-session
