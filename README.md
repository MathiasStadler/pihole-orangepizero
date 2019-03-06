# pihole

## sources

```txt
https://install.pi-hole.net
https://www.kuketz-blog.de/pi-hole-schwarzes-loch-fuer-werbung-raspberry-pi-teil1/
```

## env

- orange pi zero 512MByte EFI Boot
- Armbian Strech distro 5.65

## delete ( if available ) desktop packages

- active network device not necessary software

```bash
sudo tasksel --list-tasks
# e.g for XFCE
sudo tasksel remove xfce-desktop
```

## change hostname

```bash
# set hostname
sudo hostnamectl set-hostname pihole-home

# check hostname
sudo hostnamectl

```

## set static ip and dns out of DHCP range

- edit/change /etc/network/interfaces

```bash
# depend of available network
source /etc/network/interfaces.d/*
# Network is managed by Network manager
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.178.245
    netmask 255.255.255.0
    gateway 192.168.178.1
    dns-search fritz.box
    dns-nameservers 8.8.8.8 8.8.4.4
```

| REBOOOT the system for activate the settings safely

- check your ip

```bash
> ip addr show eth0
 ```

- and hostname

```bash
> hostname

```

check dns

```bash
dig +short linux.org

```

## install pihole

```bash
sudo curl -sSL https://install.pi-hole.net | sudo bash
# follow instruction
# select all defaults
```

**SAVE** the password in the last dialog for the pi-hole gui

## start the gui of pi-hole in your browser

- open your favorite browser
- visit the page <ip of pi-hole device>/admin

## TODO pi-hole https

## big block list

- [big block list](https://der-pcfuchs.de/wp-content/uploads/2018/03/Big-Pi-hole-Blocklist.txt)
- [tutorial](https://der-pcfuchs.de/big-pi-hole-blocklist/) for inport to pi-hole

```bash
# edit manual addlist
sudo vi /etc/pihole/adlists.list
```

## easy list

- [easylist](https://github.com/justdomains/blocklists#using-with-pi-hole)


