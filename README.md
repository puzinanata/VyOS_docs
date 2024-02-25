## Installation latest available build Vyos to VM
### Step 1. Connect to test environment.

 1. IP address of test environment: `192.168.1.78`
 2. Login: `infra`
 3. Password: `infra`

```bash
ssh infra@192.168.1.78
```

Expected output after login:
```
ssh infra@192.168.1.78
infra@192.168.1.78's password: 
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 6.5.0-21-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

8 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Sat Feb 24 18:50:20 2024 from 192.168.1.71
infra@infra:~$ 

```
### Step 2. Download the latest build 
Install virt-manager according to instruction by link:
https://gist.github.com/davesilva/da709c6f6862d5e43ae9a86278f79188

Go to link https://vyos.net/get/nightly-builds/ and in topic "Available builds" you should choose the latest build, Copy Link Address ( in menu by right click of mouse) and insert link to terminal bash with code below:

```bash
# change directory 
cd /home/infra/Downloads
# to download file (the latest build) to current directory
wget https://github.com/vyos/vyos-rolling-nightly-builds/releases/download/1.5-rolling-202402251233/vyos-1.5-rolling-202402251233-amd64.iso
```
### Step 3. Installation virtual machine.
In local station you should run in terminal bash code below:
```
virt-manager --connect="qemu+ssh://infra@192.168.1.78/system?socket=/var/run/libvirt/libvirt-sock"
```
After running this code application Virtual Machine Manager will open.
In Virtual Machine Manager to do:
1. Push button (the first left button in the top) "Create a new virtual machine"
2. Choose "Local install media (ISO image or CDROM)" then "Forward"
3. Push button "Browse" and choose the latest downloaded build from Step 2 then "Choose volume" then "Forward"
4. Choose Memory=2048 and CPUs=1 then "Forward"
5. Put 4 GB to field "Create a disk image for virtual machine"then "Forward"
6. Put name "VyOS-NP" and mark "Customize configuration before install" then "Finish"
7. In opened menu choose item "Display spice" and choose Type - "VNC server", Listen type -"Address", Address - "All interfaces" then "Apply"
8. Push button (the first left button in the top) "Begin installation"
9. After running Virtual machine put 
    login: vyos 
    password: vyos
Expected output: Welcome to VyOS!

### Step 4. Installation VyOS to VM



