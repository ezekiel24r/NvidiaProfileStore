# VR Settings Guide for MSFS2020 with RTX 3070 & Quest 3 Link Cable

This was orignially a reddit post but reddit did not like me posting image links.

Keep in mind, tuning for VR is extremely dependent on your GPU, CPU, and potentially other system hardware. So this config may only work for systems very similar to mine, and also dependent on the versions on all the software versions I will list. Also, I'm sure there are tons of settings in here that are inconsequential/redundant but I want to capture everything. My goal with configuring my system was to get the cockpit readable with good performance. This is just a starting point, feel free to up terrain LOD, object LOD, and Buldings and Trees to Medium if you have a good baseline.

My System Info (yours doesn't have to match, this is just for reference)

**Hardware**

- MB: Z790 GAMING PRO WIFI
	- Latest Bios Firmware
- CPU: Intel i7-14700K, 3400 Mhz
	- Intel XTU is able to benchmark to ~5200Mhz at max temps though
- GPU: Gigabyte RTX 3070 8GB VRAM
	- Using MSI Afterburner with auto core clock curve and a temp limit of 83C
- RAM: 64GB of DDR5 7000 RAM (4x16)
	- Not using XMP in bios, might try it out later
- Oculus Quest 3 with official link cable

**Software**

- Windows 11 Version 10.0.22631 Build 22631
- Nvidia Game Ready Driver 551.52 (and Enabled Experimental Features)
- Meta Link App Version 62.0.0.235.346 (Opted out of Public Test Channel)
- Oculus Debug Tool Version 62.0.0.235.346
- Oculus Tray Tool 0.87.8.0
- OpenXR Toolkit Companion App v1.3.2

Alright here comes the wall of text:

First things first, **create a system restore point before you change all this stuff incase something goes wrong.**

**Bios settings**

- Check to make sure Resizable Bar is enabled

- Overclocking settings to your preference
	- My computer by default already enabled intel's turbo boost technology, which allows the OS to do a substantial overclock. You can see this happening in the Intel XTU tool if you do the stress test.
 	- **Advanced:** The setting CPU Lite Load can help undervolt your CPU which can reduce the thermal output of the CPI. Mine is set to 3, but you might need to find the right setting for your PC because low values can cause applications to crash and also blue screen your PC.

**Windows Settings**

- Disable Hardware-accelerated GPU scheduling
- Turn on Variable Refresh Rate
- Turn off Core Isolation (look up the risks if you dont understand what this is)
- Power Plan Setting to High Performance
- Edit properties of all USB Hubs in Device Manager and disable "Allow the computer to turn off this device to save power"
- In Virus & Threat protection settings: Add a scan exclusion to the Oculus folder
    - You probably dont need to do this, its a security risk, but maybe it helps?

**Oculus App**

- For the Quest3 Headset: 72hz refresh rate, resolution manual and maxed out to the right.
- Make sure Oculus is set as the OpenXR runtime
	- Settings -> General - > OpenXR Runtime- > Set Meta Quest Link as active runtime. If its disabled then its already set.

**Oculus Debug Tool**

![Screenshot 2024-02-17 103708](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/ea596cda-31d3-4b51-9989-76247bc15c25)
- Located in your oculus install directory: Oculus\Support\oculus-diagnostics
- Make a desktop shortcut for easy access.
- In the top toolbar click on "Service" and "Toggle Console Window Visibility" so it shows the window
  - Not sure if you still need to do this, but this was an old fix to windows 11 borking the process scheduling
- These are my settings, YMMV
- You could probably put the Dynamic Bitrate Max higher, but 200 seems fine to me.

**Oculus Tray Tool**

![Screenshot 2024-02-17 104121](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/f59aa321-5826-4ff1-b4fc-eb2382a71bb4)
![Screenshot 2024-02-17 104502](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/67af9e19-8949-4cbc-b3a7-7affcd12cf64)


- Find online and download

- Everything else is default.

- Main thing here is that you can change your FOV to reduce the render to what your eyes see when the headset is on, and that depends on your IPD so just figure out what works for you.

	- I use 0.95 (horizontal) and 0.85 (Vertical)

- Also, when you change the ASW mode it changes it on the fly, so play around with 45hz (on) or Off (no ASW) while in the sim. Auto mode is supposed to do this automatically based on framerate, but I just choose 45hz or off.

**OpenXR Toolkit Companion App**

![Screenshot 2024-02-17 121150](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/6bfa658d-2606-4269-9ed2-04787d795b4b)

- Find it online and download

- Make sure it's not disabled

**NVIDIA GeForce Experience App**

- Turn off the Nvidia Game Overlay

**Nvidia Profile Inspector**

- Download Nvidia Profile Inspector

- This could screw up your other games or flatscreen experiences, so make a backup!

- In the top toolbar, click "Export user defined profiles" and check the boxes for the base profile and Microsoft Flight Simulator. Hold on to this file somewhere to revert incase anything gets weird. You can also revert everything to nvidia defaults through the app if things really go wrong.

- You can find my profile settings on this github page by looking at the repo files

- Download the VR Good Performance.nip file and import it within the Nvidia Profile Inspector (top toolbar -> Import Profiles...)
	- It's on this github page but if you are struggling to find it you can click [here](http://https://github.com/ezekiel24r/NvidiaProfileStore/blob/56490abf1079c091f9a9cc02bceb43100476ea4f/VR%20Good%20Performance.nip "here")

- This configures a DLSS 0.8 render scale, which greatly increases the quality of DLSS. At the same time though it will make all DLSS settings look pretty much the same so you wont get the huge FPS increase that performance and high performance settings would give you at the loss of quality.

- Another thing to note is that Texture Filtering LOD Bias (DX) is set to -2.5, which is a personal preference on quality for me.

- Also this enables resizable bar for MSFS, not sure if it changes much though.

- Make sure to click Apply Changes at the top right when viewing the Base profile, and also click it again when viewing the Microsoft Flight Simulator profile. The app is finicky so just check that it saves after rebooting the PC.

- Reboot your PC and check that changes listed above were applied (0.8 render scale, rbar enabled, LOD bias -2.5)

- **Future Nvidia Driver updates will probably revert these settings automatically, so check your profile settings after a driver update if the performance isnt to your liking.**

**Microsoft Flight Simulator Settings**

- opt into the SU15 beta on steam

	- **PC (Flatscreen) settings**
![Screenshot 2024-02-17 112909](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/9e58b754-ec45-4e98-8999-977737016db4)
![Screenshot 2024-02-17 113152](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/f2258548-5846-42e6-8a0a-f1db764c79a2)
![Screenshot 2024-02-17 113230](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/4c2474ba-87f7-40aa-ba9a-766e07a0f390)
		- Just posting this for reference. I don't think any of these settings matter except:
  			- Texture Resolution set to the same as your VR setting, in this case, Medium.
     			- DLSS set to High Performance. Seems to help when switching between flatscreen and VR.
    
		- Restart MSFS to actually get that texture setting to change.

	- **VR Settings**
![Screenshot 2024-02-17 114748](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/8d641df5-f36f-4ec8-8f86-6255756eb3f0)
![Screenshot 2024-02-17 113900](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/1f728a55-3907-4215-8501-ee7c72ea1f33)
		- I know, there are alot of things on Low, but honestly you can't see things that far away in VR anyway.
			- I've since upped my Buldings and Trees to Medium and increased the LOD sliders slightly, similar performance and looks great.
   			- I have also found that volumentric clouds on high or ultra is ok for my PC in non congested areas, in congested areas I'm not able to do that.
		- Having your Rolling Cache working properly and flying in a location you've flown before is a huge performance increase.

		- Reduce Traffic settings to 0 or very low values. Multiplayer off.

			- You could try these out with VR, I just haven't yet.

		- Under Experimental, turn on Low Power Mode

			- Hides the 3D hanger and plane in the main menu when starting MSFS.

**TAA vs DLSS**

- With all the settings described TAA will produce better readability for glass instruments, while DLSS will have a slight blur that can make glass instruments hard to read when you are sitting far away from them (like in an airliner). If your not reading glass however, DLSS is the way to go. Switch between them on the fly for what you want.

**OpenXR Toolkit Settings**

![Screenshot 2024-02-17 123156](https://github.com/ezekiel24r/NvidiaProfileStore/assets/11917879/4a23b922-788c-4187-96a6-c85b569666fe)

- Foveated rendering is a must for performance, with TAA you will notice shimmering on cockpit instruments on the edges of your vision, but with DLSS it just becomes a nice blur.

- You'll have to launch MSFS in VR to see the menu in your headset (open with Ctrl+F2)

- Navigate with the hotkeys listed at the bottom of the window

- Expert Settings in the last tab might have to be enabled to see the same settings I have.

- If you have a problem with reading things because you looking closely inward (an eye is looking inward towards your nose), try bumping up the horizontal scale of the foveated rendering or just play around with the inner ring size.

**How to start all the software for a VR session**

- Restart your computer

	- Some of the steps above wont apply till you restart your computer. Also it's a good idea to always restart your computer before starting a VR session, some apps hog VRAM after you have been using the PC for a bit.

- Start Oculus Debug Tool, Oculus Tray Tool, and Oculus App

	- The OVRServer console window should already popup when your computer starts if you made the window "always visible"

- Turn on your headset, plug in link cable to headset, and connect with Quest Link

- Open Microsoft Flight Simulator in Steam

- Once the game fully loads, put your headset on, and hit the hotkey (F12 for me) to enter VR mode

- When you start a flight, you may have to change the ASW mode in the oculus tray tool to off and then to 45hz. You can also try the other settings if you like, but 45hz has produced the most solid performance and visuals for me. Some people really don't like ASW, and are ok with lower fps having it off, but to each their own.

**Caveats**

- 45hz ASW will produce some screen tearing when moving your head quickly, but for me seeing things at the headset's 72hz is worth it.

- There is still a huge difference in performance with where you choose to fly in MSFS. Flying out of my home airport of KCMA is incredible performance, and visually looks stunning. Flying just over the hill by KLAX may push you to reduce your settings.

- Because my profile in Nvidia Profile Inspector fixed DLSS to a 0.8 render scale, the other DLSS settings don't really look any different, because they all go to 0.8 scale. I do seem to notice some difference in fidelity and fps when switching between quality and performance modes, but not as much before this change.

	- Also, this will give you the "Ultra Quality" DLSS setting in MSFS (yay) but really just keep DLSS on "Quality", I can't tell much of a difference and I think it's just worse FPS.

- As mentioned previously, this will probably affect your other games because you are changing the **Global** driver profile for Nvidia. That's why you should make the backup.
- For whatever reason, there can be a weird bug where just your left eye will have this terrible compression/temporal aliasing on it
	- To fix, just change the DLLS mode from Quality to High Performance and then back to Quality.

**Other things to look into**
- I haven't disabled High Precision Event Timer in the windows device manager but I've heard that can help with performance too.
- Encode Resolution Width in the Oculus debug tool might be worth upping, I believe 4032 is the max the Nvidia NVEC encoder allows anyway.

I think that covers everything, I will edit and add to this if I remember anything else I have done that I forgot to write up. Happy flying!

TLDR: It takes a shit ton of setup and research to get MSFS VR to work appropriately on your system.
