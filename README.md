# Shimbootfor3100
This repository is designed specifically for Chromebook 3100 users, specifically in the CPS school district. Read below for instructions.
Credits: [https://sh1mmer.me/](url) and [https://github.com/ading2210/shimboot#prerequisites](url)

<img width="504" height="672" alt="IMG_3771" src="https://github.com/user-attachments/assets/0701840b-cf0e-4791-a8cb-029ed13c0800" />

<sub>A Chromebook running this exact Shimboot installation.</sub>

# Getting Started
"Well what is shimbooting?" you may ask.
Well, shimbooting is a type of thing where you run an operating system on a Chromebook off of a live USB. However, it's a special one because you're spoofing the USB to make your computer and enrollment system think that you're actually booting into a recovery USB instead of the Debian 12 USB we'll be using.

In order to shimboot on a Dell Chromebook 3100, you must first meet the prerequisites. Since we're booting off a USB, you won't need any storage requirements.

You will need, however,
- A USB that has at least 8 GB of storage that you are ok with formatting (Formatting basically means deleting everything and replacing it with a bootable OS.)

- At least 4 GB memory

- A laptop or PC that has either Windows or Linux (not creating Mac/OS X instructions yet) (also you must have admin permissions to that computer) (and also at least 8 GB of free space on there)

You will also need to be okay with **erasing EVERYTHING on your Chromebook's local disk**. This includes:
- Screenshots
- Screen recordings
- All saved files

   I would recommend you **back up all your files to Google Drive.**
  **IT IS EXTREMELY RECOMMENDED TO DO THIS AT HOME, BECAUSE THE WIFI PASSWORD TO THE CPS NETWORK HAS NOT BEEN OBTAINED.**
  
  **IT IS ALSO RECOMMENDED TO ENABLE CLOUDFLARE WARP WHEN CONNECTING TO WIFI ON YOUR SHIMBOOT.**

  Now onto the real stuff.

  # Preparing the USB
  In order to prepare the USB, first install the .zip file in the Releases tab. The name will have "octopus", the baseboard family name used for the Chromebook 3100.
  Now, this is where you utilize your PC.
  
  ## Linux instructions
  First, you'll wanna unzip the archive. Run "unzip ~/Downloads/shimboot_octopus.zip -d ~/Downloads/" and replace your file path promptly.

  First, plug in the installation medium into your machine.

  You'll want to then run "lsblk", and it's usually gonna be mounted in /dev/sda or /dev/sdb. It looked like this for me.
  
  <img width="396" height="475" alt="image" src="https://github.com/user-attachments/assets/eb3f0f21-0323-4b9d-8359-11c8b482fac7" />

  Now you'll wanna run "sudo dd bs=4M if=/home/YOURUSERNAME/Downloads/shimboot_octopus.bin of=/dev/sda status=progress oflag=sync".

  **MAKE SURE YOU HAVE YOUR FILE PATHS CORRECT, OTHERWISE YOU RISK FORMATTING YOUR MAIN DRIVE.** (You can do this by replacing /dev/sda with the actual installation medium drive node name, and replacing the file path (which is "/home/YOURUSERNAME/Downloads/shimboot_octopus.bin") with the actual file path you downloaded the zip archive to.

  If it went well, it'll output something like this.
  <img width="752" height="171" alt="image" src="https://github.com/user-attachments/assets/17210510-87f3-43b7-8928-771bc87b1c64" />

After that, you'll need to follow the "Booting Instructions". They are later in this file.

## Windows Instructions <sub>(i dont have images for this because im lazy)</sub>
Okay, so first you'll wanna unzip the archive, almost like in the Linux instructions.

First, go to your File Explorer. Then you'll wanna right-click your zip archive and extract it to any folder, so for example the Downloads folder.

Now, the file should end in "bin" and be named something like shimboot_octopus.bin.

Next, the simplest options, launch up Google Chrome. (firefox better all the way)

Then go to the Chrome Web Store, and search "Chromebook Recovery Utility".

Now, install it to Chrome.

Next, connect your USB drive to any available port on your machine.

In the Chromebook Recovery Utility window, click the Gear icon in the corner.

A file explorer window will open. Select the extracted file.

Then, identify your flash drive in the Select menu, and hit Continue.

**Make sure you remember that hitting Continue will COMPLETELY FORMAT AND ERASE THE USB DRIVE.**

# Booting Instructions
In order to boot into your brand new Debian USB, make sure all ports are unplugged from any peripherals. Don't worry, you can plug these right back in after you boot into the USB.

Now, press POWER+ESC+RELOAD (hitting it in this order will prevent a normal reboot)

Once you're there, it'll tell you to insert a recovery USB or SD card. Hit CTRL+D and press ENTER. 

**If you want to cancel, press ESC and Power+Refresh to boot back into ChromeOS. Otherwise, if you're okay with losing all your local files, proceed.**

Now, in the CPS network, it won't let you into Developer Mode right away. However, it will say that "OS verification is OFF" and it will look a little something like this.


<img width="640" height="480" alt="image" src="https://github.com/user-attachments/assets/e33e60f3-3753-418f-a629-848800e56f2b" />


<sub>If you see that black text in the corner that says "Developer mode is disabled..." and "OS verification is OFF", it should have worked. Don't worry, it'll boot just fine even without dev mode. </sub>

Now, insert your USB into the Chromebook.

Then, press POWER+ESC+RELOAD in the exact order. Text will scroll and you'll see options.


<img width="252" height="336" alt="image" src="https://github.com/user-attachments/assets/fd72b015-860b-4a8f-bbed-6c9cfb487054" />


In my case, it says 3 for debian on /dev/sda4. In that case, press 3 and press ENTER.
A bunch of stuff will begin scrolling now.


<img width="384" height="512" alt="IMG_3774" src="https://github.com/user-attachments/assets/e775afad-95b3-4054-b7b8-2abc9c8029eb" />


Eventually, you'll end up right at the login screen.

The credentials are "user" for both the username and password.

Now, assuming you won't know how to use Linux yet, you can use the terminal to do stuff, it comes with Firefox preinstalled, and you can adjust WiFi and display settings at the top bar.

This runs Debian 12 in the XFCE desktop environment, made to be very lightweight on this type of hardware.

For extra security, if you are on a WiFi network managed by your school, install Cloudflare WARP and turn it on. [Click here for installation, and make sure you select Linux](1.1.1.1)

# Booting back into ChromeOS
First, you'll wanna press Power+Reload. This will bring you back to that white screen. 

Now, unplug your USB. 

Next, press ENTER. This will clear all your local data and boot you right back into ChromeOS.

Then, connect to your WiFi. This can be either your home network or a CPS network if, by some miracle, you have the password.

This will now re-enroll your device. It will usually automatically enroll your Chromebook, but if for some reason it fails and doesn't, just do the manual enrollment, and when it gives you text fields for serial numbers and stuff, just leave them how they are because they are usually gonna be correct and match your device.

Now, if you didn't manually enroll, you must log in to your CPS account.


<img width="252" height="336" alt="IMG_3775" src="https://github.com/user-attachments/assets/6dc1c139-6fa4-4598-b366-e0cdeadc6ed5" />


And now you're good to go! Of course, switching won't be seamless, but it'll be good enough to bypass pretty much everything. (Man this would have been good in 2020)
