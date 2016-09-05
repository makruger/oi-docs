<!--

The contents of this Documentation are subject to the Public Documentation License Version 1.01
 (the "License"); you may only use this Documentation if you comply with the terms of this License.
A copy of the License is available at http://illumos.org/license/PDL.


The Original Documentation is _________________.

The Initial Writer of the Original Documentation is ___________ Copyright (C)_________[Insert year(s)].
All Rights Reserved. (Initial Writer contact(s):________________[Insert hyperlink/alias]).

Contributor(s): ______________________________________.

Portions created by ______ are Copyright (C)_________[Insert year(s)].
All Rights Reserved. (Contributor contact(s):________________[Insert hyperlink/alias]).

-->

# OpenIndiana Handbook - Getting Started

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

This document is a work in progress (draft).

</div>

Import and validate (compare with FAQ, etc.): [old handbook intro](https://wiki.openindiana.org/oi/1.+Introduction)

## Introduction

The OpenIndiana project is the open source community which develops, maintains, and supports the [OpenIndiana](https://en.wikipedia.org/wiki/OpenIndiana) distribution, an [illumos](https://en.wikipedia.org/wiki/Illumos) based Unix-like operating system derived from OpenSolaris.
The purpose of the OpenIndiana Project is to ensure the continued availability of an openly developed distribution based on OpenSolaris.
The OpenIndiana project is also a continuation of the collaborative effort and community spirit of the [OpenSolaris project](https://en.wikipedia.org/wiki/OpenSolaris).

For a comprehensive history of the OpenSolaris project, see Jim Grisanzio's [OpenSolaris timeline](https://jimgrisanzio.wordpress.com/opensolaris/).

## OpenIndiana software releases

<!--

The content for this section is pulled from the OpenIndiana FAQ (section 'What is the OpenIndiana Release Schedule?').
As the FAQ evolves, try to keep this section in sync.

-->

Approximately every six months, the OpenIndiana project releases a snapshot of the Hipster rolling release branch.
Ideally suited for both workstations and servers, simply choose the installer type which best serves your needs.

| Workstation | Server
| --- | ---
| Live installer (Gnome desktop) | Text installer (command line console)

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

* The legacy oi-dev-151x branch is no longer maintained.
* While upgrades to Hipster are possible, the most trouble free method is to perform a clean install.

</div>

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

Hipster is a rapid development branch where software versions are frequently updated.
While every package is tested to ensure stability, caution is nevertheless warranted when deploying Hipster into mission critical production environments.

</div>


## System requirements

<!--

The content for this section is pulled from the OpenIndiana FAQ (section 'What are the recommended hardware specifications?').
As the FAQ evolves, try to keep this section in sync.

-->

| CPU | Disk Space | Memory (RAM)
| --- | --- | ---
| 64 Bit | 20GB (or more) | 2GB (or more)


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

* For the best performance (and to reduce the possibility of disk swapping), allocate 4GB RAM or more.
* For desktops, ensure total system memory (RAM + swap) are at least 4GB or greater.
* The default size of the OpenIndiana swap file is 50% of installed memory.
    * Minimum and maximum default swap allocations are 512MB and 32GB respectively.

</div>


## Exploring OpenIndiana

There are several ways in which you can explore OpenIndiana without having to perform a bare metal install.

* Live media (USB/DVD)
* Virtual machines (PC emulation via software)
* Vagrant (virtual machine image automation)


### Live Media

Available in both DVD and USB formats, the OpenIndiana GUI installer also functions as live media.
This allows you try OpenIndiana without the need to install it.
Exploring OpenIndiana via the live media is an especially good way to test your hardware compatibility prior to installing the operating system.


### Virtual machines

OpenIndiana is known to work with the following virtualization software:

* [VirtualBox](https://www.virtualbox.org)
* [VMWare Fusion](https://www.vmware.com/products/fusion.html)
* [VMWare Workstation Pro](https://www.vmware.com/products/workstation.html)
* [VMWare Workstation Player](https://www.vmware.com/products/player.html)
* [VMWare VSphere](http://www.vmware.com/products/vsphere.html)
* [Linux KVM](http://www.linux-kvm.org/page/Main_Page)
* illumos KVM - (The illumos port of Linux KVM)

Virtual machines provide a PC emulation layer in which you install OpenIndiana just as you would on physical 'bare metal' hardware.


### Vagrant

Vagrant provides an excellent way to explore OpenIndiana as it fully automates the process of bringing a virtual machine online.
OpenIndiana comes with an official [Vagrant](https://www.vagrantup.com) box, which can be used for exploring OpenIndiana before installing it.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

At this time, the OpenIndiana Vagrant box is only available in the form of a text based console.
Additionally, Virtualbox is the only currently supported Vagrant provider.
In the future the OpenIndiana project hopes to provide additional Vagrant box options.

</div>

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

Vagrant is officially available for Mac OS X, Windows and Linux.

</div>

* Download and install the latest version of Vagrant for your platform from the [official download page](https://www.vagrantup.com/downloads.html).
* Download and install the latest version of Virtualbox for your platform from the [official download page](https://www.virtualbox.org/wiki/Downloads).


<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

Older versions of Vagrant (as packaged by many LTS Linux distributions), may not support downloading the Vagrant box instance.
To work around this limitation, be sure to remove any previously installed instances of Vagrant and obtain the latest Vagrant software directly from the Vagrant website.

</div>


* Run the following command to download and boot the OpenIndiana vagrant box:

```
mkdir ~/openindiana_test
cd ~/openindiana_test
vagrant init openindiana/hipster
vagrant up --provider virtualbox
```

This will create a file titled _Vagrantfile_ under the ~/openindiana_test directory.
The Vagrant box will also be booted.

* Once, the Vagrant box virtual machine is online, connect to it using the following command:

```
vagrant ssh
```

* To destroy the OpenIndiana Vagrant instance, issue the following command:

```
vagrant destroy
```


## Preparation for installing OpenIndiana

Prior to installing OpenIndiana:

* Ensure your system meets the recommended hardware requirements.
* Ensure to consult the HCL.


<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

Installing OpenIndiana on unsupported hardware may cause excessive CPU usage, instability, or other problems.

Please be sure to consult the hardware compatibility list (HCL):

* [Illumos HLC](https://www.illumos.org/hcl/)
* [OpenIndiana HCL - components](https://wiki.openindiana.org/oi/Components)
* [OpenIndiana HCL - systems](https://wiki.openindiana.org/oi/Systems)

</div>


### Backing up data

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

Before attempting to install OpenIndiana, first ensure you backup any important data.
Do not save the data on another partition or on another disk within the same system.
Instead save the data to an external device such as a USB hard drive, or external system (network backup service, or a networked system).
Always verify your backed up data.

</div>


### Deciding where to install OpenIndiana

By default the OpenIndiana installer creates an EFI partition using a GPT partition table.
Using this option, OpenIndiana will use the entire disk.
No other operating system can share the same disk.

Optionally you may use a legacy MBR partition.
MBR partitions will allow you to create multiple partitions.
MBR will also support dual booting another operating system.

Another option is to install to a virtual machine.


### Gathering network information

If your network uses a DHCP server, OpenIndiana can be configured to automatically obtain it's network information.
If a DHCP server is not available, then you will need to manually configure your network settings.

Obtain the following information:

1. IP address
2. Subnet mask
3. Gateway
4. Network domain name
5. Network DNS servers


### Downloading the software

<!--

The content for this section is pulled from the OpenIndiana FAQ (section 'Where can I download OpenIndiana Hipster?').
As the FAQ evolves, try to keep this section in sync.

-->
Primary download mirror (London, England):

* [ISO's and USB Images](http://dlc.openindiana.org/isos/hipster)
* [Torrents](http://dlc.openindiana.org/torrents)

Alternate mirrors (Asia, Europe, and North America)

* <https://wiki.openindiana.org/oi/Mirrors>


If you wish to purchase a ready made DVD or USB drive there is also [OSDISC.COM](https://www.osdisc.com/products/solaris/openindiana).

Download Example:

```
wget "http://dlc.openindiana.org/isos/hipster/OI-hipster-gui-20160421.iso"
wget "http://dlc.openindiana.org/isos/hipster/OI-hipster-gui-20160421.iso.sha256sum"
```

### Checking the MD5/SHA

Checksum verification example:

```
sha256sum --check OI-hipster-gui-20160421.iso.sha256sum
OI-hipster-gui-20160421.iso: OK
```


## Creating a bootable OpenIndiana DVD


### BSD/illumos/Solaris

**UNIX Console** <i class="fa fa-sun-o" aria-hidden="true"></i>

The command to use for writing a CD or DVD is `cdrecord`.
The syntax of the command is: `cdrecord dev=device imagefile.iso`

Examples:

* `cdrecord dev=/dev/rdsk/c4t1d0p0 imagefile.iso`
* `cdrecord dev=4,1,0 imagefile.iso`


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

If you are re-using a DVD-RW, be sure to blank it first.

For example: `cdrecord dev=/dev/rdsk/c4t1d0p0 blank=fast`

Warning: Blanking the disk will destroy all data on the disk.

</div>


Locating your DVD or CD writing device:

* For BSD, use `cdrecord -scanbus` to locate your device.

For example:

`cdrecord -scanbus`

```
Cdrecord-ProDVD-ProBD-Clone 3.00 (i386-pc-solaris2.11) Copyright (C) 1995-2010 J�rg Schilling
Warning: Using USCSI interface.
Using libscg version 'schily-0.9'.
scsibus4:
        4,0,0   400) 'ATA     ' 'HITACHI HTS72321' 'C50B' Disk
        4,1,0   401) 'HL-DT-ST' 'DVDRAM GSA-U20N ' 'HX12' Removable CD-ROM
        4,2,0   402) *
        4,3,0   403) *
        4,4,0   404) *
        4,5,0   405) *
        4,6,0   406) *
        4,7,0   407) *
```

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

When using `cdrecord -scanbus` to determine the device name, specify the device using the SCSI bus ID.

For example: `cdrecord dev=4,1,0 imagefile.iso`

</div>

* For illumos/Solaris, you may use either `rmformat -l` or `cdrecord -scanbus` to locate your device.

For example:

`rmformat -l`

```
Looking for devices...
     1. Logical Node: /dev/rdsk/c4t1d0p0
        Physical Node: /pci@0,0/pci17aa,20f8@1f,2/cdrom@1,0
        Connected Device: HL-DT-ST DVDRAM GSA-U20N  HX12
        Device Type: CD Reader
        Bus: <Unknown>
        Size: 810.2 MB
        Label: <None>
        Access permissions: Medium is not write protected.
```

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

When using `rmformat -l` to determine the device name, specify the device using the _Logical Node_.

For example: `cdrecord dev=/dev/rdsk/c4t1d0p0 imagefile.iso`

</div>

**UNIX GUI** <i class="fa fa-sun-o" aria-hidden="true"></i>
<div class="well">

Use the application specific to your desktop (Brasero, K3B, etc.)

</div>

### Linux

**Linux Console** <i class="fa fa-linux fa-lg" aria-hidden="true"></i>

The command to use to write a CD or DVD on Linux is `wodim`.
The syntax of the command is: `wodim -v dev=device -dao imagefile.iso`

For example:

`wodim -v dev=/dev/sr0 -dao imagefile.iso`


Locating your DVD or CD writing device:

* On Linux use the `lsblk` command to locate your device.

For example:

`lsblk`

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk
├─sda1   8:1    0 227.8G  0 part /
├─sda2   8:2    0     1K  0 part
└─sda5   8:5    0     4G  0 part
sr0     11:0    1  1024M  0 rom
```

**Linux GUI** <i class="fa fa-linux fa-lg" aria-hidden="true"></i>
<div class="well">

There are several different CD/DVD writer applications available for Linux.

| Desktop | Application
| --- | ---
| GNOME | Brasero
| KDE | K3B

Other desktops may offer additional choices.
For further information, please consult the help documentation for your Linux distribution.

</div>


### Mac OS X

**MAC Console** <i class="fa fa-apple fa-lg" aria-hidden="true"></i>

```
growisofs -Z /dev/dvdrw=image.iso
```


**MAC GUI** <i class="fa fa-apple fa-lg" aria-hidden="true"></i>
<div class="well">

Applications > Utilities > Disk Utility

</div>


### Windows

**Windows Console** <i class="fa fa-windows fa-lg" aria-hidden="true"></i>

Isoburn is a Windows GUI utility which can be launched via the command prompt as follows:

```cmd
ISOBURN.EXE [/Q] [<drive letter>:] <disk image file name>
```

**Windows GUI** <i class="fa fa-windows fa-lg" aria-hidden="true"></i>
<div class="well">

From within Windows Explorer:

* Browse to and select the ISO image file
* Right click the ISO image file
* From the right click menu, select "Burn Disk Image"

</div>


## Creating a bootable OpenIndiana USB flash drive

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
There are two unique methods for creating bootable USB flash drives.
The method to use depends on the release date of the USB image you intend to write.

#### Method 1

* Applies to the experimental releases of July 2016 and all subsequent (newer) releases.

#### Method 2

* Applies to all OpenIndiana releases up to and including the OpenIndiana Hipster 2016.04 release.
* This includes the legacy oi-dev-151a series of OpenIndiana releases.
</div>


<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
OpenIndiana Hipster does not yet support USB 3.0 or UEFI.

* If you intend to install OpenIndiana Hipster on a system with USB 3.0 and or UEFI capabilities, please be sure to disable these features.
* When attaching backward compatible USB 3.0 flash devices to your system, please ensure they are *NOT* attached to a USB 3.0 port.
</div>


### Prerequisites

#### Methods 1 & 2

* USB flash drive - (2GB or larger).
* Download the OpenIndiana USB installer image.

#### Method 2

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
Header files are only required when writing a legacy image **AND** using the dd utility.
</div>

* Download the appropriate OpenIndiana 1G or 2G header file
    * There are 2 unique USB header files (1G and 2G).
    * Please ensure you have selected the correct file as the files are **NOT** interchangeable.
        * The 1G.header is only suitable for use with the text installer (Command line console).
        * The 2G.header is only suitable for use with the live installer (Gnome desktop).

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
Failure to use the correct USB header file can result in the USB drive either failing to boot, or only partially booting.
</div>


### Identifying the path to your USB device

| Operating system | Command | Device
| --- | --- | ---
| BSD | `camcontrol devlist` | `/dev/da*`
| illumos/Solaris | `rmformat -l` | `/dev/rdsk/c*t*d*`
| Linux | `lsblk` | `/dev/sd*`
| MAC OS X | `diskutil list` | `/dev/disk*`


<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
When issuing the USB copy command:

* Make sure you identify the correct storage device as all data on the device will be erased.
* Be sure to specify the entire USB device without appending any partition or slice number.

For example:

| Example | Device
| --- |---
| Correct | `/dev/sda`
| Incorrect | `/dev/sda1`
| Correct | `/dev/rdsk/c0t0d0`
| Incorrect | `/dev/rdsk/c0t0d0p1`

* If any file systems are located on the USB storage device, they must first be unmounted.
    * Desktops may automatically mount removable devices.
    * As necessary, select any desktop icons for the USB device and issue an 'Eject' or 'Unmount' command.
    * For Linux, use `umount <path>`.
    * For illumos/Solaris use `rmumount <path>`.
    * for MAC OS X use `diskutil unmountDisk <path>`.
    * Verify using the `mount` command.
</div>


### BSD/Linux/OS X

Replace `X` with the appropriate letter for your USB device.


#### Method 1 (New releases)

```
sudo dd bs=4M if=./image.usb of=/dev/sdX status=progress && sync
```

#### Method 2 (Legacy releases)

```
cat 1G.header image.usb | sudo dd bs=1024k of=/dev/sdX
```

For live images larger than 1GB, use the following command instead.

```
cat 2G.header image.usb | sudo dd bs=1024k of=/dev/sdX
```


### illumos/Solaris

Replace `X` with the appropriate letter for your USB device.


#### Method 1 (New releases)

```
sudo /usr/gnu/bin/dd bs=4M if=./image.usb of=/dev/sdb status=progress && sync
```

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
The command above uses the GNU version of dd `/usr/gnu/bin/dd`, which should support the `status=progress` option.
If however you are using illumos dd `/usr/bin/dd`, bear in mind it may not support this option.
</div>

#### Method 2 (Legacy releases)

For illumos based distributions including OpenIndiana, a script [(USBCOPY)](https://raw.githubusercontent.com/OpenIndiana/slim_source/oi/hipster/usr/src/cmd/install-tools/usbcopy) is available to copy the USB image onto a USB device.

Be sure to run as root or with SUDO as the script exits if not run with elevated permissions.

`sudo ./usbcopy image.usb`

```
Found the following USB devices:
0:    devices/dev/rdsk/c4t0d0p0    3.9 GB    USB    DISK 2.0       1.00
Enter the number of your choice: 0

WARNING: All data on your USB storage will be lost.
Are you sure you want to install to
USB DISK 2.0 1.00, 3900 MB at /dev/rdsk/c4t0d0p0 ?  (y/n) y
Copying and verifying image to USB device
Finished 1643 MB in 685 seconds (2.3MB/s)
0 block(s) re-written due to verification failure
Installing grub to USB device /dev/rdsk/c4t0d0s0
Completed copy to USB
```

### Windows

#### Method 1 (New releases)

Newer releases can be written using [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
By default the Win32 Disk Imager utility is looking for `.img` files and won't see files with a `.usb` extension.
To resolve this issue, be sure to select the `*.*` (all files) option from the file extension drop down menu.
</div>

#### Method 2 (Legacy releases)

The OpenSolaris Live USB Creator is a small stand alone GUI utility suitable for creating an OpenIndiana live USB stick.

[OpenSolaris USB Creator](http://devzone.sites.pid0.org/OpenSolaris/opensolaris-liveusb-creator)


## Booting OpenIndiana installer media

Insert the bootable media (DVD or USB flash drive) and boot (start/restart) your computer.
When you see the boot menu, press the enter key to start OpenIndiana on your computer.
As it runs, you will be prompted with a few questions.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

For the computer to boot from the media, you may need to either:

* Specify the appropriate boot device by pressing the boot order hotkey.
* Change the boot device order found in your computer's system BIOS configuration.

</div>

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

OpenIndiana does not yet support the following technologies:

* Secure boot (UEFI boot path validation)
* UEFI (Unified Extensible Firmware Interface)
* USB 3.0 (eXtensible Host Controller Interface)

To successfully boot the OpenIndiana installer, these technologies must first be disabled.
For further information, consult the manufacturers documentation for your computer hardware.

</div>


### Booting the OpenIndiana installer on virtual hardware

The most efficient way to boot a virtual machine is to boot directly from the DVD ISO file.
Alternately, you may use host to guest DVD/USB passthrough to boot from physical media.
See the notes below for optimizing OpenIndiana for several popular hypervisors.

| Hypervisor | Configuration Notes
| --- | ---
| Virtualbox | OS type = Solaris 11 64-bit
| Vmware player | OS type = Solaris 11 64-bit
| KVM | <ul><li>OS type = Sun OpenSolaris</li><li>Remove USB Tablet</li><li>NIC = e1000</li><li>sound = AC97</li><li>Processor = Copy host CPU configuration</li><li>Disable CPU feature _'xsave'_</li><li>Video = QXL</li></ul>

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

The OpenIndiana Project recommends the Oracle Virtualbox hypervisor as it provides the best support for illumos based distributions such as OpenIndiana.

If you experience difficulties booting OpenIndiana on virtual hardware, or find virtual hardware devices which are either not properly recognized, or fail to function as expected, please report the problem to the upstream illumos Project. You may do so by submitting an issue using the [illumos project bug tracker](https://www.illumos.org/issues).

</div>


### The OpenIndiana installer boot menu

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

The OpenIndiana installer will automatically boot the selected (highlighted) entry within 30 seconds.

* To stop the boot timer, press the `Esc` (escape) key.
* To edit a boot entry, press the `e` (edit) key.
* For a command line press the `c` (command) key.

</div>

![grub menu](./images/boot/grub_menu.png)

The OpenIndiana installer boot menu offers multiple choices:

* OI Hipster (normal boot)
* OI Hipster VESA driver
* OI Hipster text console
* Boot from Hard Disk
* OI Hipster Enable SSH
* OI Hipster with magnifier
* OI Hipster with screen reader

Use the up and down arrow keys to select a boot entry.
Once you have made a boot menu selection, press the `Enter` key to initialize the OpenIndiana installer boot process.


### Selecting keyboard layout and display language

![Select keyboard layout](./images/boot/keyboard.png)

OpenIndiana offers 47 different keyboard layouts.
Select your keyboard layout by entering the number corresponding to your desired keyboard layout.
For example, select `18` for German, or `35` for Russian, etc.
The default keyboard layout is selection `47` US-English.
Once you have selected a keyboard layout, press the `Enter` key to continue.

![Select display language](./images/boot/language.png)

OpenIndiana offers 22 different language options.
Select a language by entering the number corresponding to your desired language.
For example, select `3` for Chinese - Simplified, or `18` for Portuguese - Brazil, etc.
The default language selection is `7` for English.
Once you have selected a language, press the `Enter` key to continue.


### The live media desktop

![live desktop](./images/live_desktop/live_desktop.png)

The Live Media DVD and USB installers provide a graphical live environment where you can explore OpenIndiana and test the compatibility of your hardware.
When using Live Media, no changes are made to your system unless you explicitly choose to install OpenIndiana or alter the configuration of your disk using the Gparted Partition Editor.

The following options are available to you from the Live Media Desktop:

* Install OpenIndiana using the Text Installer
* Install OpenIndiana (graphical installer)
* Device Driver Utility
* Gparted Partition Editor


### Using the device driver utility

Available from the Live Media desktop, the _Device Driver Utility_ may be used to scan your hardware for compatibility.
The utility generates a list of hardware devices along with the corresponding driver in use for each device.
The utility will also show you devices for which there is no driver loaded.
The device driver utility allows you to check whether your hardware requires additional drivers.


### Using the Gparted Partition Editor

The Gparted partition editor allows you to add, remove, or resize partitions in preparation for installing OpenIndiana.

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
Editing partition tables is a potentially destructive process.
While you are unlikely to physically damage the disk, there is a risk of losing data.
Before using the partition editor, please be sure to back up your data to a remote system or device.
</div>


### Live media authentication

The user login for the live media session is `jack` along with the password `jack`.
For administrative or elevated access, prepend your commands with `sudo`.

You may obtain root using the `su` command along with the password `openindiana`.


## Installing OpenIndiana

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **DOC TEAM NOTE:**
<div class="well">
For some guidance writing this section:

* Installation walkthrough: [web link](http://technodrone.blogspot.com/2012/05/openindiana-installation-walkthrough.html)
* Installation videos: [web link](https://www.youtube.com/watch?v#VVWP_5oAy3w)
</div>

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
Before you install OpenIndiana on a system that is running the Linux OS, save a copy of the menu.lst file.
The contents of the GRUB menu.lst file dictate what is displayed in the GRUB menu when you boot the system.
You will need to update the GRUB menu after the installation.
</div>

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
Please be advised of the following important considerations:

* The installation overwrites the whole disk layout if one of the following is true:
    * The disk table cannot be read.
    * The disk was not previously partitioned.
* If an existing Solaris fdisk partition is on a multiboot system, and the user makes no modifications to the existing partitions, the installation overwrites the Solaris fdisk partition only.
Other existing partitions are not changed.
</div>


### Installing OpenIndiana from live media

To install OpenIndiana from Live Media, you have two options.

* Install OpenIndiana using the Text Installer
* Install OpenIndiana (graphical installer)

Each of these options is represented by a desktop icon.
Select the appropriate installer option by clicking the corresponding desktop installer icon.


### Install OpenIndiana (graphical installer)

![Launch the installer](./images/gui_install/install_1.png)

To launch the OpenIndiana graphical installer, locate and double click the desktop icon labeled: _**Install OpenIndiana**_.

As shown below, and in the subsequent screens, the installer starts a new process, running within it's own window.

![First install screen](./images/gui_install/install_2.png)

When the installer starts, the first screen you will see is the welcome page.
Please take some time to read the additional guidance provided below.
When ready to begin, click the _**Next**_ button to continue on with the installation process.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
Please disregard the reference to the getting started guide.
This guide no longer exists on the Live Media installer.

_**A bug has been opened for this issue and a new getting started guide is being created**_.

Also, when clicking the link for the release notes, please click it only once and wait until Firefox finishes loading.
The Firefox web browser will open to the 'OpenIndiana Releases' page of the OpenIndiana Wiki.
This however, is not where you will find the release notes.
_**A bug has been opened to correct this issue**_.

The release notes may be accessed in one of the following ways:

* Perform a search within the Wiki site for the release notes.
* Browse to the following Wiki page: <https://wiki.openindiana.org/oi/Release+Notes>.
</div>


![Disk selection and partitioning menu -1](./images/gui_install/install_3.png)

The top portion of the disk selection and partitioning screen shows all the disks found on the system, including removable disks.
Each disk is represented with a disk icon.
Below each disk icon the installer displays the size of each disk in Gigabytes (GB) and the disk type (IDE, ATA, etc.).
Within this upper panel, select the disk where you wish to install OpenIndiana.
The lower portion of this screen displays partitioning options.

Within the lower panel, select one of the following options:

| Option | Description
| --- | ---
| Use the whole disk | When the _Use the whole disk_ option is selected, the entire disk is used for the installation. For the selected disk, all existing partitions and any data which they may contain, will be overwritten with the OpenIndiana operating system.
| Partition the disk | When _Partition the disk_ option is selected, the bottom portion of this panel displays the disk partitioning layout. Prior to selecting this option, please be sure to review all the informational notes and warnings concerning the use of the partitioning option.

![Disk selection and partitioning menu -2](./images/gui_install/install_4.png)
If you choose to partition the disk, you have additional options as shown above.
Please take some time to read the additional guidance provided below.
When you have revised the partitioning as needed, click the _**Next**_ button to continue.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
Regardless of the partitioning option chosen for the installation, manual control of the OpenSolaris file system layout is not supported.
During the installation, the Solaris fdisk partition is reformatted with a default ZFS file system layout.
All existing file systems on the Solaris partition are destroyed.
The installation uses a Solaris fdisk partition to create a ZFS storage pool.
</div>


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
If you choose to partition the disk, review the following partitioning guidelines, then revise the partitioning panel settings as needed.

* Only one Solaris partition is allowed.
If an existing Solaris partition is available, that Solaris partition will be the target for the installation.
Or, if you do not have an existing Solaris partition, you can change any existing partition to a Solaris partition.
* You can resize existing partitions, delete partitions, and create new partitions in this panel.
For this option, one existing Solaris partition must be available as the target for the installation.
* If you used a third-party partitioning tool such as GParted, then the Disk panel displays a partition named Linux-swap on which you can install OpenIndiana.
    * In this panel, use the drop-down list for the Linux-swap partition name to change the partition name to Solaris.
</div>

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
If the existing partition table cannot be read, a warning is displayed, and the panel displays proposed partitioning.
In this case, all data on the selected disk is destroyed.

If the table can be read, then the following information applies:

* The partitions are displayed in physically sequential order as they are laid out on the disk.
* Resizing a Solaris partition destroys the data on that partition and all physically subsequent partitions.
    * Existing data is not moved to conform to a new partition layout.
    * However, resizing the last partition or appending a new partition does not affect the data that already exists in other partitions.
* Non-Solaris partitions cannot be resized.
* To make additional space available, you can change an existing partition to Unused.
    * However, if you change an existing partition to Unused, all subsequent non-Solaris partitions are also changed to Unused.
* New partitions can only use the available space that follows the last defined partition.
* The installer cannot utilize unallocated chunks of space between existing defined partitions.
* Use the fdisk(1M) command to create new partitions that use the free space between exiting partitions.
</div>


![Time zone, date and time](./images/gui_install/install_5.png)

This screen enables you to type the correct time zone, date, and time for the system to be installed.
The top half of the panel displays a world map with major cities marked.
The bottom half of the panel provides drop-down selections.
You can choose the time zone either from the map or from the drop-down list.

* If you select the time zone from the map, click on a city or click anywhere on the map.

If you click on the map, but not on a city, the map automatically magnifies that area.
You can click on a location within that magnified area.
You can drag the cursor to move the magnified area to a different location on the map.
When you select a site on the map, the drop-down selections automatically populate with the time zone, date, and current time for that map selection.
You can right-click to undo magnification.

* Instead of using the map, you can make your selections in the drop-down fields.

Select your region, then select Location. Finally, select time zone.
The options for each drop-down field are determined by the selection made in the prior drop-down field.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
After making your selections, you may also edit the default date and time that is provided.
</div>

When the settings are correct, click Next to continue.


![Locale](./images/gui_install/install_6.png)

This screen enables you to select a language and locale.
These selections determine the language support, the default date and time, and other data formats for the installed system.

* You can accept the default language selection or change the selection.

* A language selection is required.
You can select “no default language support.”

* The language chosen automatically determines the available locales in the drop-down list.
Only one locale can be selected.


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
Any time that you log in to the installed system, you can change either the locale for that particular session or the default locale by using the Options button in the Login dialog box.
</div>

![Users](./images/gui_install/install_7.png)

Review the following guidelines:


* Root login is not enabled either on the Live CD or on the installed system.
You must log in as the user that you create in this panel.
After you log in, you can then become root to configure the system.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
If you do not create a user account in this panel, root is set up as a normal account on the installed system, instead of as a role.
This is the only situation where you can log in to the installed system as root.
</div>


* Both the root password and user account are optional.
However, for better security, do complete these fields.
If the root password is not defined, a reminder is displayed when you click Next.
If you do not want to define a root password, you can proceed.


* A user account requires only a Login name for the account to be valid.
For better security, however, do complete all fields.
If the user account information is not valid, a reminder is displayed when you click Next.
If you do not want to define a user account, you can proceed.


* Type a computer name or accept the default.
The computer name field cannot be blank.

![Installation summary](./images/gui_install/install_8.png)

This screen summarizes the configuration options which will be used to perform the installation.
Be sure to take the time to review this summary.
If a configuration option needs to be changed, you may do so by clicking the _**Back**_ button.
If the installation options are acceptable, click the _**Install**_ button to begin the installation.

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">
Once you have clicked the _**Install**_ button, the option to _**Quit**_ the installation is no longer available.
Do not attempt to interrupt an installation already in progress or the system will be left in an inconsistent state.
</div>


![Installation in progress](./images/gui_install/install_9.png)

During the installation, a progress bar is displayed.
The time required to complete the installation is dependent on your hardware.

![Completion summary](./images/gui_install/install_10.png)

The final screen displays completion messages.
From within this panel you may review the installation log.
To view the installation log, click the link titled _**OpenIndiana Installation Log**_.
The installation log will open in a new window.

![Installation log](./images/gui_install/install_11.png)

Using the slider located on the right side of the log viewer window, you may scroll up and down to view the entire log file.
After reviewing the log, you may exit the log viewer by clicking the _**Close**_ button.

**Congratulations!**
You have completed the installation of the OpenIndiana Hipster operating system.

From here you now have several options:

* Quit the installer by clicking the _**Quit**_ button and continue to explore the Live Media.
* Quit the installer by clicking the _**Quit**_ button and then manually shut down or restart your system.
* Reboot the computer by clicking the _**Reboot**_ button.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
To prevent the Live Media from starting again after the reboot, eject the Live Media as the next boot begins.
Or alternately, when presented with the Live Media installer options menu, select the _**Boot from Hard Disk**_ option.
</div>


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
After you have installed OpenIndiana, if you have another operating system on your system, you might need to update the GRUB menu.
The GRUB menu displays a list of operating systems that can be booted.
Solaris and Windows operating systems are displayed automatically on the GRUB menu.
The contents of the GRUB `menu.lst` file define what is displayed in the GRUB menu when you boot the system.
If you have an additional OpenIndiana or a Linux OS that is not displayed on the menu, you may need to edit the GRUB `menu.lst` file.
</div>


### Install OpenIndiana using the Text Installer

The text based guided install starts and runs within a command line console.
Navigation within the installer is performed by pressing specifically designated navigation keys (F2, Tab, etc.).

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

The non-graphical text based bootable media installer also uses this very same _Text based Guided Install_.

</div>

Begin installing OpenIndiana using the text based installer by double clicking the desktop icon labeled:

_Install OpenIndiana using the Text Installer_.


![Welcome Screen](images/text_install/text_install1.png)

The _Install OpenIndiana using the Text Installer_ process begins with a welcome screen.

The welcome screen also provides:

* Location of the installation log file
* Navigational guidance

When ready to begin, press the F2 key to continue.

![Disks](images/text_install/text_install2.png)

The installer identifies the disks which are available for installation.

* If you have only a single disk, it is already selected.
* If you have multiple disks, use the arrow keys to select the appropriate disk.

When ready, press the F2 key to continue.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

While the minimum and recommended disk sizes are technically accurate, they do not take into account periodic disk usage growth resulting from:

* ZFS snapshots
* Backup boot environments created by `pkg install`
* Boot environments created by `pkg update`

To account for this, your disk should be at least 20GB or more.

</div>

![GPT Warning](images/text_install/text_install3.png)

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

If your disk contains a GPT disk label, the entire disk will be used.

* Any existing GPT partitions will be destroyed
* A new single GPT partition will be created.

This warning serves as your advisory.

</div>

If reformatting the entire disk is acceptable with you, press the enter key to continue.
Otherwise use the arrow keys to select cancel and press the enter key..

If you select cancel, you will have the following options:

* Select another disk
* Abort the installation so you may provide remedial action such as:
    * Modifying the partition table using Gparted
    * Adding another disk to the system


![Fdisk Partitions](images/text_install/text_install4.png)

In this screen you are presented with the following choices for how to partition the disk:

* Use the whole disk (EFI)
* Use a partition of the disk (MBR)

Using the arrow keys, select the appropriate choice.
When ready, press the F2 key to continue.

![Network 1](images/text_install/text_install5.png)

Specify the computer name (system hostname) you wish to use.
By default the computer name is _openindiana_.
Using the backspace key, you may remove the default choice and provide another hostname.
When ready, proceed to the next screen shot where you will be provided additional guidance for completing this screen.

![Network 2](images/text_install/text_install6.png)

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">
This screen is identical to the previous screen.
We have illustrated it twice to help clarify the 2 distinct configuration tasks which need to be completed:

* Setting the system hostname
* Selecting your network configuration

</div>

After configuring the system hostname, navigate to the lower portion of the screen to select your networking configuration.

You have the following choices:

* Automatically configure the (networking) connection (using DHCP)
* Do not configure the network at this time.

Use the arrow keys to select your choice.
When ready, press the F2 key to continue.

![Time Zone - Region](images/text_install/text_install7.png)

In this screen (and the following 2 screens) you will configure your time zone.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

If you select UTC/GMT, you will only be presented with this single screen.

</div>

Using the arrow keys, select your time zone _region_.
When ready, press the F2 key to continue.

![Time Zone - Location](images/text_install/text_install8.png)

Using the arrow keys, select your time zone _location_.
When ready, press the F2 key to continue.

![Time Zone](images/text_install/text_install9.png)

Using the arrow keys, select your _time zone_.
When ready, press the F2 key to continue.

![Date and Time](images/text_install/text_install10.png)

In this screen you may reconfigure the date and time as necessary.
Using the arrow keys, navigate between the fields.
When ready, press the F2 key to continue.

![Users](images/text_install/text_install11.png)

In this screen you are presented with several different user name and password fields to configure.
Using the arrow keys, navigate between the fields and enter the required information.
When ready, press the F2 key to continue.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE**
<div class="well">

* The regular user specified on this screen is granted the _root_ role.
* In effect this means the following:
    * Without any further configuration, the user you specify will be granted the authority to perform administrative task by assuming the root role as needed.
    * The first user created on the system is granted the root role via _Role Based Access Control_ (RBAC).

Please take note the following additional information:

* Immediately after installation the root password is automatically expired and needs to be changed prior to being used for any administrative task.

</div>

![Installation Summary](images/text_install/text_install12.png)

Now that you have completed the installation configuration, you are presented with an _Installation Summary_.
If these configuration settings are correct, begin the installation by pressing the F2 key.

![Transferring Contents](images/text_install/text_install13.png)

Depending on the speed of your computer, the installation may take several minutes to complete.
Installation progress is measured by means of a status bar.

![Installation Complete](images/text_install/text_install14.png)

After the installation has completed you are presented with a summary screen.
The installation logs are available by pressing the F4 key.
If you ran the installation from Live Media, you may exit the installation by pressing the F9 key.
Otherwise, you will want to reboot the system by pressing the F8 key.


### Installing OpenIndiana using the text installer (DVD ISO or USB)

The text installer DVD ISO and USB installer options are not graphical nor do they provide a live environment.
When booting from the text based installer, you are presented with the following choices:

* Install OpenIndiana
* Spawn a shell to be used as a rescue disk.

The procedure for installing from the text based installer follows the same process as the previously described [Install OpenIndiana using the Text Installer](./getting-started/#install-openindiana-using-the-text-installer)


## Post installation steps

### Resetting the root password

The root password is immediately expired after installation and you will be required to select a new password.

Use the following steps to change the root password:

* Open a Terminal
* Execute `su -` and provide the password you chose for your account at installation time
* You will be informed that root's password has expired and prompted to change it
* Once changed you can exit the su session
* You should be able to login/authenticate as root now.


## Troubleshooting installations

* If you do not see a menu after booting your computer with the DVD or USB device, and instead see some text and a ``grub>`` prompt, there may be an error in your copy of the installer, or it was created incorrectly.
* If you see a ``login:`` prompt after selecting your keyboard and language and no desktop appears after several seconds, there may be a problem with the drivers for your graphics hardware.
    * Please let us know via IRC or the mailing list if this happens.
    * When you contact us, please include any error messages you see on the console, as well as the output of the `svcs -xv` command.
    * If possible, also include the contents of the file `/var/log/Xorg.0.log`.


### USB 3.0 issues

**DOC TEAM NOTE:**

Bring this guidance in alignment with the USB 3.0 warnings found elsewhere in the handbook, FAQ, etc.

* OpenIndiana Hipster does not currently support USB3.
* You cannot boot a USB thumbdrive installer from a USB3 port.


## The Image Package System (IPS)

The image packaging system is delivered as part of the OpenIndiana userland.
As such, the pkg related man pages are not available on the illumos.org website.
These pages are only available by running the man page viewer locally on your system.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **DOC TEAM NOTE:**
<div class="well">

Have a look at: [pgk cheat sheet](https://wiki.openindiana.org/oi/pkg+Cheat+Sheet) to see whether there is anything there which we might want to import and validate.

</div>

### Introduction

<!--The majority of the text below was taken from the PDL licensed document titled 'Getting Started with OpenSolaris 2008.11' -->

After an initial installation of the OpenIndiana Hipster operating system, you will find many of the software applications you use on a regular basis are not immediately available to you.
These software applications are available as packages in a remote Image Packaging System (IPS) repository for downloading and installing over the Internet.

Written in Python, IPS is a network-centric packaging system which enables users to connect to a remote repository for the purpose of downloading and installing packages.
OpenIndiana Hipster uses IPS for its packaging system.

Besides installing packages from a repository, users can also perform the following tasks:

* Create and publish their own IPS packages
* Set up an OpenIndiana Hipster repository
* Mirror an existing repository
* Publish existing packages to a repository

Once you have installed packages, IPS enables you to search, update, and manage those packages on your system.

With IPS , you can upgrade your system to a newer build of OpenIndiana Hipster, install and update your software to the latest available versions, and retrieve packages from mirror repositories.

If the system on which IPS is installed is located on a network, IPS can automatically access the OpenIndiana Hipster package repository.
For OpenIndiana Hipster, your IPS client can access the packages from <https://pkg.openindiana.org/hipster>.


### IPS packages

An IPS package is defined as a collection of files, directories, links, drivers and dependencies in a defined format.

Note the following points about IPS packages:

* An IPS package consists of a set of actions.
Actions are defined when an IPS package is created.
Actions are used for defining the files and directories of the package, setting package attributes, declaring dependencies on other packages, creating users and groups, and installing device drivers.
Some actions may optionally have tags that provide meta information about the action such as locale information and debug configuration.
* IPS packages can only be installed from an IPS repository.
    * IPS package repositories can be local to the system or on a remote networked system.


### IPS commands

The Image Packaging System software provides the following commands:

| Command | Description
| --- | ---
| `pkg`<sup>1</sup> | Use the `pkg`<sup>1</sup> command to create an image, to install packages to your image, and to manage packages on your image.
| `pkgsend`<sup>1</sup> | Use the `pkgsend`<sup>1</sup> command to publish packages from your image to an existing repository.
| `pkg.depotd`<sup>1M</sup> | Use the `pkg.depotd`<sup>1M</sup> command to create and manage your own network repository or set up a mirror repositories.
| `pkgrecv` | Use the `pkgrecv` command to download the contents of a package from a server. The user can then modify the contents by adding additional package attributes and republish the package with the `pkgsend` command.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

* The `pkg`<sup>5</sup> man page describes the overall Image Packaging System.
* The `pkg`<sup>1</sup> man page describes the image packaging retrieval client.

</div>


### pkg<sup>1</sup> uses FMRIs

Each IPS package is represented by a _Fault Management Resource Identifier_ (FMRI).
The pkg<sup>1</sup> command uses valid FMRI package information to perform its command actions.
The FMRI includes descriptive information about the package, such as the package name, version information, and date.

For example:

```
FMRI: pkg://openindiana.org/image/editor/gimp@2.8.16-2016.0.0.0:20160702T042138Z
```

* Scheme – pkg
* Authority – openindiana.org
* PackageName – gimp
* Version String – Consists of three components :
    * Build Version – 2.8.16
    * Branch Version – 2016.0.0.0
    * Timestamp – 20160702T042138Z


### Searching for packages

The `pkg search` command is used to search locally or remotely for information about packages.
If no search options are specified, the search is restricted to the local system.
Using the `-r` option, the command searches the remote repository (or repositories) associated with the system.

For example:

`pkg search -r xchat`

```
INDEX                ACTION VALUE                                   PACKAGE
pkg.summary          set    HexChat is an IRC client based on XChat pkg:/desktop/irc/hexchat@2.12.1-2016.0.0.1
pkg.summary          set    XChat IRC Client                        pkg:/desktop/irc/xchat@2.8.8-2016.0.0.5
basename             file   usr/bin/xchat                           pkg:/desktop/irc/xchat@2.8.8-2016.0.0.5
com.oracle.info.name set    xchat                                   pkg:/desktop/irc/xchat@2.8.8-2016.0.0.5
pkg.fmri             set    openindiana.org/desktop/irc/xchat       pkg:/desktop/irc/xchat@2.8.8-2016.0.0.5
```


The `pkg search` command may also be used to find the package containing a particular file.

For example:

`pkg search -l /usr/bin/gpg2`

```
INDEX      ACTION VALUE        PACKAGE
path       file   usr/bin/gpg2 pkg:/crypto/gnupg@2.0.28-2016.0.0.0
```

When using the `pkg search` command bear it mind it works much like the Unix `find` command.
If you have troubles finding a package you know should exist, try using wildcards with your commands.


### Listing information about packages

To list information about packages installed on the local system use the command `pkg list <package-name>`.

For example:

`pkg list gimp`

```
NAME (PUBLISHER)                                  VERSION                    IFO
image/editor/gimp                                 2.8.16-2016.0.0.2          i--
```

To list the entire contents of a package, use the command: `pkg contents <package-name>`.
If the package is not installed on the local system, use the `-r` option to search the remote repositories defined on the system.

The `pkg contents` command can also be used to list the dependencies found in a package.

For example:

`pkg contents -H -t depend -o fmri xchat`

```
pkg:/library/desktop/gdk-pixbuf@2.31.6-2016.0.0.0
pkg:/library/desktop/gtk2@2.24.30-2016.0.0.0
pkg:/library/desktop/libsexy@0.1.11-2016.0.0.0
pkg:/library/desktop/pango@1.36.8-2016.0.0.2
pkg:/library/glib2@2.43.4-2016.0.0.3
pkg:/library/security/openssl@1.0.2.8-2016.0.0.3
pkg:/runtime/perl-522@5.22.1-2016.0.0.1
pkg:/runtime/python-27@2.7.12-2016.0.0.0
pkg:/runtime/tcl-8@8.5.19-2016.0.0.1
pkg:/system/library/libdbus-glib@0.100.2-2016.0.0.0
pkg:/system/library@0.5.11-2016.0.0.15685
pkg:/x11/library/libx11@1.6.3-2016.0.0.0
```


### Installing packages

Use the following command to install a package.

`pkg install [options] <package-name>`

Some commonly used options are:

| Option | Description
| --- | ---
| -v | Issue verbose progress messages
| -n | Perform a dry run (no actual changes are made)
| -q | Hides progress messages


For example:

`pkg install xchat`

```
           Packages to install:   1
            Packages to update:   1
            Services to change:   2
       Create boot environment:  No
Create backup boot environment: Yes

DOWNLOAD                                PKGS         FILES    XFER (MB)   SPEED
Completed                                2/2         38/38      2.6/2.6  746k/s

PHASE                                          ITEMS
Removing old actions                             4/4
Installing new actions                         69/69
Updating modified actions                        2/2
Updating package state database                 Done
Updating package cache                           1/1
Updating image state                            Done
Creating fast lookup database                   Done
```


<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **NOTE:**
<div class="well">

* The `pkg install` command is also used to update specific packages on the system.
* The `pkg install` command automatically checks for newer versions of specific packages or package groups and installs them if they are available.
Any dependent packages are also automatically updated.
* To install a specific version of a package you may substitute the common name for the FMRI.

</div>


### Updating packages

The command to use for updating packages on the system is:

`pkg update [options] [package(s)]`

Some commonly used options are:

| Option | Description
| --- | ---
| -v | Issue verbose progress messages
| -n | Perform a dry run (no actual changes are made)
| -q | Hides progress messages

To update all the packages installed on a system to their latest available version, use the `pkg update` command without specifying any package names.

For example:

`pkg update`

```
            Packages to remove:    4
           Packages to install:   11
            Packages to update: 1018
            Packages to change:    2
           Mediators to change:    1
       Create boot environment:  Yes
Create backup boot environment:   No

DOWNLOAD                                PKGS         FILES    XFER (MB)   SPEED
Completed                          1035/1035     7502/7502  303.4/303.4  886k/s

PHASE                                          ITEMS
Removing old actions                       3931/3931
Installing new actions                     6889/6889
Updating modified actions                11999/11999
Updating package state database                 Done
Updating package cache                     1022/1022
Updating image state                            Done
Creating fast lookup database                   Done

A clone of openindiana-1 exists and has been updated and activated.
On the next boot the Boot Environment openindiana-2 will be
mounted on '/'.  Reboot when ready to switch to this updated BE.


---------------------------------------------------------------------------
NOTE: Please review release notes posted at:

http://wiki.openindiana.org/display/oi/oi_hipster
---------------------------------------------------------------------------
```


### Removing packages

To remove a package from the system, use the command: `pkg uninstall <package-name>`


### IPS package repositories

As previously mentioned, the IPS repository is the remote network location where IPS packages reside.
Below is a list of commands for adding, removing, or replacing repositories.

| Task | Command
| --- | ---
| List configured repositories | `pkg publisher`
| Add a repository | `pkg set-publisher \ ` <br> `-g <repository_URL> \ ` <br> `<repository_name>`
| Remove a repository | `pkg set-publisher \ ` <br> `-G <repository_URL> \ ` <br> `<repository_name>`
| Replace a repository | `pkg set-publisher \ ` <br> `-G <old_repository_URL> \ ` <br> `-g <new_repository_URL> \ ` <br> `<repository_name>`

Example (Listing the repositories configured on the system):

`pkg publisher`

```
PUBLISHER                   TYPE     STATUS P LOCATION
openindiana.org             origin   online F https://pkg.openindiana.org/hipster/
hipster-encumbered          origin   online F https://pkg.openindiana.org/hipster-encumbered/
```

Example (Replacing a repository):

```
pkg set-publisher \
-G http://pkg.openindiana.org/hipster-2015 \
-g https://pkg.openindiana.org/hipster openindiana.org
```

### Listing information about repositories

While the `pkgrepo` command is primarily used for creating and working with IPS repositories.
It can also be used for querying the contents of a repository.

For example:

`pkgrepo info -s https://pkg.openindiana.org/hipster/`

```
PUBLISHER       PACKAGES STATUS           UPDATED
openindiana.org 3692     online           2016-08-21T07:03:11.566484Z
```

If you want to directly query the remote repository for a full list of all available packages, you can do so using the `pkgrepo list` command.

* `pkgrepo list -s <repo_URL>`

Do keep in mind you may want to filter the output of the command in some way to keep the list more manageable.
If not, you're likely to see thousands of lines scroll through your console window.


### IPS package repository precedence

When multiple remote IPS repositories are associated with a system and when using the `pkg` command-line interface with only package names, the following rules apply.
These rules can be overridden by using explicit publishers and package version numbers.

| Package Installation Type | Rules When Only Package Names Are Provided
| --- | ---
| New package installations | The latest available version of new packages are always installed from the preferred publisher unless the publisher is provided in the FMRI during installation. Even if later versions of the package are available in other publishers, those later versions are not installed by default.
| Package updates: package originally installed from preferred publisher | If the package was originally installed from the preferred publisher, then the latest available update of the package can be installed from the _current_ preferred publisher. The package can be install from the _current_ preferred even if the preferred publisher designation had been moved to another publisher after the package had been originally installed. Even if later versions of the package are available in other publishers, those later versions are not installed by default.
| Package updates: package originally installed from non-preferred publisher | If the package was originally installed from a non-preferred publisher, then the latest available update of the package is installed from the publisher from which the package was originally installed. Even if later versions of the package are available in other publishers, those later versions are not installed by default.


### Listing package history

To list the IPS transactional history, use the `pkg history` command.

For example:

`pkg history`

```
START                    OPERATION                CLIENT             OUTCOME
2016-04-21T03:30:04      purge-history            pkg                Succeeded
2016-07-02T16:09:56      uninstall                pkg                Succeeded
2016-07-02T16:10:33      uninstall                pkg                Succeeded
2016-07-02T16:11:08      uninstall                pkg                Succeeded
2016-07-02T16:11:42      uninstall                pkg                Succeeded
2016-07-02T16:12:18      set-property             pkg                Succeeded
2016-07-02T16:12:22      set-property             pkg                Succeeded
2016-07-02T16:37:06      refresh-publishers       pkg                Succeeded
2016-07-02T16:37:06      update                   pkg                Succeeded
2016-07-02T16:37:32      rebuild-image-catalogs   pkg                Succeeded
2016-07-02T17:33:44      install                  pkg                Succeeded
2016-07-02T17:35:11      install                  pkg                Succeeded
2016-07-02T18:31:39      install                  pkg                Succeeded
2016-07-04T19:49:19      install                  pkg                Succeeded
2016-07-04T19:49:23      refresh-publishers       pkg                Succeeded
2016-07-04T19:49:56      rebuild-image-catalogs   pkg                Succeeded
2016-07-09T01:16:43      install                  pkg                Succeeded
2016-07-09T01:16:45      refresh-publishers       pkg                Succeeded
2016-07-09T01:17:20      rebuild-image-catalogs   pkg                Succeeded
2016-07-09T11:33:05      install                  pkg                Succeeded
2016-07-09T11:33:07      refresh-publishers       pkg                Succeeded
2016-07-09T11:33:37      rebuild-image-catalogs   pkg                Succeeded
2016-07-09T12:27:23      update                   pkg                Succeeded
```

To view more details of a particular IPS transaction, use the command:

`pkg history -t 2016-07-09T11:33:05 -l`

The `-t` switch allows you to specify a particular transaction and the `-l` switch provides extended details of that transaction.


### IPS package archives (.p5p)

When the IPS system was originally conceived there was no standard on-disk format for an IPS package.
Hence, unlike a .rpm file, an SVR4 package, or a .nbm file, it was not possible to transfer IPS packages from system to system.
The remote IPS repository where the IPS package resided was the only source for the package.
This is because in its native state, the IPS package is not something you can normally download as a single archive file.

Recognizing this limitation of IPS, the `.p5p` IPS archive format was developed.
For IPS archives, files are stored in the pax archive format, along with additional metadata, such as IPS manifest files, and a specific layout of the contents.

IPS p5p archives are not like Linux packages where you can install software directly from the package.
Instead p5p archives are a portable repository format containing a collection of packages.
This allows you to create p5p archives for transfer to non-networked systems.
IPS package archives are also useful for sharing packages for the purpose of testing.

IPS archives allow you to:

* Download one or more packages (along with all necessary dependencies) into a p5p archive file.
* Create a local repository based on the contents of the p5p archive file.
* Install packages from the locally created repository.


#### Creating the p5p package

To create an IPS archive, the `pkgrecv` command is used.

For example, to create a `.p5p` IPS package archive containing the package `userland/web/browser/firefox` and all of its dependencies from the repository located at `http://example.com:10000`, use the following command:

```
pkgrecv -s http://example.com:10000 -d ~/firefox_test.p5p -a -r pkg://userland/web/browser/firefox@45.3.0-2016.0.0.0:20160817T064143Z
```


#### Listing the contents of a p5p package

There are at least two different ways to view the contents of an IPS archive.

`pkgrepo -s ~/firefox_test.p5p list`

```
PUBLISHER NAME                                          O VERSION
userland  library/expat                                   2.1.0-2015.0.1.1:20150901T125810Z
userland  library/glib2                                   2.43.4-2016.0.0.4:20160705T121550Z
userland  library/glib2/charset-alias                     2.43.4-2016.0.0.4:20160705T121609Z
userland  system/library/fontconfig                       2.11.95-2016.0.0.0:20160512T122747Z
userland  web/browser/firefox                             45.3.0-2016.0.0.0:20160817T064143Z
userland  x11/library/toolkit/libxt                       1.1.4-2016.0.0.0:20160706T165209Z
```

This also works:


`pkg list -f -g  ~/firefox_test.p5p`

```
NAME (PUBLISHER)                                  VERSION                    IFO
library/expat (userland)                          2.1.0-2015.0.1.1           ---
library/glib2 (userland)                          2.43.4-2016.0.0.4          ---
library/glib2/charset-alias (userland)            2.43.4-2016.0.0.4          ---
system/library/fontconfig (userland)              2.11.95-2016.0.0.0         ---
web/browser/firefox (userland)                    45.3.0-2016.0.0.0          ---
x11/library/toolkit/libxt (userland)              1.1.4-2016.0.0.0           ---
```


#### Adding the package as a local repository

`pkg set-publisher -p firefox_test.p5p`


#### Installing software from the local repository

`pkg install firefox@45.3.0-2016.0.0.0:20160817T064143`


### Finding help with pkg

The primary source of help for any OpenIndiana command is to review the man page for the command.
Therefore, be sure to consult the `pkg`<sup>1</sup> man page for full command information and usage examples.

For example: `man pkg`

To reference command usage directly from the command line, use `pkg help`.

To retrieve additional information about a specific command use: `pkg help <command name>`

For example:

`pkg help update`

```
Usage:
        pkg update [-fnvq] [-C n] [-g path_or_uri ...] [--accept] [--ignore-missing]
            [--licenses] [--no-be-activate] [--no-index] [--no-refresh]
            [--no-backup-be | --require-backup-be] [--backup-be-name]
            [--deny-new-be | --require-new-be] [--be-name name]
            [-r [-z image_name ... | -Z image_name ...]]
            [--sync-actuators | --sync-actuators-timeout timeout]
            [--reject pkg_fmri_pattern ...] [pkg_fmri_pattern ...]
```


### Legacy package management tools

OpenIndiana continues to support the use of legacy package tools for managing SVR4 packages.
Here are some of the available tools:

* pkginfo
* pkgadd
* pkgrm


### 3rd party package management tools


<i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **DOC TEAM NOTE:**
<div class="well">
ITEMS TO WRITE ABOUT:

* <https://pkgsrc.joyent.com/>
* <https://pkgsrc.joyent.com/install-on-illumos/>

* Need to answer the questions - Where and how can I install more software?
* Discuss 3rd party package managers (PKGIN, etc.)
* Discuss the various 3rd party repos (opencsw, sfe, pkgsrc.joyent, etc.), what's available in them, and which might break compatibility, etc.
* Describe SFE (SPEC FILES EXTRA) and how it differs from OI and other repos.
* How to add additional repos, etc.
* How to compile your own software.
    * I think there is an existing wiki page for this.
    * Given the limited number of IPS packages currently available, this is a pretty important subject to write about.
    * Also could look here (might be outdated):
    * [web link](http://www.inetdaemon.com/tutorials/computers/software/operating_systems/unix/Solaris/compiling_software.shtml)

</div>

In addition to IPS and SVR4 package management tools, it is also possible to use `pkgsrc`.

For more information about pkgsrc, see the [Joyent package source website](https://pkgsrc.joyent.com/).

<!-- CAUTION: --> <i class="fa fa-exclamation-triangle fa-lg" aria-hidden="true"></i> **CAUTION:**
<div class="well">

The use of 3rd party repositories and package managers increases the likelihood of conflicts between package versions and their dependencies.
Furthermore, the OpenIndiana project cannot guarantee the qualify of packages obtained from 3rd party repositories.
Therefore, use 3rd party repositories and 3rd party package tools at your own risk.

</div>


## Managing boot environments

A boot environment is a bootable instance of an OpenIndiana operating system image plus any other application software packages installed into that image.
You can maintain multiple boot environments on your system, and each boot environment could have different software versions installed.
Upon the initial installation of OpenIndiana onto your system, a boot environment is created.
Use the `beadm`<sup>1M</sup> utility to administer additional boot environments on your system.

The `beadmn` utility is designed to work in concert with the ZFS file system and the IPS package manager.

### Why use multiple boot environments?

With multiple boot environments, the process of updating software becomes a low risk operation because you can create backup boot environments before making any software updates to your system.
If needed, you have the option of booting a backup boot environment.

Here are some specific examples where having more than one OpenIndiana boot environment, and managing them with the `beadm` utility, is useful:

* When you use the `pkg update` command to update all the packages in your active OpenIndiana boot environment, this process automatically creates a clone of that boot environment.
The packages are updated in the clone rather than in the original boot environment.
After successfully completing the updates, the new clone is activated.
Then, the clone will become the new default boot environment on the next reboot.
The original boot environment remains on the GRUB menu as an alternate selection.
You can use the `beadm list` command to see a list of all the boot environments on the system, including the backup boot environment that still has its original, unchanged software.
If you are not satisfied with the updates made to the environment, you can use the `beadm activate` command to specify that the backup will become the default boot environment on the next reboot.

* If you are modifying a boot environment, you can take a snapshot of that environment at any stage during modifications by using the `beadm create` command.
A snapshot is a read-only image of a dataset or boot environment at a given point in time.
You can create custom names for each snapshot that identify when or why the snapshot was created.
For example, if you are doing monthly upgrades to your boot environment, you can capture snapshots for each monthly upgrade.
You can use the `beadm list -s` command to view the available snapshots for a boot environment.
A snapshot is not bootable.
But, you can create a boot environment, based on that snapshot, by using the `-e` option for the `beadm create` command.
Then you can use the `beadm activate` command to specify that this boot environment will become the default boot environment on the next reboot.

* You can maintain more than one boot environment on your system, and perform various upgrades on each of them as needed.
For example, you can clone a boot environment by using the `beadm create` command.
A clone is a bootable copy of a boot environment.
Then, you can install, test, and update different software packages on the original boot environment and on its clone.
Although only one boot environment can be active at a time, you can mount an inactive boot environment by using the `beadm mount` command.
Then you can use the `pkg update` command with the `-R` option to update all the packages in that inactive, mounted environment.
Or, use the `pkg install packagename` with the `-R` option to update specific packages on that environment.


### Features of the beadm utility

The `beadm` utility has the following features:

* The `beadm` utility aggregates all datasets in a boot environment and performs actions on the entire boot environment at once.
You no longer need to perform ZFS commands to modify each dataset individually.

* The `beadm` utility manages the dataset structures within boot environments.
For example, when the `beadm` utility clones a boot environment that has shared datasets, the utility automatically recognizes and manages those shared datasets for the new boot environment.

* The `beadm` utility enables you to perform administrative tasks on your boot environments.
These tasks can be performed without upgrading your system.

* The `beadm` utility automatically manages and updates the GRUB menu.
For example, when you use the `beadm` utility to create a new boot environment, that environment is automatically added to the GRUB menu.

The `beadm` utility enables you to perform the following tasks:

* Create a new boot environment based on the active boot environment
* Create a new boot environment based on an inactive boot environment
* Create a snapshot of an existing boot environment
* Create a new boot environment based on an existing snapshot
* Create a new boot environment and add a custom title to the GRUB menu.
* Activate an existing, inactive boot environment
* Mount a boot environment
* Unmount a boot environment
* Destroy a boot environment
* Destroy a snapshot of a boot environment
* Rename an existing, inactive boot environment
* Display information about your boot environment snapshots and datasets


### beadm command reference

|Command | Description
| --- | ---
| `beadm` | Displays command usage
| `beadm activate <BE>` | Makes the specified boot environment the active boot environment upon the next reboot.
| `beadm create <BE>` | Creates a new boot environment with the name specified. Unless the `-e` option is provided, the new boot environment is created as a clone of the currently running boot environment.
| `beadm create <BE@snapshot>` | Creates a snapshot of the existing boot environment with the specified snapshot name.
| `beadm destroy <BE>` | Destroys the boot environment named BE or destroys an existing snapshot, BE@snapshot, of a boot environment. Prompts for confirmation before destroying the boot environment.
| `beadm list <BE>` | Lists information about the specified boot environment, or lists information for all boot environments if a boot environment name is not provided. The default is to list boot environments without any additional information.
| `beadm mount <BE> <mountpoint>` | Mounts the specified boot environment at the specified mount point. The mount point must be an already existing, empty directory.
| `beadm rename <old BE> <new BE>` | Renames the specified boot environment.
| `beadm unmount [-f] <BE>` | Unmounts the specified boot environment. `-f` – Forcefully unmounts the boot environment even if it is currently busy.

For detailed instructions about the `beadm` utility, see the `beadm`<sup>1M</sup> man page.

### beadm zones support

Zones partitioning technology is used to virtualize operating system services and provide an isolated and secure environment for running applications.
Each OpenIndiana system is a global zone.
Within a global zone, specific non-global zones can be created.

### Zones support limitations

Note the following limitations of support for non-global zones in the beadm utility and in related processes:

* When using the `pkg update` command, the `-r` switch is required to upgrade all zones.
* The `beadm` utility is not supported inside a non-global zone.
* Non-global zone support is limited to ZFS support.
Zones are not supported unless they are on ZFS.
* Zones are not supported in the rpool/ROOT namespace.
Non-global zones are cloned or copied only when the original zone is within the shared area for the global zone, for example, within rpool/export or within rpool/zones.
* Although the `beadm` utility affects the non-global zones on your system, the `beadm` utility does not display zones information.
Use the `zoneadm` utility to view changes in the zones in your boot environment.
For example, use the `zoneadm` list command to view a list of all current zones on the system.

For further information, see the `zoneadm`<sup>1M</sup> man page.


### Zones support specifications

The beadm command impacts the non-global zones in your boot environments as follows:

| Command | Support Details
| --- | ---
| `beadm create` | When you clone a boot environment by using the beadm create command, all zones in that boot environment are copied into the new boot environment.
| `beadm destroy` | When you destroy an inactive boot environment, the zones that belong to that boot environment are also destroyed.
| `beadm mount` | When you mount a boot environment, the zones in that environment are mounted relative to the mount points for the environment.
| `beadm unmount`| When you unmount a boot environment, the zones in that environment are also unmounted. All mount points are returned to their states prior to being mounted.
| `beadm rename` | When you rename a boot environment, that change does not impact the names of the zones or the names of the datasets that are used for those zones in that boot environment. The change does not impact the relationships between the zones and their related boot environments.


## The X-Window system

Nearly all cards can use the VESA driver, and are therefore supported for 2D.

### Video card support (3D)

* Nearly all NVidia GPU's are supported by the Nvidia binary driver.
* Beginning with the July 2016 experimental release, most Intel GPU's are now supported.
* While AMD GPU's are not currently supported (VESA driver only), development is currently underway to provide 3D support for both legacy and modern AMD GPU's.

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **DOC TEAM NOTE:**
<div class="well">

* Talk about the expected behavior when booting the live CD from a system with an NVIDIA card.
* Discuss procedure for adding an NVIDIA card to a system that was using VESA or some other non-3d video driver.
* Troubleshooting - what logs to look at, manual configuration, etc.
* Walk through NVIDIA utility screens.

</div>


### How does one add a missing device driver?

<!-- NOTE: --> <i class="fa fa-info-circle fa-lg" aria-hidden="true"></i> **DOC TEAM NOTE:**
<div class="well">

Write about:

* Finding hardware id's
* Searching for drivers
* Installing and loading drivers
* Adding device ID's to `/etc/driver_alias`, etc.

</div>

