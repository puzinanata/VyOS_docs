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
7. Delete item "Display spice" in the left menu
8. Push button (the first left button in the top) "Begin installation"
9. After running Virtual machine put 
    login: vyos 
    password: vyos
Expected output after login:
```
Welcome to VyOS!

Check out project news at https://blog.vyos.io
and feel free to report bugs at https://vyos.dev

You can change this banner using "set system login banner post-login" command.

VyOS is a free software distribution that includes multiple components,
you can check individual component licenses under /usr/share/doc/*/copyright
```

### Step 4. Installation VyOS to VM

In opened Linux terminal you should do following steps for installation VyOS to virtual machine as image:

run code 
```
install image
```
push "enter"

Expected output:
```
Welcome to VyOS installation!
This command will install VyOS to your permanent storage.
Would you like to continue? [y/N] 
```
type
```
y
```
push "enter"

Expected output:
```
What would you like to name this image? (Default: 1.5-rolling-202402251233)
```
push "enter"

Expected output:
```
Please enter a password for the "vyos" user (Default: vyos)
```
push "enter"

Expected output:
```
What console should be used by default? (K: KVM, S: Serial, U: USB-Serial)? (Default: K)
```
type
```
S
```
push "enter"

Expected output:
```
Probing disks
1 disk(s) found
The following disks were found:
Drive: /dev/vda (4.0 GB)
Which one should be used for installation? (Default: /dev/vda) 
```
push "enter"

Expected output:
```
Installation will delete all data on the drive. Continue? [y/N]
 ```
type
```
y
```
push "enter"

Expected output:
```
Searching for data from previous installations
No previous installation found
Would you like to use all the free space on the drive? [Y/n]
 ```
type
```
y
```
push "enter"

Expected output:
```
Creating partition table...
Creating temporary directories
Mounting new partitions
Creating a configuration file
Copying system image files
Installing GRUB configuration files
Installing GRUB to the drive
Cleaning up
Unmounting target filesystems
Removing temporary files
The image installed successfully; please reboot now.
```
run code
```
reboot
```
After reboot put 
```
 login: vyos 
 password: vyos
```
Expected output after login:
```
Welcome to VyOS!

Check out project news at https://blog.vyos.io
and feel free to report bugs at https://vyos.dev

You can change this banner using "set system login banner post-login" command.

VyOS is a free software distribution that includes multiple components,
you can check individual component licenses under /usr/share/doc/*/copyright
```
Congratulations! You installed VyOS to VM.
