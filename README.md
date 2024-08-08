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

#### Gray Router 

```VyOS
configure

set interfaces ethernet eth0 address 192.168.0.2/30
set interfaces ethernet eth1 address 101.96.128.33/30

commit
save
exit
```

#### Red Gateway

``` Vyos
configure

set interfaces ethernet eth0 address 101.96.128.34/30
set interfaces ethernet eth0 address 192.168.2.1/24

set nat source rule 100 source address '192.168.2.0/24'
set nat source rule 100 translation address masquerade

set protocols static route 192.168.0.0/30 next-hop 101.96.128.33

commit
save
```

#### Red Win 10

```powershell
netsh interface ip set address name="Ethernet" static 192.168.2.102 255.255.255.0 192.168.2.1
```
