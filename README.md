### Setting udev-rules
```shell
cd /etc/udev/rules.d
sudo gedit 10-bagas.rules
```
### Setting AutoStart Service
```shell
cd /etc/systemd/system
sudo gedit bagas.service
sudo systemctl start bagas
sudo systemctl enable bagas
sudo systemctl status bagas
```
