---
layout: post
title: Install Hamachi VPN on Western Digital My Cloud
author: Matt
permalink: "/2014/05/install-hamachi-vpn-on-western-digital-my-cloud/"
published: false
---

Recently, I bought a Western Digital My Cloud network attached storage device to use for bacing up our PCs and storing our photos. This is a fantastic device and comes with a bunch of great features. What's even better is that it runs Linux and SSH access can be easily enabled through the web-based control panel. This post will walk you through how to install the Hamachi VPN client on the WD My Cloud so that you can access your files from anywhere.

LogMeIn recently announced Beta support for the Linux distributions of their Hamachi software. We will make some slight modifications to that so that it works for the WD My Cloud. First, let's enable SSH on the device:

Navigate to `http://wdmycloud` in your web browser to access the device's control panel. From there click on Settings and the Network. Under Network Services, flip the switch to enable SSH access. By default, the username is `root` and the password is `welc0me`.

Next, login to your WD My Cloud via SSH using the credentials above. The WD My Cloud runs on an ARM HF architecture. Download the latest version of the Hamachi software for Linux from the LogMeIn website using the following command:

{% gist mbmccormick/3c90ccd38ae673c7e85a %}

If that doesn't work for you, you can download the package on your local machine and copy it over via Windows Explorer.

Next, we need to extract the package and make a slight modification to the install and uninstall scripts. Do that with the following commands:

{% gist mbmccormick/ef513f416d4392ed56e3 %}

The modified install and uninstall scripts that I created remove the dependency on the LSB package, which I couldn't manage to install on the WD My Cloud. It turns out that the only thing that Hamachi is using in the LSB package for is to install the init.d script so that the Hamachi daemon is started on boot. I managed to get around this by using update-rc.d instead and removing the checks to see if LSB is installed.

Next, run the modified install script to install Hamachi:

{% gist mbmccormick/21b71e25f6bf2f48c6fc %}

Hamachi should now be installed and you can bring it online, join networks, etc. using the `hamachi` command. The Hamachi daemon will also start and go online whenever the WD My Cloud reboots. You should now be able to access your WD My Cloud from any of the machines on your Hamachi networks!