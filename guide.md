# What is it?
The EverIot is a blockchain-based platform for remote control of your devices. All data is securely stored and encrypted in blockchain. That keeps sensitive information as confidential.
## Some introductory words
It's mandatory to own your personal Keenetic or OpenWRT router to participate alpha test. 

## Alpha-test FAQ
The main goal of alpha testing is to research additional use cases, fix bugs and errors, and improving UX.
# Quick Start
## Install app guide
First, install a mobile application for your platform - iOS / Android. Links:
* Android - https://appdistribution.firebase.dev/i/89e35cb759f4a089
* iOS - https://testflight.apple.com/join/R7MyUZXv

You have to accept an invitation to join Alpha testing.

In the application, you can create a new account with a seed phrase, or restore an existing account. If you never used our service before, click 'Create New Account' and follow the steps.

## Install device module
To control your device with our service, you have to install some components. Currently, two types of devices are supported.
### Keenetic
This is a guide to installation on Keenetic devices. 
Minimum requirements: Keenetic device with USB port.

1. Download the corresponding module from this repo on your computer
2. Make sure your Keenetic device and computer are in one network.
4. Make sure your router has an OPKG module installed for the router's admin tools
5. Install Entware to your router. Please refer to Keenetic's guide https://help.keenetic.com/hc/ru/articles/360021214160.

6. On your computer execute following script in Command Line(Win) or Terminal(Mac and Linux): ```scp iot4b_keenetic.ipk root@192.168.X.X:/tmp/ ```
where 192.168.X.X is your Keenetic router address
7. Open your router with SSH:
```ssh root@192.168.X.X```
8. In your SSH session run 
```opkg install /tmp/iot4b_keenetic.ipk```
9. In the setup wizard enter the device group address and owner address, the mobile application will show you after registration

### OpenWrt
This is a guide of installation on OpenWRT devices. 
Minimum requirements: OpenWRT device with USB port.

1. Download the corresponding module from this repo on your computer
2. Make sure your OpenWRT device and computer are in one network.
3. On your computer execute following script in Command Line(Win) or Terminal(Mac and Linux): ```scp iot4b_openwrt.ipk root@192.168.X.X:/tmp/ ```
where 192.168.X.X is your OpenWRT router address
4. Open your router with SSH:
```ssh root@192.168.X.X```
5. In your SSH session run 
```opkg install /tmp/iot4b_openwrt.ipk```
6. In the setup wizard enter the device group address and owner address, the mobile application will show you after registration


## How to add a deposit
In the application, click Create New Devices Group. In its details, you can get the group's address. Then transfer your Ever funds to this address.
We will cover all your expenses ever in the app during the alpha test. Just let us know your device group address.

## How to add a device to the application
After our module setup is complete, the device has its address number. Just copy this address from a device disk ??? and go to the application. Then click add device button, and enter a device's address into the field.  

## Device management
All the device management tools are placed in device details view. Simply click device name in Group list, and you will get it.
You can send commands to your device with Send CMD option, lock and unlock your device by using a toggle and view a history of events.
## Owners management

# How it works
You can find more explanations on https://github.com/ever-iot/docs/blob/main/README.md
# Roadmap
