# Installing Ubuntu as dual boot OS

To install Ubuntu as a dual boot on a Windows machine is reasonably straightforward, but only if you know a few tricks. Recently, I had to install Ubuntu on a Dell laptop that already has Windows. Dell has very helpfully provided a guide to installing Ubuntu as dual boot [here](https://www.dell.com/support/article/en-uk/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en), but it is missing a few crucial hints. So here are my steps so I can do it again if necessary :wink:

1. Go to the [official Ubuntu downloads page ](https://ubuntu.com/download/desktop) and download the iso you want-- preferably do this on the computer you are creating the dual boot on to make sure you are downloading the correct iso for your system architecture.

2. Install [Rufus](rufus.ie) and create a bootable USB stick with the iso you have just downloaded. This step is crucial-- just saving the iso file to a usb stick isn't going to make it bootable.

3. Shrink the Windows partition (Windows Disk Manager -> select volumn to shrink -> select `all tasks` then `shrink volumn`)

4. Turn off `Fast startup` (Control panel -> power options -> select `choose what the power button does` => Select `Change settings that are currently unavailable` -> make sure that the `fast startup` option is turned off)

5. Restart the computer and press `F2` repeatedly while it boots to go into the BIOs settings editor: you have to make sure that the RST (Intel Rapid Storage Technology) is turned off since Ubunut can't be installed with it on. In the bios menu you should be able to change this option to AHCI. Save and exit-- the computer will again restart.

6. As the computer restarts, plug in your installable ubuntu USB stick and this time press repeated the `F12` button. In the boot option screen that shows up, you should be able to see your usb stick as a boot option. Go into this and you should be able to see the Ubuntu installation GUI. Follow this to install Ubuntu.
