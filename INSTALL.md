# Installation Guide

## VPS Installation
- Create an account on [OVH Cloud][OVHCloud].
- Purchase basic version, as we do not need anything more to handle what we are running (Upgrade if you plan on using modpacks or plugins on the server).
- When purchasing the VPS select Debian as the OS option for it to run on.
- Choose closest location to you.
- Open the EMAIL sent once the server is created and save the IP, and login info, that way you can connect to the VPS via and SSH connection.

## Connecting To VPS
- Download [Putty][PuTTY] and [WinSCP][WinSCP] as you will need both of them.
   - For Putty go through the installer and choose where you want the install to go.
   - For WinSCP, you can download it the same way. For MACs and other file transfer systems, refer to the [ReadMe][README.md]
   - Once all is installed, open up Putty, and click on SSH for a secure connection. Enter the IP adress as the hostname.
     - Once the Putty console opens up, enter the username and password provided to you in the email.

## Update & Upgrace System
- Before we create a new user we have to update and upgrade our system
- run these commands:
  - `apt update`
  - `apt upgrade`
  

## Installing Minecraft Server Package
- Go to this [link][MCServer] and copy the link from the most recent jar file.
- On the command line, enter the jar file link:
 - `wget https://launcher.mojang.com/v1/objects/c8f83c5655308435b3dcf03c06d9fe8740a77469/server.jar`
- Update the server with the command:
 - `sudo apt update`
- Install the java for the correct version of the Minecraft server, the most recent command is the following:
 - `sudo apt install openjdk-17-jre-headless`
 - `y` to confirm download

## Create Minecraft Folder
- Open up WinSCP, and select SFTP protocol, and enter the Hostname/IP, username and password once again.
- Click update on the prompt that opens up.
- On the server side of WinSCP, right click, click new, and make a new folder labeled "minecraft".
- Drag the server.jar file into the minecraft folder.
- Return to WinSCP and enter the command:
 - `cd minecraft`
- Return back to the [link][MCServer] and copy the command that is shown.
- Open up PuTTY again, and enter the following, but switch part of the text to server.jar, as that is what we labeled the jar file and execute:
 - `sudo java -Xmx1024M -Xms1024M -jar sever.jar nogui` 

## Updating EULA
- Open up WinSCP and go into the minecraft folder.
- Double click to open the eula.txt document, and edit the eula=false > eula=true and save it.
  
## Install and Run Screen
- Return to PuTTY and exit the back to the main directory by running:
 - `cd`
- Run the following command into the line:
 - `sudo apt-get install screen
- Run the command:
 - `screen`
- Press Enter to exit back into the screened command line.

## Running Server
- Change back to the minecraft directory:
 - `cd minecraft`
- Run the command from before:
 - `sudo java -Xmx1024M -Xms1024M -jar sever.jar nogui`
- Let it run and generate the world.

## Joining Server
- Open up Minecraft and enter multiplayer.
- Click on add server, and in the IP bar, enter the IP of your VPS.
- Click join, and you are finally in the server.

## Using Bash Script 
- To simplify things, there is [this][#minecraft.sh] bash script that can be run from PuTTY.
- Open WinSCH, and drop that file into the /home/debian/ directory to save it.
- To run the command, go to the main PuTTY command line and enter:
 - `sh minecraft.sh`
- When the server is closed, this command automatically starts it up by executing the changing of directories and running the java command to bootup the server instead of doing it automatically.
- If you want to add a SCREEN to that Bash script, you would have to setup the screen function before hand, by simply adding the word "screen" before changing directory.

## More Info
- If any help is needed contact me via email, peterisaacfishman@gmail.com

### Credits
- You can find a tutorial to a perfect step by step explanation here:
 - [![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/LLS4xgwMTQQ&t.jpg)](https://www.youtube.com/watch?v=LLS4xgwMTQQ&t)

[PuTTY]:https://docs.oracle.com/en/cloud/paas/event-hub-cloud/admin-guide/generate-ssh-key-pair-using-puttygen.html
[WinSCP]:https://winscp.net/eng/download.php
[OVHCloud]:https://www.ovhcloud.com/en-ca/?xtor=SEC-13-GOO-[ca_lab_2020_ovh_brand_undefinite_sale_acquisition_srch_defensive_brand_canada(CA-Trademark)]-[581164829161]-S-[ovh%20cloud]&xts=563736&gclid=Cj0KCQjwg_iTBhDrARIsAD3Ib5hk9g28VIM5ZIvkaPGwFCbEPpKl1vKsf4xlpbp1ZvuqXZS611cHYvsaAk53EALw_wcB
[MCServer]:https://www.minecraft.net/en-us/download/server
