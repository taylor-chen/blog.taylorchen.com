---
title: Dual Boot Elementary OS Freya and Windows 8.1
---
I have been wanting to install Linux for quite a while now mostly because I dislike using Cygwin or remote desktoping a Linux machine whenever I want to use the shell. Late last night I was super bored and finally pulled the trigger and decided I wanted to dual boot my Windows 8.1 with a flavour of Linux. The following article show the steps I took for it to work on my system.
I have an ASUS TP550L, i7-4500U, 8gb RAM, with Intel HD Graphics 4400/ NVDIA GeForce 820M.

Elementary OS
=============
I picked [Elementary OS](http://elementary.io/) out of tons of distros for no reason other than how it looks. As you probably guessed from the title, I ended up installing [Freya](http://beta.elementary.io/) over Luna even thought Freya is in beta. I actually loaded Luna first from a CD I burned before actually installing Freya. However, when I ran Luna I unfortunately had terrible [WiFi issues known to occur with Ubuntu 12.04](https://www.google.ca/search?q=ubuntu+wifi+problem#q=ubuntu+wifi+problem+12.04). Since I was too lazy to find an Ethernet cable, I hopped back on Windows and tried again with Freya. Lo and behold, 5 bars of WiFi.  
Luna is based on Ubuntu 12.04 LTS and has had a stable version since August 2013. Freya is based on Ubuntu 14.04 and is in it's second beta at the time of writing. Since Elementary OS (eOS) is based on Ubuntu, it may be a good idea to look for Ubuntu resources if you can't find any eOS resources.

Checklist
=========
Step 0: Backup your data
------------------------
Call me a hypocrite but I did not perform this step. My reason for NOT backing up is because I only had this laptop for <2 months and don't have anything important to lose. I also trust in my ability to fix Windows if I were to destroy it. **SO PLEASE CONSIDER BACKING UP WINDOWS IF YOU HAVE ANYTHING TO LOSE EVEN IF YOU DECIDE YOU DON'T WANT LINUX ANYMORE**

Step 1: Download and create a live USB/CD
-----------------------------------------
Download [Luna](http://elementary.io/) or [Freya](http://beta.elementary.io/). Follow the instructions on [creating an install disk](http://elementary.io/docs/user-guide/creating-an-install-disk). Luna is only 694MB so it's perfect to burn on your spare 700MB CDs.

Step 2: Shrink Windows Partition
--------------------------------
You need to make space for eOS on your machine. Start by searching for "Partitions" from the search button in the Start screen. The Disk Management screen will appear.
![Disk Management](/images/disk-management.jpg )  
Right click a drive and click "Shrink Volume.." and enter a value in "Enter the amount of space to shrink in MB." I shrunk one of my partitions by 300GB but how much space you want for eOS is personal preference. If you choose to shrink your OS (Usually C:) drive, **beware to not shrink for more than offered because you can break your Windows 8.1 operating system.**

Step 3: Turn off fast startup
-----------------------------
Open "Power Options" from your Control Panel (or from the Taskbar if you're on a laptop). On the left, click "Choose what the power buttons do."
![Fast Boot](/images/fast-start.jpg )   
Click "Change settings that are currently unavailable," scroll to the bottom and uncheck "Turn on fast startup."

Step 4: Turn off secure boot
----------------------------
This turned out to be a pain in the behind for me because... ASUS. It should be a lot easier.  

To do this you need to click on the power button the Start screen and press shift while clicking on restart. Find the option to modify your UEFI boot settings, it should prompt you to restart. In the UEFI, you should be able to find and turn off the secure boot option. Save and exit the UEFI settings.

If your secure boot was grayed out like mine was, you need to delete all secure boot keys then save and exit. After opening it again you **should** be able to turn it off, or you may find that it is already off. If that doesn't work then Google is your friend. ;)

Step 5: Boot from your USB/CD
-----------------------------
You can do one of two things to boot from your USB/CD. Before your computer boots up press F2, F10 or F12 (could also be something else) to go to your boot menu. From there change the boot option to USB or Removable Media, or CD. Alternatively if you're already in windows with the CD or USB connected, shift click the restart button like earlier and there should be an option to boot from your media device/CD.

Step 6: Install!
----------------
By now you should have eOS running from your chosen media! The following images are from [itsfoss.com](http://itsfoss.com/). Note that I'll be omitting steps that are straight forward. They also chose to make partition space in eOS rather than in Windows 8.1 so you can skip those steps, and I chose to partition more space than the images provided so keep that in mind.  

Keep clicking Continue until the reach the following page, choose "Something else"
![Installation](/images/install1.jpeg )   

Step 7: New Partitions
----------------------
You should be able to see the free space we created earlier, select the free space and click "Add..."
![Installation](/images/install2.jpeg )   
Create a root **/** partition, I put in 50000.  
![Installation](/images/install3.jpeg )   
Create a swap partition **Make sure you did in fact select swap area**, generally this is supposed to be double your RAM so I put in 16000. [I found a source that says rule of thumb is the size of your RAM plus .5 GB](http://www.howtogeek.com/196238/how-big-should-your-page-file-or-swap-partition-be/). I might have put too much, oops.
![Installation](/images/install4.jpeg )   
Create a home **/home** partition, I put in the rest of my free space.  
![Installation](/images/install5.jpeg )   
At this point it should look something like this:
![Installation](/images/install6.jpeg )   

Step 8: Finish and Restart:
---------------------------
Once that is done you should click through some trivial settings and reach...
![Installation](/images/done.jpeg )   
Congrats! You've installed eOS Freya (or Luna). When you're restarting you should go into your boot menu and select to boot Linux first instead of Windows boot manager. If you still load into Windows, try rebooting again. On future reboots you should see 4 options:  
1.  elementary OS  
2.  Advanced options for elementary OS  
3.  Windows Boot Manager  
4.  System setup  

Choose option 1 for eOS and option 3 for Windows!

Remember to update your system after installation because eOS Freya is still in beta and has a lot of continuous updates and bug fixes. I might write a review on the OS once I play around and get more comfortable. In the meantime, If you have any questions shoot me an email at t84chen@uwaterloo.ca, I really hope this has helped someone. Thanks for reading!
