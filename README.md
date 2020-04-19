# Linux-Hall-of-Shame
A shaming hall for every time I have to wipe my computer's butt because something simple doesn't work or it can't figure out how to do something very easy. I'm using a Ubuntu Long Term Support release, not Arch for those wondering. Life shouldn't have to be this hard.

The year of Linux on the Desktop for those wondering, is probably one day after the heat death of the universe the way things look currently. No human should have to experience this misery. 

# Steam 
https://askubuntu.com/questions/1038754/steam-wont-start-on-18-04

# Laptop Graphics crap (horrendous on Linux):
## Check graphics cards
lspci -k | grep -A 2 -i "VGA"

## Switch to using integrated graphics on a linux laptop with nvidia x server installed
## https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu
sudo prime-select intel

## Switch to using nvidia graphics on a linux laptop with nvidia x server installed (for games, ML, etc.)
sudo prime-select nvidia

## query which graphics device is active (is a liar sometimes, rquires log out and in to apply)
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

