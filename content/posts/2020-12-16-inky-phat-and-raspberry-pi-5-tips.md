---
title: "Inky pHat and Raspberry Pi. 5 How To Tips And Tricks Automate Weather Reports."
date: "2020-12-16"
categories: 
  - "computer-science"
  - "inspiration"
  - "learning"
tags: 
  - "inky-phat"
coverImage: "gabriele-diwald-j2OprKAcWkQ-unsplash-scaled.jpg"
---

For the annual i&i-conference, I try to find a 'new' gadget for speakers and board members. Last year we bought Inky Phats with a Raspberry Pi Zero W. To be used as interactive name badges. A great success! In this article, I'll share 5 tips on using the display, and I'll be discussing a few problems. Inky pHat is an e-paper display with a dedicated controller in the PCB. Plug and play! And big thanks for the [excellent documentation](https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-inky-phat) @Pimoroni!

![Inky pHat, a Raspberry Pi with a pHat on top of it. Displaying a squid](images/inky_phat.jpg)

[Inky pHat](https://shop.pimoroni.com/products/inky-phat?variant=12549254217811) by Pimoroni is easy to use 'phat' A HAT is an extension for the Raspberry Pi platform. Hardware attached on top or HAT. With the sturdy HAT construction, there a three benefits;

- **No soldering**; plug it onto the Raspberry Pi.
- **Robust mechanical design**, it can handle a school environment.
- '**Autoconfiguration**,' all the software is provided. Just attached and install. 'Plug and play/pray.'

I am thrilled with the HAT-system. It just works, no tinkering and no failure with a faulty connection. The design can handle some rough handling (always be careful when handling hardware!), and with the software backend from the manufacture, it's just a few commands in the CLI, and it works. Most of the times ;-)

## Tip 1 how to update Raspberry Pi

It's always good to work with an updated Raspberry Pi. [Sudo apt-get update, sudo apt-get upgrade](https://askubuntu.com/questions/94102/what-is-the-difference-between-apt-get-update-and-upgrade). It will take some time when this is the first time you are using their commands. Keep in mind; these commands are going to be typed into the terminal or SSH. To keep things organized, I always end the update sessions with sudo apt-get **autoclean**. This removes all the no longer used files after an update.

## Tip 2 Please use a stable power supply

It sounds like a normal thing to do, right... but I found out the hard way that this needs some TCL. The Raspberry Pi was giving strange errors, rebooted, and shutdown for no apparent reason. The installation on the sd-card went corrupt, and I couldn't find the problem. I swapped the card, reinstalled the OS on the card, and even swapped Raspberry Pis. And with some deduction, Sherlock would be proud; I discovered a faulty power supply to be the problem. Double-check the quality of the Micro USB cable! And be careful when installing the Inky pHat. The pins of the Raspberry Pi and Inky pHat need to be aligned. DO-NOT-FORCE.

## Tip 3 How to install software with CLI

The documentation by Pimoroni is excellent. [Getting Started With Inky pHat](https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-inky-phat) is a great start. It helps with the correct commands for the CLI. Again, this display is a _command-line_ interface only. It's a quick installation with a few commandos. I've summarized the commands under this text block. The dollar ($) sign is a new line on the CLI. Keep in mind; this is a United Kindom based company. And over there, color is spelled with 'ou.' ;-).

```
$ curl https://get.pimoroni.com/inky | bash
$ cd /home/pi/Pimoroni/inky/examples
$ python name-badge.py --type "auto" --colour "red" --name "Ramon"
```

## Tip 4 Automate the sh\*t with CRON

CRON is the automation tool in Linux. It's 'easy' to use. I had a few challenges when I wanted to automate the update of the display. CRON was for me. I never used it. This [resource](https://forums.pimoroni.com/t/need-help-with-inky-phat-crontab-update/7207) helped me a lot! I started with calling the python script directly from CRON. After a few failures, I found that CRON does understand .sh scripts. This is my .sh script. I called it phat.sh. Open a new file with nano phat.sh. Be in the root of your folders; cd is the command to return to the root. Exit nano with ctrl+x and save (!) the file. After saving, make the file executable. Type in the same folder as the phat.sh : _chmod +x phat.sh_

```
#!/bin/bash
cd /home/pi/Pimoroni/inky/examples/phat/
python weather-phat.py --colour red
```

In the CRON tab, I added the following. The /10 executes the script every 10 minutes (starting at .0 every hour)—only between 8 and 22 hrs. The bash is used to run the script. Pay attention to the **absolute** path with a / at the beginning.

```
*/10 8-22 * * * * bash /home/pi/phat.sh
```

## Tip 5 This works, what's next?

And how what? You have a mobile weather station. It runs from a power bank or even [a dedicated battery.](https://www.hackster.io/news/pisugar-is-a-compact-battery-solution-designed-specifically-for-the-raspberry-pi-zero-416b503732e6) I'm going to install it on the fridge with a micro USB cable to provide power. With the 10-minute update cycle, the screen isn't heavily used and will work for quite some time. **Inky Phat is a fun display**. The use cases are immense, and I am slowly figuring out what else I can build with it.
