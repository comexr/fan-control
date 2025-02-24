# Clevo Fan Control on Linux
Tested on and created for some laptops of the laptop Laptopwithlinux.com sells.
The default profile is specifically adjusted for the L141AU.

## Ubuntu installation

### Build from source
1. Optionally remove conflicting packages: `sudo apt remove -y libayatana-appindicator3-1`
2. Install the necessary packages (dependencies): `sudo apt install -y gcc cmake libappindicator3-dev libgtk-3-dev pkg-config git`
3. Clone the repo: `git clone https://github.com/comexr/fan-control.git`
4. Enter the directory: `cd fan-control`
5. Install the driver: 
```shell
cmake -DUSER=$(whoami) -DGROUP=$(whoami) -DHOME=/home/$(whoami) ~/fan-control
cmake --build .
sudo cmake --install .
```
7. Reboot to apply changes: `reboot`

## Debian installation

### Build from source
1. Remove conflicting packages: `sudo apt remove -y libayatana-appindicator3-1`
2. Temporarily add Buster repo for dependency: `echo "deb http://deb.debian.org/debian buster main" | sudo tee /etc/apt/sources.list.d/temp.list`
3. Update repo list: `sudo apt update`
4. Install the necessary packages (dependencies): `sudo apt install -y gcc cmake libappindicator3-dev libgtk-3-dev pkg-config git gnome-shell-extension-appindicator`
5. Remove buster repo : `sudo rm /etc/apt/sources.list.d/temp.list`
6. Update repo list: `sudo apt update`
7. Clone the repo: `git clone https://github.com/comexr/fan-control.git`
8. Enter the directory: `cd fan-control`
9. Install the driver: 
```shell
cmake -DUSER=$(whoami) -DGROUP=$(whoami) -DHOME=/home/$(whoami) ~/fan-control
cmake --build .
sudo cmake --install .
```
7. Reboot to apply changes: `reboot`


## Fedora installation
### Build from source
1. Install debug kernel (for ec_sys module): `sudo dnf install -y kernel-debug`
2. Boot into debug kernel by default: `sudo sed -i 's/GRUB_DEFAULT=saved/GRUB_DEFAULT=0/' /etc/default/grub`
3. Update grub: `sudo grub2-mkconfig -o /boot/grub2/grub.cfg`
4. Install the necessary packages (dependencies): `sudo dnf install -y gcc cmake libappindicator-gtk3-devel pkg-config git gnome-shell-extension-appindicator`
5. Enable indicator: `gnome-extensions enable appindicatorsupport@rgcjonas.gmail.com`
6. Clone the repo: `git clone https://github.com/comexr/fan-control.git`
7. Enter the directory: `cd fan-control`
8. Install the driver: 
```shell
cmake -DUSER=$(whoami) -DGROUP=$(whoami) -DHOME=/home/$(whoami) ~/fan-control
cmake --build .
sudo cmake --install .
```
10. Reboot to apply changes: `reboot`

### Uninstalling

Use the `install_manifest.txt` generated when installing to remove the
files.

```shell
sudo xargs rm < install_manifest.txt
```

## Disclaimer
Use at your own risk! We are not responsible for any damage this software may cause to your computer. We cannot and will not provide any warranty on this!
Tested on and created for some laptops of the laptop Laptopwithlinux.com sells.
Changes in configuration and/or wrongful use may result in overheating and permanent damage of hardware.

