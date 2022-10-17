# How to install Lapce on Ubuntu 22.04.1 LTS (in VirtualBox 6.1.38)

Tutorial on how i got Lapce to work on a freshly installed Ubuntu in VirtualBox.

Lapce code editor: [https://github.com/lapce/lapce](https://github.com/lapce/lapce)

## Download Ubuntu

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

### Update your system from the settings and reboot if required

```bash
/usr/bin/update-manager
```

### Update apt packages
```bash
sudo apt update
sudo apt upgrade
```

### Install apt packages
```bash
sudo apt install -y g++ curl git cmake pkg-config libfontconfig-dev libgtk-3-dev
```

### Install rust
```bash
curl https://sh.rustup.rs -sSf | sh
export PATH="$PATH:$HOME/.cargo/bin"
cargo --version
```

### Fetch Lapce source code
```bash
git clone https://github.com/lapce/lapce.git ~/lapce
```

### Build Lapce
```bash
cd ~/lapce
cargo build --release
```

### Start Lapce
```bash
~/lapce/target/release/lapce
```

### Create a desktop file
```bash
echo "[Desktop Entry]
Version=1.0
Name=Lapce
Exec=$HOME/lapce/target/release/lapce
Path=$HOME/lapce/target/release/
Icon=$HOME/lapce/extra/images/logo_color.svg
Terminal=false
Type=Application
Categories=Utility;Development;" > $HOME/.local/share/applications/lapce.desktop
xdg-desktop-menu forceupdate
```
