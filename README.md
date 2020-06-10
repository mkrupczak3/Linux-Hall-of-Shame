# Linux-Hall-of-Shame

## A wailing wall for a lost soul fighting Linux
A shaming hall for every time I have to wipe my computer's ass because something simple doesn't work or it can't figure out how to do something very easy. I'm using a Ubuntu Long Term Support release, not Arch for those wondering. Life shouldn't have to be this hard.

The year of Linux on the Desktop for those wondering, is probably one day after the heat death of the universe the way things look currently. No human should have to experience this misery. 

Say what you will about Microsoft or Apple, but to their credit their computers actually work when you turn them on instead of having to deal with this hot trash

# Steam 
https://askubuntu.com/questions/1038754/steam-wont-start-on-18-04

# UPDATE 2020-04-20T18:10-05:00
Aparently, I have to update my graphics drivers before even %#$!@ing steam will launch.

The only way I can do this is to manually turn off the computer/dispaly service and run a proprietary binary from NVIDIA

Neither the PPA that is widely recommended nor the Ubuntu driver GUI window that shipped with the OS I'm trying to use ACTUALLY #$%!!ing work. (this is actually very normal). Again, I'm not asking for the moon, I'm on a long term support release of the most popular "user friendly" distro of Linux (Ubuntu) using some of the "best supported" hardware (Intel/NVIDIA).

First I had to manually edit my grub file to add back in a GRUB bootloader display screen to the bootup sequence, then I had to GO IN AND MANUALLY EDIT THE GRUB BOOTLOADER TO BOOT INTO SINGLE USER MODE

WHEN THAT DIDN'T WORK, I HAD TO REBOOT AND EDIT IT AGAIN TO BOOT INTO RUNLEVEL 3 (no gui)

[try explaining this to your grandmother or snot nosed nephew who wants to play minecraft or call of duty]

Also, after installing it, my display driver is @#$@k'ed, and I only have display output at 1024x768. 

NOW I HAVE TO WADE THROUGH $(@*#* of log files and figure out how I burned down my house while trying to change a broken window that the contractor couldn't be #$%% to install correctly, and also, my phone (PPA) wouldn't work to call the company who sells them ....

# UPDATE 2020-04-20T19:08-05:00
[Solution](https://askubuntu.com/q/1191638)

After working on this for over an hour and a half, I was able to fix it NOT by uninstalling and reinstalling different versions of the driver binary (old, stable, development, etc.) from NVIDIA, but through:

1. MANUALLY $%$^#%@%'ing BLACKLISTING THE NOUVEAU DRIVER (this may or may not be necessary)

2.  :
```
$ sudo apt purge nvidia*
## if you reboot here, the computer will use Nouveau driver
## check recommended drivers
$ ubuntu-drivers device
## Shows me that nvidia-driver-440 is recommended, 
##     even though I just recently installed that and
##     and it didn't work (WTF?)
```

3:

~~sudo apt install nvidia-340~~


So, given that 440 is the curent number, you think I would be correct in assuming I need to run "sudo apt install nvidia-440" right?

WRONG. Instead, the package name was changed for NO DISCERNABLE REASON to nvidia-driver-XXX and NOBODY TOLD ME, or likely anyone else for that matter [not in any of the many forum posts I saw] (this is very common in the Linux ecosystem).

Every time I would try to run "sudo apt install nvidia-440" it would very calmly and dumbly say "no package available by that name".

JESUS CHRIST HOW THICK IN THE HEAD DO YOU HAVE TO BE TO RELEASE SOFTWARE PACKAGED LIKE THIS AND NOT AT LEAST INCLUDE A GODFORSAKEN ALIAS THAT WOULD TAKE NO MORE THAN 3 KEYSTROKES TO SET UP. 

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH. 

3: (part 2)
```bash
$ sudo apt install nvidia-driver-440
```

and it works. it just f'ing works. And I feel like an idiot. And also like I've been used or mistreated somehow....

# Update 2020-04-20T19:47-05:00
I [spoke too soon](https://github.com/ValveSoftware/steam-for-linux/issues/5778) [+](https://github.com/ValveSoftware/steam-for-linux/issues/6366)

(I'm unsure of whether I more want to power through this problem, or just set my computer on fire or drop it from the top of my residence onto the pavement below. I'm opting for number 2, because then at least no one else will have to ever use this pile of garbage ever again)

So, aparrently, the PPA version (I installed "easily" using apt install nvidia-driver-440) DID NOT INSTALL 32-bit COMPATIBILITY LIBRARIES THAT ARE REQUIRED BY STEAM TO RUN (WTF?)

WHO THE HELL ON EARTH IS LOOKING TO USE A LINUX COMPUTER WITH NVIDIA GRAPHICS DRIVERS INSTALLED WITHOUT STEAM? (not just CUDA mind you, *graphics* drivers.)
https://youtu.be/v46plhmxXU4


# Laptop Graphics crap (horrendous on Linux):
## Check graphics cards
lspci -k | grep -A 2 -i "VGA"

## Switch to using integrated graphics on a linux laptop with nvidia x server installed
## https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu
sudo prime-select intel

## Switch to using nvidia graphics on a linux laptop with nvidia x server installed (for games, ML, etc.)
sudo prime-select nvidia

## query which graphics device is active ([is a liar sometimes](https://youtu.be/Zgk8UdV7GQ0), rquires log out and in to apply)
prime-select query

## Query which graphics device is active (i.e. games would actually use)
## Important when used to figure out if either Intel or Nvidia card is actually active
glxinfo|egrep "OpenGL vendor|OpenGL renderer*"

## download a YouTube video and convert the format to mp3
youtube-dl --restrict-filenames --ignore-errors -x --audio-format mp3 https://www.youtube.com/watch?v=MopniCeuWTk

## Check GPU usage of NVIDIA card:
## Setup
###     http://blog.datumbox.com/getting-the-gpu-usage-of-nvidia-cards-with-the-linux-dstat-tool/
### sudo apt-get install dstat #install dstat
### sudo pip install nvidia-ml-py #install Python NVIDIA Management Library
### wget https://raw.githubusercontent.com/datumbox/dstat/master/plugins/dstat_nvidia_gpu.py
### sudo mv dstat_nvidia_gpu.py /usr/share/dstat/ #move file to the plugins directory of dstat
dstat -a --nvidia-gpu

# Redshift (blue light removal) [pain in my #%!]
``` 
# Issue I've run into MULTIPLE times, very frustrating for something so stupid
#
# Start the redshift night-time blue light removal / display dimming service, providing it a longitude and latitude manually
# Since apparently these garbage-tier developers can't be bothered to get some of the most BASIC
# software on the planet to work on an esoteric system such as, I don't know, UBUNTU 18.04 LONG TERM SUPPORT (WTF?)
#
# https://github.com/jonls/redshift/issues/445
#
# https://manpages.ubuntu.com/manpages/trusty/man5/redshift.5.html
# @TODO change 6471 to the correct daytime color temperature (no modification/redshift)
redshift -l 4.65:-74.06 -t 6471:3600 -g 0.8 -m randr -v &
# As an aside, this is a perfect example of why I would never recommend Linux or even Ubuntu to a normal human being. 
# It just isn't designed for usability, and the contract with users
# (I do something -> it is supposed to actually work [dammit!]) even with the simplest GUI
# apps clearly doesn't even exist on this platform. 
#
# Never mind trying to convince your grandma to 
# try to mess with all this crap on the command line every time your computer forgets how to wipe its own a**.
#
# This unfortunately has been painfully demonstrated to me time and time again.
``` 
## FML
At least this is one more thing Ubuntu makes easy:
https://www.omgubuntu.co.uk/2017/10/enable-night-light-mode-on-ubuntu

Guess I don't really have any grounds to complain

# Glaring disk and IO bugs on Ubuntu 18.04
https://askubuntu.com/questions/377253/unable-to-format-usb-drive-with-disks-udisks-error-quark-0

Bugs in the very basic implementation of disk io in Ubuntu. Trying to get a simple ext4 thumbdrive working with encryption to store my private keys, but apparently this task is too much for the feeble likes of Ubuntu and it keeps crapping out, flimsing, throwing weird error messages, and generally shooting its load before actually formatting and mounting the disk properly.

I have to say, from a User Interface standpoint, it's absolutely appaling that on a long-term support release I'm having to manually look up these error messages, install gparted, reformat the disk, and then go and manually format it again using an external tool instead of pressing the TWO BUTTONS IN THE NAUTILUS FILE BROWSER THAT SHOULD JUST F***** WORK GOD F***** DAMMIT UBUNTU WTF!!!!
