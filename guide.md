# What is it?
The ?EverIot? is a blockchain-based platform for remote control your devices. All data is securely store everything encrypted in blockchain. That keep sensitive information as confidential.
## Some introductory words

## Alpha-test FAQ
The main target of alpha-testing is to research for an additional cases of usage, fixing bugs and errors and improving UX.
# Quick Start
## Install app guide
First, install a mobile application for your platform - iOS / Android. Links:
* Android - https://appdistribution.firebase.dev/i/89e35cb759f4a089
* iOS - 

You have to accept invitation to join Alpha testing.

In application you can create new account with a seed phrase, or restore existing account. If you never used our service before, click 'Create New Account' and follow the steps. 

## Install device module
To control your device with our service, you have to install some components on your device. Currently, two types of device are supported.
### Keenetic
This is a guide of installation on Keenetic devices. 
Minimum requirements: Keenetic device with USB port.

1. Download module using this link ?****? on your computer
2. Make sure your Keenetic device and computer are in one network.
4. Make sure your router have OPKG module installed for router's admin tools
5. Install Entware to your router. Please refer to Keenetic's guide https://help.keenetic.com/hc/ru/articles/360021214160.

6. On your computer execute following script in Command Line(Win) or Terminal(Mac and Linux): ```scp iot4b_keenetic.ipk root@192.168.X.X:/tmp/ ```
where 192.168.X.X is your Keenetic router address
7. Open your router with SSH:
```ssh root@192.168.X.X```
8. In your SSH session run 
```opkg install /tmp/iot4b_keenetic.ipk```
9. In setup wizard enter device group address and owner address, that mobile application will show you after registration

### OpenWrt
This is a guide of installation on OpenWRT devices. 
Minimum requirements: OpenWRT device with USB port.

1. Download module using this link ?****? on your computer
2. Make sure your OpenWRT device and computer are in one network.
3. On your computer execute following script in Command Line(Win) or Terminal(Mac and Linux): ```scp iot4b_openwrt.ipk root@192.168.X.X:/tmp/ ```
where 192.168.X.X is your OpenWRT router address
4. Open your router with SSH:
```ssh root@192.168.X.X```
5. In your SSH session run 
```opkg install /tmp/iot4b_openwrt.ipk```
6. In setup wizard enter device group address and owner address, that mobile application will show you after registration


## How to add deposit
In application, click create new devices group. In it's details you can get the group's address. Then transfer your Ever funds to this address.
## How to add device in application
After our module setup is complete, device has it's address number. Just copy this address from a device disk ??? and go to application. The click add device button, and enter a device's address into the field.  

## Device management
## Owners management

# How it works
You can find more explanations on https://github.com/ever-iot/docs/blob/main/README.md
# Roadmap
