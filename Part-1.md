# Background - Modifying - ROM Libraries and Homebrew Intro

![FinishedProject](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/gb-front.png)
## Table of Contents

- [A Brief Introduction to Game Emulation](#a-brief-introduction-to-game-emulation)
- [Distilled Timeline of Recent Key](#distilled-timeline-of-recent-key-events)
- [Modifying A Game Boy Color](#modifying-a-game-boy-color)
    - [Mod Component List](mod-component-list)
    - [Installs](#installs)
- [Creating and Loading a Library](#)  
- [Enjoying The Results](#enjoying-the-results)
- [Until Part 2](#until-part-2)

## A Brief Introduction to Game Emulation
Game emulation has been around since the 1990s, and allows for playing any game on a host system, as if on the original hardware, as closely as possible. Many game emulators offer additional features such as being able to include cheat codes, create save states, and there are even additional programs that can make modifications (including community made content updates) to a game file. Lastly, emulators make it possible to play homebrew games, which are designed by entusiasts and indie game makers.

To play games on these emulators, you need a digital copy of the original game file, which is typically stored in ROM (read-only memory). ROM files (ROMs) are obtained by using specialized hardware that downloads the data from a game cartridge. For disc-based consoles the process is a little different, but the idea is essentially the exact same.

***I should note here, playing games you've already purchased is perfectly OK...and there's plenty of places online to acquire a digital version of the games that you definitely already own, but may not be able to personally turn into ROMs yourself. I can't list in this write-up sites that you can go to for ROMs, but the internet provides. For the rest of this write-up, I am writing from a perspective of working with games that I already own, or have created myself.***

Anywho, my on-ramp to messing with ROMs was via my search to replay through titles from my childhood like Pokemon Yellow and Tomba, and via the RetroPie project. While I didn't have a working Original Playstation around, I did have a few spare Raspberry Pis on my desk. Making a RetroPie was a rewarding, fun and accessible introduction to working with a digital ROM collection. 

Eventually though, I wanted to take that ROM collection on the go. Through some searching, I found out about newer retro handheld models such as the Analogue Pocket. However, these hand helds are only available in quarterly fulfillment rounds. Through some follow on searching, I discovered Game Boy modding, ROM hacking, and applications such as GBStudio. 

![Analogue-Pocket](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/AnalogPocket.png)
(Image via Analogue, Inc [Twitter](https://twitter.com/analogue/status/1184485001737506820?s=20))


## Distilled Timeline of Recent Key Events

For those interested, here's a speedrun of the historically relevant highlights that set the stage for all the aspects that we'll cover in this write-up. 

- `September 7, 2009` - [krikzz.com](https://web.archive.org/web/20090907011717/https://krikzz.com/) Website opens, selling flashable cartridges for SEGA and N64
- `July 17, 2012` Pimoroni - Online maker goods store is founded, and  releases the famous PiBow case for the Raspberry Pi
    - Paul Beech, co-foudner of Pimoroni, also designed the Raspberry Pi logo, and is the Brand and Design Lead for the Raspberry Pi Foundation
- `July 22, 2012` RetroPie version 1.0 is publised to GitHub
    - `Shell script(s) to setup Raspberry Pi (TM) with RetroArch emulator, various cores, and EmulationStation as graphical front end.`
    - Florian Müller, project creator, also initially releases information and enumerative details on their site [petrockblock.com/retropie/](https://www.petrockblock.com/retropie/)
- `October 30th 2012` Pimoroni puts up the [PiCade Kickstarter](https://www.kickstarter.com/projects/pimoroni/picade-the-arcade-cabinet-kit-for-your-raspberry-p/description), which offered an all in one kit to build a MAME style gaming cabinet
- `October 2012` - Jools Wills, future primary developer of RetroPie backs the Picade project
- `May 25, 2014` - Krikzz releases Gameboy [Everdrive](https://web.archive.org/web/20140525215421/http://krikzz.com/index.php?route=product/product&product_id=60)
- `June 2014` Jools Wills receives his PiCade
- `July 2014`, begins making contributions to the RetroPie project in pursuit of added and improved functionality
    - Since then, and to do date, has made 3,915 commits to the project 
    - RetroPie project gains popularity due to the ready-made OS image that is ready to load ROMs into out of the box, and only requires a display connection and a controller to play. 
- `August 3, 2014` - [Hand Held Legend](https://web.archive.org/web/20140804002928/https://handheldlegend.com/) Online store opens selling parts for modifying existing Game Boy* devices. (Still open today)
- `2016` [Retro Modding®](https://www.retromodding.com/) merges with Canadian Game Boy modding pioneers ASM, creating another online developer and distributor for hand held console parts
- `October 2016` Nintendo Switch is announced
- `March 3, 2017` Nintendo relases the Nintendo Switch
- `Aug 7, 2018` - [ezflashomega.com](https://web.archive.org/web/20190129031727/https://www.ezflashomega.com/) Website opens, selling EZ Flash omega carts for Game Boy, Gameboy Color, Gameboy Advance Advance, 3DS. 
- `Aug 2018`, Nintendo continues it's lawusits of ROM providing websites LoveROMS and LoveRETRO, as well as actions against EmuParadise - who removed all their content.
    - Nintendo claims it is illegal to download ROMs, even if it is the person who owns the original game
        - States that ROMs are not authentic games
        - Also claims illegally copied Nintendo software hurts Nintendo's goodwil
    - Fans feel that their actions caused little financial harm, and that they were helping to preserve games that would otherwise have faded into time.
        - Once games had left retailers' shelves, people had limited options to purchase them. The quality of those found in second-hand shops varied, and rare or lesser-known games were impossible to find.
-  `September 18, 2018` Nintendo releases Nintendo Switch Online
    - During its first year, the Online service provided a new batch of NES games on a monthly basis, with the addition of SNES titles in September 2019
    - Eventually stated that new NES and SNES games would no longer be made available on a regular schedule, though they would continue to expand both libraries over time
    - Games are accessible as long as the user has an active subscription, and a user must connect to the internet at least once a week to continue to access games while offline.
 - `October 16, 2019` Analogue, Inc. announces [Analogue Pocket](https://www.analogue.co/pocket), a polished modernized retro hand held console designed to play Game Boy, Game Boy Color, and Game Boy Advance cartridges out of the box.
- `June 7, 2020` - [RetroGame Repair Shop](https://web.archive.org/web/20200607150142/https://retrogamerepairshop.com/) Online store opens, selling parts for modifying existing Game Boy* devices (Still open today)
- `2021` [Incube8 Games](https://incube8games.com/) is founded by Retro Modding®, offering turnkey game publishing solutions for physical releases
- `December 13, 2021` Analogue, Inc. releases Analogue Pocket
    - $220 for the base console; you purchase and await delivery in fulfillment groups, which has been victim to supply chain issues as well as incredible demand. 

## Modifying A Game Boy Color
With the background covered, that finally brings us to modding the hand held. Below is a parts list of everything I picked up. You might not care about replacement labels or swapping your buttons or membranes. I would say at a minimum though, a screen upgrade (and compatable shell) is the must-have from the below list. The flash cartridges and screen will run right through the charge on your standard batteries, but you don't have to upgrade those to dive into playing. 

![parts]https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/parts.png)

### Mod Component List
- [FunnyPlaying Game Boy Color 2.0 Q5 IPS Laminated Backlight Kit](https://retrogamerepairshop.com/collections/gbc-displays/products/funnyplaying-game-boy-color-2-0-q5-ips-laminated-backlight-kit)
    - [Install Video](https://www.youtube.com/watch?v=9KcYyHwXQTU)
- [FunnyPlaying Clear Game Boy Color & Pocket Speaker](https://retrogamerepairshop.com/collections/gbc-audio/products/funnyplaying-clear-game-boy-color-speaker?variant=37728953761964)
- [FunnyPlaying Game Boy Color 2.0 Laminated Q5 IPS Ready Shell](https://retrogamerepairshop.com/collections/gbc-shells/products/funnyplaying-game-boy-color-game-q5-ips-ready-shell?variant=39875585474732)
- [FunnyPlaying Game Boy Color Custom Buttons](https://retrogamerepairshop.com/collections/gbc-buttons/products/funnyplaying-game-boy-color-custom-buttons?variant=39932482322604)
- [FunnyPlaying Game Boy Color Silicone Button Contact Pad Membranes](https://retrogamerepairshop.com/collections/gbc-buttons/products/funnyplaying-game-boy-color-silicone-button-contact-pad-membranes?variant=41734981746860)
- [Replacement Game Boy Color OEM Style Labels](https://retrogamerepairshop.com/collections/gbc-stickers)
- [Replacement Game Cartridge Labels](https://www.etsy.com/listing/682144871/gameboy-labels-yellow-pikachu-version?ga_order=most_relevant&ga_search_type=all&ga_view_type=gallery&ga_search_query=gameboy+replacement+labels&ref=sr_gallery-1-3&frs=1&bes=1&organic_search_click=1&variation0=2496060386)
    - I opted for the Metallic Foil versions
- [Game Boy Color USB-C Charging Kit Pro](https://retrogamerepairshop.com/collections/gbc-power/products/game-boy-color-usb-c-charging-kit-pro?variant=41963211391148)
    - Li-Ion battery charger via USB-C with protection for charging level and over discharge.
    - DC-DC converter
    - Audio amplifier for speaker with potentiometer (VR1) to set max volume.
    - Integrated LED indicators for charging battery (red) and full battery (green)
    - External LED indicators board for playing (white), charging battery (red) and full battery (green).
- [1500mAh LiPo Battery Cell](https://retrogamerepairshop.com/collections/gbc-power/products/103048-1500mah-lipo-battery-cell?variant=40148868792492)
- [Jayro's GAMEBOY™ Test Cartridge](https://jayrojones.itch.io/test-cart)
    - This is helpful for testing obviously, but not required
- [Gameboy Color Stand](https://www.etsy.com/listing/894019441/nintendo-game-boy-color-acrylic-handheld?ga_order=most_relevant&ga_search_type=all&ga_view_type=gallery&ga_search_query=gameboy+stand&ref=sr_gallery-1-6&sts=1&organic_search_click=1)
- [Everdrive-GB X7](https://krikzz.com/our-products/cartridges/edgbx7.html)
    - This also requires a MicroSD card. I went with a class 10 SanDisk 64GB MicoSD

---

### Installs

#### USB-C Charging Kit:

This kit was designed by GitHub user [giltesa](https://github.com/giltesa/Game-Boy-Color-USB-C-Charging-Kit-Pro). This modification will give us the following additional features:

> - `Li-ion battery charger chip TP5000`: Switching buck single lithium battery charge management chip. Its QFN16 ultra-compact package making the TP5000 is ideal for portable equipment large current charging management applications. Meanwhile, TP5000 built-in input overcurrent, undervoltage protection, over temperature protection, short circuit protection, battery temperature monitoring, reverse battery protection.
> - `Boost Converter chip MT3540`: Constant frequency, 5-pin SOT23 current mode step-up converter intended for small, low power applications. The MT3540 switches at 1.2MHz and allows the use of tiny, low cost capacitors and inductors 2mm or less in height. Internal soft-start results in small inrush current and extends battery life.
> - `Audio Amplifier chip PAM8302A`: 2.5W Class-D mono audio amplifier. Its low THD+N feature offers high quality sound reproduction. The new filterless architecture allows the device to drive speakers directly instead of using low-pass output filters, therefore saving system cost and PCB area
> - `External LED indicators board`: Playing (white), charging battery (red) and full battery (green)
> - `Battery Test`: 1500 mAh = 8h 40m

I have a couple helpful tips that I will add in along the way, so be sure to read a couple steps ahead before soldering. 

Helpful tools though for this portion include:
- [PCBite stands](https://sensepeek.com/pcbite)
- [ChipQuik](https://www.amazon.com/SMD-Chip-Removal-Alloy-REMKIT/dp/B08KJKHCJK)
- [No Clean Flux Pen](https://www.amazon.com/MG-Chemicals-Clean-Flux-Pen)
- Some sort of finer tip on your soldering iron
- 90% Isopropyl Alcohol 
- Lint-free cotton swabs

Overall this kit was a great install experience delivered in a really attractive form factor. I really like how polished the kit looks inside the case as an addition the original hardware, and since I went with a clear shell body, wire management was  going to be a top priority for me. The first step to installing this kit, or any modifications for that matter, is to access the PCB by removing the plastic shell housing. 

1. Removing the game shell is accomplished by removing 6 screws around the perimeter of the Game Boy on the back half (4 outside and two inside under the battery compartment).

1. Next, the screen ribbon neds to be diconnected from the PCB at the top of the device, which will allow the rest of the internals to be removed from the system. I would recommend an electronics pry kit if you don't have one (right tools for the job will make all the difference in this project). 

1. Once disconnected, there are three additional tri-wing ( `Y` shape ) screws that will need to be removed that secure the PCB to the front housing. These will also require a specific screwdriver bit, but they commonly come in bit sets and electronic tool kits.

1. At this point you should be able to gently remove the PCB from the front housing. Keep in mind, the buttons and membranes are held in place only via the PCB, so if you flip the system over and try to remove the PCB by dumping it in your hand, you will drop all those parts.

1. You should take the opportunity to clean and inspect the PCB for any wear and tear. Removing any impurities will make sure that removing components from the bord easier. 90% isopropyl alcohol and lint free cleaning swabs will easily be all you need for this and the rest of clean up for the project. 

    ![PCB-Removed-Front](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/OG-PCB-front.png)
    ![PCB-Removed-Front](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/OG-PCB-back.png)

1. Per the install guide [here](https://cdn.shopify.com/s/files/1/0266/1862/6122/files/GBC_PRO_-_Quick_Guide.pdf?v=1661886837) there's quite a few components that need to be removed from the PCB to accomodate the install of the new USB-C Charging Kit, including the DC-DC Converter board (the green board in the bottom left corner of the main PCB). Also, depending on the board version, the install instuctions vary a little. Luckily, my board was a v4, so I was able to install without needing t0 follow any alternative instructions. This specific board (v4) has the following [specs](https://wiki.console5.com/wiki/Game_Boy_Color#:~:text=X1%3A%20Oscillator%3A%C2%A0%3F%3F%3F-,CGB%2DCPU%2D04,-U1%3A%20CPU%3A):

    ```
    U1: CPU: CPU CGB C
    U2: SRAM: LH52256CVT
    U3: Audio Amp: AMP MGB IR3R56N
    U4: CGB-REG (IR3E06N)
    X1: Oscillator: KDS 8.388Mhz
    ```
    And utilizes the following schematic:
![GBC-Schematic](https://wiki.console5.com/tw/images/e/e6/Nintendo_GBC_Schematic.png)

    This required that I remove the following components (with help from a symbols reference [chart](https://www.electronics-tutorials.ws/resources/basic-schematic-symbols.html)):

    ```
    - SP    -   The speaker connections
    - C3    -   Battery terminal pieces
    - C30   -   DC - DC -> Fixed Value Capacitorv -> Chassis Ground
    - D2    -   Semiconductor Diode -> Chassis Ground
    - Q2E   -   Power LED Indicator
    - D4    -   Power LED Indicator
    - EM6   -   Resistor
    - EM7   -   Resistor
    - EM10  -   Iron-core Transformer - DC Power Jack 
    - F2    -   AC Voltage Source
    - P4    -   DC Jack
    ```
    Removing the components was rather straightforward, as in any type of desoldering. However, removing the smaller components was made easier through use of a flux pen and some chipquik, along with applying fresh solder in some instances. By adding rosin and additional solder, I was able to create and maintain a larger consistent area of thermal mass, sliding the SMD components away from and off their pads. I utilized a wick to clean up excess solder before cleaning the board up with ISO. Keeping the board as clean as possible (mainly of Flux) helps prevent the project from turning into sticky mess everywhere. Flux tends to be like electrical glitter in that regard. 

1. Once all the required components are removed, the install of the kit was fairly easy. I had never secured PCB components without some sort of board-to-board interconnects or diode legs, so that was a bit of a challenge. I had to wind up reflowing the connections on the pads to guarantee a steady stable connection, but as I said earlier being clean and detail oriented really helped.
    - TIP 1: I would have added stem posts clipped from LEDs as through hole legs before trying to flow solder through from the main PCB to the USB-C charger daughterboard. 
    - TIP 2: Tinning the pads and wire ends prior to reheating them to connect them really helped keep the process clean and precise as well
    - TIP 3: The instructions say to test the board prior to installing it, and you should absolutley do that. Just making another point to call that out here.

1. After checking all my solder joints, I also installed the new speaker, which connects by two pads in the same spot as the original ones.
    - This speaker specifically contributes:
    > "Stronger magnetic force and thinner diaphragm which provides greater sound"

1. Next came the LED status light and board. The trickiest part of this install was making sure the holes lined up. After removing the old components, I cleaned out any remaining solder, cleaned the area, and then tinned the holes with solder as well as the wire ends. I lined up the right, round side of the board with the outline on the PCB, and then secured it with [Kapton tape](https://www.amazon.com/ELEGOO-Polyimide-Temperature-Resistant-Multi-Sized/dp/B072Z92QZ2/) before flowing the solder from the back of the PCB. After this, I soldered the 4 wires (3 to the LED status board and one to the audio amplifier(green)) in the order they specify in the install guide, again, tinning the pads prior to reheating to connect them.

    ![Internals-Finished](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/LED-Status-Board.png)
    (Finished LED indicator install from the rear of the main PCB) 
    
    I personally opted to route wires as compact yet tucked away as possible. As I said earlier, I opted for a clear shell, and I really wanted to keep things as tidy and organized as possible. The biggest areas you want to pay attention to though are the green wire, which can get snagged under the cartridge when switching games if not secured, and the 3 wires that run the side of the board. The group of 3 wires can prevent the case from closing all the way if not properly cable managed when being run on the side of the console.

    ![Internals-Finished](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/internals-finished.png)

---
#### FunnyPlaying IPS Screen Kit

1. Installing the new screen is the other big half of this project. Luckily, I purchased an updated version of the IPS screen, and was able to avoid most soldering that the older versions still require, aside from two wires that allow access the `START` and `SELECT` buttons, as well as one wire for `PWR`. Notably, I opted for using the alternate pin locations which are shown below. 

    ![Alternate-Pins](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/alternate-pins.png)

    I also took the opportunity to trim the cartridge connection pins to be flat agains the PCB. These pins are the double rows under the PCB version screen printing, where the white and green portions of the main PCB join. The image above is from the `Retro Game Repair Shop` site, and references their V1 install, but the pins work the same. The alternate locations are not seen later as they are hidden by the screen, where the lower orginial locations would still be visible. Clear shell being used so I opted to hide them.
    
    The screen kit install instructions also mentionseverywhere to test the sxreen before you do the complete install.

    > Test the kit before installation! Once the display is mounted it cannot always be safely removed. We ask that you test the kit by hooking it up before removing the screen protector and before fully mounting the display.

    So of course, test the screen is what I did:

    ![ScreenTest](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/screen-test.png)

    The absolute best resource I found in this whole customization process was a series of YouTube videos by [@makho](https://www.youtube.com/@makho/featured), of which their [screen install](https://www.youtube.com/watch?v=o9NvRFPqGLI) video was immensely helpful. Twitter: [@makhowastaken](https://twitter.com/makhowastaken). The install instructions that come with the screen and the video are more than enough to get your screen installed. 
        
    - TIP 4: Always be mindful of your hand placement once the display is installed, as you will be tempted to put pressure or select force on areas of the screen and case while trying to snuggly fit things, and you don't want to tweak and break the display. Most issues I read about online of people breaking their screens came from flexing the screens in some manner while reattaching the ribbon cable, installing the screen, assembling the shell, etc. 
    
    The last bit of housekeeping to do was add Kapton tape to the back of the PCB, over the cartridge pins, and also over the screen ribbon. This is more precautionary than anything, and you can't see any of it in the final assembly, but I like to air on the side of caution. I also added in the buttons, membranes, and turned over the PCB back into the case front, tucking the additional wires down into the side of the case. 
    
    The kit advises that you set the potentiometer on the USB-Charging kit daughterboard to 50%. This is accomplished by rotating the metal top portion of the variable resistor listed in the install guide. I think I settled on half a turn clockwise if I recall. The instructions don't state how to adjust this setting as part of `Step 4`, so hopefully this saves you some searching. A pair of hobbyist tweezers made quick work of it.

    ![Final-Solder](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/final-solder.png)

1. Before reassembling the case, I had to modify the case bottom to be able to close flush. The USB-C port needed an opening cut, as well as the battery housing needed trimmed down, as the USB-C Charging board components prevent the bottom from closing all the way. I made some light markings with an expo marker to indicate the USB-C port opening, which marked what areas to remove. 

    To make the cuts, I used a culinary butane torch to heat up a hobbyist/xacto knife, which cuts through plastic very smoothly and quickly. This is a common practice in the designer toy world, but remember as always to wear your PPE and work in a ventilated area. The knife cools quickly, so it takes several rounds of heating and cutting. I thought that this was the cleaner and less stressful on the case than using something like a Dremel tool would have been. 
    
    I also used a hobbyist (nail) file and model sheet snips from a Gunpla kit to cut and trim the back of the battery compartment down before using the nail file to smooth and slightly buff all of the areas that were cut. This removed any stray plastic bits and made the case modification look more like it was meant to be that way. I finished the cuts by then cleaning with ISO and drying the areas before re-assembling.

    Of note, the underside of the battery compartment (first picture below) is not even visible once the system is assembled again, as it is hidden behind the battery and battery cover.
    
    ![USB-battery](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/case-mod-USB-port.png)
    
    - TIP 5: Giltsea has since released a [Shell Trimming Tool](https://github.com/giltesa/Game-Boy-Color-USB-C-Charging-Kit-Pro/tree/master/3.%20Documentation/Cutting%20Tool) that acts as a guide for trimming out a perfect looking USB-C hole!

    - Tip 6: I packed a small piece of non conductive foam under the battery-pack once connected to keep it from rattling around in the battery compartment.
    
    ![USB-bottom](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/case-mod-battery-housing.png)

1. With the sreen installed and the PCB secured back in and connected, along with the buttons and membranes, the last bit left was to reassemble the case. I cannot stress enough how SLOW you need to go when re-assembling the back portion of the case. hand tightening 12-14 rotations for the case screws was what I went with to make sure the case was snug but not stretching the plastic screw posts.

    ![gb-front](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/gb-front.png)
    ![gb-back](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/gb-back.png)

1. About the Cartridges: 
    
    Firstly, the below is a close-up picture of the awesome metallic foil replacement labels from the Etsy shop [JandMsalesforce](https://www.etsy.com/shop/JandMsalesforce). I know replacing the labels is controversial, but the Pokemon Blue copy that I had was showing a lot of smearing and wear. Since I was going to wind up replacing one, I opted to replace them all as a set, and replaced the labels on the other original cart cases too. The other two games are shown in the photo at the top of this write-up. 

    ![labels](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/cart-label-replacements.png)
    
    Secondly, I took this time to open the carts up and clean and inspect them for any wear, which is common around the pins on the bottom of the PCB. This is also a common place for corrosion to build up, all of which looks a bit like a uniform patterned line across where the plastic meets the pin traces. [TronicsFix on YouTube](https://www.youtube.com/watch?v=xYUW0uVBp0k) had a really informative walk through on restoring a collection of broken Game Boy games that they had purchased online. They walk through most of the common scenarios and really offer a lot of great info. The screenshot below showing the corrosion line mentioned earlier is from their video. 

    ![TronicsFix](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/tronicsfix.png)

## Creating and Loading a Library

The Game Boy Color works better than ever, and the games themselves all work. The only task left is to transfer ROMs over to the Everdrive and configure that. For starters, the Everdrive requires a [firmware download](https://krikzz.com/pub/support/). 

I downloaded the firmware and grabbed a new 64GB MicoSD card, formatted it to FAT32, and moved the firmware folder over (`/GBCSYS`). I then ejected the card, reinserted it into the Everdrive, and plugged the Everdrive into the Game Boy and turned it on. The screenwill flash a prompt of `OS Loading...OS Init...` and then show a warning about how the settings have been reset (normal - just hit any button to proceeed). At this point I powered down the device and removed the microSD card, as everything was working as expected and it was time to load my ROM collection onto the cartridge (microSD card). I will cover how to read (download) games from game cartridges and other aspects in Part 2 of this write-up, which will be posted at a later time once I finish it.
    
![everdrive-internals](https://github.com/AndyDoering/Retro-2023/blob/main/Images/post/everdrive-internals.png)
(Everdrive-GB X7 internals)

Loading ROMs onto the card was as simple as plugging the microSD card back into my machine and creating folders of my choosing at the top of the directory structure (leave `/GBCSYS` alone for now). The setup process  for teh Everdrive when plugged into the GBC for the first time creates a few folders and files additionally under the `/GBCSYS` folder, but you can structure your folders outside of that to whatever suits your organizational style. I went with:

```bash
/GBCSYS
    |-/Cheats           # Auto created at setup
    |-GBCOS.bin
    |-REGISTRY.bin      # Auto created at setup
    |-/Save             # Auto created at setup
    |-/Snap             # Auto created at setup
/OEM
    |- Any originally released game titles
/Homebrew
    | Community made game titles
/Rom Hacks
    | Patched Games
    | Translated Games
    | Other patched files
/GameDev
    | Games I am working on and testing
```

There are additional settings and configuration options that you can go through, and are best described in [RetroBreak's YouTube video](https://krikzz.com/our-products/cartridges/edgbx7.html) guide. I didn't wind up adding ROM 'hacks', modifications, or game cheat codes, but the options are there and very easy to get to.

Speaking of, there's now a button on the top of the Everdrive that when pressed, will bring up a menu to access the home screen, as well as save states and game cheat codes. Lastly, a full breakout of the features of this drive are listed below:

- Features (excerpted from vendor)

    ```
    - Max ROM size: 8MByte
    - Max SAVE RAM size: 128KByte
    - Save States function and In-Game menu function
    - Isolated RTC function. 
        - Isolated" means that multiple games can use RTC without - interference.
        - Each game will have own copy of time
    - Instant loading
    - Low power consumption
    - High quality 4-layers PCB
    - Hard gold plating for cartridge contacts
    - GameGenie cheat codes
    - Soft reset to menu
    - Supported mappers: MBC1, MBC2, MBC3, MBC5
    - Micro SD cards are supported.
    - Compatible with all systems which supports GB and GBC cartridges (including Super Game Boy)
    - OS supports up to 1000 files per folder
    - PCB Rev.B (Fixed compatibility problems with Game Boy pocket)
    ```

## Enjoying The Results

To end the first part of this write-up, I wanted to briefly touch on homebrew game content. This was probably the biggest inspiration point for me to do this project. I found `itch.io` through discovery of GBStudio, and through both of those sites, discovered the world of homebrew game content.

> Itch.io is an open marketplace for independent digital creators with a focus on independent video games. It’s a platform that enables anyone to sell the content they've created. 

> GB Studio began as number of disconnected scripts and tools which were eventually used to create Chris Maltby's `Untitled GB Game`, a game built in one week for `Bored Pixels 3` (game jam on itch.io)

Homebrew games are those produced by hobbyists and indie game devleopers alike, and are often shared on sites like Itch.Io or sold through publishers like [Incub8 Games](https://incube8games.com/). These can rage from pay-what-you-can up to $100 or so for collector editions which come with printed game manuals, box art, digital game art (for emulation menus) and extra swag goodies like clothing, OSTs, etc. 

A game jam is a game development competition where competitors make a game from scratch over the course of 12 hours to a couple weeks. These games are created in line with the theme for that given game jam. 
- `Bored Pixels 3` lasted a week. 
- `Untitled GB Game` won the `EYE PLEASER` award for that game jam!

While I won't be participating in any game jams in the near future, I have been buying and playing a bunch of these like crazy to learn what the realm of possible looks like with GBStudio. 

## Until Part 2

This would be a reasonable point to stop and enjoy all the hard work that led to the finished console, however, I like to vertically integrate my hobbies. The natural next step for me is to explore making my own games.

The ability to experience other people's creations, and to try and make and share my own, really sold me on doing this project from the beginning. That makes for a nice seque into Part 2 of this write-up, which will focus on the design theory, art direction, and development of a Game Boy Color game! 

I'll be publishing details and updates for Part 2 to this repo as I work thorugh the process. For now though, thanks so much for reading! 

I hope you've found something you enjoyed, something you've learned, and something you can share with others!








