# Readme

## Intro
- This project is about making an auto-play 4k video loop on Raspberry Pi 4 at start-up. Which means, when you start a Raspberry Pi 4 or reboot it, a 4k video will be automnatically play. 
- It would be used for testing.

## Prerequisites
### What will you need
*Hardware
- A Raspberry Pi computer with an SD card or micro SD card
- A monitor with a cable (and, if needed, an HDMI adaptor)
- A USB keyboard and mouse
- A power supply
- A screen with max resolution is 4k

*Solfware
- Raspberry Pi OS
- VLC media player
- Putty if you want to connect with your RPI with SSH (optional)

## Set-up 
### Set up for Raspberry Pi 4
If you are new to Raspberry Pi, you should visit Getting started with Raspberry PI (https://projects.raspberrypi.org/en/projects/raspberry-pi-getting-started)

### Install VLC media player
1. Before we go ahead and install VLC, we must first ensure our RPI is entirely up to date.
#### Terminal $
    sudo apt update
    sudo apt upgrade
2. Next, we can now proceed to install VLC. Luckily for us, VLC is available within the Raspbian operating systems package repository.
#### Terminal $
    sudo apt install -y vlc
3. With that done, VLC should now be successfully installed to your Raspberry Pi. It will now be ready for whenever you want to watch something.

## How to do it
### 1. Start making a loop of a random video
* You can do it with a several code in command line of Terminal
- Play a video with VLC by using Terminal:
#### Terminal $
    vlc /path/to/video
- Replace path/to/video to the main PATH to your video
- Repeat that video:
#### Terminal $
    vlc -R /path/to/video

### 2. Setting a screen resolution to 4K (optional)
- While on the desktop interface of your Raspberry Pi, click the icon in the top-left hand corner of the screen.
![image](https://user-images.githubusercontent.com/80090701/110094503-7aafab00-7dce-11eb-8101-1196eb4c0451.png)
- Within the start menu, hover over “Preferences“. Then click “Screen Configuration” to load the tool that we are after.
![image](https://user-images.githubusercontent.com/80090701/110094582-9024d500-7dce-11eb-9a05-bba2ce12e4b8.png)
- With the tool loaded on our Raspberry  Pi, we can use it to change the resolution.
* First, you need to right-click the display that you want to modify the resolution of (1.).
* Next, hover over “Resolution” (2.).
* Hovering over this will show you a selection of resolutions you can set for this current display. To select a resolution, click the one you want (3.)
* Once you have chosen the resolution that you wish to use, you need to apply it by clicking the green tick button (4.)
![image](https://user-images.githubusercontent.com/80090701/110094759-c19da080-7dce-11eb-9a33-dcc594975726.png)
- To confirm this change, you will need to click the “OK” button within 10 seconds.
![image](https://user-images.githubusercontent.com/80090701/110094821-d4b07080-7dce-11eb-9a85-078ed0961175.png)

### 3. Make a bash script
- Move to the new folder
- Right-click and click "New File". Rename the file to whaterver you want. I have named it 'test_loop_4k.sh'
- You can edit it with a "Text Editor" like:
#### bash
    #!/bin/bash
    
    vlc -R path/to/video
    
### 4. Make that script executable
#### Terminal $
    chmod +x /path/to/script/nameofscript.sh

### 5. Execute a script
#### Terminal $
    cd /path/to/script # Change to your script folder
    sudo ./nameofscript.sh

#### RESULT 
You can see a video loop when execute bash script

### 6. Make a script auto-run when start-up
There are many ways to make a program or a scipt auto-run when start-up.
The way below is in my case.
#### Terminal $
    sudo nano /home/pi/.bashrc
- Add 2 lines at the end of the GNU nano you haved opened
#### GNU nano
    echo run at boot
    bash /path/to/your/script/nameofscript.sh
- Use Ctrl+O and Ctrl+X to save and exit.

### 7. See your result
-You can reboot your RPI to see what happened.
#### Teminal $
    sudo reboot
    
## Adding Contributions
If you want to contribute to my project, just make a 'pull request'


## References
1. https://projects.raspberrypi.org/en/projects/raspberry-pi-getting-started
2. https://pimylifeup.com/raspberry-pi-screen-resolution/#:~:text=With%20the%20tool%20loaded%20on,set%20for%20this%20current%20display.
3. https://askubuntu.com/questions/228304/how-do-i-run-a-script-at-start-up
4. https://www.raspberrypi.org/documentation/usage/video/
5. https://wiki.videolan.org/VLC_command-line_help
