## Hackintosh: [OpenCore] {Big Sur} Gigabyte Z390 Aorus Pro, i7 9700k, Vega 64, 32gb 3200mhz, WD SN850
The build at a high-level: Gigabyte Z390 Aorus Pro, i7 9700k, Vega 64, 32gb 3200mhz, WD SN850 NVMe

_________________________________

Hardware Specifics for this build: 
```
[CPU][Intel Core i7-9700K 3.6 GHz 8-Core Processor]
[CPU Cooler][Corsair H115i PRO 55.4 CFM Liquid CPU Cooler]
[Motherboard][Gigabyte Z390 AORUS PRO WIFI ATX LGA1151 Motherboard]
[Memory][Corsair Vengeance LPX 32 GB (2 x 16 GB) DDR4-3200 CL16 Memory]
[Storage][Western Digitial SN850 1 TB NVME] {OSX: Big Sur} 
[Storage][Samsung 970 Evo Plus 1 TB M.2-2280 NVME Solid State Drive] {Windows dedicated}
[Storage][Seagate Exos 7E8 8TB 3.5 Inch 6Gb/s 7200 RPM 256 MB Drive]
[Storage][Seagate Exos 7E8 8TB 3.5 Inch 6Gb/s 7200 RPM 256 MB Drive]
[Storage][Seagate Exos 7E8 8TB 3.5 Inch 6Gb/s 7200 RPM 256 MB Drive]
[Storage][Seagate Exos 7E8 8TB 3.5 Inch 6Gb/s 7200 RPM 256 MB Drive]
[Video Card][Sapphire Radeon RX VEGA 64 8 GB Video Card]
[Case][NZXT H510i ATX Mid Tower Case]
[Power Supply][EVGA G3 750 W 80+ Gold Certified Fully Modular ATX Power Supply]
[Wireless Network Adapter][ASUS AC68 ac1900]
[Monitor][Samsung 890 LC34H890WGNXGO 34.0" 3440x1440 100 Hz Monitor]
[Custom][Gigabyte GC-Titan Ridge Thunderbolt Controller]
```
_________________________________

I have had Clover 5122 running Catalina stable for over a year now, but decided to give OpenCore a go with the BigSur update to OSX.

## Status
I'm not a an expert here, but most of the time can stumble my way through things. Strickly following the Dortania guide– manually creating my own SSDTs, USB Mapping, etc, etc and finally at this point I have OSX 11.1 running pretty solid with OpenCore 0.6.5. iServices, sound (via Titan-ridge to Clarett2Pre thunderbolt controller), etc all working great. Waking from sleep seemed to give me some issues initially– after re-USB-mapping it seems to be okay now.

I hope this repo serves to help others in the future– for myself, the Z390 Pro fought me a lot in the beginning, so hopefully this helps surface some answers and/or save you some time.

_________________________________

## Bios
My z390 Pro is running bios F12 with CFG Lock disabled. 
XHCI Handoff = Enabled
Serial Port = Disabled
X.M.P. Profile = 1

## GC-Titan Ridge Thunderbolt Contoller
Getting Titan Ridge to work initially was a pain on my older Clover/Catalina installation, but it helped sort some kinks. After following the proper installation and recommended bios options there was a key setting in the bios for enabling power to the card on boot– I can't remember what it is called exactly, but it is in the thunderbolt specific configuration settings. 

From there, strange as it sounds, you actually have to boot into Windows to initialize the card before it would work in OSX. It has to do a power-saving feature in the controller. There is/are some ACPI work arounds that I didn't mess with. If others ares struggling like I was– try this. Further reading on this subject here: https://osy.gitbook.io/hac-mini-guide/details/thunderbolt-3-fix/ 

## Misc
Noteworthy mentions: 

Samsung 970 Evo Plus 1 TB NVME drives: Originally I had two installed on this machine– one for Windows, one for OSX. I had issues getting OSX to boot with the dual boot setup/nature of this configuration. They were both updated to the latest firmware (as I'm told that is a critical piece to gettin those drives to work), but I still couldn't get it to play nicely and boot. I was able to install Big Sur, but upon reboot couldn't reach the desktop. I used it as an excuse to try a different drive and the newer/faster Western Digital SN850 1tb which worked right away without any issues. I'm still not sure what the deal there was as I've seen others online using the 970 Evo Plus drives without issue. Either-way– no longer and issue in my case.

Sleep woes and USB Mapping fixes: In my setup motherboard connector F_USB1 is being used for my the AIO water cooler (Corsair H115i h2o cooler) which I'm told can conflict with sleep functionality (more on this: https://www.tonymacx86.com/threads/corsair-hydro-h100i-v2.194193/). Additionally, from what I've read, so can ITE Device 8595 which registers when you're creating the USB Map– from my hunt some suggest ITE Device 8595 controlls RGB lighting on the board. Another person's build suggested desginating these both as USB 2.0 drivers fixed their issues. In MY USB Mapping I have disabled BOTH ports 11 (F_USB1 or in my case the H115i) as well as 12 (ITE Device 8595). This doesn't seem to have any affect on functionality– water cooler is oppertating properly and you can't control RGB within the hackintosh anyway so that isn't a concern here.
There ARE other work-arounds for the H100 series coolers plugged into F_USB1 such as: https://www.insanelymac.com/forum/topic/339980-audiogods-aorus-z390-pro-patched-dsdt-mini-guide-and-discussion/?do=findComment&comment=2686894 

Some other decent Z390 Auros Pro builds & references:
https://www.insanelymac.com/forum/topic/339980-audiogods-aorus-z390-pro-patched-dsdt-mini-guide-and-discussion/
https://www.tonymacx86.com/threads/n-z-xtmac-pro-i9-9900k-gigabyte-aorus-z390-pro-macos-mojave-sapphire-vega-64-reference.267090/
https://github.com/blacklizard/gigabyte-z390-aorus-pro-wifi-hackintosh (a detailed guide, but note this is the Pro WIFI version- not standard Pro (no WIFI).

## Cheers!
:)
