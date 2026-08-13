# Zte MF286R (A1 ISP Firmware) 💻
This repo contains Zte MF286R Firmware, specifically from Croatian ISP "A1"<br>
<br>
<img src="repo_img/img1.jpg">
<img src="repo_img/img8.jpg"><br>
<br>
Software version: CR_A1TKHRMF286RV1.0.0B08<br>
Hardware version: MF286R-1.0 (this one is without the battery)<br>
<br>
This is the latest firmware as of 29.7.2026.<br>
It was developed somewhere in 2022 judging by the copyright date...<br><br>
Me, and many other people on various forums think that this is the latest firmware that's going to come out by A1 Croatia, since they got new routers to offer... 😭<br>
<br>
<img src="repo_img/img2.png">
<img src="repo_img/img6.jpg">
<br>
## Why have I dumped it? ❔
I wanted to change the firmware, and I noticed that the original firmware, like many other isp's firmware, was not dumped...
<br>
## Why did I want to change the firmware? ❔
With ~~retarded~~ oversimplified firmware A1 provided, you cant change much settings...<br>
With OpenWrt firmware you could add much more functionality and settings...<br>
<br>
Another huge contributing factor was that A1 can spy and modify your router at any time with TR069 💀<br>
(it phones home every 3 minutes, 24/7)
<br>
<img src="repo_img/img7.jpg">
<br>
## Dumping process ☣️
### Disassembling the router 🪛
There are small differences between MF286R routers (each isp customized their one's).<br>
Some have battery's (like ex Tele2 routers, now Telemach), some have different pcb's...<br>
<br>
<img src="repo_img/img3.jpg"><img src="repo_img/img4.jpg"><img src="repo_img/img5.jpg">
<br>
### Soldering UART wires 🧨
To communicate with the router, we need a [CP2102 USB to UART adapter (serial TTL)](https://www.aliexpress.com/item/1005008880984585.html) (its very cheap, even after eu taxes)<br><br>
<img src="repo_img/img9.PNG"><br><br>
I had some spare longer wires (you just need 3; TX RX GND), and soldered them using this [refrence](https://openwrt.org/_media/media/zte/mf286d/mf286d-serial-console.jpg)...<br><br>
<img src="repo_img/img10.jpg"><br><br>
After soldering I recommend to hot/super glue it a bit to secure it in place...<br><br>
<img src="repo_img/img11.jpg"><br><br>
I placed my wires through the empty battery pins place on the plastic shell...<br><br>
<img src="repo_img/img12.jpg"><br><br>
Now I got easy access to the UART cables, just pop off one panel 😭<br>
I also recommend to put a small sticker to label your wires...
<br>
### Dumping the firmware 😠
Connect everything (tx on rx, rx on tx, usb to pc...), install [(those drivers if on windows)](https://www.pololu.com/docs/0j7/all).<br><br>
<img src="repo_img/img13.PNG"><img src="repo_img/img14.jpg"><br><br>
Check COM port number for the CP2102 adapter.><br><br>
<img src="repo_img/img15.PNG">
Enter the COM number into putty, bitrate 115200, press ok
img15
Connect a max 4gb usb stick, formatted with FAT to the router...
img16 img17
Power up the router, you will see bootlogs. Wait for them to finish appearing. And press enter.
img18
type this command to list partitions:!!!!!!!!!!!!!!!!!!!! and enter
img19
type this command to copy over the parititons!!!, press enter a couple of times so when admin@(none):~# appears you know that it finished uploading
img21
type this command to safely remove the usb stick from the router
mg22
Wala, you got all of your partitons (firmware), copy it over somewhere safe!
img
<br>
## Where can I download the firmware, and see the boot logs? ❔
Check the release section on this repo, or follow this [link](https://github.com/TheLocalFemboyy/Zte_MF286R-A1_Isp_Firmware/releases/tag/Firmware).
## Thanks! 💌
Huge shout out to guys at [OpenWrt](https://openwrt.org/) for making custom firmware for this bad boy.<br>
The firmware was extracted using specific steps using a [guide](https://openwrt.org/toh/zte/mf286r) they made... (Step 1; Method 1, Step 2; Method 2)<br>
