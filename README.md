# macOSVirtualbox

got from : https://github.com/myspaghetti/macos-virtualbox

to use on windows cygwin: 
- start cygwin
- clone the repo
- use dos2unix on the sh file
- lauch the sh


To install guestExtension (copy paste from host etc) : 

    - In the guest Mac, open the Terminal and go for a reboot on the Recovery partition

        sudo nvram "recovery-boot-mode=unused"
        sudo reboot
  
    - Now you're in Recovery mode, enter the Terminal and do:
    
        csrutil disable
        sudo spctl kext-consent add VB5E2TV963
        nvram -d recovery-boot-mode
        reboot
        
    - Back in "normal" mode, open the Terminal, and do:
    
        sudo mount -uw /
        sudo chown :admin /System/Library/Extensions/
        sudo chmod 775 /System/Library/Extensions/
        Run the Guest Additions installer and go through the end (in principle, it goes through successfully)

    - Now in the terminal, do:

      sudo chown :wheel /System/Library/Extensions/
      sudo chmod 755 /System/Library/Extensions/
      sudo nvram "recovery-boot-mode=unused"
      sudo reboot

    - Again in Recovery mode, go into the Terminal and do:

        csrutil enable
        nvram -d recovery-boot-mode
        reboot

You should be set.

got solution for guestAddiction from : https://stackoverflow.com/questions/41691803/how-to-install-guest-addition-in-mac-os-as-guest-and-windows-machine-as-host

For full screen mode : 
cd "C:\Program Files\Oracle\Virtualbox"
VBoxManage setextradata “Your Virtual Machine Name” VBoxInternal2/EfiGraphicsResolution X

Where X can be one of 1280x720, 1920x1080, 2048x1080, 2560x1440, 3840x2160, 1280x800, 1280x1024, 1440x900, 1600x900
