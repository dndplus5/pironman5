# Pironman 5

Pironman 5 case

![image alt](https://github.com/dndplus5/pironman5/blob/main/Pironman-5.jpg?raw=true)

Quick Links:

- [Pironman 5](#pironman-5)
  - [About Pironman5](#about-pironman5)
  - [Links](#links)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Update](#update)
  - [Compatible Systems](#compatible-systems)
    - [Ubuntu 24.04 server eth0 and wifi not work](#ubuntu-2404-server-eth0-and-wifi-not-work)
    - [Debug](#debug)

## About Pironman5

## Links

- Documentation &emsp; <https://docs.sunfounder.com/en/latest/>

## Installation

If your systems doesn't have git, or python3 pre-installed you need to install them first

```bash
sudo apt-get update
sudo apt-get install git python3 -y
```

Execute the installation script

```bash
cd ~
git clone https://github.com/sunfounder/pironman5.git
cd ~/pironman5
sudo python3 install.py
```

## Usage
There are a few more steps to initiate the oled and case fans

```bash
cd ~/pironman5
sudo nano /boot/config.txt
```
## Config.txt
Add these lines of code to activate the pins for the oled and case fans

```bash
dtoverlay=gpio-power,gpio_pin=26,active_low=0
dtoverlay=gpio-ir,gpio_pin=13
```
# cntrl+o, enter, cntrl+x to save and exit the file

# Now let's turn the fans on

```bash
sudo pironman5 -gpn 0
sudo systemctl restart pironman5.service
```

## Update

<https://github.com/sunfounder/pironman5/blob/main/CHANGELOG.md>

```bash
## Compatible Systems

Operate Systems that passed the test on the Raspberry Pi 5:

Operate System | Release Date | Compatible
:---   | :---: | :---: 
Raspberry Pi OS Desktop - bookworm (64 bit) | 2024-11-19 | &#x2705;
Raspberry Pi OS Desktop - bookworm (32 bit) | 2024-11-19 |  &#x2705;
Raspberry Pi OS Full - bookworm (64 bit) | 2024-11-19 |  &#x2705;
Raspberry Pi OS Full - bookworm (32 bit) | 2024-11-19 |  &#x2705;
Raspberry Pi OS lite - bookworm (64 bit) | 2024-11-19 |  &#x2705;
Raspberry Pi OS lite - bookworm (64 bit) | 2024-11-19 |  &#x2705;
Ubuntu Desktop 24.04.1 LTS (64 bit) | 2024-08-29 |  &#x2705;
Ubuntu Server 24.04.1 LTS (64 bit) | 2024-10-10 |  &#x2705;
Ubuntu Desktop 24.10 (64 bit) | 2024-10-10 |   &#x2705;
Ubuntu Server 24.10 (64 bit) | 2024-08-29 |   &#x2705;
Kali Linux | 2024-08-27 | &#x2705;
Home Assistant OS 14.0 | 2024-12-03 | &#x2705;
Homebridge bookworm (64 bit) | 2024-05-03 | &#x2705;
Homebridge bookworm (64 bit) | 2024-05-03 | &#x2705;
Batocera Linux | 2024-07-31 | &#x2705;
```
### Ubuntu 24.04 server eth0 and wifi not work

https://www.reddit.com/r/Ubuntu/comments/1d0s8v5/ubuntu_2404_server_on_my_raspberry_pi_5_and_eth0/


### Debug

Clone the dependency you want to debug or edit

```bash
git clone https://github.com/sunfounder/pironman5.git
git clone https://github.com/sunfounder/pm_dashboard.git
git clone https://github.com/sunfounder/pm_auto.git
git clone https://github.com/sunfounder/sf_rpi_status.git
```

Make adjustments, and manually install the package

```bash
cd ~/pironman5 && sudo /opt/pironman5/venv/bin/pip3 uninstall pironman5 -y && sudo /opt/pironman5/venv/bin/pip3 install .
cd ~/pm_dashboard && sudo /opt/pironman5/venv/bin/pip3 uninstall pm_dashboard -y && sudo /opt/pironman5/venv/bin/pip3 install .
cd ~/pm_auto && sudo /opt/pironman5/venv/bin/pip3 uninstall pm_auto -y && sudo /opt/pironman5/venv/bin/pip3 install .
cd ~/sf_rpi_status && sudo /opt/pironman5/venv/bin/pip3 uninstall sf_rpi_status -y && sudo /opt/pironman5/venv/bin/pip3 install .
```

Start/stop the service for debug

```
sudo systemctl stop pironman5.service
sudo systemctl start pironman5.service
sudo systemctl restart pironman5.service
sudo pironman5 start

sudo /opt/pironman5/venv/bin/python3
```


