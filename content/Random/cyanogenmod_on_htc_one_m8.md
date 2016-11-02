Title: Putting Cyanogenmod on HTC One M8  
Date: 2016-10-24 08:30   
Category: Random   
Tags: random, phone  
Slug: cyanogenod_htc_one_m8   
Authors: Ned  
Summary: 


My HTC One M8 was starting to get a little laggy, so I thought I'd fiddle around with some custom ROMs to try and get things running more smoothly. 

There are plenty of guides for installing Cyanogenmod dotted around the internet ([this](http://www.techradar.com/how-to/phone-and-communications/mobile-phones/how-to-install-cyanogenmod-13-on-your-android-phone-1321093) one was particularly useful), but I encountered a few problems that are worth noting down - especially because I know I won't remember how I did any of this in a few weeks time!

Here's my recipe (using a Mac):

1. Install [Android Studio](https://developer.android.com/studio/index.html), and get the most recent SDK (you'll be prompted to download it the first time you open the application).

2. Add the `platform-tools` directory to your `$PATH` variable. This allows you to use the command line tools we need later on:
	
		echo 'export PATH=$PATH:'$HOME'/Library/Android/sdk/platform-tools' >> ~/.bash_profile
		
3. Enable USB debugging on your phone.

4. Unlock the phone:
	* First start the bootloader: `adb reboot bootloader`
	* Note that `fastboot oem unlock` won't work with HTC devices - you need to get the unlock authorisation code.
	* Get the identifier token: `fastboot oem get_identifier_token`
	* Copy and paste this to the HTC dev website [here](http://www.htcdev.com/bootloader/unlock-instructions/page-2) (you will need to create an account).
	* You will be sent an `Unlock_code.bin` by email. Then run `fastboot flash unlocktoken <path_to_Unlock_code.bin>`.
	* Select Yes using the volume keys and the power button.
	* The phone will restart with an unlocked bootloader.

5. Enable USB debugging agagin.

6. Install TWRP (a 'recovery' that is used for installing custom software). Download the .img from [here](https://twrp.me/Devices/).  

   Go back to the bootloader: `adb reboot bootloader`.  
   
   Then run `fastboot flash recovery path_to_downloaded_twrp.img`.  
   
   Running `adb reboot recovery` will now open TWRP.

7. Find the [Cyanogenmod](http://get.cm/?device=m8&type=snapshot) version you would like (Latest Release is probably the recommended one to go for) and download it.

8. Put it on your phone: `adb push path_to_cyanogenmod.zip /sdcard/`

9. Within TWRP, click install, then select the .zip you've just transferred. When you reboot your phone, it will now have Cyanogenomd on it. Yay!

10. Cyanogenmod doesn't come with any Google apps. To install these (Gmail, Google Maps, Calendar etc etc), you'll need [Open GApps](http://opengapps.org/). Download the options you want (to avoid running out of memory, I would recommend the 'nano' variant which installs just the Play store, then you install the rest manually). Then run:

		adb push path_to_gapps.zip /sdcard/
		
11. Then re-enable USB debugging (last time!) and go back into recovery mode (`adb reboot recovery`), hit Install, and now select the GApps .zip. 

12. You're all finished! Sit back and have a nice cuppa tea.
   

 
	