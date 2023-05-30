# Dell Latitude 5590 Hackintosh

This is the magic I used to get macOS Monterey running on the Dell Latitude 5590 laptop. Opencore bootloader is used to achieve this.

**What Works?**

- Keyboard
- Trackpad and buttons
- Graphics acceleration  
- All video ports (HDMI, VGA, USB-C)
- Battery readout (with SMCbatterymanager kext)
- USB ports (Including all USB-C port functions)
- Built in audio (headphone jack and laptop speakers)
- Built-in card reader (PCI device, Realtek Card Reader Kext)  
- Ethernet
- Intel 8265 wifi and bluetooth (Note: Airdrop is not supported with this card)   
- Brightness control (and all brightness keys)
- Sleep (With Lid, Menu, and power button)
- Webcam  
- Headphone jack line in
- Built in Microphone
- Fan control and sensor readouts (SMCDellSensors)


**Not working**  
- Airdrop and selected continuity features (WIFI card would need to be replaced)

-------------------------------------------  

**Notes**:  
- PLEASE DO NOT USE THIS EFI IF YOU DO NOT UNDERSTAND WHAT IT IS OR HOW IT WORKS. I'M NOT RESPONSIBLE FOR ANY ISSUES CAUSED BY USING THIS EFI.

- Included opencore version is 0.9.2. It was tested with macOS Monterey.

- You will need to add your own smbios BEFORE USING. Follow the opencore guide for more info. I used MacBookPro15,4. (important!) https://dortania.github.io

- You will also need to compile your own SSDT-EC (precompiled does not seem to work as well). Use SSDTTIME to do this. (included)  

- You must understand how opencore is configured before downloading.  (important!)  

- Brightness Keys require a special SSDT to load. This patches the BRT6 method of the firmware to notify macOS of brightness events. The NOTIFY code is specific to every laptop model and can be found using evtest (when booted into linux) on the primary keyboard and pressing the brightness keys.

- Any BRT6 patch must be loaded before SSDT-XOSI. ACPI load order can be defined in your config.plist.

- The included EFI folder contains opencore 0.9.2 with all SSDTs, kexts, and drivers. The resources folder is missing which only matters if you would like a graphical selection screen.   https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html. Add these to your EFI folder after making the appropriate changes to the config plist (mainly fixing the smbios) to use.
----------------------

**Specs**  

**CPU**     Intel Kaby lake -r i7-8650u  
**GPU**     Intel UHD graphics 620  
**RAM**     16GB DDR4-2400 ram 
**SSD**     Seagate baraccuda P5 500GB NVME SSD 
**WIFI**    Intel AC8265 m.2 wifi  
**Ethernet** Intel i219-LM PCI Express Gigabit Ethernet Controller   
**Audio**   Realtek ALC3246 HD audio and Intel Sunrise point HDMI audio   
**Input**  PS/2 Keyboard and Trackpad Buttons, Alps I2C Trackpad 
**Webcam**   Embedded USB webcam (built-in)  
**Screen**   15-inch screen, 1920x1080  
**BIOS**  Bios revision 1.27 (Latest) 
 

**Credits**
- Apple for macOS
- The OpenIntelWireless team for AirportItlwm
- CorpNewt for Propertree and Ssdttime
- Khronokernel and all contributors for the awesome dortania opencore guides
- Acidanthera and all contributors for Opencore
