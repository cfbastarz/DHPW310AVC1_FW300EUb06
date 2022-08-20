# DHPW310AVC1_FW300EUb06

Vagrant compilation environment for the router DHP-W310AV firmware (Hardware Version : C1, Firmware Version : 3.00EU).

## Use

This vagrant container was used in a Mac OS X environment (Big Sur 11.6.8), but it can be used with other operating systems (Linux and Windows, not tested). Make shure to install the vagrant package along with virtual box. Under Mac OS X, use the brew package manager to install vagrant:

```
brew cask install virtualbox
```

To built the Ubuntu 14.04.6:

```
vragrant init ubuntu/trusty64
```

Once the base system is installed, load the virtual environment and log into the system:

```
vagrant up
vagrant ssh
```

## Compilation

Once logged in the virtual machine, install the necessary packages:

```
sudo apt install unzip
sudo apt-get -y install openssh-server bison flex build-essential zlibc zlib1g zlib1g-dev libncurses-dev autotools-dev autoconf lib32z1 lib32ncurses5 lib32bz2-1.0
```   

Download the firmware source code, which can be found at [GPL_v3.00b06EU_20151026.zip](https://sourceforge.net/projects/dlink/files/DHP-W310AV%20C1%20FW%20v3.00%28EU%29/).

Unzip the file and enter the directory:

```
unzip GPL_v3.00b06EU_20151026.zip
cd GPL_v3.00b06EU_20151026/DHPW310AV_C1_EU
```

Compile the firmware by issuing the `make` command and follow the screen instructions.

At the end of the compilation process, the binary file `DHPW310AVC1_FW300EUb06.bin` (7176348 bytes) will be created and can be used to flash the router.

**Note:** the compilation environment requires a certain amount of RAM. In my tests 2GB is enough. If you need, you can grab my `Vagrantfile` and use it to load the virtual machine instead of making one.

cfbastarz
