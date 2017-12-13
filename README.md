# linuxTroubleResolver

A few answers to resolve troubles I got with Xubuntu on my Acer Aspire VN7-592G-574M

1. [HDMI not recognized](#hdmi-port-doesnt-work)
2. [powerline font for agnoster theme from OhMyZsh](#powerline-font-for-agnoster-theme-from-ohmyzsh)
3. [Sound mic trouble with Xubuntu](#sound-mic-trouble-with-xubuntu)



## HDMI port doesn't work.
### Problem
With Xubuntu 16.06 (LTS) the HDMI port doesn't work. if a screen is plugged in, it's not recognized by Xubuntu. Therefore I can't use dual screen.

It seems to be linked with the optimus technology. But Xubuntu 16.04 is supposed to natively deal with this architecture.

### Quick solution

#### First attempt:

 (hopefully it will be enough)

* Launch Xubuntu recovery mode (press escape during boot on acer logo screen)
* Select "advanced ubuntu options"
* Activate network
* Launch `dpkg` option which should restore XOrg. I don't remember if, when I did it, a second screen was plugged in HDMI port, but it shouldn't be a probem.
* Reboot computer and it should be fixed.

If it does'nt fix the problem, continue with the "complete solution"

#### Complete solution if first one didn't work.
* Install `aptitude` first if needed: `sudo apt-get install aptitude`
* Try to install `xserver-xorg-video-nouveau` with `aptitude` (cause apt-get install won't accept to install it) :    `aptitude install xserver-xorg-video-nouveau`    
    This will destroy the XOrg server. (The computer won't reboot with graphical mode)
* Follow [first attempt](#first-attempt) section now.

There is probably a better way to destroy then repair XOrg but this one seems to work fine.


### To test
Install NVidia proprietary drivers with this new config. Will be tried before formating the computer (in a few months).


## Powerline font for agnoster theme from OhMyZsh

### Problem

The agnoster OhMyZsh theme is not properly working

### Solution tried and checked

`sudo apt-get install powerline`



## Sound mic trouble with Xubuntu

### Problem
 Neither the built-in mic nor jack mic input is recognized

### Solution tried but not really good

1.  Add line `options snd-hda-intel model=dell-headset-multi` at the end of /etc/modprobe.d/alsa-base.conf file    
mic is recognized (at least jack mic). built in mic doesn't seems to work seems to be recognized.
however the audio output becomes bad

### Solution to try :
Check https://ubuntuforums.org/showthread.php?t=927270&p=7593640#post7593640 and try it maybe? but seems to be an old post.

Maybe mix this solution with the already tried (at least the alsa-base.conf)


# TODO 
les confs réseaux (dont VPN) se trouvent dans /etc/NetworkManager/system-connections ce qui permet de les modifier à la main en cas de soucis d'import VPN
