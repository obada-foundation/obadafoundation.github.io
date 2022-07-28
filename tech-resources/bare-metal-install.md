
# Bare Metal Install

## Hardware Prerequisites

1.  Server to host node

    | Resource | Amount | Note |
    | -------- | ------ | ---- |
    | CPU | 4 Core |  |
    | Memory | 8GB |  |
    | Hard Drive | 512GB+ | 32GB free at all times |
    | Nic | 2 | One for external public internet / one for internal network |
    | USB Drive | 1 x 8GB | For Install media |

2. Workstation to provision node.  Look at [Installation - Ubuntu](https://ubuntu.com/server/docs/installation) for minimum requirements then add resources needed for workstation load.

    | Resource | Amount | Note |
    | -------- | ------ | ---- |
    | CPU | 4 Core |  |
    | Memory | 8GB |  |
    | Hard Drive | 128GB |  |
    | Nic | 1 | One for internal network connection. Must be able to connect to node internal connection |
    | USB Drive | 1 x 8GB | For Install media |
    
* You will need a 3rd PC for preparation

## Software Prerequisites

| Resource | Software | Note |
| -------- | ------ | ---- |
| Node | Ubuntu 22.04 LTS | Desktop or server |
| Workstation | Ubuntu 22.04 LTS | Desktop |
| Github | Obada/testnode | https://github.com/obada-foundation/testnet |
| Balena | Etcher 1.7.9 | [balenaEtcher - Flash OS images to SD cards & USB drives](https://www.balena.io/etcher/), used on preparation pc |

## Preparation Checklist

1. Node

    | Parameter | Value | Note |
    | -------- | ------ | ---- |
    | Hostname |  |  |
    | IP Address |  |  |
    | Netmask |  |  |
    | Default gateway |  |  |
    | DNS Server |  |  |
    | User Name |  | First account is administrator |
    | Password |  |  |
    
2. Workstation

    | Parameter | Value | Note |
    | -------- | ------ | ---- |
    | Hostname |  |  |
    | IP Address |  |  |
    | Netmask |  |  |
    | Default gateway |  |  |
    | DNS Server |  |  |
    | User Name |  | First account is administrator |
    | Password |  |  |
    
3. Prepare Install Media to USB Drive
    1. Use Etcher to create Workstation Media
  
## Time Breakdown

Several of these steps don't require attention from the user, you don't need to wait while the job is done.

| Step | Approximate Time | Note |
| -------- | ------ | ---- |
| Source/build node hardware | 1 hour to 1 day | Can vary depending on source and availability of hardware |
| Source/build workstation | 1 hour to 1 day | Can vary depending on source and availability of hardware |
| Download prepare install media | 1 hour | Can vary based on internet seped |
| Install Operating System | 1 hour | Can vary depending on hardware |
| Configure Operating System | 1 hour | Can vary depending on environment |
| Watch testnode video | 30 minutes | [Link to Video Here](https://github.com/obada-foundation/testnet#installation--deploying-obada-node) |
| Install prerequisites | 5 minutes |  |
| Install node | 10 minutes |  |

## Setup Diagram

![setup-diagram](https://user-images.githubusercontent.com/105013305/181301849-4a5fb081-9b7e-429b-a200-9ef28329ef01.png)

## Preparation PC - Download and Create Install Media

1. Download Ubuntu Desktop
    1. Using a browser navigate to [Download Ubuntu Desktop - Download - Ubuntu](https://ubuntu.com/download/desktop)
    2. Click the 'Download' button
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
![install-u-1](https://user-images.githubusercontent.com/105013305/181302155-bb4a8de2-ea67-48c9-aaf9-2e18184e115e.png)

3. Select Keyboard layout and select 'Continue'.
![install-u-2](https://user-images.githubusercontent.com/105013305/181302431-bb0cc489-2a95-4733-93e5-cd694c739a41.png)

4. Keep default and select 'Continue'.
![install-u-3](https://user-images.githubusercontent.com/105013305/181302507-dbc8c18f-c5e1-4ca7-a137-77f5e7c076f4.png)

5. Keep default selected for 'Erase and install Ubuntu'. Then select 'Install Now'.
![install-u-4](https://user-images.githubusercontent.com/105013305/181302540-7369f25a-fcb6-48f6-9653-5b99d4e0c08d.png)

6. Confirm installation and select 'Continue'.
![install-u-5](https://user-images.githubusercontent.com/105013305/181302731-b7cd6824-aa2a-4791-8458-0416038117f5.png)

7. Select time zone and select 'Continue'.
![install-u-6](https://user-images.githubusercontent.com/105013305/181302743-042498ba-a022-4318-9529-13dbc1096fca.png)

8. Enter your user account information and hostname, Node or workstation name. Keep other defaults and select 'Continue'.
![install-u-7](https://user-images.githubusercontent.com/105013305/181302768-d4ce5c93-dd19-4b55-a49f-efcf53b94bac.png)

9. When prompted Reboot computer.
![install-u-8](https://user-images.githubusercontent.com/105013305/181302795-72762ab3-9f1a-4fca-a732-b3b3e0057a23.png)

10. After reboot, login with credentials recorded in step 8.  Click on User account for password prompt.
![install-u-9](https://user-images.githubusercontent.com/105013305/181302824-c9d18f7e-3f99-42bd-a593-045f11655c7d.png)

11. At the desktop Select the networking settings icon in title bar, expand Wired Settings, then select wired settings.
![install-u-10](https://user-images.githubusercontent.com/105013305/181302871-de6f7a3c-b0cd-4e02-846c-9ad9fdf0709f.png)

12. Select the IPv4 tab.  Click the Manual radio button.  Enter the IP address, netmask and default gateway parameters.  Uncheck automatic switch for DNS server and enter your dns server ip address in the textbox.
![install-u-11](https://user-images.githubusercontent.com/105013305/181302896-357d3567-b8c7-4a84-9de9-b5df098f5e8d.png)

## Install Node

On the Node server 
    
1. Open a terminal.
2. Update system.  At prompt enter the following commands

    > sudo apt-get update
    > 
    > sudo apt-get upgrade

3. Install dependencies.

    > sudo apt-get install openssh-server -y

Do the following steps from the workstation.

4. Open a terminal.
5. Update system.  At prompt enter the following commands.

    > sudo apt-get update
    > 
    > sudo apt-get upgrade

6. Install dependencies.

    > sudo apt install docker.io make -y

7. Add user to the docker group.

    > sudo usermod -aG docker $USER

8. Reboot computer.

9. Login and open a terminal.

10. Clone repository.

    > mkdir obada
    > 
    > cd obada
    > 
    > git clone https://github.com/obada-foundation/testnet
    > 
    > cd testnet
    > 

11. Generate server certificates.

    > make certificates

12. Add certificates to node server.
    1. Login to node server with admin credentials
    2. Open terminal and enter these commands.
  
    > mkdir .ssh
    > 
    > chmod 700 .ssh
    > 
    > cd .ssh
    > 
    > touch authorized_keys
    > 
    > vi authorized_keys

    Append the contents of ssh/obada_node_ssh_key.pub to ~/.ssh/authorized_keys

    > ~wq to save the file
    > 
    > chmod 600 authorized_keys
    > 
    > exit

13. Enter rest from workstation, Edit Make file.

    Add –ask-become-pass to end of docker run command in make file, parameter begins with a double dash.
  
    > docker run \ 
    > 
    > -it \
    > 
    > --rm \
    > 
    > -v $(pwd)/ssh:/home/ansible/.ssh \
    > 
    > -v $(pwd)/deployment:/home/ansible/deployment \
    > 
    > -v $(pwd)/inventory:/home/ansible/inventory \
    > 
    > -v $(pwd)/testnets:/home/ansible/testnets \
    > 
    > obada/ansible \
    > 
    > ansible-playbook deployment/playbook.yml -i inventory --ask-become-pass

14. Run make deploy.
    1. Enter password 
    2. Enter 1 for Test net
15. Node should be installed.



