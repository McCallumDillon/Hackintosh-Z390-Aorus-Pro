## OpenCore 0.6.4 z390, 9700k, Vega 64 Hackintosh
The build at a high-level: Gigabyte z390 pro, i9 9700k, Vega 64, 32gb 3200mhz, 970 plus NVMe

_________________________________

Hardware Specifics for this build: 
```
[CPU][Intel Core i7-9700K 3.6 GHz 8-Core Processor]
[CPU Cooler][Corsair H115i PRO 55.4 CFM Liquid CPU Cooler]
[Motherboard][Gigabyte Z390 AORUS PRO WIFI ATX LGA1151 Motherboard]
[Memory][Corsair Vengeance LPX 32 GB (2 x 16 GB) DDR4-3200 CL16 Memory]
[Storage][Samsung 860 Evo 500 GB 2.5" Solid State Drive]
[Storage][Samsung 970 Evo Plus 1 TB M.2-2280 NVME Solid State Drive]
[Storage][Samsung 970 Evo Plus 1 TB M.2-2280 NVME Solid State Drive] [Windows dedicated]
[Video Card][Sapphire Radeon RX VEGA 64 8 GB Video Card]
[Case][NZXT H510i ATX Mid Tower Case]
[Power Supply][EVGA G3 750 W 80+ Gold Certified Fully Modular ATX Power Supply]
[Wireless Network Adapter][ASUS AC68 ac1900]
[Monitor][Samsung 890 LC34H890WGNXGO 34.0" 3440x1440 100 Hz Monitor]
[Custom][Gigabyte GC-Titan Ridge]
```
_________________________________

I have had Clover 5122 running Catalina stable for over a year now, but decided to give OpenCore 0.6.4 a go with BigSur.

## Status
I'm not a seasoned expert on this sort of thing, but I followed the Dortania guide– manually created my own SSDTs, etc. and a this point have a solid OSX 11.1 running off of OpenCore 0.6.4 with iservices, sound (via Titan-ridge to Clarett2Pre thunderbolt controller), FileVault, etc all working.

I hope this repo serves to help others in the future.

_________________________________

## Bios
My z390 Pro is running bios F12 with CFG Lock disabled. 
XHCI Handoff = Enabled
Serial Port = Disabled
X.M.P. Profile = 1

## GC-Titan Ridge Thunderbolt Contoller
Getting Titan Ridge to work initially was a pain on my older Clover/Catalina installation, but it helped sort some kinks. After following the proper installation and recommended bios options there was a key setting in the bios for enabling power to the card on boot– I can't remember what it is called exactly, but it is in the thunderbolt specific configuration settings. 

From there, strange as it sounds, I had to actually boot into Windows to initialize the card before it would work in OSX. If others ares struggling like I was– try this.