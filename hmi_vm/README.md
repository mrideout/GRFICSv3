# ScadaBR

The ScadaBR VM is both an HMI and historian.

#### HMI
![hmi](figures/scadaHMIScaled.PNG)

#### Historian
![historian](figures/scadaHistorianScaled.PNG)

### Installation
1. [Install ScadaBR on a Debian server virtual machine](https://www.openplcproject.com/reference-installing-scadabr), first using a NAT adapter to make installation easier.

2. Install package updates and extra packages to ease debugging:

        apt-get update
        apt-get dist-upgrade
        apt-get install telnet nmap ssh

3. Power the VM off and change the network adapter to the host-only 192.168.95.0/24 network. Set the static IP address to 192.168.95.5 by using `sudo nano /etc/network/interfaces` and making the file look like:

        auto lo
        iface lo inet loopback

        allow-hotplug enp0s3
        iface enp0s3 inet static
        address 192.168.95.5
        netmask 255.255.255.0

4. Restart networking: `sudo systemctl restart networking`

5. On your host machine, point your browser to http://192.168.95.5:8080/ScadaBR/ and login. The default username and password are both "admin".

6. Click the "Import/Export" icon:

![importIcon](figures/scadaImport.PNG)

7. In the "Import Project (Upload)" field, click "Choose File", then select the `ChemicalPlantScadaBR.zip` file:

![chooseFile](figures/scadaChooseFileHighlighted.PNG)

8. Click "Send."

9. Click "Import."

10. To point ScadaBR to the IP address of the PLC, click on the "Data Source" icon, the "Edit Source" icon, and then edit the IP, as shown in the below screenshots:

![dataSource](figures/dataSourcesHighlighted.PNG)

![IP](figures/scadaIPHighlighted.PNG)

### Usage

The default web interface username and password are "admin".

Click the "Watchlist" button to view historian data.  Click the "Graphical Views" button to view the HMI.

![historianHMIIcons](figures/scadaHistAndHMI.PNG)
