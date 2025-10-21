# Hello_InfluxDB3_RaspberryPi
Starter repo to run InfluxDB 3 Core on Raspberry Pi

#### Pre-requisites:

1. Rapberry Pi 5
2. Terminal application connected to Raspberry Pi


### Setup & Test

1. InfluxDB 3 comes with built in Arm binaries (64-bit) which is supported on Raspebrry Pi 5. However Raspberry Pi 5 defaults to a 16KB page size, while current InfluxDB 3 Core (via jemalloc) requires a 4KB page size. This means we need to edit one configuration on the Raspeberry Pi in it's "/boot/config.txt":

```sh
sudo nano /boot/config.txt
```
Add the following line in the config.txt file 
```sh
# Force 4KB memory pages to fix InfluxDB 3 Core startup issue
kernel=kernel8.img
```
Save & Exit.

2. Install InfluxDB 3 Core by running the following command. For more information about installation, see our [guide](https://docs.influxdata.com/influxdb3/core/install)

  - Follow the prompt to install InfluxDB 3 Core and start the server when prompted to in the end.


```sh
curl -O https://www.influxdata.com/d/install_influxdb3.sh \
&& sh install_influxdb3.sh
```


3. Test InfluxDB3 Installation by running the 'influxdb3' cli to check latest version

```sh
influxdb3 --version
```
It should print the version information confirming successful installation.
