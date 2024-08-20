### Copy-Paste Files ke Root Dir
```shell
sudo cp /path/to/source/file /path/to/destination/
```
### Setting udev-rules
cara membuat udev rules:
```shell
cd ../..
cd etc/udev/rules.d
sudo gedit 10-bagas.rules
```
Masukkan identitas serial masing2 device
```shell
KERNEL=="ttyUSB*", ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", ATTRS{serial}=="0001", MODE:="0666", SYMLINK+="rplidar"
KERNEL=="ttyUSB*", ATTRS{idVendor}=="1d6b", ATTRS{idProduct}=="0002", ATTRS{serial}=="0000:00:14.0", MODE:="0666", SYMLINK+="FCU"
KERNEL=="ttyUSB*", ATTRS{idVendor}=="1a86", ATTRS{idProduct}=="7523", MODE:="0666", SYMLINK+="rosserial"
```
ID vendor&product serta serial bisa dilihat dengan 
```shell
udevadm info -a /dev/ttyUSB0
```
setelah selesai save lalu lanjut dibawah:
```shell
sudo udevadm control --reload-rules && sudo udevadm trigger
ls /dev
```
### Setting AutoStart Service
```shell
cd /etc/systemd/system
sudo gedit bagas.service
sudo systemctl start bagas
sudo systemctl enable bagas
sudo systemctl status bagas
```
