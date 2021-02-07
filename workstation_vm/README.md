# Workstation VM

The Workstation is an Ubuntu 20.04 VM with software useful for launching an attack against the PLC pre-installed.

1. Create a 64-bit Linux VM with 2 CPU cores, 2GB RAM, and a 12GB hard drive. Put it on a network that has Internet access for now to ease the rest of the setup process.

2. Install Ubuntu 20.04 64-bit workstation on the VM.

3. When prompted for the installation type, select "Minimal installation."

4. When prompted to set a hostname, username, and password enter, "workstation" into all fields.

5. Install tools for attacking the PLC:

        sudo apt-get install netcat tcpdump wireshark vim telnet nmap ssh git

6. Install the [OpenPLC Editor](https://www.openplcproject.com/plcopen-editor):

        git clone https://github.com/thiagoralves/OpenPLC_Editor
        cd OpenPLC_Editor
        ./install.sh

7. Power off the VM.

8. Change the network adapter to the host-only adapter for 192.168.95.111, then power the VM back on.

9. Power the VM back on, then configure its network card to use a static IP of 192.168.95.6, a subnet mask of 255.255.255.0, and no default gateway.

10. Verify that you can ping the PLC from the new workstation VM:

        ping 192.168.95.2
