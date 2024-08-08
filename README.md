![map drawio](https://github.com/user-attachments/assets/b726055e-fd09-4b6d-be2a-d3c7518d3233)

# Chinese Network

#### Kali

```bash
sudo nano /etc/network/interfaces
```
```nano
auto eth0
iface eth0 inet static
    address 192.168.0.2
    netmask 255.255.255.252
    gateway 192.168.0.1
```
```bash
sudo nmcli device set eth0 managed no
sudo systemctl restart networking
```

#### Router 
