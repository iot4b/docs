# What is it?
**The EverIOT is a blockchain-based distributed platform for your IOT devices 🌐📲**

We build the solution allowing users to store and process their sensitive IoT data encrypted in public blockchains, and manage their smart-devices securely.
All data is **🔐securely stored and encrypted in blockchain⛓️‍💥**. That keeps sensitive information as confidential.

The common idea of connections can be shown in a simple line:

[**IoT Device**] <--> 
    [**Node**: Gateway to blockchain and proxy for applications] <--> 
         [**BlockChain**: Secured data storage, Events processing and User access control]



You can find more detailed explanations on [our readme](https://github.com/ever-iot/docs/blob/main/README.md)

## How to start
‼️It's mandatory to own your personal Keenetic or OpenWRT router to participate alpha test. 

Then you have to pass 3 easy steps:
1. Install [mobile app](https://github.com/ever-iot/docs/edit/main/Alfa-test.md#install-app-guide)
2. Install [everIoT module](https://github.com/ever-iot/docs/edit/main/Alfa-test.md#install-device-module) to your router
3. [Connect](https://github.com/ever-iot/docs/edit/main/Alfa-test.md#how-to-add-a-device-to-the-application) mobile app and device

## Alpha-test FAQ
The main goal of alpha testing is to research additional use cases, fix bugs and errors, and improving UX. Please respond any test-related information you may find important to a Telegram channel [@iot4b](https://t.me/iot4b)

# Quick Start instructions ✅
## Install app guide
First, install a mobile application for your platform - iOS / Android. Links:
* Android - https://appdistribution.firebase.dev/i/89e35cb759f4a089
* iOS - https://testflight.apple.com/join/R7MyUZXv

You have to accept an invitation to join Alpha testing.

In the application, you can create a new account with a seed phrase, or restore an existing account. If you never used our service before, click 'Create New Account' and follow the steps.

## Install device module
To control your device with our service, you have to install some components. Currently, two types of devices are supported: **Keenetic** with USB port and **OpenWRT**.

If you have a Keenetic device then make this steps first:
1. Make sure your router has an OPKG module installed for the router's admin tools
2. Install Entware to your router. Please refer to Keenetic's guide https://help.keenetic.com/hc/en-us/articles/360021214160
3. To log in to entware shell, do it with `root` user (default password: `keenetic`)

Then the common part for both types of routers: 
1. Open your router with SSH:
```ssh root@192.168.X.X```
2. In your SSH session run commands:
```sh
opkg update
opkg install curl
/bin/sh -c "$(curl http://repo.iot4b.co/packages/install.sh)"
```
3. In the setup wizard enter the device group address and owner public key, the mobile application will show you on the "Add Device" screen ("+" button in the device group)
4. Copy the device address and use it to add the device to the application.


## How to add a deposit
🎉 GOOD NEWS! For alfa-test users all required funds will be transferred to the group and devices automatically 🤑 

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


## Community
Feel confused with your questions? Feel free to ask on telegram [@iot4b](https://t.me/iot4b) - our official telegram group for bug reports and questions. 
