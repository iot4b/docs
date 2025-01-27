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

1. Download the corresponding module from this repo on your computer - https://github.com/ever-iot/docs/blob/main/packages/iot4b_keenetic.ipk
2. Make sure your Keenetic device and computer are in one network.
3. Make sure your router has an OPKG module installed for the router's admin tools
4. Install Entware to your router. Please refer to Keenetic's guide https://help.keenetic.com/hc/ru/articles/360021214160.

5. Transfer installation file to required directory on your router. You can use built-in web admin interface to do this. Also,
you can execute following script in Command Line(Windows) or Terminal(Mac and Linux) on your computer: ```scp iot4b_keenetic.ipk admin@192.168.X.X:/tmp/ ```
where 192.168.X.X is your Keenetic router address
6. Open your router with SSH:
```ssh admin@192.168.X.X```
7. In your SSH session run 
```opkg install /tmp/iot4b_keenetic.ipk```
8. In the setup wizard enter the device group address and owner public key, the mobile application will show you on the "Add Device" screen ("+" button in the device group)

### OpenWrt
This is a guide of installation on OpenWRT devices. 
Minimum requirements: OpenWRT device with USB port.

1. Download the corresponding module from this repo on your computer - https://github.com/ever-iot/docs/blob/main/packages/iot4b_openwrt.ipk
2. Make sure your OpenWRT device and computer are in one network.
3. Transfer installation file to required directory on your router. You can use built-in web admin interface to do this. Also, you can execute following script in Command Line(Windows) or Terminal(Mac and Linux) on your computer: ```scp iot4b_openwrt.ipk admin@192.168.X.X:/tmp/ ```
where 192.168.X.X is your OpenWRT router address
4. Open your router with SSH:
```ssh admin@192.168.X.X```
5. In your SSH session run 
```opkg install /tmp/iot4b_openwrt.ipk```
6. In the setup wizard enter the device group address and owner public key, the mobile application will show you on the "Add Device" screen ("+" button in the device group)


## How to add a deposit
For alfa-test users all required funds will be transferred to the group and devices automatically

## How to add a device to the application
1. Create a group by clicking "Add Group" button or use existing group.
2. Click "+" button to add a device in a group.
3. On the device, set up a module with group address and owner public key that are shown on the "Add Device" app screen.
4. After our module setup is complete, it will display the device smart contract address.
5. Copy the device contract address above, enter it into the address field in the mobile app, and then click "Add Device".

## Device management
All the device management tools are placed in device details view. Simply click device name in Group list, and you will get it. Now available:
* send commands to your device with Send CMD option
* lock and unlock your device by using a toggle
* view a history of events
* enable or disable saving events
* take a look on details of fund usage in blockchain view. Just click on address or group address
* rename device in the application (takes some time for new name to apply)
## Owners management

# How it works
You can find more explanations on https://github.com/ever-iot/docs/blob/main/README.md
# Roadmap
