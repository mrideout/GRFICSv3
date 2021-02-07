### Installation
For installation, first keep the VM on a single NAT adapter in VirtualBox to make it easier to download everything. Note that you will change this later.

#### Simulation
1. Install jsoncpp, lapacke, pymodbus: `sudo apt-get install libjsoncpp-dev liblapacke-dev python-pymodbus`
2. Install gcc and make: `sudo apt-get install build-essential`
3. Clone the repo into the home directroy `git clone https://github.com/Fortiphyd/GRFICSv2`
4. Go to the simulation folder: `cd ~/GRFICSv2/simulation_vm/simulation`
5. Compile: `sudo make`

#### Web Visualization
1. Install php and apache2: `sudo apt install apache2 php libapache2-mod-php`
2. Remove existing index.html: `sudo rm /var/www/html/index.html`
3. Create a symlink to the apache folder `sudo ln -s ~/GRFICSv2/simulation_vm/web_visualization/* /var/www/html`

#### Networking

1. If you have not already, add host-only adapter in VirtualBox: with a 192.168.95.111 IP address and 255.255.255.0 netmask.

2. Power the VM down, and change the network adapter to the host-only adapter for 192.168.95.111.

3. Edit the interface file: `sudo nano /etc/network/interfaces` to this, where [NIC] is the name of your network, most likely enp0s3:

        auto lo
        iface lo inet loopback

        auto [NIC]:0
        iface [NIC]:0 inet static
        address 192.168.95.10
        netmask 255.255.255.0

        auto [NIC]:1
        iface [NIC]:1 inet static
        address 192.168.95.11
        netmask 255.255.255.0

        auto [NIC]:2
        iface [NIC]:2 inet static
        address 192.168.95.12
        netmask 255.255.255.0

        auto [NIC]:3
        iface [NIC]:3 inet static
        address 192.168.95.13
        netmask 255.255.255.0

        auto [NIC]:4
        iface [NIC]:4 inet static
        address 192.168.95.14
        netmask 255.255.255.0

        auto [NIC]:5
        iface [NIC]:5 inet static
        address 192.168.95.15
        netmask 255.255.255.0

4. Restart networking: `sudo systemctl restart networking`
