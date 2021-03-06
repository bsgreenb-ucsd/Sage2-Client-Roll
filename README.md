# Sage2-Client-Roll
Display Client Roll for Sage2 

##Description  

This roll will install ffmpeg and the Google Chrome browser on display tile nodes. [Sage2](http://sage2.sagecommons.org/) recommends Google Chrome over firefox for display clients. Instead of directly building google chrome from source, this roll uses the script from [Richard Lloyd](http://chrome.richardlloyd.org.uk/) to install the latest version of google chrome instead. 

It is expected you have already installed the proper video drivers (such as the cuda roll for Nvidia GPUs) on your display nodes so the they have have video output for the display wall.

##Building and Installing

In the main folder of the roll:

Run bootstrap.sh with root permissions to get the needed dependencies to build the roll:

	# ./bootstrap.sh

Build the roll using: 
		
	# make roll 2>&1 | tee make.log 
  	
If successful, this will build a .iso file called ''Sage2Client-*.disk1.iso''. 

**Installation**
	
To install on a node, execute: 
	
	# rocks add roll *.iso
	# rocks enable roll Sage2Client
	# (cd /export/rocks/install; rocks create distro)
	# rocks run roll Sage2Client | bash
	
Then reinstall on the node you want to have the sage server on:
	
	# rocks set host boot compute-X-Y action=install
	# rocks run host compute-X-Y reboot
	
**What is Installed** 

* /opt/ffmpeg : The main ffmpeg executables and libraries
* /opt/x264, /opt/lame, /opt/libtheora, /opt/libvorbis, /opt/libwebp: Dependencies for ffmpeg
* /usr/bin/google-chrome: The google chrome browser 

**How to Use**

The [Sage2-Roll](https://github.com/bsgreenb-ucsd/Sage2-Roll) repo's readme has instructions in how to use this roll in conjuction with the Sage2 server to make a fully functional Sage2 based display wall. In addition it gives a basic description on how to use the display wall. 


