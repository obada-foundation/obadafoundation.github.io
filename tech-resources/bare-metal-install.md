
# Bare Metal Install

## Hardware Prerequisites

1.  Server to host node

2. Workstation to provision node.  Look at [Installation | Ubuntu](https://ubuntu.com/server/docs/installation) for minimum requirements then add resources needed for workstation load.

* You will need a 3rd PC for preparation

## Software Prerequisites

## Preparation Checklist

1. Node

2. Workstation

3. Prepare Install Media to USB Drive
    1. Use Etcher to create Workstation Media
  
## Time Breakdown

Several of these steps don't require attention from the user, you don't need to wait while the job is done.

## Setup Diagram

## Preparation PC - Download and Create Install Media

1. Download Ubuntu Desktop
    1. Using a browser navigate to [Download Ubuntu Desktop | Download | Ubuntu](https://ubuntu.com/download/desktop)
    2 Click the 'Download' button
2. Download and install BalenaEtcher from [balenaEtcher - Flash OS images to SD cards & USB drives](https://www.balena.io/etcher/) on preparation pc.
3. Create Media
    1. Insert USB Drive into Computer being used for preparation
    2. Launch BelenaEtcher
    3. Select 'Flash from file' button
    4. When dialog box opens navigate to the folder where the Ubuntu image was downloaded and select the server file.
    5. Select Target.
    6. Select the USB Drive inserted from step a.
    7. Select 'Flash!' to initiate writing to the USB Drive.
    8. When done remove the USB.

## Node Preparation

Check your Server manual for the following steps:

1. Configure hard drives if using hardware raid.
2. Configure server bios to boot from USB Drive.
3. Place usb in a slot the server can boot from.  Not all servers enable every port for booting.
4. Power on or reboot Server.
5. Install OS, follow Install Ubuntu Desktop Instructions later in document.
6. Set hostname.
7. Configure ethernet.
8. Add routes if needed for connectivity.

## Workstation Preparation

Check your Workstation for the following steps:

1. Configure server bios to boot from USB Drive.
2. Place usb in a slot the computer can boot from.  
3. Power on Workstation.
4. Install OS, follow Install Ubuntu Desktop Instructions.
5. Set hostname.
6. Configure ethernet.
7. Add routes if needed for connectivity.

At this point you should be ready to install Node.

## Install Ubuntu Desktop

1. Do the same process for both Node and workstation, use appropriate Hostname and IP address parameters for each machine. 
2. At the Install screen select Install Button

3. Select Keyboard layout and select 'Continue'.

4. Keep default and select 'Continue'.

5. Keep default selected for 'Erase and install Ubuntu'. Then select 'Install Now'.

6. Confirm installation and select 'Continue'.

7. Select time zone and select 'Continue'.

8. Enter your user account information and hostname, Node or workstation name. Keep other defaults and select 'Continue'.

9. When prompted Reboot computer.

10. After reboot, login with credentials recorded in step 8.  Click on User account for password prompt.

11. At the desktop Select the networking settings icon in title bar, expand Wired Settings, then select wired settings.

12. Select the IPv4 tab.  Click the Manual radio button.  Enter the IP address, netmask and default gateway parameters.  Uncheck automatic switch for DNS server and enter your dns server ip address in the textbox.

## Install Node

On the Node server 
    
1. Open a terminal.
2. Update system.  At prompt enter the following commands

    > sudo apt-get update
    > sudo apt-get upgrade

3. Install dependencies.

    > sudo apt-get install openssh-server -y

Do the following steps from the workstation.

4. Open a terminal.
5. Update system.  At prompt enter the following commands.

    > sudo apt-get update
    > sudo apt-get upgrade

6. Install dependencies.

    > sudo apt install docker.io make -y

7. Add user to the docker group.

    > sudo usermod -aG docker $USER

8. Reboot computer.

9. Login and open a terminal.

10. Clone repository.

    > mkdir obada
    > cd obada
    > git clone https://github.com/obada-foundation/testnet
    > cd testnet

11. Generate server certificates.

    > make certificates

12. Add certificates to node server.
    1. Login to node server with admin credentials
    2. Open terminal and enter these commands.
  
    > mkdir .ssh
    > chmod 700 .ssh
    > cd .ssh
    > touch authorized_keys
    > vi authorized_keys

    Append the contents of ssh/obada_node_ssh_key.pub to ~/.ssh/authorized_keys

    > ~wq to save the file
    > chmod 600 authorized_keys
    > exit

13. Enter rest from workstation, Edit Make file.

    Add –ask-become-pass to end of docker run command in make file, parameter begins with a double dash.
  
    > docker run \ 
    > -it \
    > --rm \
    > -v $(pwd)/ssh:/home/ansible/.ssh \
    > -v $(pwd)/deployment:/home/ansible/deployment \
    > -v $(pwd)/inventory:/home/ansible/inventory \
    > -v $(pwd)/testnets:/home/ansible/testnets \
    > obada/ansible \
    > ansible-playbook deployment/playbook.yml -i inventory --ask-become-pass

14. Run make deploy.
    1. Enter password 
    2. Enter 1 for Test net
15. Node should be installed.


