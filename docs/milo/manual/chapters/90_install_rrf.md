# Install RRF

!!! tip "Sit Back... and Relax!"
    For those of you who are less software inclined, don't panic! We've done most of the work for you.

    RRF requires you to populate an SD card with a specific file structure and files to go with it. To
    make this easier for you, we have gone ahead and built RRF configuration releases for common hardware specifications that include mainboard and WiFi card firmware, as well as a known-good configuration for your machine.
    If you don't wish to install the pre-made firmware and would rather create your own from scratch, then
    please follow [this tutorial](https://www.youtube.com/watch?v=TAT532vIVzU&t=335s).


*[RRF]: RepRapFirmware


## Prepare your SD Card

You will need a freshly formatted SD card with a capacity of up to 32GB.

If the capacity of the card is 4GB or lower, use the FAT16 format - If the capacity is more than 4GB (up to 32GB) then you will have to use the FAT32 format.

The SD card should also be class 4 or higher.

---

## Download a Configuration Release

First, you'll need to download a zip release for the hardware configuration of your choice from the [RRF-Configs](https://github.com/MillenniumMachines/RRF-Configs/releases) repository. These releases bundle the latest version of RepRapFirmware for your mainboard, the latest WiFi firmware, a known-good configuration and (optionally, available soon) [MillenniumOS](https://github.com/MillenniumMachines/MillenniumOS).

MillenniumOS is an "operations system" for RRF that includes a Fusion 360 post-processor and custom g-code dialect to enable easy work-piece probing, tool changes, tool setting and various other quality-of-life / safety features. If you are new to machining, starting with MillenniumOS should help you focus on creating your tool paths and making your first cuts, without focusing too much on the intricacies of edge finding, tool offset calculations and other things.

The release zip files are named based on the machine hardware specification the configuration was designed for, so if you have a kit with a particular mainboard, click to download the zip file which is named based on the kit manufacturer and mainboard that you have.

If you have a kit that does _not_ conform to any known specification, please open an issue.

The releases with `mos` in the zip file name contain the latest compatible release of MillenniumOS.

![View of GitHub Releases page for RRF Config](../img/install_rrf/install_rrf_step_0.png){: .shadow-dark}

## Extract Configuration Release

Once you have the RRF configuration release downloaded, you need to extract it to the root of your formatted SD card.

Make sure the tool you use to extract the files does not create a subdirectory based on the name of the Zip file. The layout of your SD card should look like the following image:

![View of SD Card Layout after extracting RRF Config](../img/install_rrf/install_rrf_step_1.png){: .shadow-dark}

---

## Board specific setup

Some boards require jumpers to be set to allow mainboard or WiFi updates to be applied. You should check if this applies to you by reading your mainboard documentation.

For example - if you are using the Mellow FLY CDYv3, then you need to add 2 jumpers as shown below to enable on-board WiFi updates.

![View of Fly CDYv3 jumpers required for WiFi flashing](../img/install_rrf/install_rrf_step_2.png){: .shadow-dark}

---

## Initial Setup

At this point, eject the SD card from your computer and insert it into your mainboard.

Power your board either via USB or via PSU and wait. The board will install a new version of RRF, automatically update the WiFi module and then start a WiFi Access Point called `Milo`. The password for this is `millenniummachines`.

!!! note "Please be patient"
    Installing RRF, updating the WiFi module and starting a WiFi AP can take some time. After powering the board on for the first time with the SD card installed, you should leave the board for 5-10 minutes to work. If the `Milo` access point appears then this is a safe indication that the initial update and configuration process is complete, and you are ready to use the machine.

    If the WiFi AP does _not_ appear after 10 minutes, take the SD card back out of the board, plug it back into your computer and check if the `firmware.bin` file in the root of the SD card has been renamed to `FLY.CUR`. If it has _not_, then this indicates the board was not updated properly. Please use our discord or other channels for support.

---

## Accessing Duet Web Control

Once the `Milo` WiFi Access Point is visible, you can connect to it with the following details:

```
SSID:     Milo
Password: millenniummachines
```

Once connected, open a browser and go to [http://192.168.40.1](http://192.168.40.1) - note this is `http` and _not_ `https`.

!!! warning
    Some browsers may try to force you to connect to `https://` by default - you may need to specify the full URL, `http://192.168.40.1` to override this behaviour.

Once connected to Duet Web Control, you should see a screen similar to this. This is the interface that you will use to control your new CNC Mill!

![View of RRFs Duet Web Control interface](../img/install_rrf/install_rrf_step_3.png){: .shadow-dark}

---

## Configure your WiFi network

If you want to connect your Milo to an existing WiFi network rather than using the inbuilt Access Point, you can use the Web Interface to change the machine configuration.

The first step is to tell RRF about your wireless network. Click on the "Console" tab on the left hand side, and type the following into the `Send code...` box, then press ENTER:

```gcode
M587 S"your WiFi SSID" P"your WiFi password"
```

You should see a _green_ highlighted line indicating that the command was successful:

![View of DWC Console window indicating successful WiFi network configuration](../img/install_rrf/install_rrf_step_4.png){: .shadow-dark}

---

You now need to tell RRF to connect as a WiFi client rather than starting its own Access Point. To do this, browse to the "Files -> System" tab, and click on `network.g` to edit the file.

Edit the line that says `M552 S2` so that it says `M552 S1` instead. Click Save in the top right hand corner, and then run `M999` via the console, or power cycle the mainboard to trigger a restart.

Once the board has restarted, it should attempt to connect to your WiFi network.

You may have to use your router interface to identify the address that the Milo has been given on your network - this is outside of the scope of this guide.

You can also [connect to the mainboard over USB](https://teamgloomy.github.io/putty.html) using Putty or another terminal emulator depending on your operating system - watching the output of the terminal when the machine connects to the WiFi network will show the IP address that has been assigned.

---

At this point, the basic firmware setup is complete and all that remains are some firmware checks which will be covered later on in the manual.

!!! warning
    We only provide bundled firmware configurations for specific machine setups. If your machine is self-built, you will have to modify one of these configurations to match the mainboard, wiring and setup of your machine. Alternatively, you can use the [TeamGloomy Configurator](https://teamgloomy.github.io/Configurator) - but remember that this is aimed at 3D printer configurations so will need a number of changes to work effectively on Milo.

It is now safe to perform the physical install of your board into your mainboard mount.

---

[Next Chapter: Assemble Electronics](./100_assemble_electronics.md)