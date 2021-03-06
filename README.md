# Hackintosh USB-Installer using Linux    

  ### Supported macOS versions
  - High Sierra 10.13.x
  - Mojave 10.14.x
  - Catalina 10.15.x
  

**For OpenCore EFI installers**   
  Use tribeam.sh script           
  ***https://github.com/Broly1/tribeam***
    
   **GibMacOS + finalflash.sh**   
   Alternativelly if you prefere to use GibMacOS instead of ``tribeam.sh`` 
   you can use ``finalflash.sh`` script which will use either      
   the Recovery.pkg or the BaseSystem.dmg, just drop it inside GibMacOS after downloading the desired  
   version of macOS and run it from there fallowing the prompt.    
   ***https://github.com/Broly1/finalflash*** 
   <img src="pict/final.png" width=700>
        
### For manual instalation read this.
### Tools you'll need :
 GNOME Disks is a graphical front-end for udisks included in the "gnome-disk-utility" package.  
 GParted is a free partition editor for graphically managing your disk partitions.  
 DMG2IMG comand line tool that allows you to convert a (compressed) Apple Disk Images  
 gibMacOS - An awesome tool from CorpNewt ( https://github.com/corpnewt/gibMacOS )   
 A USB drive 8gb+  
 Some patience...
  

  ### Get macOS Installer with gibMacOS  
  Downloading the installer files fairly straight forward process but may take a while depending on your internet speeds.  
  To start extract gibMacOS and and open your terminal change directory to the gibmacos.command script.  
  Run it with `./gibMacOS.command `   
  ***This will allow you to choose the macOS version to download.*** 
  <img src="pict/2019-09-11_12-41.png" width=700>  

  In my case I chose option 1. It will download the macOS installer files.  
  Make sure that BaseSystem.dmg is downloaded completely thats what we will use to create the installer  
  Once downloaded you can proceed to the next step.  
  ### Creating the macOS Install USB  
  Find BaseSystem.dmg inside `/gibMacOS-master/macOS\ Downloads/publicrelease/`  
  Drag it to your desktop or somewhere else if you prefer.  
  Open your terminal and change directory to where the BaseSystem.dmg file is in my case:  
  `cd Desktop`  
  Then run `dmg2img BaseSystem.dmg base.iso` it will convert the the `dmg` file to `iso` file named `base.iso`  
  Open `Disks` AKA "Gnome-Disk-Disk-Utility" and drag `base.iso` to it and hit start restoring.
  This will take a wile.  
  <img src="pict/2019-09-11_12-54.png" width=700>  
 
  Once it is done restoring the iso open up `Gparted` and select your usb-drive.  
  <img src="pict/2019-09-11_11-39.png" width=700>  
  
 
  Rigth click in the unallocated space hit new      
  <img src="pict/novo.png" width=700>   
  
  In File system select `fat32` and in lable type `EFI`  
   <img src="pict/novo2.png" width=700>  
   
   Hit apply     
   <img src="pict/novo6.png" width=700>  
     
   Once done applying changes righ click on your new EFI partition and hit `Manage Flags`  
   <img src="pict/novo7.png" width=700>   
     
   Select boot and esp  
   <img src="pict/novo9.png" width=700>      
      
   ***Now whe need to mount the EFI partition***  
   The easiest way is to open up `Disks` again and mount it that way     
   <img src="pict/novo8.png" width=700>    
      
   Now you should see an empty EFI partition in your file system  
       
   <img src="pict/2019-09-11_12-19.png" width=700>  
   
   ### For OpenCore  
   
   ***Download OpenCore-x.x.x-RELEASE.zip***      
   https://github.com/acidanthera/OpenCorePkg/releases  
   Extract it and drop OpenCore EFI folder in the EFI partition we just created  
   and fallow the OpenCore Vanilla Guide.      
   https://dortania.github.io/OpenCore-Desktop-Guide/     
   
   ### For Clover       
   ***Download CloverISO-xx.tar.lzma***      
      https://github.com/CloverHackyColor/CloverBootloader/releases  
   Extract it then extract the iso as well and copy the EFI folder to the empty EFI partition    
   <img src="pict/2019-09-11_12-26.png" width=700>  
        
   ### Drivers  
   Now open EFI/CLOVER/drivers/UEFI and all we need there are:    
   ApfsDriverLoader.efi AptioMemoryFix.efi HFSPlus.efi    
   <img src="pict/2019-09-11_12-28.png" width=700>
        
        
   ### Kexts  
        
   Now download your kexts here:    
   https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23    
   Place your kexts in /EFI/CLOVER/kexts/other   
   To know what kexts you need check this link:    
        https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/gathering-kexts  
        
   ***This is how my kexts folder looks like***    
   <img src="pict/2019-09-11_12-31.png" width=700>     
        
   You should have a sample `config.plist` inside /EFI/CLOVER remove it.  
    If on amd cpu get your sample config.plist here:  
        https://github.com/AMD-OSX/AMD_Vanilla  
        
   If on Intel cpu you can get a sample here:  
   https://github.com/corpnewt/Hackintosh-Guide   
        
   ***Make sure to learn the basics of config.plist***  
   https://github.com/corpnewt/Hackintosh-Guide/blob/master/config.plist-basics.md  

  This shoud be enough to boot into the installer GOOD Luck!!  

        
   ## Credits to:
   **CorpNewt algrey Hackintosh Slav and many others**        
