# rhel-network-install-setup
The rhel-network-install-setup guide provides essential information for managing networking, troubleshooting, and setting up repositories for offline installation on Red Hat Enterprise Linux (RHEL)


# Table of Contents
1.[Network Management Commands](#1-network-management-commands)
- [Check Network Interfaces](#check-network-interfaces)
- [View NetworkManager Connections](#view-networkmanger-connections)
- [Manage Network Connections](#mange-network-connections)
- [Modify Connections](#modify-connections)
- [Device Information](#device-information)

2.[Network Troubleshooting Commands](#2-network-troubleshooting-commands)

3.[Repository Setup for Offline Installation](#3-repository-setup-for-offline-installation)
- [Mounting and Accessing the CD-ROM](#mounting-and-accessing-the-cd-rom)
- [Configure YUM Repositories](#configure-yum-repositories)
- [Install and Manage Packages](#install-and-manage-packages)

# 1. Network Management Commands

## Check Network Interfaces
Displays all network interfaces and their IP addresses.
ip a or ifconfig

![Screenshot from 2024-12-03 23-24-47](https://github.com/user-attachments/assets/18928bae-24cc-4c08-aad3-8cae2150a7e4)


Shows statistics for network interfaces, including RX (received packets) and TX (transmitted packets).

![Screenshot from 2024-12-03 23-25-43](https://github.com/user-attachments/assets/73ac6e04-528d-453f-8074-235967252657)


## View NetworkManager Connections
Lists all available network connections.

![Screenshot from 2024-12-03 23-26-41](https://github.com/user-attachments/assets/28ca3695-f106-4d7a-a1af-518995e449a6)


Displays the status of devices managed by NetworkManager.

![Screenshot from 2024-12-03 23-27-15](https://github.com/user-attachments/assets/f64f0394-b94d-43f8-8900-c3a1510cf487)


## Manage Network Connections

nmcli con up <connection-name>     # Activates a specified connection.
nmcli con down <connection-name>   # Deactivates a specified connection.
Examples:

Activates the connection named "con1".

![Screenshot from 2024-12-03 23-31-42](https://github.com/user-attachments/assets/b92a0ec7-f961-4fd7-9116-c2c16ae76c5f)


Deactivates the connection for the "con1" interface.

![Screenshot from 2024-12-03 23-33-03](https://github.com/user-attachments/assets/c6bf1d84-4742-4318-9c6a-afdac680294c)


Turns off networking.

![Screenshot from 2024-12-03 23-34-53](https://github.com/user-attachments/assets/aa1d8c97-32f3-48d0-8020-200246a6f9fb)


Turns on networking.

 ![Screenshot from 2024-12-03 23-35-51](https://github.com/user-attachments/assets/67fc321f-3e98-471c-938c-9cf401860adf)


## Modify Connections

nmcli con add con-name 'home' type ethernet ipv4.addresses 192.168.0.111/24

![Screenshot from 2024-12-03 23-37-47](https://github.com/user-attachments/assets/1d4b05ae-720e-499d-8a22-bf814790402a)

Modify

![Screenshot from 2024-12-03 23-39-11](https://github.com/user-attachments/assets/f98f37f4-35c0-498a-a95e-bc4a3c7bfc85)


Activates the "home" connection

![Screenshot from 2024-12-03 23-40-07](https://github.com/user-attachments/assets/b0887964-7e04-4597-907f-325f7f5f6e0f)
                  

Displays details of the "home" connection

![Screenshot from 2024-12-03 23-41-15](https://github.com/user-attachments/assets/88068e57-2c83-42ba-b85f-fe697e61347a)

you can modify this by above modify command

## Device Information
Shows detailed information about all devices.

![Screenshot from 2024-12-03 23-46-23](https://github.com/user-attachments/assets/dee88f21-93c5-4ebd-802d-7eac2319e168)



Displays detailed information for the "ens160" device.

![Screenshot from 2024-12-03 23-47-20](https://github.com/user-attachments/assets/8b08f15b-0cdf-40cc-81f8-fce59f866546)

you don't modify it 

Disables the "ens160" device.

![Screenshot from 2024-12-03 23-48-48](https://github.com/user-attachments/assets/9f686ca1-6c8e-484f-9efc-93363c294e2f)
           

Enables the "ens160" device.

 ![Screenshot from 2024-12-03 23-49-45](https://github.com/user-attachments/assets/fa76ab41-2c7a-427f-8da4-ec1346157e7d)


# 2. Network Troubleshooting Commands

ping

The ping command in Linux is used to test the connectivity between your system and another system (host) over a network. When you use ping with an IP address, it sends packets of data to that IP address and waits for a response. This helps you check if the target machine is reachable and measures the time it takes for the packets to travel back and forth

![Screenshot from 2024-12-03 23-51-07](https://github.com/user-attachments/assets/c5b070d8-0dc9-4377-9a3f-939f46b08fe4)


Traces the path to Google, showing each hop and its latency.

![Screenshot from 2024-12-03 23-57-00](https://github.com/user-attachments/assets/8f2590e2-a64e-496e-806f-e614eb2181a9)

         
# 3. Repository Setup for Offline Installation
## Mounting and Accessing the CD-ROM

Navigate to the cdrom Device

![Screenshot from 2024-12-03 23-02-21](https://github.com/user-attachments/assets/62fde5a7-908f-4dd9-8a1b-ba9f4df0681b)

             
## Create a Mount Point and Mount the CD-ROM

Creates a directory for mounting the CD-ROM.

![Screenshot from 2024-12-03 23-05-18](https://github.com/user-attachments/assets/868a4ff3-9fd9-4a85-ab07-0ddea473ab7e)



Mounts the CD-ROM to the "/install" directory.

![Screenshot from 2024-12-03 23-06-17](https://github.com/user-attachments/assets/763ce4cc-8d32-4ecb-985e-3a6926bcabb3)


In the case,you don't find BaseOs and AppOs files then mount /dev/sr1 /install   



⚠ Note: The mount is temporary and will be lost after a reboot. To persist the files:

## Configure YUM Repositories

![Screenshot from 2024-12-03 23-08-15](https://github.com/user-attachments/assets/b1309209-7c29-431d-bb28-9cf9617b7e56)


Opens a file to configure repositories.

vim redhat.repo      

## Add the following configuration:

![Screenshot from 2024-12-03 23-09-38](https://github.com/user-attachments/assets/8899e857-135f-49f9-9a92-47629bd5fc5b)


## Install and Manage Packages

Installs the Nginx web server.

![Screenshot from 2024-12-03 23-11-21](https://github.com/user-attachments/assets/dc5f94ec-c4c9-45d6-abce-1e3fce4799e1)

Installs Node.js

![Screenshot from 2024-12-03 23-12-31](https://github.com/user-attachments/assets/e284eaf7-ed6d-4b4d-8d0e-4b2a476c8ce0)


Removes Node.js

![Screenshot from 2024-12-03 23-13-40](https://github.com/user-attachments/assets/18461e1f-111f-4f09-ba45-0730f2416eda)

## Note:you can also use subscription method insided of offline repo setup 

![Screenshot from 2024-12-04 00-14-12](https://github.com/user-attachments/assets/7ef8a289-fedb-4cf3-a36c-9e18aa9456d5)


