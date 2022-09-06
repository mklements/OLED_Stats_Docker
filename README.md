# OLED_Stats_Docker

OLED Stats display script and settings for Docker implementation

The script is pre-configured for 128x64 I2C OLED Display, but can easily be modified to run on a 128x32 I2C OLED Display

## Installation Steps

The connections and setup of the display are as per my repository for running on Raspberry Pi OS - <https://github.com/mklements/OLED_Stats>

<img align="right" src="https://www.the-diy-life.com/wp-content/uploads/2022/09/187172812-de2de65c-bd30-40e7-a852-2d424edc27ab.jpg" height="220"></img>

## To install on Docker

If you do not have Docker yet

```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

## Script setup

```shell
sudo raspi-config nonint do_i2c 0
git clone https://github.com/mklements/OLED_Stats_Docker
cd OLED_Stats_Docker
docker build -t oled-stats .
docker run -d -v /etc/timezone:/etc/timezone -v /etc/localtime:/etc/localtime --network=host --device=/dev/i2c-1 --device=/dev/gpiomem --name OLED-Stats oled-stats
```
