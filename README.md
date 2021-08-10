

# **Dell Latitude 5570 Hackintosh(OpenCore)**

## **1. Introduction**
-   macOS: Big Sur 11.2.1
-   OpenCore: 0.6.6 <br/>
**The New Update**
- macOS: Monterey 12 beta 4
- OpenCore 0.7.1

<img src="https://github.com/manhhungdoan/hackintosh/blob/main/Screen%20Shot.png">

### **My Hardware**
<table>
<tr>
    <td><strong>Model</td>
    <td>Dell E5570</td>
</tr>
<tr>
    <td><strong>Processor</td>
    <td>Intel Core i7-6820HQ</td>
</tr>
	<tr>
		<td><strong>Graphics</strong></td>
		<td>Intel HD Graphics 530/ AMD R7 370</td>
	</tr>
	<tr>
		<td><strong>Memory</strong></td>
		<td>8GB 2400MHz DDR4 SODIMM</td>
	</tr>
	<tr>
		<td><strong>Dispay</strong></td>
		<td>15.6" FHD with <strong>Touchscreen</strong></td>
	</tr>
	<tr>
		<td><strong>WLAN + Bluetooth</strong></td>
		<td>Intel Dual Band Wireless-AC 8260</td>
	</tr>
	<tr>
		<td><strong>Camera</strong></td>
		<td>Integrated Camera</td>
	</tr>
	<tr>
		<td><strong>Soundcard</strong></td>
		<td>Realtek ALC293</td>
	</tr>
</table>

## **2. Status**
  ### **What's working**
  - [x] Shutdown/ Reboot/ Sleep/ Wake
  - [x] Intel HD 530 Graphics and Touchscreen 
  - [x] WiFi & Blutooth
   - [x] Intel Gigabit Ethernet
  - [x] Keyboard and Trackpad (two finger vertical swipes)
  - [x] Internal camera
  - [x] All USB ports
  - [x] SD Card Reader
  - [x] HDMI working (If not working. You try sleeping it before plugging in the HDMI cable)
  - [x] Speakers and Headphones jack
  ### **What's not working**
  - [ ] Multitouch gestures for Touchpad
  - [ ] AMD R7 370
 
## 4. Installation
### Create the USB and Install macOS
- Follow the [guide on the OpenCore documentation](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) to create a USB
-  Replace the Clover folder in the EFI partition with the contents of  my `EFI`
- Press F12 and boot the USB on your Latitude E5570 and install Mac OS on your laptop

### Edit EFI and Config File
- NOT HAVE VGA
	- Delete Child related to `SSDT-Disable-DGPU.aml` in` Root> ACPI> add` in config.plist
	- Delete `SSDT-Disable-DGPU.aml` in ACPI folder
- NOT HAVE TOUCHSCREEN
	-  Delete the Child related to `VoodooI2C`,`VoodooI2CHID` in `Root> Kernel> add`in config.plist
	- Delete `VoodooI2C.kext`,  `VoodooI2CHID.kext` in Kexts folder

## 5. Post Installation
### Booting without USB
- You need to plug in the installation USB created previously everytime you start macOS after shutdown. If you want to boot without the USB, follow [this guide by OpenCore](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb)

### Fixing iServices
- In order to get Apple Services like App Store working, you need to generate your own SMBIOS (The included one is only for reference)
- For more information on how to do that, visit the  [Dortania Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial)

### Fix keyboard shortcuts
- Download and install  [Karabiner Elements](https://pqrs.org/osx/karabiner/)
-   Download  `karabiner.json` found in repository
-   Copy `karabiner.json` to `~/.config/Karabiner`
-   You can now use F11 & F12 for brightness

### Get smooth scrolling
-   Download and install  [MOS](https://mos.caldis.me/)

## 4. Credits
- [Acidanthera](https://github.com/acidanthera)  for OpenCore, Lilu and related kexts.
-   [OpenIntelWireless](https://github.com/OpenIntelWireless)  and others whose kexts I've used.
-   [Dortania](https://dortania.github.io/)  for installation and other guides.
-   Everyone else who contributed to this repository directly/indirectly.

# > Thanks for reading. Good luck installing.
