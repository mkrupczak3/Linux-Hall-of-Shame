# Linux-Hall-of-Shame
A shaming hall for every time I have to wipe my computer's butt because something simple doesn't work or it can't figure out how to do something very easy. I'm using Ubuntu, not Arch for those wondering. 

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

